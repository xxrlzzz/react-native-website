---
id: segmentedcontrolios
title: 🚧 SegmentedControlIOS
---

> **已过时。** Use [@react-native-community/segmented-control](https://github.com/react-native-community/segmented-control) instead.

使用`SegmentedControlIOS`来在 iOS 设备上渲染一个`UISegmentedControl`组件。这是一个分段显示多个选项的组件。

#### Programmatically changing selected index

The selected index can be changed on the fly by assigning the selectedIndex prop to a state variable, then changing that variable. Note that the state variable would need to be updated as the user selects a value and changes the index, as shown in the example below.

## 示例

```
<SegmentedControlIOS
  values={['One', 'Two']}
  selectedIndex={this.state.selectedIndex}
  onChange={(event) => {
    this.setState({selectedIndex: event.nativeEvent.selectedSegmentIndex});
  }}
/>
```

<center><img src="assets/SegmentedControlIOS/example.gif" width="360"></img></center>

---

# 文档

## Props

### `enabled`

If false the user won't be able to interact with the control. Default value is true.

| 类型 | 必需 |
| ---- | ---- |
| bool | 否   |

<center><img src="assets/SegmentedControlIOS/enabled.png" width="360"></img></center>

---

### `momentary`

If true, then selecting a segment won't persist visually. The `onValueChange` callback will still work as expected.

| 类型 | 必需 |
| ---- | ---- |
| bool | 否   |

<center><img src="assets/SegmentedControlIOS/momentary.gif" width="360"></img></center>

---

### `onChange`

Callback that is called when the user taps a segment; passes the event as an argument

| 类型     | 必需 |
| -------- | ---- |
| function | 否   |

---

### `onValueChange`

Callback that is called when the user taps a segment; passes the segment's value as an argument

| 类型     | 必需 |
| -------- | ---- |
| function | 否   |

---

### `selectedIndex`

The index in `props.values` of the segment to be (pre)selected.

| 类型   | 必需 |
| ------ | ---- |
| number | 否   |

---

### `tintColor`

Accent color of the control.

| 类型   | 必需 |
| ------ | ---- |
| string | 否   |

<center><img src="assets/SegmentedControlIOS/tintColor.png" width="360"></img></center>

---

### `values`

The labels for the control's segment buttons, in order.

| 类型            | 必需 |
| --------------- | ---- |
| array of string | 否   |

---

##### 本文档贡献者：[sunnylqm](https://github.com/search?q=sunnylqm&type=Users)(99.06%), [sunnylqm](https://github.com/search?q=sunnylqm&type=Users)(0.94%)
