<template>
  <div class="q-pa-lg home">
    <div class="row">
      <div class="col"><q-input v-model="ipaddress" label="IP address" /></div>
      <div class="col">
        <q-btn
          color="secondary"
          label="Get AWS IP address ranges"
          @click="findRange()"
        />
      </div>
    </div>
    <br />
    <div class="row">
      <div class="col">
        <q-table
          title="IP Address ranges"
          :data="result"
          row-key="name"
          :pagination.sync="pagination"
        />
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import { Netmask } from 'netmask'

export default {
  name: "Home",
  components: {},
  data: function () {
    return {
      ipaddress: "3.10.127.32",
      result: [],
      allIPranges: {},
      pagination: {
        rowsPerPage: 30, // current rows per page being displayed
      },
    };
  },
  methods: {
    findRange() {
      this.result = []

      var iprangesURL = "https://ip-ranges.amazonaws.com/ip-ranges.json";

      axios.get(iprangesURL).then((res) => {
        var allIPranges = res.data.prefixes;

        for (var i = 0; i < allIPranges.length; i++) {
          const block = new Netmask(allIPranges[i].ip_prefix)
          if (block.contains(this.ipaddress)) {
            this.result.push(allIPranges[i])
          }
        }
      });

    },
  },
};
</script>
