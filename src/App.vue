<template>
  <div>
    <h1>Our Class Timetable</h1>

    
    <div class="buttons">
      <button 
        v-for="day in days" 
        :key="day" 
        @click="selectedDay = day"
      >
        {{ day }}
      </button>
    </div>

    
    <div v-if="selectedDay">
      <h2>{{ selectedDay }}</h2>

      <table>
        <tr>
          <th>Time</th>
          <th>Subject</th>
        </tr>

        <tr v-for="(item, index) in timetable[selectedDay]" :key="index">
          <td>{{ item.time }}</td>
          <td>{{ item.subject }}</td>
        </tr>
      </table>
    </div>

    
    <div class="activities" v-if="selectedDay">
      <h2>{{ selectedDay }} Activities</h2>
      <ul>
        <li v-for="(activity, index) in activities[selectedDay]" :key="index">
          {{ activity }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const days = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday"]
const selectedDay = ref("Monday")

const timetable = {
  Monday: [
    { time: "08:00", subject: "ui/ux" },
    { time: "09:00", subject: "DJF" },
    { time: "10:00", subject: "MATH" },
    { time: "11:00", subject: "GD" }
  ],
  Tuesday: [
    { time: "08:00", subject: "DJF" },
    { time: "09:00", subject: "DJF" },
    { time: "10:00", subject: "CL" },
    { time: "11:00", subject: "VC Pract" }
  ],
  Wednesday: [
    { time: "08:00", subject: "VC" },
    { time: "09:00", subject: "DGV" },
    { time: "10:00", subject: "FREE " },
    { time: "11:00", subject: "MATH" }
  ],
  Thursday: [
    { time: "08:00", subject: "VC" },
    { time: "09:00", subject: "DJF" },
    { time: "10:00", subject: "PHY" },
    { time: "11:00", subject: "DJF" }
  ],
  Friday: [
    { time: "08:00", subject: "DGV" },
    { time: "09:00", subject: "FR" }
  ]
}

const activities = {
  Monday: ["general assembly", "Assembly", "Homework"],
  Tuesday: ["Group Work", "Reading", "Assignments"],
  Wednesday: ["Sports Practice", "Discussion", "Revision"],
  Thursday: ["Project Work", "Presentation", "Homework"],
  Friday: ["General Cleaning", "Clubs", "Review"]
}
</script>

<style>
body {
  font-family: Arial, sans-serif;
  background: #f5f7fa;
  margin: 0;
  padding: 0;
}

h1 {
  text-align: center;
  margin-top: 20px;
}

.buttons {
  text-align: center;
  margin: 20px;
}

button {
  margin: 5px;
  padding: 8px 14px;
  border: none;
  background-color: #2c3e50;
  color: white;
  cursor: pointer;
  border-radius: 5px;
}

button:hover {
  background-color: #34495e;
}

table {
  margin: 20px auto;
  border-collapse: collapse;
  width: 60%;
  background: white;
}

th {
  background-color: #2c3e50;
  color: white;
  padding: 10px;
}

td {
  padding: 10px;
  text-align: center;
  border: 1px solid #ddd;
}

tr:nth-child(even) {
  background-color: #f2f2f2;
}

h2 {
  text-align: center;
}

.activities {
  width: 60%;
  margin: 20px auto;
  background: white;
  padding: 15px;
  border-radius: 5px;
}

ul {
  list-style-type: square;
  padding-left: 20px;
}
</style>