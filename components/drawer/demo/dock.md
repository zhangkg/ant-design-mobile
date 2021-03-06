---
order: 1
title:
  zh-CN: 嵌入文档模式
  en-US: 'Inner Document'
---

嵌入到文档流中


````jsx
import { Drawer, List, NavBar } from 'antd-mobile';

class App extends React.Component {
  state = {
    docked: false,
  }
  onDock = (d) => {
    this.setState({
      [d]: !this.state[d],
    });
  }
  render() {
    const sidebar = (<List>
      {[...Array(20).keys()].map((i, index) => {
        if (index === 0) {
          return (<List.Item key={index}
            thumb="https://zos.alipayobjects.com/rmsportal/eOZidTabPoEbPeU.png"
            multipleLine
          >分类</List.Item>);
        }
        return (<List.Item key={index}
          thumb="https://zos.alipayobjects.com/rmsportal/eOZidTabPoEbPeU.png"
        >分类{index}</List.Item>);
      })}
    </List>);

    const drawerProps = {
      docked: this.state.docked,
      open: false,
      position: 'left',
    };
    return (<div style={{ height: '100%' }}>
      <NavBar iconName="ellipsis" onLeftClick={() => this.onDock('docked')}>嵌入文档</NavBar>
      <Drawer
        className="my-drawer"
        style={{ minHeight: document.documentElement.clientHeight - 200 }}
        sidebar={sidebar}
        dragHandleStyle={{ display: 'none' }}
        sidebarStyle={{ border: '1px solid #ddd' }}
        contentStyle={{ color: '#A6A6A6', textAlign: 'center', paddingTop: 42 }}
        {...drawerProps}
      >
        请点击左上角图标
      </Drawer>
    </div>);
  }
}

ReactDOM.render(<App />, mountNode);
````
````css
.my-drawer {
  position: relative;
  overflow: auto;
}
.my-drawer .am-drawer-sidebar {
  background-color: #fff;
  overflow: auto;
}
.my-drawer .am-drawer-sidebar .am-list {
  width: 6rem;
  padding: 0;
}
````
