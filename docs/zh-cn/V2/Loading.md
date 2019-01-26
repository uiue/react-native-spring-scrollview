# 上拉加载

### 预览
![Preview](../res/LoadingAndroid.gif)
![Preview](../res/LoadingIOS.gif)

### 代码

导入

```$js
import { SpringScrollView } from "react-native-spring-scrollview";
import { ChineseWithLastDateFooter } from "react-native-spring-scrollview/Customize";
```

使用SpringScrollView可以非常简单地实现上拉加载的功能, 本库默认提供了一个NormalFooter类供用户使用,中文用户推荐使用Customize目录下的ChineseWithLastDateFooter

```$js
<SpringScrollView
  ref={ref => (this._scrollView = ref)}
  loadingFooter={ChineseWithLastDateFooter}
  allLoaded={this.state.allLoaded}
  onLoading={()=>{
    setTimeOut(()=>{
      this._scrollView.endLoading();
      setTimeOut(()=>this.setState({prop:"your changed props"}));
    },2000);
  }>
    <Text key={item} style={styles.text}>
      This is a Normal Loading Test
    </Text>
</SpringScrollView>
```


### 属性

属性  |  类型  |  默认值  |  作用  
---- | ------ | --------- | --------
onLoading | ()=>any | undefined | 上拉加载的回调函数
allLoaded | boolean | false | 数据是否加载完成。
loadingFooter | LoadingFooter | NormalFooter | 上拉加载组件，用户如果不希望自定义，则可以使用NormalFooter,如果需要高度自定义，请参看[自定义上拉加载](CustomLoading)