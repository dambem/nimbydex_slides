
---
layout: center
class: text-center
---
# Big Statistics
---
---

# Frontend: First Svelte Experience

<div grid="~ cols-2 gap-4">
<div>
````md magic-move 
```javascript 
// - Hardest Part was integrating 
// Tailwindcss + daisyUI
// - Svelte data loading is pristine
// - Far easier to do javascript & reactivity
//+page.svelte
<script>
  import Map from '$lib/Map.svelte';
  export let data;
</script>  

<Map points={data.points} 
nimby_score={data.nimby_score}/>
```
```javascript 
//+page.js
export async function load({ fetch }) {
    try {
      const response = await fetch('/points.geojson'); 
      const nimby_r = await fetch('/nimby_score.json');  

      const geojson = await response.json();
      const nimby_score = await nimby_r.json();
      
      return {
        points: geojson.features,
        nimby_score: nimby_score
      };
    } catch (error) {
      console.error('Error loading GeoJSON:', error);
      return {
        points: []
      };
    }
  }
```

```javascript
### LOOK AT HOW CLEAN THIS LOOKS
#### I HATE REACT I HATE REACT I HATE REACT

// components/Map.svelte
<div class="grid grid-cols-2 gap-4" 
class:hidden={selectedFeature}>
    {#each stats as stat}
        <div class="stat shadow bg-base-100">
            <div class="stat-title">{stat.label}</div>
            <span class="stat-value">{stat.value}</span>
            <span class="stat-desc">{stat.trend}</span>
        </div>
    {/each}
</div>
```

````

</div>
<div>
<img src="./assets/svelte_bf.webp" class="h-100 rounded shadow" />
</div>
</div>


---
layout: center
---

# Kryptonite of Gemini API  - Massive PDFs

<v-clicks>

- PDFs tend to be massive council minutes filled with irrevelant information
- Gemini has 1 mil token context length
- But API Costing is finite 

- Need to work out a better parsing method for large minutes.
</v-clicks>


---


# Challenges 

<v-clicks>

- MapGL Filtering is a labyrinth
- Dealing with massive PDF documents (even gemini can't deal with the pointless context length of council minutea)
- Google Search API rate limits
- Gemini sometimes getting too sassy with commentary
</v-clicks>

```js {*}{maxHeight:'250px'}
const accuracy1 = nimby_score.filter(item => item['Accuracy Score'] >= 70)
const accuracy2 = nimby_score.filter(item => item['Accuracy Score'] < 70)

const nimbyRefIds = new Set(accuracy1.map(item => item.refid || ''));
const nimbyRefIds2 = new Set(accuracy2.map(item => item.refid || ''));

// You expect me to believe this is logical?
'circle-color': [
    'case',
    ['boolean', ['feature-state', 'selected'], false],
    '#fbb03b',  
    [
        'case',
        ['in', ['get', refProperty], ['literal', [...nimbyRefIds]]],
        '#a8323a',  
        [
        'case',    
            ['in', ['get', refProperty], ['literal', [...nimbyRefIds2]]],
            '#ffa000',
            '#d3d3d3'   
        ]
    ]
],
```

