<script setup lang="ts">
import DataTable from "datatables.net-vue3";
import DataTablesLib from "datatables.net";
import jsZip from "jszip";
import pdfMake from "pdfmake/build/pdfmake";
import pdfFonts from "pdfmake/build/vfs_fonts";
import "datatables.net-select";
import "datatables.net-buttons";
import "datatables.net-buttons/js/buttons.html5";
import "datatables.net-buttons/js/buttons.print";
import "datatables.net-buttons/js/buttons.flash";
import "datatables.net-buttons/js/dataTables.buttons";
import "datatables.net-buttons/js/buttons.colVis";

DataTable.use(DataTablesLib);
pdfMake.vfs = pdfFonts.pdfMake.vfs;
window.JSZip = jsZip;

const columns = [
  { data: "name" },
  { data: "position" },
  { data: "office" },
  { data: "extn" },
  { data: "start_date" },
  { data: "salary" },
];

const options = {
  dom: "Bfrtip",
  select: true,
  buttons: ["csv", "copy", "print", "flash", "pdf", "excel"],
};
</script>

<template>
  <div>
    <h1>DataTables extensions</h1>
    <h2>DataTables + Vue3 example</h2>
    <p>
      This example demonstrates how DataTables' extensions can be used with
      Vue3. The key is to import and then register them with the
      <code>DataTable.use()</code> method. They can then be used as a regular
      DataTable extension. In this example I demonstrate Select and Buttons
      being loaded in.
    </p>

    <DataTable
      id="example"
      :columns="columns"
      :options="options"
      ajax="/data.json"
      class="display"
      width="100%"
    >
      <thead>
        <tr>
          <th>Name</th>
          <th>Position</th>
          <th>Office</th>
          <th>Extn.</th>
          <th>Start date</th>
          <th>Salary</th>
        </tr>
      </thead>
      <tfoot>
        <tr>
          <th>Name</th>
          <th>Position</th>
          <th>Office</th>
          <th>Extn.</th>
          <th>Start date</th>
          <th>Salary</th>
        </tr>
      </tfoot>
    </DataTable>
  </div>
</template>

<style>
@import "datatables.net-dt";
@import "datatables.net-buttons-dt";
@import "datatables.net-select-dt";
</style>
