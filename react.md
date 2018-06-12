# react

标签（空格分隔）： 未分类

---

##ReactDOM.render
        ReactDOM.render(组件或者标签,挂载点,当挂载完成之后的回调函数)
        
        *** 顶层元素只能有一个标签

        *** 所有的class都要写成className

        *** {可以执行js代码}

            {[1,2,3,4]} -> 1,2,3,4 展开数组

            不能直接放对象，可以放对象的属性,如果要显示对象
            使用JSON.stringify(obj)转一道。

        *** 单标签要有结束符 /

            <input />  <img />

##组件
        *** 首字母必须大写
    
            声明一个类，继承React.Component || Component
        
            在组件中render方法必须有。
        
            传递数据通过属性来传递，通过this.props去接收
        
            在循环中必须加key，为了优化。

##受控组件
        当input添加value值之后就变成了受控组件
        
        受控组件:
            输入框中的内容就锁定了（修改不了）
        
        只有改变了数据，才会修改输入框中的内容。
        
        加 onChange={} 事件，不然会报错 
        
#总结


        1.npm start 启动
    
        2.index.js
    
        3.引入react,react-dom
    
        4.ReactDOM.render(component,el,callback)
    
        5.定义组件
            class App extends Component {
                constructor(){
                    super();
                    this.state = {
                        //初始化数据
                    }
                }
                render(){
                    return (
                        <div> //顶层只能有一个元素
                            <h1 className="active"></h1>
                            <input />
                            {执行js,[]:展开}
                        </div>
                    )
                }
            }
        6.
            let arr = [1,2,3,4];
            ReactDOM.render(<App arr={arr}/>,el,callback)
            this.props去拿
    
        7.
            this.setState();修改状态->改变视图
    
        8.
            onClick,onMouseOver.... = {this.fn}
            onClick,onMouseOver.... = {(e)=>{this.fn(e)}}
            fn = () => {}
    
        9.
            受控组件
                表单加了value就变成受控组件
    
                必须要:
                    onChange
    
            非受控组件:
                defaultValue
