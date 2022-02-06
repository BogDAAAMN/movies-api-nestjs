# DEPT Movies API Nestjs

## Description

A movies API that provides basic information provided by TMDB. Built with [Nestjs](https://github.com/nestjs/nest).

## API References

hey

## Development
### Installation

```bash
$ git clone https://github.com/BogDAAAMN/movies-api-nestjs/
$ npm install
```

Create and edit an `.env` file, as seen in [`.env.example`](/.env.example).

```
TMDB_KEY=your-tmdb-priivate-key-here
TMDB_URL=https://api.themoviedb.org/3
```
  
You can get your `TMDB_KEY` API key by logging in to your [TMDB account](https://www.themoviedb.org/settings/account) and clicking the [API link](https://www.themoviedb.org/settings/api) of your account page. More details and screenshots on the [TMDB API Docs](https://developers.themoviedb.org/3/getting-started/introduction).

### Development

```bash
# watch mode
$ npm run start:dev
```

### Test

```bash
# unit tests
$ npm run test

# e2e tests
$ npm run test:e2e
```

The current unit tests coverage: (generated by [istanbul](https://istanbul.js.org/)) 

```
-----------------------|---------|----------|---------|---------|-
File                   | % Stmts | % Branch | % Funcs | % Lines | 
-----------------------|---------|----------|---------|---------|-
 src/movies            |     100 |    57.14 |     100 |     100 | 
  movies.controller.ts |     100 |      100 |     100 |     100 | 
  movies.service.ts    |     100 |    57.14 |     100 |     100 | 
 src/search            |     100 |      100 |     100 |     100 | 
  search.controller.ts |     100 |      100 |     100 |     100 | 
  search.service.ts    |     100 |      100 |     100 |     100 | 
 src/tmdb              |     100 |      100 |     100 |     100 | 
  tmdb.service.ts      |     100 |      100 |     100 |     100 | 
-----------------------|---------|----------|---------|---------|-
```

### Cache

The API uses the Nest built-in in-memory caching system. The data is stored in to the application's memory and it is served before making TMDB API requests (if possible). The current cache configuration is:

- `ttl`: 
  - 86400 for `/movies`
  - 3600 for `/search`
- `max`: 100k

Latency benchmark for `/movies` route (generated by [autocannon](https://github.com/mcollina/autocannon)):

```
Running 10s test @ http://localhost:3000/movies/550
10 connections
┌───────────────────┬────────┬────────┬────────┬────────┬───────────┬──────────┐
│ Stat              │ 2.5%   │ 50%    │ 97.5%  │ 99%    │ Avg       │ Stdev    │
├───────────────────┼────────┼────────┼────────┼────────┼───────────┼──────────┤
│ Non-cache Latency │ 103 ms │ 119 ms │ 187 ms │ 194 ms │ 124.17 ms │ 22.96 ms │
├───────────────────┼────────┼────────┼────────┼────────┼───────────┼──────────┤
│ Cache Latency     │   3 ms │   5 ms │  11 ms │  13 ms │   5.19 ms │  5.38 ms │
└───────────────────┴────────┴────────┴────────┴────────┴───────────┴──────────┘

- Non-cache: 166 requests in 10.02s,  123 kB read
- Cache:     18k requests in 10.01s, 13.9 MB read
```

### Security

hey

## License

- Nest is [MIT licensed](LICENSE).
- TMDb offers the API service for free as long as you properly attribute the source of the data and/or images used.
