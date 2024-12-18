@charset "UTF-8";

## 建立在懂 react 用法的基础上

### 入门基础

1. reactnative 自带组件（需引入），类似 html 来搭建页面；它的渲染方式如下：

```
import React, { Component } from 'react';
import { AppRegistry, Text, TextInput, View } from 'react-native';

class MyTest extends Component {
  constructor(props) {
    super(props);
    this.state = {text: ''};
  }

  render() {
    return (
      <View style={{padding: 10}}>
        <TextInput
          style={{height: 40}}
          placeholder="Type here to translate!"
          onChangeText={(text) => this.setState({text})}
        />
        <Text style={{padding: 10, fontSize: 42}}>
          {this.state.text.split(' ').map((word) => word && '🍕').join(' ')}
        </Text>
      </View>
    );
  }
}
// 注册应用(registerComponent)后才能正确渲染
// 注意：只把应用作为一个整体注册一次，而不是每个组件/模块都注册
AppRegistry.registerComponent('MyTest', () => MyTest);
```

2. Image 组件用来显示图片，用法需要注意：

```
// 这里的source可以直接填写url地址字符串
<Image source={require('./img/favicon.png')} />

// 也可以外面定义变量来引用
<Image source={pic} style={{width: 193, height: 110}} />
```

3. props 和 state 的工作原理同 react 相同；

4. 样式的两种用法，其中一种如上 Image 组件，另一种使用 StyleSheet 创建（需引入）如下：

```
// 使用
import { AppRegistry, StyleSheet, Text, View } from 'react-native';

<Text style={styles.bigblue}>just bigblue</Text>
<Text style={[styles.bigblue, styles.red]}>bigblue, then red</Text>

// 定义
const styles = StyleSheet.create({
  bigblue: {
    color: 'blue',
    fontWeight: 'bold',
    fontSize: 30,
  },
  red: {
    color: 'red',
  },
});
```

5. 高度与高度：如果父容器既没有固定的 width 和 height，也没有设定 flex，则父容器的尺寸为零，其子组件如果使用了 flex，也是无法显示的。

6. Flexbox 布局：工作原理和 css 基本一致，差异：默认值不同，flexDirection 的默认值是 column 而不是 row，而 flex 也只能指定一个数字值。

7. 处理文本输入 --- 允许用户输入文本的基础组件

- onChangeText 属性：此属性接收一个函数，而此函数会在文本变化时被调用。
- onSubmitEditing 属性：此属性会在文本被提交后（用户按下软键盘上的提交键）调用。

8. ScrollView 滚动视图：

- 可以垂直滚动，还能水平滚动（通过 horizontal 属性来设置）。
- 只适合用来显示数量不多的滚动元素。

9. ListView 长列表：FlatList 或是 SectionList（后面做详细讲解）。

### 组件
