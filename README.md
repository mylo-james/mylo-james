Hey there! 👋 

Here's a little bit about me!

```js
import coffee from 'starbucks';
import { moba } from 'online-gaming';

const aboutMe = {
  name: 'Mylo James',
  pronouns: 'He/Him',
  code: ['JavaScript', 'React', 'Redux', 'Express.js'],
  work: {
    job: 'Software Engineering Instructor',
    place: 'App Academy',
    task: 'lecturing',
  },
  favorites: {
    coffee: coffee.psl,
    movie: 'A Wes Anderson movie',
    game: moba.toxic.Dota2,
  },
};
```

Have you ever wondered what I'd look like as a component?

I'm sure you haven't... but here it is! 🤣

```jsx
import { drink } from 'native-code';
import { useCallback, useEffect, useState } from 'react';

const Mylo = ({ name, work, favorites, code }) => {
  let [currActivity, setCurrActivity] = useState('sleeping');
  
  const goToWork = useCallback(() => {
    setCurrActivity(`${work.task} about ${code.join(', ')} at ${work.place}`);
  }, [code, work]);

  useEffect(() => {
    (async () => {
      setCurrActivity('drinking coffee');
      const res = await fetch(`https://ordercoffee.com/${favorites.coffee}`);
      const { yum } = res.json();
      drink(yum);
      goToWork();
    })();
    return () => setCurrActivity('sleeping');
  }, [favorites.coffee, goToWork]);

  async function endWork() {
    const res = await fetch('https://check-if-friends-are-online.com');
    if (res.status === 200) {
      setCurrActivity(`playing ${favorites.game}`);
    } else {
      setCurrActivity(`watching ${favorites.movie}`);
    }
  }

  return (
    <>
      <h1>{`${name} is ${currActivity}`}</h1>
      {currActivity.endsWith(work.place) ? (
        <button onClick={endWork}>End Work</button>
      ) : (
        <button onClick={() => setCurrActivity('sleeping')}>Go to Sleep</button>
      )}
    </>
  );
};

export default Mylo;
```
