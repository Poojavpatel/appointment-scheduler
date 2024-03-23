# Appointment Scheduler - Technical Design Doc

## Non functional requirements

- Availability
- Reliability
- Easy to maintain
- Error logging and monitoring

## Functional requirements

- Doctor should be able to provide time slots for appointments
- Patient should be able to call a voice bot to book a new appointment
- Patient should be able to call a voice bot to reschedule an existing appointment
- Patient should be able to call a voice bot to cancel an existing appointment

<br/>

## Technical requirements

- A frontend system for doctor to provide availability
- Save doctor availability in a database
- API to get available slots
- Voice bot that a patient can call
- AI tech to process user input, understand context, and construct req body
- Functions to book appointment, get appointment details, reschedule appointment, cancel appointment
- Save booked appointment data in database
- AI tech to generate response text based on API response

<br/>

## Technical decisions (scoping down)

- For this project, we will assume a Single doctor clinic
- Time slots will be 30 mins slots each
- Doctor will provide weekly availability
- Patient will be provided with available slots for a day, not for a week or month or year

<br/>
<br/>

## Implementation

### High level design and user flow

<img src="./img/appointment_scheduler_hld.drawio.svg" width="65%">

<br/>

<img src="./img/appointment_scheduler_lld.drawio.svg" width="85%">

<br/>

<!-- ### DB models

```js
patient
{
  name:"",
  phone:"", //indexed, primary
  createdAt:"",
  updatedAt:""
}

doctorAvailability
{
  id:"", //primary
  day:"", //indexed
  slotTime:""
}

doctorSchedule
{
  id:"",
  date:"",
  slot:"",
  patientId:"",
  day:"",
  purpose:""
}

````

-->

### API contracts

<!--
```js
// get user appointment
POST /appointment
req:{
  phone:""
}
res:{
  exists:true,
  date:"",
  slots:"",
  name:""
}

//update/reschedule user appointment
PUT /appointment
req:{
  phone:"",
  slot:"",
  date:""
}
res:{
  updated:true,
  slot:"",
  date:""
}

// get available appointment slots
POST /appointment/slots
req:{
  date:"",
  timeRange:""
}
res:{
  slotsAvailable:true,
  slots:[
    {
      date:"",
      time:""
    },
    {
      date:"",
      time:""
    },
  ]
}

// book appointment
POST /appointment/book
req:{
  date:"",
  slot:"",
  purpose:"",
  phone:""
}
res:{
  booked:true,
  date:"",
  slot:"",
  name:""
}

// cancel appointment
DELETE /appointment
req:{
  phone:""
}
res:{
  canceled:true,
  name:""
}

// create appointment slots for given range
POST /doctor/slots
req:{
  day:"",
  timeRange:""
}
res:{
  status:true
}
``` -->

<br/>
<br/>

## Tasks and timelines

T001 - Spike : Learn about AI models suited for voice and language processing  
Add findings under [Spike Findings](./Spike_AI.md)

T002

<br/>

## Future scope

**Handle double booking problem**  
As the app scales and user base increase, we might encounter problems related to race condition, commonly known as double booking  
To handle this implement db locking and use transactions

**International customers**  
Make updates to handle multiple timezones, these will include updating slot configurations to save UTC timestamps and handling timezones when saving and listing available slots

**Book appointments based on doc qualifications**
Assuming doctor is a dermatologist, our system should be able to respond appropriately for queries not related to dermatology

**Implement Patient follow up**  
Update system to be able to book follow up appointments for patients
