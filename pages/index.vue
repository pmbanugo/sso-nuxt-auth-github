<script setup lang="ts">
const { status, signIn, signOut, data } = useAuth()

const loggedIn = computed(() => status.value === 'authenticated')

async function handleSignIn() {
  await signIn()
}

async function handleSignOut() {
  await signOut()
}
</script>

<template>
  <section class="dashboard" aria-label="User Dashboard">
    <aside class="dashboard-sidebar">
      <figure class="profile-picture-container">
        <img class="profile-picture" 
             :src="data?.user?.image" 
             :alt="`Profile Picture of ${data?.user?.name}`" />
      </figure>
      <nav class="dashboard-nav">
        <ul>
          <li><a href="#overview">Overview</a></li>
          <li><a href="#settings">Settings</a></li>
          <li><a href="#reports">Reports</a></li>
        </ul>
      </nav>
      <div class="dashboard-actions">
        <button v-if="loggedIn" 
                class="btn sign-out" 
                @click="handleSignOut"
                aria-label="Sign Out Button">Sign Out</button>
        <button v-else 
                class="btn sign-in" 
                @click="handleSignIn"
                aria-label="Sign In Button">Sign In</button>
      </div>
    </aside>
    <main class="dashboard-main">
    <h1 class="dashboard-title">Hi, <span v-if="data?.user?.name">{{data.user.name}},</span> welcome to your dashboard</h1>
    <div class="dashboard-content">
      <!-- A simple bar chart -->
      <div class="analytics-section">
        <h2>Website Traffic</h2>
        <!-- Replace with a real chart component and data -->
        <div class="bar-chart-placeholder">Bar Chart</div>
      </div>

      <!-- A simple data table -->
      <div class="analytics-section">
        <h2>Recent User Signups</h2>
        <!-- Replace with a real table component and data -->
        <table>
          <tr>
            <th>Name</th>
            <th>Email</th>
            <th>Signup Date</th>
          </tr>
          <tr>
            <td>John Doe</td>
            <td>john.doe@example.com</td>
            <td>2023-06-15</td>
          </tr>
          <!-- More rows go here... -->
        </table>
      </div>
    </div>
  </main>
  </section>
</template>

<style scoped>
.dashboard {
  display: flex;
  background-color: #f1f1f1;
  padding: 20px;
  border-radius: 4px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.12), 0 1px 2px rgba(0, 0, 0, 0.24);
  height: 100vh;
}

.dashboard-sidebar {
  width: 20%;
  padding-right: 20px;
}

.profile-picture-container {
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
}

.profile-picture {
  width: 120px;
  height: 120px;
  object-fit: cover;
  border-radius: 50%;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.dashboard-nav {
  margin-bottom: 20px;
}

.dashboard-nav ul {
  list-style-type: none;
  padding: 0;
}

.dashboard-nav li {
  margin-bottom: 10px;
}

.dashboard-actions {
  margin-bottom: 20px;
}

.dashboard-main {
  flex-grow: 1;
  padding-left: 20px;
  border-left: 1px solid #ddd;
}

.dashboard-title {
  font-size: 24px;
  margin-bottom: 20px;
  color: #333;
}

.dashboard-content {
  /* add styles for the main content area */
}

.btn {
  display: block;
  width: 100%;
  padding: 10px 20px;
  font-size: 16px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.3s ease;
}

.btn:hover {
  transform: scale(1.05);
}

.sign-out {
  background-color: #dc3545;
  color: #fff;
  margin-top: 10px;
}

.sign-out:hover {
  background-color: #c82333;
}

.sign-in {
  background-color: #007bff;
  color: #fff;
  margin-top: 10px;
}

.sign-in:hover {
  background-color: #0069d9;
}
.dashboard-content {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
  }

  .analytics-section {
    width: 45%;
    margin-bottom: 20px;
    background-color: #fff;
    padding: 20px;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.12), 0 1px 2px rgba(0, 0, 0, 0.24);
  }

  .bar-chart-placeholder, table {
    width: 100%;
    height: 200px;  /* Adjust based on your needs */
  }

  table {
    border-collapse: collapse;
    text-align: left;
  }

  table th, table td {
    border-bottom: 1px solid #ddd;
    padding: 10px;
  }
</style>

