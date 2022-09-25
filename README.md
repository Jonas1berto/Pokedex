# Projeto Pokedex

## Consumindo pela primeira vez uma api.
### Api utilizada https://pokeapi.co/

## Tecnologias usadas no Projeto
- ![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white)   
- ![CSS3](https://img.shields.io/badge/css3-%231572B6.svg?style=for-the-badge&logo=css3&logoColor=white)    
- ![JavaScript](https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E)

# Aqui é onde verifico o status da Api.
## Ela so vai funcionar se o status dela for igual a 200.

```
const fetchPokemon = async (pokemon) => {
  const APIResponse = await fetch(`https://pokeapi.co/api/v2/pokemon/${pokemon}`)

  if (APIResponse.status === 200) { 
    const data = await APIResponse.json()
    return data;
  }
}
```

# Buscando o pokemon na api pelo Id ou nome, se o pokemon existir na api vai ser mostrado na tela, se não, vai mostrar uma mensagem de error.

```
const renderPokemon = async (pokemon) => {
  pokemonName.innerHTML = 'Loading...'
  pokemonNumber.innerHTML = ''

  const data = await fetchPokemon(pokemon)
  if (data) {
    pokemonImage.style.display = 'block'
    pokemonName.innerHTML = data.name;
    pokemonNumber.innerHTML = data.id;
    pokemonImage.src = data['sprites']['versions']['generation-v']['black-white']['animated']['front_default']; 
    input.value = ''
    searchPokemon = data.id
  } else {
    pokemonImage.style.display = 'none'
    pokemonName.innerHTML = 'Not Found'
    pokemonNumber.innerHTML = ''
  }
}
```
