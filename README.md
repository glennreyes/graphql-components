# graphql-components

## Install

```
yarn add graphql-components
```

## Usage

```js
import { gql } from 'graphql-components';

const GetDogsQuery = gql`
  query GetDogs {
    dogs {
      id
      name
    }
  }
`;

const GoodDogsBrent = () => (
  <GetDogsQuery>
    {({ loading, error, data }) => {
      if (error) return <Error />
      if (loading || !data) return <Fetching />

      return <DogList dogs={data.dogs} />
    }}
  </GetDogsQuery>
)
```

Or use `.graphql` files directly by adding following loader to your webpack config;

```js
{
  test: /\.graphql/,
  use: 'graphql-components/loader',
},
```

```js
import GetDogsQuery from './getDogsQuery.graphql';

const GoodDogsBrent = () => (
  <GetDogsQuery>
    {({ loading, error, data }) => {
      if (error) return <Error />
      if (loading || !data) return <Fetching />

      return <DogList dogs={data.dogs} />
    }}
  </GetDogsQuery>
)
```
