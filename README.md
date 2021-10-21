Hey there! 👋 

Have you ever wondered what I'd look like as a component?

I'm sure you haven't... but here it is! 🤣

```jsx
import coffee from 'starbucks';
import { moba } from 'online-gaming';
import { drink } from 'native-code';
import { useEffect, useState } from 'react';

const aboutMe = {
  name: 'Mylo James',
  pronouns: 'He/Him',
  code: [
    'JavaScript',
    'React',
    'Redux',
    'Express.js',
    'Python',
    'Flask',
    'PostgreSQL',
  ],
  work: {
    job: 'Software Engineering Instructor',
    place: 'App Academy',
    task: 'lecturing',
  },
};

const favorites = {
  coffee: coffee.pumpkinSpice,
  movie: 'A Wes Anderson movie',
  game: moba.toxic.Dota2,
};

const Mylo = () => {
  let [currActivity, setCurrActivity] = useState('sleeping');

  useEffect(() => {
    (async () => {
      setCurrActivity('drinking coffee');
      const res = await fetch(`https://ordercoffee.com/${favorites.coffee}`);
      const { yum } = res.json();
      drink(yum);
      goToWork();
    })();
    return () => setCurrActivity('sleeping');
  }, []);

  function goToWork() {
    setCurrActivity(
      `${aboutMe.work.task} about ${aboutMe.code.join(', ')} at ${
        aboutMe.work.place
      }`
    );
  }

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
      <h1>{`${aboutMe.name} is ${currActivity}`}</h1>
      {currActivity.endsWith(aboutMe.work.place) ? (
        <button onClick={endWork}>End Work</button>
      ) : (
        <button onClick={() => setCurrActivity('sleeping')}>Go to Sleep</button>
      )}
    </>
  );
};

export default Mylo;

```
