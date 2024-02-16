<template>
  <nav class="navbar bg-dark text-white">
    <div class="container-fluid">
      <span class="navbar-brand mb-0 h1 text-white text-center mx-auto">Bezla.com LLC</span>
    </div>
  </nav>
  
  <div style="margin-right: 20px; margin-left: 20px;">
  <div class="container mt-4 card p-5 shadow">
    <h3 style="color: #c65353;">Budget</h3>
    <p>
      Bezla created the Budget to help hoteliers utilize precise forecasts and allocate optimal pricing and revenue management strategies. 
      <br>Enter your predicted revenue and expenses to see a clear picture of the hotel's budget simulation.
    </p>
  </div>

  <div class="container-fluid card mt-5 p-3 shadow">
    <div class="table-responsive">
      <table class="table table-hover mx-auto">
        <thead>
          <tr>
            <th scope="col">Rooms</th>
            <td scope="col">Jan</td>
            <td scope="col">Feb</td>
            <td scope="col">Mar</td>
            <td scope="col">Apr</td>
            <td scope="col">May</td>
            <td scope="col">Jun</td>
            <td scope="col">Jul</td>
            <td scope="col">Aug</td>
            <td scope="col">Sep</td>
            <td scope="col">Oct</td>
            <td scope="col">Nov</td>
            <td scope="col">Dec</td>
            <td scope="col"></td>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td scope="row">Number of rooms</td>
            <td><input type="number" v-model="roomJan" @keyup.enter="calculateRooms" min="0" @blur="handleInputBlurRooms"></td>
            <td><input type="number" v-model="roomFeb" @keyup.enter="calculateRooms" min="0" @blur="handleInputBlurRooms"></td>
            <td><input type="number" v-model="roomMar" @keyup.enter="calculateRooms" min="0" @blur="handleInputBlurRooms"></td>
            <td><input type="number" v-model="roomApr" @keyup.enter="calculateRooms" min="0" @blur="handleInputBlurRooms"></td>
            <td><input type="number" v-model="roomMay" @keyup.enter="calculateRooms" min="0" @blur="handleInputBlurRooms"></td>
            <td><input type="number" v-model="roomJun" @keyup.enter="calculateRooms" min="0" @blur="handleInputBlurRooms"></td>
            <td><input type="number" v-model="roomJul" @keyup.enter="calculateRooms" min="0" @blur="handleInputBlurRooms"></td>
            <td><input type="number" v-model="roomAug" @keyup.enter="calculateRooms" min="0" @blur="handleInputBlurRooms"></td>
            <td><input type="number" v-model="roomSep" @keyup.enter="calculateRooms" min="0" @blur="handleInputBlurRooms"></td>
            <td><input type="number" v-model="roomOct" @keyup.enter="calculateRooms" min="0" @blur="handleInputBlurRooms"></td>
            <td><input type="number" v-model="roomNov" @keyup.enter="calculateRooms" min="0" @blur="handleInputBlurRooms"></td>
            <td><input type="number" v-model="roomDec" @keyup.enter="calculateRooms" min="0" @blur="handleInputBlurRooms"></td>
            <td><b>{{ Math.round(roomsAvg) }}</b></td>
          </tr>
          <tr>
            <td scope="row">Occupancy</td>
            <td><input type="number" v-model="occupancyJan" @keyup.enter="calculateOccupancy" step="0.01" min="0" @blur="handleInputBlurOccupancy">%</td>
            <td><input type="number" v-model="occupancyFeb" @keyup.enter="calculateOccupancy" step="0.01" min="0" @blur="handleInputBlurOccupancy">%</td>
            <td><input type="number" v-model="occupancyMar" @keyup.enter="calculateOccupancy" step="0.01" min="0" @blur="handleInputBlurOccupancy">%</td>
            <td><input type="number" v-model="occupancyApr" @keyup.enter="calculateOccupancy" step="0.01" min="0" @blur="handleInputBlurOccupancy">%</td>
            <td><input type="number" v-model="occupancyMay" @keyup.enter="calculateOccupancy" step="0.01" min="0" @blur="handleInputBlurOccupancy">%</td>
            <td><input type="number" v-model="occupancyJun" @keyup.enter="calculateOccupancy" step="0.01" min="0" @blur="handleInputBlurOccupancy">%</td>
            <td><input type="number" v-model="occupancyJul" @keyup.enter="calculateOccupancy" step="0.01" min="0" @blur="handleInputBlurOccupancy">%</td>
            <td><input type="number" v-model="occupancyAug" @keyup.enter="calculateOccupancy" step="0.01" min="0" @blur="handleInputBlurOccupancy">%</td>
            <td><input type="number" v-model="occupancySep" @keyup.enter="calculateOccupancy" step="0.01" min="0" @blur="handleInputBlurOccupancy">%</td>
            <td><input type="number" v-model="occupancyOct" @keyup.enter="calculateOccupancy" step="0.01" min="0" @blur="handleInputBlurOccupancy">%</td>
            <td><input type="number" v-model="occupancyNov" @keyup.enter="calculateOccupancy" step="0.01" min="0" @blur="handleInputBlurOccupancy">%</td>
            <td><input type="number" v-model="occupancyDec" @keyup.enter="calculateOccupancy" step="0.01" min="0" @blur="handleInputBlurOccupancy">%</td>
            <td><b>{{ occupancyAvg.toFixed(2) }} %</b></td>
          </tr>
          <tr>
            <td scope="row">ADR</td>
            <td>$<input type="text" v-model="adrJan" @keyup.enter="calculateAdr" @blur="handleInputBlurAdr" @keydown="handleKeyDown"></td>
            <td>$<input type="number" v-model="adrFeb" @keyup.enter="calculateAdr" @blur="handleInputBlurAdr" @keydown="handleKeyDown"></td>
            <td>$<input type="number" v-model="adrMar" @keyup.enter="calculateAdr" @blur="handleInputBlurAdr" @keydown="handleKeyDown"></td>
            <td>$<input type="number" v-model="adrApr" @keyup.enter="calculateAdr" @blur="handleInputBlurAdr" @keydown="handleKeyDown"></td>
            <td>$<input type="number" v-model="adrMay" @keyup.enter="calculateAdr" @blur="handleInputBlurAdr" @keydown="handleKeyDown"></td>
            <td>$<input type="number" v-model="adrJun" @keyup.enter="calculateAdr" @blur="handleInputBlurAdr" @keydown="handleKeyDown"></td>
            <td>$<input type="number" v-model="adrJul" @keyup.enter="calculateAdr" @blur="handleInputBlurAdr" @keydown="handleKeyDown"></td>
            <td>$<input type="number" v-model="adrAug" @keyup.enter="calculateAdr" @blur="handleInputBlurAdr" @keydown="handleKeyDown"></td>
            <td>$<input type="number" v-model="adrSep" @keyup.enter="calculateAdr" @blur="handleInputBlurAdr" @keydown="handleKeyDown"></td>
            <td>$<input type="number" v-model="adrOct" @keyup.enter="calculateAdr" @blur="handleInputBlurAdr" @keydown="handleKeyDown"></td>
            <td>$<input type="number" v-model="adrNov" @keyup.enter="calculateAdr" @blur="handleInputBlurAdr" @keydown="handleKeyDown"></td>
            <td>$<input type="number" v-model="adrDec" @keyup.enter="calculateAdr" @blur="handleInputBlurAdr" @keydown="handleKeyDown"></td>
            <td><b>${{ adrAvgFormatted }}</b></td>
          </tr>
          <tr>
            <th scope="row">Total</th>
            <td>$<input type="text" readonly :value="formattedRevJan > '0.00' ? formattedRevJan : '0.00'"></td>
            <td>$<input type="text" readonly :value="formattedRevFeb > '0.00' ? formattedRevFeb : '0.00'"></td>
            <td>$<input type="text" readonly :value="formattedRevMar > '0.00' ? formattedRevMar : '0.00'"></td>
            <td>$<input type="text" readonly :value="formattedRevApr > '0.00' ? formattedRevApr : '0.00'"></td>
            <td>$<input type="text" readonly :value="formattedRevMay > '0.00' ? formattedRevMay : '0.00'"></td>
            <td>$<input type="text" readonly :value="formattedRevJun > '0.00' ? formattedRevJun : '0.00'"></td>
            <td>$<input type="text" readonly :value="formattedRevJul > '0.00' ? formattedRevJul : '0.00'"></td>
            <td>$<input type="text" readonly :value="formattedRevAug > '0.00' ? formattedRevAug : '0.00'"></td>
            <td>$<input type="text" readonly :value="formattedRevSep > '0.00' ? formattedRevSep : '0.00'"></td>
            <td>$<input type="text" readonly :value="formattedRevOct > '0.00' ? formattedRevOct : '0.00'"></td>
            <td>$<input type="text" readonly :value="formattedRevNov > '0.00' ? formattedRevNov : '0.00'"></td>
            <td>$<input type="text" readonly :value="formattedRevDec > '0.00' ? formattedRevDec : '0.00'"></td>
            <td><b>${{ totalRevenue > '0.00' ? totalRevenue : '0.00' }}</b></td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
  </div>
</template>

<script>
  import { ref, onMounted, watchEffect, computed } from 'vue';

  export default {
    name: 'App',
    setup() {
      const roomJan = ref('0');
      const roomFeb = ref('0');
      const roomMar = ref('0');
      const roomApr = ref('0');
      const roomMay = ref('0');
      const roomJun = ref('0');
      const roomJul = ref('0');
      const roomAug = ref('0');
      const roomSep = ref('0');
      const roomOct = ref('0');
      const roomNov = ref('0');
      const roomDec = ref('0');

      const ValidateInputRoom = () => {
        if(roomJan.value === null || roomJan.value === '' || isNaN(roomJan.value) || parseInt(roomJan.value, 10) < 0){ roomJan.value = '0'; }
        if(roomFeb.value === null || roomFeb.value === '' || isNaN(roomFeb.value) || parseInt(roomFeb.value, 10) < 0){ roomFeb.value = '0'; }
        if(roomMar.value === null || roomMar.value === '' || isNaN(roomMar.value) || parseInt(roomMar.value, 10) < 0){ roomMar.value = '0'; }
        if(roomApr.value === null || roomApr.value === '' || isNaN(roomApr.value) || parseInt(roomApr.value, 10) < 0){ roomApr.value = '0'; }
        if(roomMay.value === null || roomMay.value === '' || isNaN(roomMay.value) || parseInt(roomMay.value, 10) < 0){ roomMay.value = '0'; }
        if(roomJun.value === null || roomJun.value === '' || isNaN(roomJun.value) || parseInt(roomJun.value, 10) < 0){ roomJun.value = '0'; }
        if(roomJul.value === null || roomJul.value === '' || isNaN(roomJul.value) || parseInt(roomJul.value, 10) < 0){ roomJul.value = '0'; }
        if(roomAug.value === null || roomAug.value === '' || isNaN(roomAug.value) || parseInt(roomAug.value, 10) < 0){ roomAug.value = '0'; }
        if(roomSep.value === null || roomSep.value === '' || isNaN(roomSep.value) || parseInt(roomSep.value, 10) < 0){ roomSep.value = '0'; }
        if(roomOct.value === null || roomOct.value === '' || isNaN(roomOct.value) || parseInt(roomOct.value, 10) < 0){ roomOct.value = '0'; }
        if(roomNov.value === null || roomNov.value === '' || isNaN(roomNov.value) || parseInt(roomNov.value, 10) < 0){ roomNov.value = '0'; }
        if(roomDec.value === null || roomDec.value === '' || isNaN(roomDec.value) || parseInt(roomDec.value, 10) < 0){ roomDec.value = '0'; }
      }

      const roomsAvg = ref(0);
      const handleInputBlurRooms = () => {
        ValidateInputRoom();
        calculateRooms();
        calculateRevenue();
      };
      const calculateRooms = () => {
        ValidateInputRoom();
        const roomValues = [
          roomJan.value, roomFeb.value, roomMar.value, roomApr.value, roomMay.value,
          roomJun.value, roomJul.value, roomAug.value, roomSep.value, roomOct.value,
          roomNov.value, roomDec.value
        ];
        const hasInvalidInput = roomValues.some(value => {
          const parsedValue = parseFloat(value);
          return isNaN(parsedValue) || parsedValue < 0;
        });
        if (hasInvalidInput) {
          //alert('Invalid input. Please enter positive numbers.');
          return;
        }
        const roomsSum = roomValues.reduce((sum, value) => sum + parseFloat(value), 0);
        roomsAvg.value = roomsSum / 12;
        calculateRevenue();
      };

      const occupancyJan = ref('0.00');
      const occupancyFeb = ref('0.00');
      const occupancyMar = ref('0.00');
      const occupancyApr = ref('0.00');
      const occupancyMay = ref('0.00');
      const occupancyJun = ref('0.00');
      const occupancyJul = ref('0.00');
      const occupancyAug = ref('0.00');
      const occupancySep = ref('0.00');
      const occupancyOct = ref('0.00');
      const occupancyNov = ref('0.00');
      const occupancyDec = ref('0.00');

      const formatInputOccupancy = () => {
        if (occupancyJan.value === null || occupancyJan.value === '' || isNaN(occupancyFeb.value) || parseFloat(occupancyJan.value) < 0.00 || parseFloat(occupancyJan.value) > 100.00) { occupancyJan.value = '0.00';} 
        else { occupancyJan.value = parseFloat(occupancyJan.value).toFixed(2); }
        if(occupancyFeb.value === null || occupancyFeb.value === '' || isNaN(occupancyFeb.value) || parseFloat(occupancyFeb.value) < 0.00 || parseFloat(occupancyFeb.value) > 100.00){ occupancyFeb.value = '0.00'; }
        else{ occupancyFeb.value = parseFloat(occupancyFeb.value).toFixed(2); }
        if(occupancyMar.value === null || occupancyMar.value === '' || isNaN(occupancyMar.value) || parseFloat(occupancyMar.value) < 0.00 || parseFloat(occupancyMar.value) > 100.00){ occupancyMar.value = '0.00'; }
        else{ occupancyMar.value = parseFloat(occupancyMar.value).toFixed(2); }
        if(occupancyApr.value === null || occupancyApr.value === '' || isNaN(occupancyApr.value) || parseFloat(occupancyApr.value) < 0.00 || parseFloat(occupancyApr.value) > 100.00){ occupancyApr.value = '0.00'; }
        else{ occupancyApr.value = parseFloat(occupancyApr.value).toFixed(2); }
        if(occupancyMay.value === null || occupancyMay.value === '' || isNaN(occupancyMay.value) || parseFloat(occupancyMay.value) < 0.00 || parseFloat(occupancyMay.value) > 100.00){ occupancyMay.value = '0.00'; }
        else{ occupancyMay.value = parseFloat(occupancyMay.value).toFixed(2); }
        if(occupancyJun.value === null || occupancyJun.value === '' || isNaN(occupancyJun.value) || parseFloat(occupancyJun.value) < 0.00 || parseFloat(occupancyJun.value) > 100.00){ occupancyJun.value = '0.00'; }
        else{ occupancyJun.value = parseFloat(occupancyJun.value).toFixed(2); }
        if(occupancyJul.value === null || occupancyJul.value === '' || isNaN(occupancyJul.value) || parseFloat(occupancyJul.value) < 0.00 || parseFloat(occupancyJul.value) > 100.00){ occupancyJul.value = '0.00'; }
        else{ occupancyJul.value = parseFloat(occupancyJul.value).toFixed(2); }
        if(occupancyAug.value === null || occupancyAug.value === '' || isNaN(occupancyAug.value) || parseFloat(occupancyAug.value) < 0.00 || parseFloat(occupancyAug.value) > 100.00){ occupancyAug.value = '0.00'; }
        else{ occupancyAug.value = parseFloat(occupancyAug.value).toFixed(2); }
        if(occupancySep.value === null || occupancySep.value === '' || isNaN(occupancySep.value) || parseFloat(occupancySep.value) < 0.00 || parseFloat(occupancySep.value) > 100.00){ occupancySep.value = '0.00'; }
        else{ occupancySep.value = parseFloat(occupancySep.value).toFixed(2); }
        if(occupancyOct.value === null || occupancyOct.value === '' || isNaN(occupancySep.value) || parseFloat(occupancySep.value) < 0.00 || parseFloat(occupancySep.value) > 100.00){ occupancyOct.value = '0.00'; }
        else{ occupancyOct.value = parseFloat(occupancyOct.value).toFixed(2); }
        if(occupancyNov.value === null || occupancyNov.value === '' || isNaN(occupancyNov.value) || parseFloat(occupancyNov.value) < 0.00 || parseFloat(occupancyNov.value) > 100.00){ occupancyNov.value = '0.00'; }
        else{ occupancyNov.value = parseFloat(occupancyNov.value).toFixed(2); }
        if(occupancyDec.value === null || occupancyDec.value === '' || isNaN(occupancyDec.value) || parseFloat(occupancyDec.value) < 0.00 || parseFloat(occupancyDec.value) > 100.00){ occupancyDec.value = '0.00'; }
        else{ occupancyDec.value = parseFloat(occupancyDec.value).toFixed(2); } 
      };

      const occupancyAvg = ref(0);
      const handleInputBlurOccupancy = () => {
        formatInputOccupancy();
        calculateOccupancy();
        calculateRevenue();
      };
      const calculateOccupancy = () => {
        formatInputOccupancy();
        const occupancyValues = [
          occupancyJan.value, occupancyFeb.value, occupancyMar.value, occupancyApr.value, occupancyMay.value,
          occupancyJun.value, occupancyJul.value, occupancyAug.value, occupancySep.value, occupancyOct.value,
          occupancyNov.value, occupancyDec.value
        ];
        const hasInvalidInput = occupancyValues.some(value => {
          const parsedValue = parseFloat(value);
          return isNaN(parsedValue) || parsedValue < 0 || parsedValue > 100;
        });
        if (hasInvalidInput) {
          //alert('Invalid input. Please enter positive numbers.');
          return;
        }
        const occupancySum = occupancyValues.reduce((sum, value) => sum + parseFloat(value), 0);
        occupancyAvg.value = occupancySum / 12;
        calculateRevenue();
      };

      const adrJan = ref('0.00');
      const adrFeb = ref('0.00');
      const adrMar = ref('0.00');
      const adrApr = ref('0.00');
      const adrMay = ref('0.00');
      const adrJun = ref('0.00');
      const adrJul = ref('0.00');
      const adrAug = ref('0.00');
      const adrSep = ref('0.00');
      const adrOct = ref('0.00');
      const adrNov = ref('0.00');
      const adrDec = ref('0.00');

      const handleKeyDown = (event) => {
        const allowedKeys = ['Backspace', 'Delete', 'Enter', '.'];
        if (!allowedKeys.includes(event.key) && (event.key < '0' || event.key > '9')) {
          event.preventDefault();
        }
      };

      const formatInputAdr = () => {
        adrJan.value = formatDecimalWithCommas(adrJan.value);
        adrFeb.value = formatDecimalWithCommas(adrFeb.value);
        adrMar.value = formatDecimalWithCommas(adrMar.value);
        adrApr.value = formatDecimalWithCommas(adrApr.value);
        adrMay.value = formatDecimalWithCommas(adrMay.value);
        adrJun.value = formatDecimalWithCommas(adrJun.value);
        adrJul.value = formatDecimalWithCommas(adrJul.value);
        adrAug.value = formatDecimalWithCommas(adrAug.value);
        adrSep.value = formatDecimalWithCommas(adrSep.value);
        adrOct.value = formatDecimalWithCommas(adrOct.value);
        adrNov.value = formatDecimalWithCommas(adrNov.value);
        adrDec.value = formatDecimalWithCommas(adrDec.value);
      };

      const adrAvgFormatted = computed(() => {
        const adrAvgValue = adrAvg.value;
        const roundedValue = Math.round(adrAvgValue * 100) / 100;
        return formatDecimalWithCommas(roundedValue);
      });

      const formatDecimalWithCommas = (value) => {
        let formattedValue = value.toString().replace(/,/g, '');
        const parts = formattedValue.split('.');
        let integerPart = parts[0];
        let decimalPart = parts[1] || '';
        let formattedIntegerPart = '';
        let count = 0;
        for (let i = integerPart.length - 1; i >= 0; i--) {
          formattedIntegerPart = integerPart[i] + formattedIntegerPart;
          count++;
          if (count % 3 === 0 && i !== 0) { formattedIntegerPart = ',' + formattedIntegerPart; }
        }
        formattedValue = formattedIntegerPart + (decimalPart ? '.' + decimalPart : '');
        if (decimalPart === '') { formattedValue += '.00'; }
        return formattedValue;
      };

      const adrAvg = ref(0);
      const handleInputBlurAdr = () => {
        calculateAdr();
        calculateRevenue();
        formatInputAdr();
      };
      const calculateAdr = () => {
        formatInputAdr();
        const adrValues = [
          adrJan.value, adrFeb.value, adrMar.value, adrApr.value, adrMay.value,
          adrJun.value, adrJul.value, adrAug.value, adrSep.value, adrOct.value,
          adrNov.value, adrDec.value
        ];
        const hasInvalidInput = adrValues.some(value => {
          const parsedValue = parseFloat(value.replace(/,/g, ''));
          return isNaN(parsedValue) || parsedValue < 0;
        });
        if (hasInvalidInput) {
          //alert('Invalid input. Please enter positive numbers.');
          return;
        }
        const adrSum = adrValues.reduce((sum, value) => sum + parseFloat(value.replace(/,/g, '')), 0);
        adrAvg.value = adrSum / 12;
        calculateRevenue();
      };

      const revJan = ref('0.00');
      const revFeb = ref('0.00');
      const revMar = ref('0.00');
      const revApr = ref('0.00');
      const revMay = ref('0.00');
      const revJun = ref('0.00');
      const revJul = ref('0.00');
      const revAug = ref('0.00');
      const revSep = ref('0.00');
      const revOct = ref('0.00');
      const revNov = ref('0.00');
      const revDec = ref('0.00');

      const calculateRevenue = () => {
        revJan.value = parseFloat(roomJan.value) * parseFloat(occupancyJan.value) * parseFloat(adrJan.value) * 31;
        revFeb.value = parseFloat(roomFeb.value) * parseFloat(occupancyFeb.value) * parseFloat(adrFeb.value) * 28;
        revMar.value = parseFloat(roomMar.value) * parseFloat(occupancyMar.value) * parseFloat(adrMar.value) * 31;
        revApr.value = parseFloat(roomApr.value) * parseFloat(occupancyApr.value) * parseFloat(adrApr.value) * 30;
        revMay.value = parseFloat(roomMay.value) * parseFloat(occupancyMay.value) * parseFloat(adrMay.value) * 31;
        revJun.value = parseFloat(roomJun.value) * parseFloat(occupancyJun.value) * parseFloat(adrJun.value) * 30;
        revJul.value = parseFloat(roomJul.value) * parseFloat(occupancyJul.value) * parseFloat(adrJul.value) * 31;
        revAug.value = parseFloat(roomAug.value) * parseFloat(occupancyAug.value) * parseFloat(adrAug.value) * 31;
        revSep.value = parseFloat(roomSep.value) * parseFloat(occupancySep.value) * parseFloat(adrSep.value) * 30;
        revOct.value = parseFloat(roomOct.value) * parseFloat(occupancyOct.value) * parseFloat(adrOct.value) * 31;
        revNov.value = parseFloat(roomNov.value) * parseFloat(occupancyNov.value) * parseFloat(adrNov.value) * 30;
        revDec.value = parseFloat(roomDec.value) * parseFloat(occupancyDec.value) * parseFloat(adrDec.value) * 31;
      };

      const formatRevenue = (value) => {
        const stringValue = value.toString();
        const integerPart = stringValue.slice(0, -2).replace(/\B(?=(\d{3})+(?!\d))/g, ',');
        const decimalPart = stringValue.slice(-2);
        return integerPart + '.' + decimalPart;
      };

      const formattedRevJan = computed(() => formatRevenue(revJan.value));
      const formattedRevFeb = computed(() => formatRevenue(revFeb.value));
      const formattedRevMar = computed(() => formatRevenue(revMar.value));
      const formattedRevApr = computed(() => formatRevenue(revApr.value));
      const formattedRevMay = computed(() => formatRevenue(revMay.value));
      const formattedRevJun = computed(() => formatRevenue(revJun.value));
      const formattedRevJul = computed(() => formatRevenue(revJul.value));
      const formattedRevAug = computed(() => formatRevenue(revAug.value));
      const formattedRevSep = computed(() => formatRevenue(revSep.value));
      const formattedRevOct = computed(() => formatRevenue(revOct.value));
      const formattedRevNov = computed(() => formatRevenue(revNov.value));
      const formattedRevDec = computed(() => formatRevenue(revDec.value));

      const totalRevenue = computed(() => {
        const sum = [
          revJan.value,
          revFeb.value,
          revMar.value,
          revApr.value,
          revMay.value,
          revJun.value,
          revJul.value,
          revAug.value,
          revSep.value,
          revOct.value,
          revNov.value,
          revDec.value,
        ].reduce((acc, value) => acc + parseFloat(value), 0);
        return formatRevenue(sum);
      });

      return {
        roomJan,
        roomFeb,
        roomMar,
        roomApr,
        roomMay,
        roomJun,
        roomJul,
        roomAug,
        roomSep,
        roomOct,
        roomNov,
        roomDec,
        ValidateInputRoom,
        calculateRooms,
        roomsAvg,
        occupancyJan,
        occupancyFeb,
        occupancyMar,
        occupancyApr,
        occupancyMay,
        occupancyJun,
        occupancyJul,
        occupancyAug,
        occupancySep,
        occupancyOct,
        occupancyNov,
        occupancyDec,
        formatInputOccupancy,
        calculateOccupancy,
        occupancyAvg,
        adrJan,
        adrFeb,
        adrMar,
        adrApr,
        adrMay,
        adrJun,
        adrJul,
        adrAug,
        adrSep,
        adrOct,
        adrNov,
        adrDec,
        handleKeyDown,
        formatInputAdr,
        calculateAdr,
        adrAvg,
        adrAvgFormatted,
        handleInputBlurRooms,
        handleInputBlurOccupancy,
        handleInputBlurAdr,
        formatDecimalWithCommas,
        calculateRevenue,
        revJan,
        revFeb,
        revMar,
        revApr,
        revMay,
        revJun,
        revJul,
        revAug,
        revSep,
        revOct,
        revNov,
        revDec,
        formatRevenue,
        formattedRevJan,
        formattedRevFeb,
        formattedRevMar,
        formattedRevApr,
        formattedRevMay,
        formattedRevJun,
        formattedRevJul,
        formattedRevAug,
        formattedRevSep,
        formattedRevOct,
        formattedRevNov,
        formattedRevDec,
        totalRevenue,
      };
    }
  };
</script>

<style>
  input{
    width: 100px;
    border: none;
  }
  input:hover{
    cursor: pointer;
  }
  input::-webkit-outer-spin-button,
  input::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }
</style>