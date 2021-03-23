<!--
@component
  ### FetchData
  A reusable fetch function, that takes 2 argument
  -- url (the path to the resource you want to fetch) and
  -- second parameter (object that allows you to control different settings).

  - @props **url** string: ''
  - @props **settings** object: {}
-->
<!-- context="module" -> attribute runs once when the module first evaluates, rather than for each component instance -->
<script lang="ts" context="module">
  export const fetchData = async (url: string, settings: object) => {
    const response = await fetch(url, {
      headers: {
        'Content-Type': 'application/json'
      },
      ...settings
    })

    return await response.json() // parses JSON response into native JavaScript objects
  }
</script>

