<template>
  <div id="burger-table">
    <div>
      <div id="burger-table-header">
        <div class="order-id">#:</div>
        <div>Cliente:</div>
        <div>Pão:</div>
        <div>Carne:</div>
        <div>Opcionais:</div>
        <div>Ações:</div>
      </div>
    </div>
  </div>
  <div id="burger-table-rows">
    <div class="burger-table-row">
      <div class="order-number">1</div>
      <div>João</div>
      <div>Pão</div>
      <div>Carne</div>
      <div>
        <ul>
          <li>Salame</li>
          <li>Manga</li>
        </ul>
      </div>
      <div>
        <select class="status" name="status">
          <option value="">Selecione</option>
        </select>
        <button class="btn-delete">Cancelar</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {

}
</script>

<style scoped>
#burger-table {
  max-width: 1200px;
  margin: 0 auto;
}

#burger-table-header,
#burger-table-rows,
.burger-table-row {
  display: flex;
  flex-wrap: wrap;
}

#burger-table-header {
  font-weight: bold;
  padding: 12px;
  border-bottom: 3px solid #333;
}

.burger-table-row {
  width: 100%;
  padding: 12px;
  border-bottom: 1px solid #CCC;
}

#burger-table-header div,
.burger-table-row div {
  width: 19%;
}

#burger-table-header .order-id,
.burger-table-row .order-number {
  width: 5%;
}

select {
  padding: 12px 6px;
  margin-right: 12px;
}

.btn-delete {
  background-color: #222;
  color: #FCBA03;
  font-weight: bold;
  border: 2px solid #222;
  padding: 10px;
  font-size: 16px;
  margin: 0 auto;
  cursor: pointer;
  transition: .5s;
}

.btn-delete:hover {
  background-color: transparent;
  color: #222;
}
</style>