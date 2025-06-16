<template>
  <div class="container">
    <h1>Barangay Mineral Water Delivery</h1>
    <form @submit.prevent="submitOrder">
      <input v-model="form.name" type="text" placeholder="Your Name" required />
      <input v-model="form.address" type="text" placeholder="Address" required />
      <input v-model="form.contact" type="tel" placeholder="Contact Number" required />

      <select v-model="form.waterType" required>
        <option disabled value="">Select Water Type</option>
        <option>Container (5 Gallons)</option>
        <option>Bottled (1L)</option>
      </select>

      <input v-model="form.deliveryTime" type="time" required />

      <select v-model="form.paymentMethod" required>
        <option disabled value="">Mode of Payment</option>
        <option>Gcash</option>
        <option>Cash</option>
      </select>

      <p v-if="form.paymentMethod === 'Gcash'" class="gcash-info">
        📱 Send payment to: <strong>09123456789</strong>
      </p>

      <textarea v-model="form.remarks" placeholder="Remarks (optional)"></textarea>
      <button type="submit">Place Order</button>
    </form>

    <div v-if="orders.length" class="orders">
      <h2>My Orders</h2>
      <ul>
        <li v-for="(order, index) in orders" :key="index">
          {{ order.name }} - {{ order.waterType }} @ {{ order.deliveryTime }}<br>
          Mode of Payment: {{ order.paymentMethod }}<br>
          Remarks: {{ order.remarks || 'N/A' }}<br>
          OR #: {{ order.orNumber }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'WaterHome',
  data() {
    return {
      form: {
        name: '',
        address: '',
        contact: '',
        waterType: '',
        deliveryTime: '',
        paymentMethod: '',
        remarks: '',
      },
      orders: [],
      orCounter: 1,
    };
  },
  methods: {
    submitOrder() {
      const orNumber = `OR-${this.orCounter.toString().padStart(4, '0')}`;
      this.orders.push({
        ...this.form,
        orNumber,
      });
      this.orCounter++;

      // Clear form
      this.form = {
        name: '',
        address: '',
        contact: '',
        waterType: '',
        deliveryTime: '',
        paymentMethod: '',
        remarks: '',
      };
    },
  },
};
</script>

<style scoped>
.container {
  max-width: 500px;
  margin: auto;
  padding: 1rem;
}
input, select, button, textarea {
  display: block;
  width: 100%;
  margin: 0.5rem 0;
  padding: 0.5rem;
}
button {
  background-color: #2c3e50;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
button:hover {
  background-color: #1a252f;
}
.orders {
  margin-top: 1rem;
  background: #f9f9f9;
  padding: 1rem;
  border-radius: 8px;
}
textarea {
  resize: vertical;
}
.gcash-info {
  background: #e3f2fd;
  padding: 0.5rem;
  border-radius: 5px;
  margin-bottom: 0.5rem;
  font-weight: bold;
  color: #0d47a1;
}

</style>
