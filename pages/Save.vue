<script setup lang="ts">
// const data = await useFetch("https://v3.football.api-sports.io/leagues", {
//   method: "GET",
//   headers: {
//     "x-rapidapi-host": "v3.football.api-sports.io",
//     "x-rapidapi-key": "082cef903c18d9f143583be71fb6bd86",
//   },
// }).catch((error) => console.log("error", error));

const config = useRuntimeConfig();

const teamData = await useFetch(
  "https://v3.football.api-sports.io/teams?id=33",
  {
    method: "GET",
    headers: {
      "x-rapidapi-host": "v3.football.api-sports.io",
      "x-rapidapi-key": "082cef903c18d9f143583be71fb6bd86",
      // "x-rapidapi-key": config.public.FOOTBALL_API_KEY as string,
    },
  }
);

const statistics = await useFetch(
  "https://v3.football.api-sports.io/teams/statistics",
  {
    method: "GET",
    headers: {
      "x-rapidapi-host": "v3.football.api-sports.io",
      "x-rapidapi-key": "082cef903c18d9f143583be71fb6bd86",
      // "x-rapidapi-key": config.public.FOOTBALL_API_KEY as string,
    },
    params: {
      team: 33,
      league: 39,
      season: 2022,
    },
  }
);

const standing = await useFetch("https://v3.football.api-sports.io/standings", {
  method: "GET",
  headers: {
    "x-rapidapi-host": "v3.football.api-sports.io",
    "x-rapidapi-key": "082cef903c18d9f143583be71fb6bd86",
    // "x-rapidapi-key": config.public.FOOTBALL_API_KEY as string,
  },
  params: {
    league: 39,
    season: 2022,
  },
});
</script>

<template>
  <div>
    <div>
      <NuxtImg src="https://media.api-sports.io/football/teams/33.png" />
    </div>
    result
    <!-- <pre>{{ teamData }}</pre>
    <pre>{{ statistics }}</pre> -->
    <pre>{{ standing }}</pre>
  </div>
</template>
