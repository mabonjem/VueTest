<template>
  <div class="Eevnt">
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

          <div v-for="val in array" :key="val">
            <div class="form-group-inline">
              <div class="form-check">
                <input class="radio" id="radio-3" name="rd" type="radio" />
                <label tabindex="5" for="radio-3" class="radio-label">{{val.Title}}</label>
                <div> {{val.SessionTime}} </div>
                <div> Number Of Attendees : {{val.NumberOfAttendees}} </div>
              </div>
            </div>
          </div>

          <button type="submit" class="btn btn-primary">Sign in</button>
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
      //  Title: null,
      //  ImageURL: "// 125 ",
      //  FromDate: null ,
      //  ToDate: "Date To",
      //  Location: "Ryaidh",
      array: null
    };
  },
  
  methods: {
    
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
        // "http://stcs-portaldevt:8080/en/STCsEvents/_api/web/lists/GetByTitle('CalendarEvents')/items?$filter=ID%20eq%20" + eventId,
        "https://demo5445955.mockable.io/Test123",
        config
      );
      // eslint-disable-next-line no-unused-vars

      this.AllData = res.data.d.results[0];

           // eslint-disable-next-line no-unused-vars
     const res2 = await axios.get(
        // "http://stcs-portaldevt:8080/en/STCsEvents/_api/web/lists/GetByTitle('CalendarEvents')/items?$filter=ID%20eq%20125",
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
</script>





