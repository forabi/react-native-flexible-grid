# React Native Flexible Grid

[![CI](https://github.com/iNerdStack/react-native-flexible-grid/actions/workflows/ci.yml/badge.svg)](https://github.com/iNerdStack/react-native-flexible-grid/actions/workflows/ci.yml)
[![npm package](https://img.shields.io/npm/v/react-native-flexible-grid.svg?style=flat-square)](https://www.npmjs.org/package/react-native-flexible-grid)
[![npm downloads](https://img.shields.io/npm/dt/react-native-flexible-grid.svg?maxAge=2592000)]()


`React Native Flexible Grid` is an advanced grid layout system inspired by CSS Grid, designed to facilitate responsive, customizable, and dynamic grid layouts in React Native applications. It supports both responsive and fixed layouts, enabling the creation of intricate designs with minimal effort.


## 🌟 Features

- **Responsive Design**: Adapts fluidly to both screen and container sizes, ensuring your content looks perfect on any device. This guarantees that your grid will seamlessly accommodate different resolutions and orientations, making it ideal for responsive mobile applications.
- **Dynamic Item Sizing**: Offers great flexibility to define both fixed and dynamic grid item dimensions, enabling a diverse range of layout configurations. Whether you're aiming for a Masonry-style list, arranging items with uneven widths and heights, or replicating complex layouts similar to Instagram Explore and Pinterest.
- **Virtualization Support**: Dramatically boosts the performance of grids handling large data by employing virtualization. By rendering only the items in the immediate viewport and a buffer zone, this feature ensures smooth scrolling and responsive interactions.
- **Two-Way Scrolling Support**: Facilitates navigation beyond the initial viewport in both horizontal and vertical directions. This advanced scrolling capability enhances user experience by providing fluid access to off-screen content, making it easier to explore large grids without compromising on performance.
- **Customizable**: Offers a wide range of customization options, allowing fine-tuning of the grid according to specific requirements. From styling adjustments to functional tweaks.
- **Minimal Dependencies**: Built exclusively with React Native components for better integration and ensures broad compatibility while maintaining a minimal footprint.
- **Universal Compatibility**: Seamlessly supports Android & iOS and tested extensively with Expo & web.

## 🎥 Demo

<table>
  <tr>
    <td align="center"><img src="https://raw.githubusercontent.com/iNerdStack/react-native-flexible-grid/main/example/assets/gifs/instagram-explore-example.gif" alt="Instagram Explore Example" width="180px" height="360px"  /></td>
       <td align="center"><img src="https://raw.githubusercontent.com/iNerdStack/react-native-flexible-grid/main/example/assets/gifs/pinterest-example.gif" alt="Grid System Demo" width="180px" height="360px"  /></td>

  </tr>
  <tr>
    <td align="center"><a href="https://github.com/iNerdStack/react-native-flexible-grid/blob/main/example/src/InstagramExploreExample.tsx"> Instagram Explore Example</a> </td>
    <td align="center"> <a href="https://github.com/iNerdStack/react-native-flexible-grid/blob/main/example/src/PinterestHomeExample.tsx">Pinterest Example</a>
</td>
  </tr>
</table>


<table>
  <tr>
       <td><img src="https://raw.githubusercontent.com/iNerdStack/react-native-flexible-grid/main/example/assets/gifs/gridboard-overflow-example.gif" alt="Grid Board Example" width="403px" height="100%" /></td>
  </tr>
  <tr>
    <td align="center"> <a href="https://github.com/iNerdStack/react-native-flexible-grid/blob/main/example/src/PinterestHomeExample.tsx">Grid Board Example </a> </td>
  </tr>
</table>



## 📦 Installation

```sh
npm install react-native-flexible-grid
```
or
```sh
yarn add react-native-flexible-grid
```

## 💡 Usage

### 1. Flex Grid
`FlexGrid` is designed for creating highly flexible and dynamic grid layouts, capable of two-way scrolling to accommodate content that extends beyond both the viewport's width and height. By leveraging `maxColumnRatioUnits`, `itemSizeUnit`, and smooth scrolling mechanics, `FlexGrid` facilitates precise control over the grid's arrangement, dimensions, and scrolling behavior. This makes it exceptionally suited for applications requiring a versatile grid system that can display content in both horizontally and vertically overflowed layouts with ease.



#### Use Cases:
- **Interactive Galleries**: Optimal for galleries where users can explore content through both horizontal and vertical navigation.
- **Board Layout**: Ideal for creating grid board with documents or media or files in a grid that exceeds the viewport, allowing for comprehensive exploration.
- **Complex Layouts**: Perfect for applications demanding intricate grid arrangements that go beyond simple lists, including dashboards or design portfolios.


```jsx
import { FlexGrid } from 'react-native-flexible-grid';

export default function App() {
  const data = [
    { imageUrl: 'https://picsum.photos/200/300?random=1', widthRatio: 1, heightRatio: 1 },
    { imageUrl: 'https://picsum.photos/200/300?random=2', widthRatio: 2, heightRatio: 1 },
    { imageUrl: 'https://picsum.photos/200/300?random=3', widthRatio: 2, heightRatio: 1 },
  ];

  const renderItem = (item, index) => (
    <TouchableOpacity style={styles.boxContainer} onPress={() => console.log(`Item ${item.text} pressed`)}>
      <View style={styles.box}>
        <Text style={styles.text}>{item.text}</Text>
      </View>
    </TouchableOpacity>
  );

  return (
    <View style={styles.container}>
      <FlexGrid
        maxColumnRatioUnits={60}
        itemSizeUnit={60}
        data={data}
        virtualizedBufferFactor={2}
        renderItem={renderItem}
        virtualization={true}
        showScrollIndicator={false}
        style={{ flex: 1 }}
      />
    </View>
  );
}

```


#### See Examples:
1. <a href="https://github.com/iNerdStack/react-native-flexible-grid/blob/main/example/src/PinterestHomeExample.tsx">Grid Board Example </a>



### 2. Responsive Grid

The `ResponsiveGrid` is designed for optimal responsiveness, dynamically adjusting grid items based on the container's width or a specified width within the component's style properties. Utilizing a combination of `maxItemsPerColumn` alongside item-specific `widthRatio` and `heightRatio`, it efficiently organizes content into a vertically scrollable grid. This component is ideally suited for layouts where vertical scrolling is preferred and where the grid's adaptability to varying container widths or device width is crucial.

#### Use Cases:
- **Content Feeds**: Perfect for vertically scrolling content feeds that require adaptability to different screen sizes.
- **Image Galleries**: Ideal for image galleries where images need to be displayed in a responsive, organized or uneven manner.
- **Product Listings**: Suitable for e-commerce apps needing to showcase products in a neatly arranged, responsive grid.



```jsx
import { ResponsiveGrid } from 'react-native-flexible-grid';

export default function App() {
  const data = [
    { imageUrl: 'https://picsum.photos/200/300?random=1', widthRatio: 1, heightRatio: 1 },
    { imageUrl: 'https://picsum.photos/200/300?random=2', widthRatio: 2, heightRatio: 1 },
    { imageUrl: 'https://picsum.photos/200/300?random=3', widthRatio: 2, heightRatio: 1 },
  ];

  const renderItem = (item, index) => (
    <TouchableOpacity style={styles.boxContainer} onPress={() => console.log(`Item ${item.text} pressed`)}>
      <View style={styles.box}>
        <Text style={styles.text}>{item.text}</Text>
      </View>
    </TouchableOpacity>
  );

  return (
    <View style={styles.container}>
      <ResponsiveGrid
        maxItemsPerColumn={3}
        data={data}
        renderItem={renderItem}
        style={{ padding: 5 }}
      />
    </View>
  );
}


```

#### See Examples:
1. <a href="https://github.com/iNerdStack/react-native-flexible-grid/blob/main/example/src/InstagramExploreExample.tsx"> Instagram Explore Example</a>
2.  <a href="https://github.com/iNerdStack/react-native-flexible-grid/blob/main/example/src/PinterestHomeExample.tsx">Pinterest Example</a>



## ⚙️ Props

### 1. `FlexGrid` Props

<table>
  <thead>
    <tr>
      <th>Prop</th>
      <th>Type</th>
      <th>Default</th>
      <th>Required</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>data</code></td>
      <td><code>Array</code></td>
      <td><code>[]</code></td>
      <td><code>true</code></td>
      <td>The array of items to be rendered in the grid.</td>
    </tr>
    <tr>
      <td><code>renderItem</code></td>
      <td><code>Function</code></td>
      <td><code> () => null</code></td>
           <td><code>true</code></td>
      <td>Its used for defining how each individual item should appear, it allows utilizing the item's properties to construct a custom layout or UI for that item within the grid.</td>
    </tr>
    <tr>
      <td><code>maxColumnRatioUnits</code></td>
      <td><code>Number</code></td>
      <td><code>1</code></td>
           <td><code>true</code></td>
      <td>The value controls the maximum number of ratio units that can be allocated to a single column, either from one item or cumulatively from multiple items that a column can accommodate, this defines the grid layout density and item sizing and positioning within each column of the grid.</td>
    </tr>
    <tr>
      <td><code>itemSizeUnit</code></td>
      <td><code>Number</code></td>
      <td><code>50</code></td>
           <td><code>true</code></td>
      <td> Defines the base unit size for grid items. The actual displayed size of each item in the grid is calculated by multiplying this unit by the item's <code>widthRatio </code> and <code>
      heightRatio</code> </td>
    </tr>
      <tr>
      <td><code>virtualization</code></td>
      <td><code>Boolean</code></td>
      <td><code>true</code></td>
      <td><code>false</code></td>
      <td> Virtualization significantly optimizes performance by only rendering the items currently visible in the viewport, plus buffer. This reduces the number of components rendered at any given time, leading to improved frame rates and smoother scrolling experiences, especially with large data.
      <br/>
      <br/>
      Disabling virtualization results in all items being rendered at once, regardless of their visibility. It can impact performance and responsiveness for larger data. This is only suitable for grids with a small number of items to render.
  </td>
    </tr>
    <tr>
      <td><code>virtualizedBufferFactor</code></td>
      <td><code>Number</code></td>
      <td><code>2</code></td>
           <td><code>false</code></td>
      <td>Defines the buffer size for pre-loading items outside the current viewport. The buffer's actual dimensions are determined by multiplying this factor by the <code>containerHeight</code> for vertical scrolling and <code>containerWidth</code> for horizontal scrolling.
      <br/>

A higher buffer factor increases the number of items pre-loaded outside the viewport, contributing to a smoother scrolling experience as more content is ready for immediate display when scrolling. However, setting a large buffer factor can affect overall performance, especially on devices with limited resources, as it increases the number of components rendered off-screen.
 <br/>

While, a lower buffer factor reduces the off-screen component count, optimizing performance and resource usage. This setting is beneficial for large data or resource-constrained environments. However, it may lead to brief moments where content needs to catch up with the user's scroll speed, momentarily displaying blank areas until new items are rendered.
      </td>
    </tr>
       <tr>
      <td><code>scrollEventInterval</code></td>
      <td><code>Number</code></td>
      <td><code>200</code></td>
           <td><code>false</code></td>
      <td>Specifies the interval, in milliseconds, at which scroll events are processed for the purpose of recalculating visible items and buffer in a virtualized grid. By setting this prop, developers can throttle the frequency of scroll event handling, optimizing performance during rapid scrolling by reducing the computational load associated with updating the list of visible items and buffer.

A lower value results in more frequent updates, offering smoother visual updates of the grid's content at the potential cost of higher computational overhead. While, a higher interval decreases the frequency of updates, potentially improving performance but with less immediate recalculation triggered by scroll actions. This is crucial for fine-tuning the performance and experience of virtualized grid.
</td>
    </tr>
    <tr>
      <td><code>showScrollIndicator</code></td>
      <td><code>Boolean</code></td>
      <td><code>true</code></td>
           <td><code>false</code></td>
      <td>Controls the visibility of the scroll indicator.</td>
    </tr>
      <tr>
      <td><code>style</code></td>
      <td><code>ViewStyle</code></td>
      <td><code>{}</code></td>
           <td><code>false</code></td>
      <td> Accepts a React Native ViewStyle object. This applied to the outermost container of the component, can be used to set a fixed width, height, etc </td>
    </tr>
  </tbody>
</table>

<br/>
<br/>

### 2. `ResponsiveGrid` Props

<table>
  <thead>
    <tr>
      <th>Prop</th>
      <th>Type</th>
      <th>Default</th>
      <th>Required</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code>data</code></td>
      <td><code>Array</code></td>
      <td><code>[]</code></td>
      <td><code>true</code></td>
      <td>The array of items to be rendered in the grid.</td>
    </tr>
    <tr>
      <td><code>renderItem</code></td>
      <td><code>Function</code></td>
      <td><code> () => null</code></td>
           <td><code>true</code></td>
      <td>Its used for defining how each individual item should appear, it allows utilizing the item's properties to construct a custom layout or UI for that item within the grid.</td>
    </tr>
    <tr>
      <td><code>maxItemsPerColumn</code></td>
      <td><code>Number</code></td>
      <td><code>3</code></td>
      <td><code>true</code></td>
      <td>Defines the maximum number of items that can be displayed within a single column of the grid. This property is required for ensuring a balanced and visually appealing layout across various screen sizes and orientations, optimizing the use of available space. Suitable for responsive designs, allows for dynamic adjustments based on the container's width, ensuring a consistent and adaptable presentation of content.</td>
    </tr>
     <tr>
      <td><code>itemUnitHeight</code></td>
      <td><code>Number</code></td>
      <td><code>containerWidth / maxItemsPerColumn</code></td>
      <td><code>false</code></td>
      <td> Specifies the base unit height for items within the grid. This value serves as a foundational measure to determine the actual height of each grid item. The item's final height is calculated by multiplying this base unit height (<code> itemUnitHeight</code>) by the item's heightRatio, allowing for proportional scaling of items based on their content or design requirements. While <code>widthRatio</code> affects the item's width in relation to the column width, <code> itemUnitHeight</code> and <code>heightRatio</code> together define the item's vertical dimension, enabling dynamic grid layouts that adapt seamlessly to varying content sizes.</td>
    </tr>
    <tr>
      <td><code>virtualization</code></td>
      <td><code>Boolean</code></td>
      <td><code>true</code></td>
      <td><code>false</code></td>
      <td> Virtualization significantly optimizes performance by only rendering the items currently visible in the viewport, plus buffer. This reduces the number of components rendered at any given time, leading to improved frame rates and smoother scrolling experiences, especially with large data.
      <br/>
      <br/>
      Disabling virtualization results in all items being rendered at once, regardless of their visibility. It can impact performance and responsiveness for larger data. This is only suitable for grids with a small number of items to render.
  </td>
    </tr>
    <tr>
      <td><code>virtualizedBufferFactor</code></td>
      <td><code>Number</code></td>
      <td><code>2</code></td>
           <td><code>false</code></td>
      <td>Defines the buffer size for pre-loading items outside the current viewport. The buffer's actual dimensions are determined by multiplying this factor by the <code>containerHeight</code> for vertical scrolling
      <br/>

A higher buffer factor increases the number of items pre-loaded outside the viewport, contributing to a smoother scrolling experience as more content is ready for immediate display when scrolling. However, setting a large buffer factor can affect overall performance, especially on devices with limited resources, as it increases the number of components rendered off-screen.
 <br/>

While, a lower buffer factor reduces the off-screen component count, optimizing performance and resource usage. This setting is beneficial for large data or resource-constrained environments. However, it may lead to brief moments where content needs to catch up with the user's scroll speed, momentarily displaying blank areas until new items are rendered.
      </td>
    </tr>
       <tr>
      <td><code>scrollEventInterval</code></td>
      <td><code>Number</code></td>
      <td><code>200</code></td>
           <td><code>false</code></td>
      <td>Specifies the interval, in milliseconds, at which scroll events are processed for the purpose of recalculating visible items and buffer in a virtualized grid. By setting this prop, developers can throttle the frequency of scroll event handling, optimizing performance during rapid scrolling by reducing the computational load associated with updating the list of visible items and buffer.

A lower value results in more frequent updates, offering smoother visual updates of the grid's content at the potential cost of higher computational overhead. While, a higher interval decreases the frequency of updates, potentially improving performance but with less immediate recalculation triggered by scroll actions. This is crucial for fine-tuning the performance and experience of virtualized grid.
</td>
    </tr>
    <tr>
      <td><code>showScrollIndicator</code></td>
      <td><code>Boolean</code></td>
      <td><code>true</code></td>
           <td><code>false</code></td>
      <td>Controls the visibility of the scroll indicator.</td>
    </tr>
      <tr>
      <td><code>style</code></td>
      <td><code>ViewStyle</code></td>
      <td><code>{}</code></td>
           <td><code>false</code></td>
      <td> Accepts a React Native ViewStyle object. This applied to the outermost container of the component, can be used to set a fixed width, height, etc </td>
    </tr>
  </tbody>
</table>


## 🚀 Vision and Roadmap
Our mission is not just to provide a flexible layout solution but to improve grid systems and layout flexibility in React Native. By continuously refining our algorithm and incorporating feedback, we aim to bring CSS Grid-like capabilities to the React Native ecosystem, fostering creativity and pushing the boundaries of what's possible in app design with React Native.

## 🤝 Contributing

See the [contributing guide](CONTRIBUTING.md) to learn how to contribute to the repository and the development workflow.

## 📄 License

[MIT](CONTRIBUTING.md)

---
