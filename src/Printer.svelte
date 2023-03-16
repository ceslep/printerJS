<script>
  import printJS from "print-js";
  //--kiosk-printing
  let datos = [
    {
      item: "Arroz Blanco",
      precio: 2500,
    },
    { item: "Aceite", precio: 12500 },
    { item: "Sardina", precio: 7500 },
  ];

  let imprimiendo = false;

  const imprimir = () => {
    /*  printJS({
      printable: datos,
      type: "json",
      properties: ["item", "precio"],
      header: "Prueba de Impresion",
      headerStyle: "font-weight: 300;color:blue;",
      documentTitle: "",
      maxWidth:300
    }); */
    printJS({
      printable: "table",
      type: "html",
     /*  header: "Prueba de Impresion",
      headerStyle: "font-weight: 300;color:blue;", */
      documentTitle: "",
      maxWidth:300,
      css:"./printer.css"
    });
  };
</script>

<button class="btn btn-primary" on:click={imprimir}> Imprimir </button>

<table class="table table-bordered table-sm" id="table">
  <thead>
    <th>N°</th>
    <th>Item</th>
    <th>Valor</th>
  </thead>
  <tbody>
    {#each datos as {item,precio}, index}
      <tr>
        <td>{index + 1}</td>
        <td>{item}</td>
        <td class="text-end">{precio}</td>
      </tr>
    {/each}
  </tbody>
</table>
