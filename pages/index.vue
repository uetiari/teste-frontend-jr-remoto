<template>
  <div class="leads">
    <Logo />
    <!-- <Logo dark-background /> -->
    <h1 class="leads__title">Leads</h1>
    <main>
      
    </main>
  </div>
</template>

<script>
async function getContent() {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/users')
    const data = await response.json()

    show(data)
  } catch (error) {
    console.log(error)
  }
}

getContent()

function show(users) {
  let output = ''
  for (let user of users) {
    output += `
    <div class="leads__contact">
      <div class="leads__userphoto">
        <User />
      </div>
      <div class="leads__info">
        <ul>
          <li>Name: ${user.name}</li>
          <li>Email: ${user.email}</li>
          <li>Phone: ${user.phone}</li>
          <li>Website: 
            <a href="${user.website}" target="_blank">${user.website}</a></li>
          <li>Company: ${user.company.name}</li>
        </ul>
      </div>
      <div class="leads__address">
        <ul>
          <li>Street: ${user.address.street}</li>
          <li>Suite: ${user.address.suite}</li>
          <li>City: ${user.address.city}</li>
          <li>Zip Code: ${user.address.zipcode}</li>
        </ul>
      </div>
    </div>
    `
  }

  document.querySelector('main').innerHTML = output
}
</script>

<style lang="scss" scoped="true">
.leads {
  &__title {
    margin: 1rem 0;
    padding: 1.4rem 0;
    border-top: $border-color 1px solid;
  }
}
</style>
