<template>

  <div class="DNForm">

      <div class="form-row">
      <div class="form-group col-md-8">
        <label>PO Number</label>
        <input type="text" class="form-control" id="IPONumber" placeholder="PO Number" />
      </div>

      <div class="form-group col-md-2">
          <br/>
         <button type="submit" class="btn btn-primary">Search</button>    
      </div>
    </div>


    <div class="form-row">
      <div class="form-group col-md-6">
        <label>Project</label>
        <input type="text" class="form-control" id="IProject" placeholder="Project" />
      </div>

      <div class="form-group col-md-6">
        <label>PO</label>
        <input type="text" class="form-control" id="IPO" placeholder="PO" />
      </div>
    </div>

    <div class="form-row">
      <div class="form-group col-md-6">
        <label>Customer PO</label>
        <input type="text" class="form-control" id="ICustomerPO" placeholder="Customer PO" />
      </div>

      <div class="form-group col-md-6">
        <label>Delivered by</label>
        <input type="text" class="form-control" id="IDeliveredby" placeholder="Delivered by" />
      </div>
    </div>

     <div class="form-row">
      <div class="form-group col-md-6">
        <label>Delivered Date</label>
        <input type="text" class="form-control" id="IDeliveredDate" placeholder="Delivered Date" />
      </div>

      <div class="form-group col-md-6">
        <label>Short Description</label>
        <input type="text" class="form-control" id="IShortDescription" placeholder="Short Description" />
      </div>
    </div>


       
       <table class="table">
  <thead>
    <tr>
      <th scope="col">#</th>
      <th scope="col">First</th>
      <th scope="col">Last</th>
      <th scope="col">Handle</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">1</th>
      <td>Mark</td>
      <td>Otto</td>
      <td>@mdo</td>
    </tr>
    <tr>
      <th scope="row">2</th>
      <td>Jacob</td>
      <td>Thornton</td>
      <td>@fat</td>
    </tr>
    <tr>
      <th scope="row">3</th>
      <td>Larry</td>
      <td>the Bird</td>
      <td>@twitter</td>
    </tr>
  </tbody>
</table>



     
     <div class="form-row">
      <div class="form-group col-md-6">
        <label>Customer Name</label>
        <input type="text" class="form-control" id="ICustomerName" placeholder="Customer Name" />
      </div>

      <div class="form-group col-md-6">
        <label>Signature</label>
        <input type="text" class="form-control" id="ISignature" placeholder="Signature" />
      </div>
    </div>

    <div class="form-row">
      <div class="form-group col-md-6">
        <label>Contact Person</label>
        <input type="text" class="form-control" id="IContactPerson" placeholder="Contact Person" />
      </div>

      <div class="form-group col-md-6">
        <label>Telephone No</label>
        <input type="text" class="form-control" id="ITelephoneNo" placeholder="Telephone No" />
      </div>
    </div>

    <div class="form-row">
      <div class="form-group col-md-6">
        <label>Email Address</label>
        <input type="text" class="form-control" id="!EmailAddress" placeholder="Email Address" />
      </div>

      <div class="form-group col-md-6">
        <label>FAX No</label>
        <input type="text" class="form-control" id="IFAXNo" placeholder="FAX No" />
      </div>
    </div>

    <div class="form-row">
      <div class="form-group col-md-6">
        <label>Bldg. Address</label>
        <input type="text" class="form-control" id="IBldgAddress" placeholder="Bldg. Address" />
      </div>

      <div class="form-group col-md-6">
        <label>TEL </label>
        <input type="text" class="form-control" id="ITEL" placeholder="TEL" />
      </div>
    </div>

    <div class="form-row">
      <div class="form-group col-md-6">
        <label>City</label>
        <input type="text" class="form-control" id="ICity" placeholder="City" />
      </div>

      <div class="form-group col-md-6">
        <label>Remarks</label>
        <input type="text" class="form-control" id="IRemarks" placeholder="Remarks" />
      </div>
    </div>


  </div>
</template>



<script>
export default {
        name: "DelivaryNote", 
        data() 
        {
                
        },
        methods: {
            
        },
}
</script>