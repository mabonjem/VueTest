<template>
  <div class="DNForm">
    <div class="form-row">
      <div class="form-group col-md-8">
        <label>PO Number</label>
        <input
          type="number"
          class="form-control"
          v-model="POFilter"
          id="IPONumber"
          required
          placeholder="PO Number"
        />
      </div>

      <div class="form-group col-md-2">
        <br />
        <button type="submit" @click="getPO" class="btn btn-primary">
          Search
        </button>
      </div>
    </div>

    <div v-if="!loading">
      <div class="form-row">
        <div
          v-if="noteDataBodyProjectHeader.PROJECT_NAME != null"
          class="form-group col-md-6"
        >
          <label>Project</label>
          <input
            type="text"
            class="form-control"
            v-model="noteDataBodyProjectHeader.PROJECT_NAME"
            id="IProject"
            placeholder="Project"
          />
        </div>

        <div
          v-if="noteDataBodyProjectHeader.PO_NUMBER != null"
          class="form-group col-md-6"
        >
          <label>PO</label>
          <input
            type="text"
            class="form-control"
            id="IPO"
            v-model="noteDataBodyProjectHeader.PO_NUMBER"
            placeholder="PO"
          />
        </div>
      </div>

      <div
        v-if="noteDataBodyProjectHeader.CUSTOMER_PO != null"
        class="form-row"
      >
        <div class="form-group col-md-6">
          <label>Customer PO</label>
          <input
            type="text"
            v-model="noteDataBodyProjectHeader.CUSTOMER_PO"
            class="form-control"
            id="ICustomerPO"
            placeholder="Customer PO"
          />
        </div>

        <div class="form-group col-md-6">
          <label>Delivered by</label>
          <input
            type="text"
            class="form-control"
            id="IDeliveredby"
            v-model="customOb.deliveredby"
            placeholder="Delivered by"
          />
        </div>
      </div>

      <div class="form-row">
        <div class="form-group col-md-6">
          <label>Delivered Date</label>
          <input
            type="text"
            v-model="customOb.deliveredDate"
            class="form-control"
            id="IDeliveredDate"
            placeholder="Delivered Date"
          />
        </div>

        <div class="form-group col-md-6">
          <label>Short Description</label>
          <input
            type="text"
            v-model="customOb.shortDescription"
            class="form-control"
            id="IShortDescription"
            placeholder="Short Description"
          />
        </div>
      </div>

      <table class="table">
        <thead>
          <tr>
            <th scope="col">#</th>
            <th scope="col">ITEM_CODE</th>
            <th scope="col">ITEM_DESCRIPTION</th>
            <th scope="col">QUANTITY</th>
            <th scope="col">QUANTITY_RECEIVED</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item in noteDataProjectLine" :key="item.PO_LINE_NUM">
            <td><button @click="deleteItem(item)">delete</button></td>
            <td>{{ item.ITEM_CODE }}</td>
            <td>{{ item.ITEM_DESCRIPTION }}</td>
            <td>{{ item.QUANTITY }}</td>
            <td><input v-model="item.QUANTITY_RECEIVED" type="text" /></td>
          </tr>
        </tbody>
      </table>

      <div v-if="noteDataBodyProjectHeader.CUSTOMER" class="form-row">
        <div class="form-group col-md-6">
          <label>Customer Name</label>
          <input
            type="text"
            class="form-control"
            v-model="noteDataBodyProjectHeader.CUSTOMER"
            id="ICustomerName"
            placeholder="Customer Name"
          />
        </div>

        <div class="form-group col-md-6">
          <label>Signature</label>
          <input
            type="text"
            v-model="customOb.signature"
            class="form-control"
            id="ISignature"
            placeholder="Signature"
          />
        </div>
      </div>

      <div class="form-row">
        <div class="form-group col-md-6">
          <label>Contact Person</label>
          <input
            type="text"
            v-model="customOb.contactPerson"
            class="form-control"
            id="IContactPerson"
            placeholder="Contact Person"
          />
        </div>

        <div class="form-group col-md-6">
          <label>Telephone No</label>
          <input
            type="text"
            v-model="customOb.telephoneNo"
            class="form-control"
            id="ITelephoneNo"
            placeholder="Telephone No"
          />
        </div>
      </div>

      <div class="form-row">
        <div class="form-group col-md-6">
          <label>Email Address</label>
          <input
            type="text"
            v-model="customOb.emailAddress"
            class="form-control"
            id="!EmailAddress"
            placeholder="Email Address"
          />
        </div>

        <div class="form-group col-md-6">
          <label>FAX No</label>
          <input
            type="text"
            v-model="customOb.fAXNo"
            class="form-control"
            id="IFAXNo"
            placeholder="FAX No"
          />
        </div>
      </div>

      <div class="form-row">
        <div class="form-group col-md-6">
          <label>Bldg. Address</label>
          <input
            type="text"
            v-model="customOb.bldg"
            class="form-control"
            id="IBldgAddress"
            placeholder="Bldg. Address"
          />
        </div>

        <div class="form-group col-md-6">
          <label>TEL </label>
          <input
            type="text"
            v-model="customOb.tel"
            class="form-control"
            id="ITEL"
            placeholder="TEL"
          />
        </div>
      </div>

      <div class="form-row">
        <div class="form-group col-md-6">
          <label>City</label>
          <input
            type="text"
            v-model="customOb.city"
            class="form-control"
            id="ICity"
            placeholder="City"
          />
        </div>


          <div class="form-row">
        <div class="form-group col-md-6">
          <label>Received Date</label>
          <input
            type="text"
            v-model="customOb.ReceivedDate"
            class="form-control"
            id="ICity"
            placeholder="City"
          />
        </div>

        <div class="form-group col-md-6">
          <label>Remarks</label>
          <input
            type="text"
            class="form-control"
            id="IRemarks"
            v-model="customOb.remarksitem"
            placeholder="Remarks"
          />
        </div>
      </div>

      <div class="form-group col-md-12">
        <br />
        <button type="submit" @click="printToPdf" class="btn btn-primary">
          Print
        </button>
      </div>
    </div>
  </div>
</template>

<script>
const axios = require("axios");

export default {
  name: "DelivaryNote",
  data() {
    return {
      POFilter: null,
      noteDataBodyProjectHeader: null,
      noteDataProjectLine: null,
      customOb: {
        deliveredby: "",
        deliveredDate: "",
        shortDescription: "",
        signature: "",
        contactPerson: "",
        telephoneNo: "",
        emailAddress: "",
        fAXNo: "",
        bldg: "",
        tel: "",
        city: "",
        remarksitem: "", 
        ReceivedDate: ""
      },
      loading: true
    };
  },

  methods: {
    getPO() {
      if (this.POFilter == null) return;
      axios
        .get("http://demo2625458.mockable.io/Diliverynote")
        .then(response => {
          //    alert(response.data.ResponseBody.ProjectHeader.PROJECT_NUMBER);
          this.noteDataBodyProjectHeader =
            response.data.ResponseBody.ProjectHeader;
          this.noteDataProjectLine = response.data.ResponseBody.ProjectLine;
          if (this.noteDataBodyProjectHeader.PO_NUMBER != null)
            this.loading = false;
          else this.loading = true;

         });
    },
    deleteItem(itemToDelete) {
      this.noteDataProjectLine.splice(
        this.noteDataProjectLine.indexOf(itemToDelete),
        1
      );
    },
    printToPdf() {
     
     // eslint-disable-next-line no-console
     console.log(JSON.stringify(this.noteDataProjectLine));
     // eslint-disable-next-line no-console
     console.log(JSON.stringify(this.customOb)) ;
     // eslint-disable-next-line no-console
        console.log(JSON.stringify(this.noteDataBodyProjectHeader));
 
    

      axios
        .post(
          "http://localhost:58431/api/ToPDF/ToPdfConvertor",
          {
            noteDataBodyProjectHeader: JSON.stringify(this.noteDataBodyProjectHeader),
            noteDataProjectLine: JSON.stringify(this.noteDataProjectLine),
            customOb: JSON.stringify(this.customOb)
          },
          {
            headers: { 
          "Access-Control-Allow-Origin": "*",
         "Access-Control-Allow-Methods": "GET, POST, PATCH, PUT, DELETE, OPTIONS",
         "Access-Control-Allow-Headers": "Origin, Content-Type, X-Auth-Token"
          }
          }
        )
        .then(function(response) {
          alert(response);
        })
        .catch(function(error) {
          alert(error);
        });
    }
  }
};
</script>
