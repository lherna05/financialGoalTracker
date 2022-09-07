<script>
import { writable } from 'svelte/store';

let renderData = writable([
    { component: 'Answer', count: 5},
    { component: 'App', count: 5},
    { component: 'Bank', count: 15},
    { component: 'Board', count: 5},
    { component: 'Guess', count: 8}, 
    { component: 'Question', count: 9}, 
    { component: 'Team', count: 9}
  ]); 


</script>>