# booking-Car-Inventory
This programming helps how to control an inventory, and Booking a car ,tour  etc<br>
using Javascript, html 
The output looks like the pic below<br>
![BMI Screenshot](https://github.com/Pybraham/booking-Car-Inventory/blob/main/bookingcarr.jpg)
 <br>Assume You Have downloaded the prerequsites<br>
   Visual Studio Code or any IDE development Environment to write the programm<br>
   Enable Download javascript,PHP,  MySQL for the inventory data base.<br>
   create a directory on your PC directory to save the program files<br>
   The Architechture looks like this <br>
    C: Javascript, Html  ()CSS is optional As formating styling will be included in the javascript.<br>

    sample code below<br>
    '''<!DOCTYPE html>
<html lang="en">
<head>
   <style>
  </style>
</head>
<h1>Car Inventory and  Booking Form</h1>
  <form id="bookingForm" onsubmit="return calculateCost(event)">
    <label for="carType">Car Type:</label>
    <select id="carType" required>
      <option value="" disabled selected>Select a car type</option>
      <option value="bmw">BMW</option>
      .//Add Any amount of inventory Car type
      .
      .
    </select>

    <label for="startDate">Rental Start Date:</label>
    <input type="date" id="startDate" required />
        .
        .
        .
        Add Any Parameters lables you want to like, mileage travvled, km at start
     <button type="submit">Calculate Total Cost</button>
  </form>
<div id="result"></div>
<script>
    function calculateCost(event) {
      event.preventDefault();

      const carType = document.getElementById('carType').value;
      const startDate = new Date(document.getElementById('startDate').value);
      const endDate = new Date(document.getElementById('endDate').value);
      const kmAtRent = parseFloat(document.getElementById('kmAtRent').value);
      const personName = document.getElementById('personName').value.trim();
      const mileageReturn = parseFloat(document.getElementById('mileageReturn').value);
      const repairCosts = parseFloat(document.getElementById('repairCosts').value) || 0;

      if (endDate < startDate) {
        alert('End date must be after start date.');
        return false;
      }

      // Calculate rental days
      const timeDiff = endDate.getTime() - startDate.getTime();
      const days = Math.ceil(timeDiff / (1000 * 3600 * 24)) + 1;

      // Base cost per km by car type
      const baseCostPerKmMap = {
        Opel:0.3,
        Citreaon6: 0.3,
        sedan: 0.5,
        suv: 0.7,
        hatchback: 0.4,
        convertible: 1.0,
        bmw: 0.6,
        mercedes: 0.9
      };

      const baseCostPerKm = baseCostPerKmMap[carType] || 0.5;

      // Calculate cost for kilometers at rent
      const costKmAtRent = kmAtRent * baseCostPerKm;

      // Calculate extra mileage cost if mileageReturn > kmAtRent
      const extraMileage = Math.max(0, mileageReturn - kmAtRent);
      const extraMileageCost = extraMileage * baseCostPerKm * 1.5; // 50% surcharge on extra mileage

      // Total cost calculation
      const totalCost = costKmAtRent + extraMileageCost + repairCosts;

      const resultDiv = document.getElementById('result');
      resultDiv.textContent = `Total cost for ${personName} (${carType.toUpperCase()}), for ${days} day(s): $${totalCost.toFixed(2)}`;

      return false;
    }
  </script>
</body>
</html>'''

