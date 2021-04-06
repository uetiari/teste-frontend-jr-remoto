<template>
  <div class="leads">
    <Logo />
    <!-- <Logo dark-background /> -->
    <h1 class="leads__title">Leads</h1>
    <main>
      <table>
        <thead>
          <tr>
            <th>Name</th>
            <th>Email</th>
            <th>Phone</th>
            <th>Company Name</th>
            <th></th>
          </tr>
        </thead>
        <tbody>

        </tbody>
      </table>
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
    <tr>
      <td>${user.name}</td>
      <td>${user.email}</td>
      <td>${user.phone}</td>
      <td>${user.company.name}</td>
      <td>More info</td>
      <hr />
    </tr> <hr />
    `
  }

  document.querySelector('tbody').innerHTML = output
}
</script>

<style lang="scss" scoped="true">
.leads {
  &__title {
    margin: 1.4rem 0;
    padding: 1.4rem 0;
    border-top: $border-color 1px solid;
  }
}
</style>
