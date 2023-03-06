# Live Search Results

To suggest Pokemon that match what is typed by the user in a search box in a React JS form using the Pokemon API, you can follow these steps:

1. Create a state variable to store the user's input value and a state variable to store the suggested Pokemon data.

```javascript
const [searchValue, setSearchValue] = useState("");
const [suggestedPokemon, setSuggestedPokemon] = useState([]);
```

1. Create a function to handle the user's input change and make an API call to get the suggested Pokemon data.

```javascript
const handleSearchInputChange = async (event) => {
  const value = event.target.value;
  setSearchValue(value);

  if (value.length > 0) {
    const response = await fetch(`https://pokeapi.co/api/v2/pokemon?limit=5&offset=0&search=${value}`);
    const data = await response.json();
    setSuggestedPokemon(data.results);
  } else {
    setSuggestedPokemon([]);
  }
};
```

In this example, we limit the suggested Pokemon data to five results and search for Pokemon names that contain the user's input value.

1. Render the search box input and the suggested Pokemon data.

```javascript
<div>
  <input type="text" value={searchValue} onChange={handleSearchInputChange} />
  {suggestedPokemon.length > 0 && (
    <ul>
      {suggestedPokemon.map((pokemon) => (
        <li key={pokemon.name}>{pokemon.name}</li>
      ))}
    </ul>
  )}
</div>
```

In this example, we render the suggested Pokemon names as an unordered list.

With these steps, you can suggest Pokemon that match what is typed by the user in a search box in a React JS form using the Pokemon API.
