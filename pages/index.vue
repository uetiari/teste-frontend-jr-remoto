<template>
  <div class="leads">
    <Logo />
    <!-- <Logo dark-background /> -->
    <h1 class="leads__title">Leads</h1>
    <div class="searchbox">
      <input type="text" id="search_name" name="name" placeholder="Search by Name" />
      
      <input type="text" id="search_name" name="company" placeholder="Search by Company Categories" />
    </div>
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
    <!-- Foto do usuário -->
      </div>
      <div class="leads__info">
        <ul>
          <li><b>Name:</b> ${user.name}</li>
          <li><b>Email:</b> ${user.email}</li>
          <li><b>Phone:</b> ${user.phone}</li>
          <li><b>Website:</b> 
            <a href="${user.website}" target="_blank">${user.website}</a></li>
          <li><b>Company:</b> ${user.company.name}</li>
        </ul>
      </div>
      <div class="leads__address">
        <ul>
          <li><b>Street:</b> ${user.address.street}</li>
          <li><b>Suite:</b> ${user.address.suite}</li>
          <li><b>City:</b> ${user.address.city}</li>
          <li><b>Zip Code:</b> ${user.address.zipcode}</li>
        </ul>
      </div>
    </div>
    `
  }

  document.querySelector('main').innerHTML = output
}

function filterByName() {

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
