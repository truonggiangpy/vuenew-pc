<template>
  <transition name="modal-fade">
    <div class="modal-backdrop">
      <div
        class="modal"
        role="dialog"
        aria-labelledby="modalTitle"
        aria-describedby="modalDescription"
      >
        <header class="modal-header" id="modalTitle">
          <slot name="header">
            Model Lọc Dữ Liệu
            <button
              type="button"
              class="btn-close"
              @click="closeFilter"
              aria-label="Close modal"
            >
              X
            </button>
          </slot>
        </header>
        <section class="modal-body" id="modalDescription">
          <slot name="body">
            <div style="text-align: center"><input type="checkbox" id="all" value="all" v-model="checkedNames"><label for="all">Tất Cả Dự Liệu</label></div><br/>
            <div style="display: flex;  justify-content: space-between; ">
              <div style="flex:1;">
                <div>
                  <label >Type: </label>
                  <select
                  v-model="Type"
                  >
                    <option value="Payoll">Payoll</option>
                    <option value="Production">Production</option>
                  </select>
                </div>
                <div>
                <label >Conpany: </label>
                  <input
                    placeholder="Nhập Company"
                    v-model="Company"
                    name="Company"
                  />
                </div>
              </div>
            <div style="flex: 1">
              <label >Active: </label>
              <select
                v-model="Active">
                <option value="Active">Active</option>
                <option value="Archive">Archive</option>
              </select>
              <div>
                <label>Version Date</label>
                <br>
              <input class="create" type="date" v-model="VersionDate1" />
              <label>to</label>
              <input class="create" type="date" v-model="VersionDate2" />
              </div>
            </div>
            </div>
          </slot>
        </section>
        <footer class="modal-footer">
          <button
            type="button"
            class="btn-green"
            @click="allData"
            aria-label="Close modal"
          >
            All
          </button>
          <button
            type="button"
            class="btn-green"
            @click="filter"
            aria-label="Close modal"
          >
            Filter
          </button>
          <button
            type="button"
            class="btn-green"
            @click="closeFilter"
            aria-label="Close modal"
          >
            Cancel
          </button>
        </footer>
      </div>
    </div>
  </transition>
</template>
<script>
export default {
  name: 'modal',
  data () {
    return {
      checkedNames: [],
      Temlate: '',
      Type: '',
      Company: '',
      VersionDate1: '',
      VersionDate2: '',
      Active: ''
    }
  },
  methods: {
    close () {
      this.$emit('close')
    },
    filter (e) {
      let data = {}
      if (this.checkedNames[0] === 'all') {
        data.Type = ''
        data.Company = ''
        data.VersionDate1 = ''
        data.VersionDate2 = ''
        data.Active = ''
        data.checkall = 'all'
      } else {
        data.checkedNames = this.checkedNames
        data.Type = this.Type
        data.Company = this.Company
        data.VersionDate1 = this.VersionDate1
        data.VersionDate2 = this.VersionDate2
        data.Active = this.Active
        data.checkall = 'loc'
      }
      // alert(data.VersionDate)
      this.$emit('confirmFilter', data)
      this.Temlate = ''
      this.Type = ''
      this.Company = ''
      this.VersionDate = ''
      this.Active = ''
    },
    closeFilter (e) {
      this.$emit('closeFilter')
    },
    allData (e) {
      this.$emit('allData')
    },
    versionDate1 (e) {

    }
  }
}
</script>
<style>
.modal-backdrop {
  z-index: 10;
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.3);
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal {
  background: #ffffff;
  box-shadow: 2px 2px 20px 1px;
  overflow-x: auto;
  display: flex;
  width: 800px;
  font-size: 25px;
  flex-direction: column;
}

.modal-header,
.modal-footer {
  padding: 15px;
  display: flex;
}

.modal-header {
  border-bottom: 1px solid #eeeeee;
  color: #ff0000;
  justify-content: space-between;
}

.modal-footer {
  border-top: 1px solid #eeeeee;
  justify-content: flex-end;
}

.modal-body {
  position: relative;
  padding: 20px 10px;
}

.btn-close {
  border: none;
  font-size: 20px;
  padding: 20px;
  cursor: pointer;
  font-weight: bold;
  color: #ff0000;
  background: transparent;
}

.btn-green {
  margin-right: 10px;
  color: white;
  font-size: 25px;
  background: #fc0000;
  border: 1px solid #000000;
  border-radius: 2px;
}
</style>
