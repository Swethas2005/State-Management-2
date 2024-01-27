# State-Management-2

### [why the console.log shows the older value of count ?]
Ans: Imagine you have a robot friend, and you give it a task. In this case, you're telling your robot friend to count how many times you click a button. You also want your friend to tell you the count every time you click the button.

Now, your robot friend is a bit slow. When you tell it to count, it takes a little time to update its count. So, when you ask your friend to tell you the count immediately after you tell it to increase, it hasn't finished counting yet. It's like asking your friend, "How many candies do I have now?" right after you gave them more candies. They haven't finished counting, so they'll give you the old number until they finish counting.

In the same way, when you click the button, React (which is like your robot friend) takes a little time to update the count. So, when you ask React to show you the count right after telling it to increase, it shows the older count because it hasn't finished updating yet.

###### [Here is the corrected code..⬇️]

import React from 'react';

function App() {
  const [count, setCount] = React.useState(0);

  const handleClick = () => {
    setCount((prevCount) => {
      const newCount = prevCount + 1;
      console.log(newCount); 
      return newCount;
    });
  };

  return (
    <div>
      <p>Button is clicked {count} times</p>
      <button onClick={handleClick}>Click Me</button>
    </div>
  );
}

export default App;

**************************************************


 ### [why count value is not updated to 3 as expected ?]
 Ans: imagine you have a toy that you can count, like candies. Let's say you start with 0 candies. Now, you want to add 1, 1, and 1 more candy to your count when you press a button three times.

So, you have a counter (let's call it count) set to 0. When you press the button, you want to add 1 candy three times. But here's the tricky part: every time you press the button, it's like asking someone else (let's call them the "setCount helper") to add 1 candy to your count. However, the helper doesn't know the current count; they only know the original count (which is 0 in the beginning).

So, when you press the button for the first time, you tell the helper, "Hey, add 1 candy to the count." The helper adds 1, and now your count is 1. But here's where it gets tricky: when you press the button again and again, you keep telling the helper, "Add 1 candy to the count." However, the helper always starts from the original count (0) and adds 1, so it doesn't remember the new count from before.

So, even though you pressed the button three times, each time the helper started counting from the original 0, and your count didn't get updated the way you expected. That's why the count value is not updated to 3 as you thought it would be.
import React from 'react';

 ### [If you want to update the value 3 as expected here is the corrected code⬇️]

function App2() {
  const [count, setCount] = React.useState(0);

  const handleClick = () => {
    // Use the functional form of setCount to ensure correct state updates
    setCount((prevCount) => prevCount + 1);
    setCount((prevCount) => prevCount + 1);
    setCount((prevCount) => prevCount + 1);
    console.log(count); // Will log the updated count
  };

  return (
    <div>
      <p>Button is clicked {count} times</p>
      <button onClick={handleClick}>Click Me</button>
    </div>
  );
}

export default App2;

************************************************