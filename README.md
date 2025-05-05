# Third-Party Packages Cheat Sheet 🚀

This cheat sheet provides a quick reference for using third-party packages in React applications. It covers the advantages, selection criteria, and examples of popular third-party packages such as `react-player`, `recharts`, `react-chrono`, `react-slick`, and `reactjs-popup`.

## Concepts in Focus 🔍

### Third-Party Packages

#### Advantages ✅
- **Easy Integration**: Simplifies the process of adding new functionalities.
- **Time-Saving**: Reduces development time by providing pre-built solutions.
- **Productivity**: Enhances productivity with fewer lines of code.
- **Error Handling**: Often comes with robust error handling mechanisms.
- **Customization**: Offers more customization options to fit specific needs.

#### Selecting a Third-Party Package 🔍
When choosing a third-party package, consider the following:
- **User Satisfaction**: Check reviews and ratings.
- **Popularity**: Look at the number of stars and downloads.
- **Maintenance**: Ensure the package is actively maintained.
- **Documentation**: Good documentation is crucial for ease of use.
- **Unresolved Issues**: Fewer unresolved issues indicate a more stable package.

### Third-Party Package: `react-player` 🎬

`react-player` is a React component for playing various URLs, including file paths, YouTube, Facebook, etc.

#### Installation
```bash
npm install react-player
```

#### React Player Props
| Prop      | Description                                      | Default Value |
|-----------|--------------------------------------------------|---------------|
| `playing` | Set to true or false to pause or play the media  | `false`       |
| `controls`| Display native player controls                  | `false`       |
| `light`   | Show video thumbnail, loads full player on click| `false`       |
| `width`   | Set the width of the player                     | `640px`       |
| `height`  | Set the height of the player                    | `360px`       |
| `className`| Add custom styles to ReactPlayer                | -             |

#### Example
```jsx
import ReactPlayer from 'react-player';

const videoURL = 'https://youtu.be/YE7VzlLtp-4';
const VideoPlayer = () => (
  <div className="video-container">
    <h1 className="heading">Video Player</h1>
    <div className="responsive-container">
      <ReactPlayer url={videoURL} controls />
    </div>
  </div>
);

export default VideoPlayer;
```

### Third-Party Package: `recharts` 📊

`recharts` is a third-party package to display charts in your application. It supports various types of charts like Bar Chart, Pie Chart, Area Chart, etc.

#### Installation
```bash
npm install recharts
```

#### Advantages ✅
- **Responsive**: Adapts to the size of the parent container.
- **Built for React**: Designed specifically for React applications.
- **Customizable**: Highly customizable to fit your needs.

#### Bar Chart Example
```jsx
import { BarChart, Bar, XAxis, YAxis, Legend, ResponsiveContainer } from 'recharts';

const data = [
  { group_name: 'Group A', boys: 200, girls: 400 },
  { group_name: 'Group B', boys: 3000, girls: 500 },
  { group_name: 'Group C', boys: 1000, girls: 1500 },
  { group_name: 'Group D', boys: 700, girls: 1200 },
];

const App = () => {
  const DataFormatter = (number) => {
    if (number > 1000) {
      return `${(number / 1000).toString()}k`;
    }
    return number.toString();
  };

  return (
    <ResponsiveContainer width="100%" height={500}>
      <BarChart data={data} margin={{ top: 5 }}>
        <XAxis dataKey="group_name" tick={{ stroke: 'gray', strokeWidth: 1 }} />
        <YAxis tickFormatter={DataFormatter} tick={{ stroke: 'gray', strokeWidth: 0 }} />
        <Legend wrapperStyle={{ padding: 30 }} />
        <Bar dataKey="boys" name="Boys" fill="#1f77b4" barSize="20%" />
        <Bar dataKey="girls" name="Girls" fill="#fd7f0e" barSize="20%" />
      </BarChart>
    </ResponsiveContainer>
  );
};

export default App;
```

![Bar Chart Example](https://res.cloudinary.com/doldp5vju/image/upload/q_auto:best/v1628327297/recharts-bar-chart_dofim3.png)

#### Pie Chart Example
```jsx
import { PieChart, Pie, Legend, Cell, ResponsiveContainer } from 'recharts';

const data = [
  { count: 809680, language: 'Telugu' },
  { count: 4555697, language: 'Hindi' },
  { count: 12345657, language: 'English' },
];

const App = () => {
  return (
    <ResponsiveContainer width="100%" height={300}>
      <PieChart>
        <Pie
          cx="70%"
          cy="40%"
          data={data}
          startAngle={0}
          endAngle={360}
          innerRadius="40%"
          outerRadius="70%"
          dataKey="count"
        >
          <Cell name="Telugu" fill="#fecba6" />
          <Cell name="Hindi" fill="#b3d23f" />
          <Cell name="English" fill="#a44c9e" />
        </Pie>
        <Legend iconType="circle" layout="vertical" verticalAlign="middle" align="right" />
      </PieChart>
    </ResponsiveContainer>
  );
};

export default App;
```

![Pie Chart Example](https://res.cloudinary.com/doldp5vju/image/upload/q_auto:best/v1628327297/recharts-pie-chart_iyrbtg.png)

### Third-Party Package: `react-chrono` 🕒

`react-chrono` is a third-party package to display timelines in your application. It provides a React component `Chrono` to build a timeline that displays events chronologically.

#### Installation
```bash
npm install react-chrono
```

#### Advantages ✅
- **Multiple Modes**: Render timelines in horizontal, vertical, and tree modes.
- **Autoplay**: Supports slideshow mode for autoplay.
- **Keyboard Navigation**: Navigate the timeline via keyboard.

#### Chrono Props
| Prop    | Description                                      | Default Value       |
|---------|--------------------------------------------------|---------------------|
| `mode`  | Sets the mode of the component                   | `'HORIZONTAL'`      |
| `items` | Collection of Timeline Item Model                | `[]`                |
| `theme` | Customizes the colors                           | No default value    |

#### Example
```jsx
import { Chrono } from 'react-chrono';

const items = [
  {
    title: 'May 1940',
    cardTitle: 'Dunkirk',
    cardSubtitle: 'Men of the British Expeditionary Force.',
    cardDetailedText: 'On 10 May 1940, Hitler began his long-awaited offensive in the west by invading neutral Holland and attacking northern France.',
  },
];

const App = () => (
  <div className="chrono-container">
    <Chrono items={items} />
  </div>
);

export default App;
```

![Chrono Example](https://assets.ccbp.in/frontend/content/react-js/react-chrono-timeline-items-prop.png)

#### Custom Content Example
```jsx
import { Chrono } from 'react-chrono';

const items = [{ title: '2018' }, { title: '2019' }];

const App = () => (
  <div className="chrono-container">
    <Chrono mode="VERTICAL" items={items}>
      <img
        src="https://assets.ccbp.in/frontend/react-js/csk-logo-img.png"
        className="image"
        alt="chennai-super-kings"
      />
      <div>
        <h1>Mumbai Indians</h1>
        <p>IPL Team winner for the year 2019 is Mumbai Indians.</p>
      </div>
    </Chrono>
  </div>
);

export default App;
```

![Custom Content Example](https://assets.ccbp.in/frontend/content/react-js/react-chrono-timeline-with-title.png)

### Third-Party Package: `react-slick` 🎠

`react-slick` is a third-party package that provides a React component `Slider` to add a carousel to your application.

#### Installation
```bash
npm install react-slick
npm install slick-carousel
```

#### Advantages ✅
- **Easy to Use**: Simple integration and usage.
- **Highly Customizable**: Customize the carousel to fit your needs.
- **Performant**: Optimized for performance.

#### Slider Props
| Prop          | Description                                      | Default Value |
|---------------|--------------------------------------------------|---------------|
| `slidesToShow`| Number of slides to show in one frame            | `1`           |
| `dots`        | Display dots under the carousel                  | `true`        |
| `slidesToScroll` | Number of slides to scroll at once              | `1`           |
| `dotsClass`   | CSS class for styling dots                       | `"slick-dots"`|

#### Example
```jsx
import Slider from 'react-slick';
import 'slick-carousel/slick/slick.css';
import 'slick-carousel/slick/slick-theme.css';

const ReactSlick = () => {
  const settings = {
    dots: true,
    slidesToShow: 1,
    slidesToScroll: 1,
  };
  return (
    <div className="slider-container">
      <Slider {...settings}>
        <div><h3>1</h3></div>
        <div><h3>2</h3></div>
        <div><h3>3</h3></div>
        <div><h3>4</h3></div>
      </Slider>
    </div>
  );
};

export default ReactSlick;
```

![React Slick Example](https://assets.ccbp.in/frontend/content/react-js/react-slick-output.gif)

### Third-Party Package: `reactjs-popup` 🗣️

`reactjs-popup` is a third-party package to display popups in your application. It provides a React component that helps you create simple and complex Modals, Tooltips, and Menus.

#### Installation
```bash
npm install reactjs-popup
```

#### Advantages ✅
- **Modal, Tooltip, and Menu**: Supports various popup types.
- **Controlled Modals & Tooltips**: Provides support for controlled components.

#### ReactJS Popup Props
| Prop          | Description                                      | Default Value       |
|---------------|--------------------------------------------------|---------------------|
| `trigger`     | Element to be rendered in-place                  | JSX element         |
| `modal`       | Display content as a modal                      | `false`             |
| `position`    | Position of the tooltip                         | `'bottom center'`   |
| `open`        | State of the popup (opened or not)               | `false`             |
| `overlayStyle`| Custom overlay style                            | `object`            |

#### Example
```jsx
import Popup from 'reactjs-popup';
import 'reactjs-popup/dist/index.css';

const ReactPopUp = () => (
  <div className="popup-container">
    <Popup
      trigger={<button className="trigger-button" type="button">Trigger</button>}
      modal
    >
      {close => (
        <>
          <div><p>React is a popular and widely used programming language</p></div>
          <button type="button" className="trigger-button" onClick={() => close()}>Close</button>
        </>
      )}
    </Popup>
  </div>
);

export default ReactPopUp;
```

![React Popup Example](https://assets.ccbp.in/frontend/content/react-js/popup-with-close.gif)

#### Position Prop Example
```jsx
const ReactPopUp = () => (
  <div className="popup-container">
    <Popup
      trigger={<button type="button" className="trigger-button">Trigger</button>}
      position="bottom left"
    >
      <p>React is a popular and widely used programming language</p>
    </Popup>
  </div>
);

export default ReactPopUp;
```

![Position Prop Example](https://assets.ccbp.in/frontend/content/react-js/popup-with-position.gif)

#### Overlay Style Prop Example
```jsx
const overlayStyles = {
  backgroundColor: '#ffff',
};

const ReactPopUp = () => (
  <div className="popup-container">
    <Popup
      modal
      trigger={<button type="button" className="trigger-button">Trigger</button>}
      overlayStyle={overlayStyles}
    >
      <p>React is a popular and widely used programming language</p>
    </Popup>
  </div>
);

export default ReactPopUp;
```

![Overlay Style Prop Example](https://assets.ccbp.in/frontend/content/react-js/popup-overlay-styles.gif)

## References 📚

- [`react-player` Documentation](https://www.npmjs.com/package/react-player)
- [`recharts` Documentation](https://recharts.org/en-US)
- [`react-chrono` Documentation](https://www.npmjs.com/package/react-chrono)
- [`react-slick` Documentation](https://react-slick.neostack.com/docs/get-started)
- [`reactjs-popup` Documentation](https://react-popup.elazizi.com/component-api/)
