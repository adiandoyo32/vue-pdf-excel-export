<template>
    <div class="home">
        <img alt="Vue logo" src="../assets/logo.png" />
        <HelloWorld msg="Welcome to Your Vue.js App" />

        <table ref="table">
            <thead>
                <tr>
                    <th rowspan="2" class="text-center">Tanggal</th>
                    <th rowspan="2" class="text-center">No. Bukti</th>
                    <th>Supplier</th>
                    <th colspan="2" class="text-right">Bruto</th>
                    <th class="text-right">Disc</th>
                    <th class="text-right">PPN</th>
                    <th rowspan="2" class="text-right">Netto</th>
                </tr>
                <tr>
                    <th>Nama Barang</th>
                    <th class="text-center">Kuantitas</th>
                    <th class="text-right">Harga</th>
                    <th class="text-right">Disc. Item</th>
                    <th class="text-center">Panjang</th>
                </tr>
            </thead>
            <tbody ref="body">
                <tr>
                    <td rowspan="2">2021-09-20</td>
                    <td rowspan="2">112112</td>
                    <td>Amin</td>
                    <td colspan="2" data-type="asd">40.000,002</td>
                    <td>0</td>
                    <td>4,000</td>
                    <td rowspan="2">4.0000</td>
                </tr>
                <tr>
                    <td>coil</td>
                    <td>4</td>
                    <td>10.000</td>
                    <td>0</td>
                    <td>0</td>
                </tr>
            </tbody>
        </table>

        <button type="button" v-on:click="onexport">Excel download</button>
    </div>
</template>

<script>
// @ is an alias to /src
import XLSX from "xlsx";
import HelloWorld from "@/components/HelloWorld.vue";

export default {
    name: "Home",
    components: {
        HelloWorld,
    },
    data: () => ({}),
    methods: {
        onexport() {
            var table = this.$refs.table;
            this.$refs.body.children.forEach((element) => {
                element.children.forEach((child, index) => {
                    if (child.dataset.type) {
                        console.log(child, child.dataset.type);
                        // var number = parseFloat(child.innerHTML);
                        child.innerHTML = child.innerHTML.replace(/\./g, ',').replace(/\,/g, '.')
                    }
                    // console.log(parseFloat(child.innerHTML))
                    // console.log(child)
                });
            });
            // console.log(this.$refs.body.children[0].children[0].innerHTML = 'asd')
            // table.innerHTML = "aasdasd"
            // var wb = XLSX.utils.table_to_book(table);

            //  XLSX.writeFile(wb, 'book.xlsx')
        },
    },
};
</script>

<style scoped>
table {
    border: 1px solid black;
}

table th,
table td {
    border: 1px solid black;
}
</style>
