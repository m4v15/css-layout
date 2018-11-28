# Mentor Notes

Generally it is good to show you messing around and changing the CSS in dev tools, then put it in the file, below is a loose script

## Steps 1-3 - mobile

### Step 1 - Flex

- Seems ok, but a & b are wrong, size are wrong
- Flexbox will help us here 
- *Give container class `display:flex;`*
- Will default to `direction:row`, change to column
- a & b still wrong - if you look at the design they are like 1 row of the flex box, so we can wrap them in a div, with a class `a-b` (Would be title or header or something in real life)
- Looks like this does nothing, until you give it `display:flex`

### Step 2 - grow and basis

- Ask how we can make the a/b ratio correct
- Use `flex-basis` you can set the size - if you give `b` `50%`, you can see it will be 50% of the parent container width :tada:
- `flex-grow` allows our items to use the empty space, can give both items `flex-grow` of 1 to split the emtpy space evenly between them
- this can be shortened to the `flex` syntax, where the first number is `flex-grow` and the second value is `flex-basis` when it's a % or px value (if it's unitless it becomes `flex-shrink`)
- should do the same with the rest items in the main container - everything can have a flex-grow of 1 and change the basis appropriately. This can be annoying to work out, just get close enough
- note that `a-b` is one of the flex items here, `a` and `b` are not

### Step 3 - Margin

- Finally need a margin - add `10px` to `content` class

## Steps 4 - 8 Desktop

- So now we need to style the desktop - do the below in the media query for the desktop size, `@media (min-width: 768px)`

### Step 4 - change direction

- Design gives the container a different height - set height to `70vh`
- This makes a mess of the rest of it
- look at the design can see the direction of things is basically now a row
- Change `flex-direction` to `row`

### Step 5 - define the sections

- Break the design into 3 sections
- Create div's around a,b,c,d & e and also around g&h
- should be reflected in the render of the HTML
- sizes are wrong, now need to give these flex items `flex:1 x%`
- the first one should be 50% then 25% and 25% 

### Step 6 - a flex within a flex 

- So now we need to take each section (a-e, f, g-h) and do their internal layouts
- Give `g-h` display `flex` and change the direction to `column`
- The content's already have flex grow so we are nearly there already.
- however, a bit wrong - in the media query let's give `g` `flex:1 60%`, `h` `flex:1 20%`

### Step 7 - a flex within a flex within a flex!

- Give `a-b-c-d-e` display `flex` and change the direction to `column`
- The content's already ahve flex grow so we are nearly there already.
- however, now c d and e need to be in the same row... wrap them!
- give this new div `display` `flex` and `direction` `row`
- but now c & d need their own thing!
- wrap, give `flex` and `column`

### Step 8 - growing pains

- Now we just need to set the flex grow and basis correctly for this left hand column (contents a-e)
- fiddle in dev tools! first lets do the two outer sections - a-b & c-d-e
- a-b already has `flex` `1 10%` from the mobile design so leave that
- give `c-d-e` `1 25%` should look decent.
- Now lets do the a-b container
- lets give a `1 30%` and b `1 70%`
- Now onto the `c-d-e` container - `c-d` should have 
- Finally, c & d are good how they are!

## Finished...? Nope
### Step 9... Uh Oh
- :tada: oh wait, lets check we haven't ruined the mobile design with all our new div's...
- damn, what can we do now...

- Lets go back to our design and now think about it in the sections of the divs...
- Hm actually we have 3 evenly sized sections!
- Copy and paster the sections (`a-b-c-d-e`, `g-h`) css to outside of the media query and give them  `flex:1` (i.e. lose the 50%)
- back in the media query, we can delete the bits we copied, except for the `flex:1 x%`
- we should also change the `.f` class outside to just have `flex:1`

### Step 10 Almost there!
- now we can change the individual elements `flex` property according to their own section - outside of the media query
- For `a-b-c-d-e` section, we have `a-b` which is already outside of the media query, and `c-d-e` which we need to copy and paste out - making sure to change the `flex-direction` to column. We should change the `flex` to `1 50%`
- We can then delete the `display` part inside the media query
- We need to do the same for `c-d-e` section - `c-d-e` can come out, and be give `flex: 1 50%` and e can have `flex: 1 10%` Remember to delete the repeated stuff in the media query
- Lets do the `g-h` section now, this is easier as we have already pulled the bit out of the media query
- give `g` `flex: 1 75%` and `h` `flex: 1 25%`

## Finished! :tada:

- Nice work, now it looks exactly like the design! 
- Make sure nothing has broken in then desktop version. 



