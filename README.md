# ScssLearnings
- Sycntaticaly awesome StyleSheet
- Scss is the preprocessor for css with features like variables,functions,loops
- npm sass i -d 
- download developer dependency
- "start":"sass ./css/style.scss ./css/style.css --watch"
- to create a compiled css file and --Watch is used to live compile
- npm start to get compiled css file
  ### variables partial
- Example
- $primary-color:#3498db;
### Nesting
- Example
- nav{
    background-color: #222;
    a{
        color: #fff;
        &:last-child{
            color: #ffd000;
        }
        &:nth-child(2){
            color: red;
        }
        &:hover{
            color: greenyellow;
        }
    }

}
### Mixin
- The @mixin directive lets you create CSS code that is to be reused throughout the website
- The @include directive is created to let you use (include) the mixin.
- Example
- @mixin button($back-color,$text-color){
    background-color: $back-color;
    color:$text-color;
    border-radius: 5px;
    &:hover{
        background-color: darken($back-color,10%);
    }
}
-- darken in nuil method used to dark the color
.button-primary{
    @include button(#7aa4ba, white)
}
.button-win{
    @include button(red, white)
}
.button-lose{
    @include button(green, white)

}
### Maps
- Maps in Sass hold pairs of keys and values, and make it easy to look up a value by its corresponding key.
- Example
- $colors:(
    "primary":#3498db,
    "win":#198754,
    "lose":#dc3545,
    "info":tomato
);


@debug map-get($colors,"primary"); //get the value saved in key 
@debug map-has-key($colors,"win"); //return true
@debug map-has-key($colors,"wanted"); //return false
@debug map-remove($colors,"info");// reomve the key
@debug map-merge($colors , ( //add new key value pair
    "sec":violet
));
### Each loop
- Example
- @each $key,$val in $colors{ //geting the key and value from the colors variable
    .text-#{$key}{ //string interpolation
        color:$val;
    }
    .bg-#{$key}{
        background-color: $val;
    }
    .text-white{
        color: white;
    }
  }
  ### forLoop
  - Example
  - @for $i from 1 through 3{
        .text-#{$key}-lighten-#{$i}{
            //color:lighten($color: #000000, $amount: 0)
            color:lighten($val, $i*10);
        }
        .bg-#{$key}-lighten-#{$i}{
            //color:lighten($color: #000000, $amount: 0)
            background-color:lighten($val, $i*10);
        }
    }
    ## IF Else
    - Example
    - @if($width>=600px){
    background-color: yellow;
      }
     @else{
     backgorung-color:red;
      }
  ### Functions
- @function px_to_rem($px){
    @return ($px/16)+rem;
}

