<template>
<div id="container">
    <div class="container2">
      <div id='control'>
        <div style="color:blue">
          <a
            @click="createTemp"
            href="#id01"
            id="Union"
            style="color: blue;"
            >+ Union Templates &nbsp; &nbsp;</a
          >
        </div>
        <div style="color:blue">
          <a @click="addtableline" href="#" id="Filter" style="color: blue;"
            >Add Data &nbsp; &nbsp;</a
          >
        </div>
          <div style="color:blue">
          <a @click="FilterData" href="#" id="FilterData" style="color: blue;"
            >Filter data &nbsp; &nbsp;</a
          >
        </div>
      </div>
      <div class="search-wrapper">
        <input id="hahaserch" type="text" v-model="search" placeholder="Search TemPlate Name"/>
      </div>
    </div>
    <div class="flex-container">
      <div @click="sortData" class="style col1" style="border-top-left-radius: 10px">arrayTem ID#</div>
      <div class="style col2" @click="sortData">TemPlate Name</div>
      <div class="style col3" @click="sortData">Type</div>
      <div class="style col4" @click="sortData">Company</div>
      <div class="style col5" @click="sortData">Version Date</div>
      <div class="style col6" @click="sortData">Expiration D</div>
      <div class="style col7" @click="sortData">ACTIVE</div>
      <div class="style col8" style="border-top-right-radius: 10px"></div>
    </div>
    <div id="tablefull">
      <div class="tdata">
        <div
          class="flex-container"
          v-for="(user,idx) in arrayTemtam"
          :key="idx"
          v-on:dblclick="editLine"
        >
          <div class="col1">{{ user.idfrom }}</div>
          <div class="col2" v-if="user.node2 == 'Edit'">{{ user.Temlate }}</div>
          <div class="col2" v-else-if="user.node2 == 'Cancel'">
            <input
              v-on:keyup.esc="Cancel"
              v-on:keyup.enter="ConfirmEnter"
              style="width: 90%; flex-grow: 1"
              type="text"
              class="create"
              placeholder="Nhập Temlate"
              v-model="Temlate"
              name="Temlate_Name"
            />
          </div>
          <div class="col2" v-else-if="user.node2 == 'Cancel_row'">
            <input
              v-on:keyup.esc="Cancel_row"
              v-on:keyup.enter="ConfirmEnter"
              style="width: 90%; flex-grow: 1"
              type="text"
              class="create"
              placeholder="Nhập Temlate"
              v-model="arrayTemtam[index_edit].Temlate"
              name="Temlate_Name"
            />
          </div>
          <div class="col3" v-if="user.node2 == 'Edit'">{{ user.Type }}</div>
          <div class="col3" v-else-if="user.node2 == 'Cancel'">
            <select
              v-on:keyup.enter="ConfirmEnter"
              v-on:keyup.esc="Cancel"
              style="width: 90%"
              class="create"
              v-model="Type"
              id="type"
              name="type"
            >
              <option value="1">Payoll</option>
              <option value="2">Production</option>
            </select>
          </div>
          <div class="col3" v-else-if="user.node2 == 'Cancel_row'">
            <select
              v-on:keyup.enter="ConfirmEnter"
              v-on:keyup.esc="Cancel_row"
              style="width: 90%"
              class="create"
              v-model="arrayTemtam[index_edit].Type"
              id="type"
              name="type"
            >
              <option value="Payoll">Payoll</option>
              <option value="Production">Production</option>
            </select>
          </div>
          <div class="col4" v-if="user.node2 == 'Edit'">{{ user.Company }}</div>
          <div class="col3" v-else-if="user.node2 == 'Cancel'">
            <input
              v-on:keyup.enter="ConfirmEnter"
              v-on:keyup.esc="Cancel"
              style="width: 90%"
              v-model="Company"
              type="text"
              class="create"
              id="fname"
              placeholder="Nhập Conpany"
              name="Company"
            />
          </div>
          <div class="col3" v-else-if="user.node2 == 'Cancel_row'">
            <input
              v-on:keyup.enter="ConfirmEnter"
              v-on:keyup.esc="Cancel_row"
              style="width: 90%"
              v-model="arrayTemtam[index_edit].Company"
              type="text"
              class="create"
              id="fname"
              placeholder="Nhập Conpany"
              name="Company"
            />
          </div>
          <div class="col5" v-if="user.node2 == 'Edit'">
            {{ user.VersionDate }}
          </div>
          <div class="col3" v-else-if="user.node2 == 'Cancel'">
            <input
              v-on:keyup.enter="ConfirmEnter"
              v-on:keyup.esc="Cancel"
              style="width: 90%"
              v-model="VersionDate"
              type="date"
              class="create"
              id="myDate"
              value="0000-00-00"
            />
          </div>
          <div class="col3" v-else-if="user.node2 == 'Cancel_row'">
            <input
              v-on:keyup.enter="ConfirmEnter"
              v-on:keyup.esc="Cancel_row"
              style="width: 90%"
              v-model="arrayTemtam[index_edit].VersionDate"
              type="date"
              class="create"
              id="myDate"
              value="0000-00-00"
            />
          </div>
          <div class="col6" v-if="user.node2 == 'Edit'">
            {{ user.ExpirationDate }}
          </div>
          <div class="col3" v-else-if="user.node2 == 'Cancel'">
            <input
              v-on:keyup.enter="ConfirmEnter"
              v-on:keyup.esc="Cancel"
              style="width: 90%"
              v-model="ExpirationDate"
              type="date"
              class="create"
              id="myDate"
              value="0000-00-00"
            />
          </div>
          <div class="col3" v-else-if="user.node2 == 'Cancel_row'">
            <input
              v-on:keyup.enter="ConfirmEnter"
              v-on:keyup.esc="Cancel_row"
              style="width: 90%"
              v-model="arrayTemtam[index_edit].ExpirationDate"
              type="date"
              class="create"
              id="myDate"
              value="1999-02-10"
            />
          </div>
          <div class="col7" v-if="user.node2 == 'Edit'">{{ user.Active }}</div>
          <div class="col3" v-else-if="user.node2 == 'Cancel'">
            <select
              v-on:keyup.enter="ConfirmEnter"
              v-on:keyup.esc="Cancel"
              v-model="Active"
              style="width: 90%"
              class="create"
              id="country"
              name="country"
            >
              <option value="1">Active</option>
              <option value="2">Archive</option>
            </select>
          </div>
          <div class="col3" v-else-if="user.node2 == 'Cancel_row'">
            <select
              v-on:keyup.enter="ConfirmEnter"
              v-on:keyup.esc="Cancel_row"
              v-model="arrayTemtam[index_edit].Active"
              style="width: 90%"
              class="create"
              id="country"
              name="country"
            >
              <option value="Active">Active</option>
              <option value="Archive">Archive</option>
            </select>
          </div>
          <div
            id="dd"
            class="col8"
            v-if="user.node2 == 'Edit'"
            style="text-align: center"
          >
          <!-- <div class="dropup">
            <a @click="optionSetting" class="dropbtn">...</a>
             <div class="dropup-content">
              <a href="#home">Home</a>
              <a href="#about">About</a>
              <a href="#contact">Contact</a>
            </div>
          </div> -->
        <div class="dropup">
          <button class="dropbtn" @click="dropLeft" check="0">...</button>
          <div class="dropup-content">
            <button @click="edit">Edit</button>
            <button ><a style ="color: rgb(0, 0, 0)" @click="removeLine"  href="#id01">remove</a></button>
            <!-- <button>Link 3</button> -->
          </div>
        </div>
          </div>
          <div
            class="col8"
            v-else-if="user.node2 == 'Cancel'"
            style="text-align: center"
          >
            <a href="#" class="add" @click="Confirm">Confirm</a>
            <a href="#" class="remove" @click="Cancel">Cancel</a>
          </div>
          <div
            class="col8"
            v-else-if="user.node2 == 'Cancel_row'"
            style="text-align: center"
          >
            <a href="#" class="add" @click="confirmEdit">Confirm</a>
            <a href="#" class="remove" @click="cancelEdit">Cancel</a>
          </div>
        </div>
      </div>
      <div id="nextpage">
        <button class="nextpage" name="button" type="button">
          <a href="javascript:;" class="next"> &larr; </a>
        </button>
        <button class="nextpage" name="button" type="button">
          <a href="javascript:;" class="next"> &rarr; </a>
        </button>
      </div>

    </div>
    <compCreateUnion
     v-bind:evenRemove="evenRemove"
     @confirmRemove="confirmRemove"
     :confirmBoolean="confirmBoolean"
    />
  </div>

</template>
<script>
import compCreateUnion from './compCreateUnion.vue'
export default {
  name: 'container',
  components: {
    compCreateUnion
  },
  props: {
    // index_edit: String
  },
  data () {
    return {
      evenRemove: {},
      confirmBoolean: '',
      index_edit: '',
      idarrayTem: '',
      Temlate: '',
      Type: '',
      Company: '',
      VersionDate: '',
      ExpirationDate: '',
      Active: '',
      arrayTemtam: [],
      arrayTem: [
        // Temlate: this.Temlate,Type: this.Type, Company: this.Company,VersionDate: this.VersionDate, ExpirationDate: this.ExpirationDate, Active: this.Active
        {
          idfrom: '1115',
          Temlate: 'bahaha hihhi ',
          Type: 'Production',
          Company: 'Peptico',
          VersionDate: '17-12-2020',
          ExpirationDate: '17-12-2020',
          Active: 'Active',
          node1: 'Remove',
          node2: 'Edit'
        },
        {
          idfrom: '1113',
          Temlate: 'a3325243-AFM-B6-TV-RADIOCOMMERCIALS-11-15',
          Type: 'Production',
          Company: 'Haitico',
          VersionDate: '20-11-2020',
          ExpirationDate: '20-11-2020',
          Active: 'Archive',
          node1: 'Remove',
          node2: 'Edit'
        },
        {
          idfrom: '1111',
          Temlate: 'huhuhahahahaahahahaah',
          Type: 'Payoll',
          Company: 'Haitico',
          VersionDate: '25-12-2020',
          ExpirationDate: '20-11-2020',
          Active: 'Active',
          node1: 'Remove',
          node2: 'Edit'
        },
        {
          idfrom: '1114',
          Temlate: 'c324-AFM-B6-TV-RADIOCOMMERCIALS-11-15',
          Type: 'Production',
          Company: 'Peptico',
          VersionDate: '20-11-2020',
          ExpirationDate: '20-11-2020',
          Active: 'Active',
          node1: 'Remove',
          node2: 'Edit'
        },
        {
          idfrom: '1112',
          Temlate: '1999-AFM-B6-TV-RADIOCOMMERCIALS-11-15',
          Type: 'Payoll',
          Company: 'Peptico',
          VersionDate: '22-12-2020',
          ExpirationDate: '20-11-2020',
          Active: 'Archive',
          node1: 'Remove',
          node2: 'Edit'
        }
      ]
    }
  },
  created () {
    for (let i = 0; i <= this.arrayTem.length - 1; i++) {
      this.arrayTemtam.push(this.arrayTem[i])
    }
  },
  computed: {

  },
  methods: {
    edit (event) {
      let elementtable = event.target.parentNode.parentNode.parentNode.parentNode.childNodes
      let getid = elementtable[0].innerHTML
      let getTemlate = elementtable[2].innerHTML
      let getType = elementtable[4].innerHTML
      let getCompany = elementtable[6].innerHTML
      let getVersionDate = elementtable[8].innerHTML
      let getExpirationDate = elementtable[10].innerHTML
      let getActive = elementtable[12].innerHTML
      let data1 = {
        idfrom: getid,
        Temlate: getTemlate,
        Type: getType,
        Company: getCompany,
        ExpirationDate: getExpirationDate,
        VersionDate: getVersionDate,
        Active: getActive,
        node1: 'Confirm_row',
        node2: 'Cancel_row'
      }
      let index = 0
      let check = true

      for (let [i, v] of this.arrayTem.entries()) {
        if (String(data1.idfrom) === String(v.idfrom)) {
          index = i
        }
        if (v.node2 === 'Cancel_row' || v.node2 === 'Cancel') {
          check = false
        }
      }

      if (check) {
        this.index_edit = index
        data1.ExpirationDate = this.convertDate(data1.ExpirationDate.trim(), '-', 'dd_mm_yyyy')
        data1.VersionDate = this.convertDate(data1.VersionDate.trim(), '-', 'dd_mm_yyyy')
        this.arrayTem[-2] = this.arrayTem[index]
        this.arrayTem.splice(index, 1, data1)
      }

      this.arrayTem[-2].node2 = 'Edit'
      this.dropLeft(event.target.parentNode.parentNode.childNodes[0])
      this.arrayTemtam = []
      for (const [i] of this.arrayTem.entries()) {
        this.arrayTemtam.push(this.arrayTem[i])
      }
    },
    confirmEdit (e) {
      const lengtharrayTem = e.target.parentNode.parentNode
      let Temlate = lengtharrayTem.childNodes[2].childNodes[0].value.length
      if (Temlate === 0) {
        alert('Trường Dữ Liệu Chưa được nhập')
      } else {
        let getidaddfilterC = e.target.parentNode.parentNode.childNodes
        let id = getidaddfilterC[0].innerHTML
        let getTemlate = this.arrayTemtam[this.index_edit].Temlate
        let getType = this.arrayTemtam[this.index_edit].Type
        let getCompany = this.arrayTemtam[this.index_edit].Company
        let getVersionDate = this.arrayTemtam[this.index_edit].VersionDate
        let getExpirationDate = this.arrayTemtam[this.index_edit].ExpirationDate
        let getActive = this.arrayTemtam[this.index_edit].Active
        let DataAddfilterC = {
          idfrom: id,
          Temlate: getTemlate,
          Type: getType,
          Company: getCompany,
          VersionDate: getVersionDate,
          ExpirationDate: getExpirationDate,
          Active: getActive,
          node1: 'Remove',
          node2: 'Edit'
        }
        let index = 0
        DataAddfilterC.ExpirationDate = this.convertDate(DataAddfilterC.ExpirationDate, '-', 'yyyy_mm_dd')
        DataAddfilterC.VersionDate = this.convertDate(DataAddfilterC.VersionDate, '-', 'yyyy_mm_dd')
        // for (i = 0; i < this.arrayTem.length; i++) {
        //   if (DataAddfilterC.idfrom === this.arrayTem[i].idfrom) {
        //     index = i
        //   }
        // }
        // for (let i in this.arrayTem) {
        //   if (DataAddfilterC.idfrom === this.arrayTem[i].idfrom) {
        //     index = i
        //   }
        // }
        this.arrayTem.forEach((v, i) => { // foreach duyetj từ 0 - length
          if (DataAddfilterC.idfrom === this.arrayTem[i].idfrom) {
            index = i
          }
        })
        this.arrayTem.splice(index, 1, DataAddfilterC)
        this.arrayTemtam = []
        // for (let i in this.arrayTem) {
        //   this.arrayTemtam.push(this.arrayTem[i])
        // }
        // for (const v of this.arrayTem) {
        //   this.arrayTemtam.push(v)
        // }
        this.arrayTem.forEach((v, i) => // foreach duyetj từ 0 - length
          this.arrayTemtam.push(v)
        )
        // for (let i = 0; i <= this.arrayTem.length - 1; i++) {
        //   this.arrayTemtam.push(this.arrayTem[i])
        // }
      }
      // cập nhật rỗng cho các input khi them line mới
      this.Temlate = ''
      this.Type = ''
      this.Company = ''
      this.VersionDate = ''
      this.ExpirationDate = ''
      this.Active = ''
    },
    cancelEdit (e) {
      let getid = e.target.parentNode.parentNode.childNodes
      let id = getid[0].innerHTML
      let Data = {
        idfrom: id
      }

      let index = 0
      for (let [i] of this.arrayTem.entries()) {
        if (Data.idfrom === this.arrayTem[i].idfrom) {
          index = i
        }
      }
      this.arrayTem.splice(index, 1, this.arrayTem[-2])
      this.arrayTemtam = []
      for (let v of this.arrayTem) {
        this.arrayTemtam.push(v)
      }
      // for (let i = 0; i <= this.arrayTem.length - 1; i++) {
      //   this.arrayTemtam.push(this.arrayTem[i])
      // }
    },
    editLine (e) {
      let elementtable = event.target.parentNode.childNodes
      let getid = elementtable[0].innerHTML
      let getTemlate = elementtable[2].innerHTML
      let getType = elementtable[4].innerHTML
      let getCompany = elementtable[6].innerHTML
      let getVersionDate = elementtable[8].innerHTML
      let getExpirationDate = elementtable[10].innerHTML
      let getActive = elementtable[12].innerHTML
      let data1 = {
        idfrom: getid,
        Temlate: getTemlate,
        Type: getType,
        Company: getCompany,
        ExpirationDate: getExpirationDate,
        VersionDate: getVersionDate,
        Active: getActive,
        node1: 'Confirm_row',
        node2: 'Cancel_row'
      }
      let index = 0
      let check = true
      for (let [i] of this.arrayTem.entries()) {
        if (String(data1.idfrom) === String(this.arrayTem[i].idfrom)) { // cùng dữ liệu nếu không sẻ bị lỗi
          index = i
        }
        if (this.arrayTem[i].node2 === 'Cancel_row' || this.arrayTem[i].node2 === 'Cancel') {
          check = false
        }
      }
      if (check) {
        this.index_edit = index
        data1.ExpirationDate = this.convertDate(data1.ExpirationDate.trim(), '-', 'dd_mm_yyyy')
        data1.VersionDate = this.convertDate(data1.VersionDate.trim(), '-', 'dd_mm_yyyy')
        this.arrayTem[-2] = this.arrayTem[index]
        this.arrayTem.splice(index, 1, data1)
      }
      this.arrayTem[-2].node2 = 'Edit'
      this.arrayTemtam = []
      for (let v of this.arrayTem) {
        this.arrayTemtam.push(v)
      }
    },
    removeLine (e) {
      const elementtable = event.target.parentNode.parentNode.parentNode.parentNode.parentNode.childNodes
      let getid = elementtable[0].innerHTML
      let getTemlate = elementtable[2].innerHTML
      let getType = elementtable[4].innerHTML
      let getCompany = elementtable[6].innerHTML
      let getVersionDate = elementtable[8].innerHTML
      let getExpirationDate = elementtable[10].innerHTML
      let getActive = elementtable[12].innerHTML
      let thaydoi = 'Remove'
      this.dropLeft(event.target.parentNode.parentNode.parentNode.childNodes[0])
      this.confirmBoolean = 'Remove'
      let data1 = {
        id: getid,
        Temlate: getTemlate,
        Type: getType,
        Company: getCompany,
        ExpirationDate: getExpirationDate,
        VersionDate: getVersionDate,
        Active: getActive,
        Change: thaydoi
      }
      this.evenRemove = data1
    },
    confirmRemove (e) {
      let index = 0
      let check = true
      for (let [i] of this.arrayTem.entries()) {
        if (String(e.id) === String(this.arrayTem[i].idfrom)) {
          index = i
        }
        if (this.arrayTem[i].node2 === 'Cancel_row' || this.arrayTem[i].node2 === 'Cancel') {
          check = false
        }
      }
      if (check) {
        this.arrayTem.splice(index, 1)
        this.$emit('removeline', e)
      } else {
        alert('đang có trường xử lý')
      }
      this.arrayTemtam = []
      for (let v of this.arrayTem) {
        this.arrayTemtam.push(v)
      }
    },
    createTemp (e) {
      this.confirmBoolean = 'Create'
      // console.log("apphihi"+ this.create_confirm_boolean)
      // this.$emit('changeeven',e)
      this.arrayTemtam = []
      for (let v of this.arrayTem) {
        this.arrayTemtam.push(v)
      }
    },
    ConfirmEnter (e) {
      this.confirmEdit(e)
    },

    sortData (e) {
    },
    search (e) {
    },
    addtableline (e) {
    },
    FilterData (e) {
    },
    Handlechange (e) {
    },
    dropLeft (e) { // kiểm tra dropup hiển thị và ẩn
      let checkEvent
      try {
        checkEvent = e.target.getAttribute('check') // nếu lỗi thì e là một đối tượng được gọi hàm trong methods
        checkEvent = e.target
      } catch (err) {
        checkEvent = e
      }
      if (checkEvent.getAttribute('check') === '0') {
        checkEvent.parentNode.style = 'display: block'
        checkEvent.parentNode.childNodes[2].style = 'display: block'
        checkEvent.setAttribute('check', '1')
      } else {
        checkEvent.parentNode.style = 'display: inline-block'
        checkEvent.parentNode.childNodes[2].style = 'display: none'
        checkEvent.setAttribute('check', '0')
      }
    },
    convertDate: function (date, tt, type) {
      let ngay
      let thang
      let nam
      if (type === 'dd_mm_yyyy') {
        ngay = date.slice(0, 2)
        thang = date.slice(3, 5)
        nam = date.slice(6, 10)
        return nam + tt + thang + tt + ngay
      }
      if (type === 'yyyy_mm_dd') {
        nam = date.slice(0, 4)
        thang = date.slice(5, 7)
        ngay = date.slice(8, 10)
        return ngay + tt + thang + tt + nam
      }
    }
  }
}
</script>
<style scoped>
.container2 {
  margin: 5px;
}
#control{
  display: flex;

}
#hahaserch {
  width: 600px;
  height: 30px;
  border: 2px solid blue;
  border-radius: 5px;

}
.nextpage:hover {
  background: red;
  color: white;
}

#container_child {
  margin-left: 10px;
  margin-right: 10px;
}

#title {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 40px;
}

.container2 {
  display: flex;
}

#content {
  margin: 20px;
  color: white;
}
table {
  border-collapse: collapse;
  height: 100%;
  background-color: rgb(167, 190, 119);
}

table tr:first-child th:first-child {
  border-top-left-radius: 15px;
  border: none;
}

table tr:first-child th:last-child {
  border-top-right-radius: 15px;
  border: none;
  background-attachment: fixed;
}

th {
  font-size: large;
  background-color: red;
  color: white;
}
td,
th {
  border: 1px solid #000000;
  text-align: left;
  padding: 15px;
}

a {
  text-decoration: none;
  color: white;
}

.tron {
  border-radius: 50%;
}
#content > div {
  padding: 5px;
}
.flex-container {
  z-index: 5;
  min-width: 1100px;
  padding: 0px;
  margin: 0px;
  color: red;
  display: flex;
  background-color: rgb(255, 0, 0);
  border-top-right-radius: 10px;
  border-top-left-radius: 10px;
}
.flex-container > .style {
  background-color: rgb(255, 0, 0);
  font-size: 20px;
  padding: 10px;
  flex:1;
  border: 1px solid black;
  color: white;
}
.flex-container > .style:hover {
    background-color: rgb(247, 173, 173);
    cursor: ns-resize;
    color: black
}
.flex-container > div {
  background-color: rgb(255, 255, 255);
  color: rgb(0, 0, 0);
  border: 1px solid black;
  padding: 10px;
  font-size: 10px;
  flex:1;
}
.flex-container:first-child div:last-child {
  background-attachment: fixed;
  background-color: D0CFCF;
}
#container {
   flex: 1;
   display: flex;
   flex-direction: column;
}
#bang {
  flex: 1;
  position: relative;
  border-top-left-radius: 15px;
  border-top-right-radius: 15px;
  display: flex;
}
#tablefull {
  position: relative;
  height: 100%;
  width: 100%;
  flex: 1;
}
.tdata {
  position: absolute;
  overflow-y: overlay;
  height: 100%;
  width: 100%;
}
#Cancel_edit {
  font-size: 20px;
  color: red;
  margin-right: 5px;
  padding-right: 5px;
}

.nextpage {
  padding: 0px;
}
#nextpage {
  position: absolute;
  width: 100%;
  text-align: center;
  bottom: 25px;
  background-color: NONE;
  width: 40px;
  margin-left: 50%;
}
.next {
  color: black;
  background-color: rgb(255, 56, 56);
}

#container_child {
  display: flex;
  flex-direction: column;

  padding-bottom: 0;
}

.add {
  font-size: 20px;
  color: red;
  border-right: 1px solid black;
  margin-right: 5px;
  padding-right: 5px;
}
.add:hover {
  color: blue;
}
#Cancel_edit:hover {
  color: blue;
}
.remove {
  font-size: 20px;
  color: red;
  border-right: 1px solid black;
  margin-right: 5px;
  padding-right: 5px;
  border-right: none;
}
.remove:hover {
  color: blue;
}

.container {
  padding: 2px 16px;
}
.container1 {
  padding: 2px 16px;
  display: flex;
  justify-content: center;
}
.col1 {
  width: 10%;
}
.col2 {
  width: 30%;
}
.col3 {
  width: 10%;
}
.col4 {
  width: 10%;
}
.col5 {
  width: 10%;
}
.col6 {
  width: 10%;
}
.col7 {
  width: 10%;
}
.col8 {
  width: 10%;
}
.dropbtn {
  font-size: 20px;
  height: 5px;
  background-color: #ffffff;
  border: 0px;
  outline:#ffffff
}

.dropup {
  position: relative;
  display: inline-block;
}

.dropup-content {
  border: 1px solid blue;
  display: none;
  position: absolute;
  background-color: #ffffff;
  min-width: 60px;
  bottom: -20px;
  right: 85px;
  z-index: 1;
}

.dropup-content>button {
 background-color: #ffffff;
  color: black;
  padding: 4px;
  border: none;
  outline: none;
  text-decoration: none;
  width: 100%;
  display: inline-block;
}

.dropup-content>button:hover {background-color: rgb(204, 204, 204)}

/* .dropup:hover .dropup-content {
  display: block;
} */

</style>
