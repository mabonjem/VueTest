<template>

  <div class="Eevnt" v-if="AllData != null">
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">

    <div class="event-details-page">
      <h2 class="heading-2">{{AllData.Title}}</h2>
      <div class="event-details-page-widget">
        <div class="archive-item">
          <div class="img">
            <img
              class="responsive-img"
              src="/en/STCsEvents/PublishingImages/Solutions-talk.png"
              title="Solutions Talk"
            />
          </div>
          <div class="event-details-header">
            <ul>
              <li>
                <span class="event-start">Start Date: {{ AllData.EventDate }}</span>
              </li>
              <li>
                <span class="event-end">End date: {{ AllData.EventDate }}</span>
              </li>
              <li>
                <span class="event-location">Location: {{AllData.Location}}</span>
              </li>
            </ul>
          </div>

         <div> {{AllData.Description}} </div>

          <div v-for="val in array" :key="val.Id">
            <div class="form-group-inline">
              <div class="form-check">
                <input class="radio" :value="val.Id" name="rd" type="radio" v-model="picked" />
                <label tabindex="5" for="radio-3" class="radio-label">{{val.Title}}</label>
                <div> {{val.SessionTime}} </div>
                <div> Number Of Attendees : {{val.NumberOfAttendees}} </div>
              </div>
            </div>
          </div>

          <button type="submit"  @click="bookItem"  v-bind:disabled="isButtonDisabled"   class="btn btn-primary">Sign in</button>
        </div>
      </div>
    </div>
  </div>
</template>



 


<script>
const axios = require("axios");

export default {
  name: "Eevnt",
  data() {
    return {
      AllData: null,
      isButtonDisabled : false,
     // picked : null , 
      array: null
    };
  },
  
  methods: {
    bookItem () 
    {
       alert(this.picked);
       var  items =  [
          {"key": "sessionId" , "value" : this.picked}
       ];
       createListItem(items ,"Register" , "/"  ); 
    }, 
   
    

  },

  async created() {
    try {

       // eslint-disable-next-line no-unused-vars
       var eventId =  new  URL(location.href).searchParams.get("EventID");
      // eslint-disable-next-line no-unused-vars
      const config = {
        headers: {
          //   Authorization: `Bearer ${token}`,
          Accept: "application/json;odata=verbose"
        }
      };
      const res = await axios.get(
        // "http://stcs-portaldevt:8080/en/STCsEvents/_api/web/lists/GetByTitle('CalendarEvents')/items?$filter=ID eq " + eventId,
        "https://demo5445955.mockable.io/Test123",
        config
      );
      // eslint-disable-next-line no-unused-vars

      this.AllData = res.data.d.results[0];

           // eslint-disable-next-line no-unused-vars
     const res2 = await axios.get(
        // "http://stcs-portaldevt:8080/en/STCsEvents/_api/web/lists/GetByTitle('CalendarEvents')/items?$filter=ID eq " + eventId,
        "https://demo5445955.mockable.io/Time",
        config
      );
      this.array = res2.data.d.results;
       
      
    } catch (e) {
      alert(e);
    }
    // eslint-disable-next-line no-unused-vars
  }

};




function createListItem( listItems , listName , siteUrl) {

    var clientContext = new SP.ClientContext(siteUrl);
    var oList = clientContext.get_web().get_lists().getByTitle('Register');
        
    var itemCreateInfo = new SP.ListItemCreationInformation();
    this.oListItem = oList.addItem(itemCreateInfo);
        listItems.forEach(element => {
           oListItem.set_item( element['key'], element['value']);
        });
          oListItem.update();

    clientContext.load(oListItem);
        
    clientContext.executeQueryAsync(Function.createDelegate(this, this.onQuerySucceeded), Function.createDelegate(this, this.onQueryFailed));
}

function onQuerySucceeded() {

    alert('Item created: ' + oListItem.get_id());
}

function onQueryFailed(sender, args) {

    alert('Request failed. ' + args.get_message() + '\n' + args.get_stackTrace());
}

</script>





