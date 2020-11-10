Eg1
====
      import React from 'react'
      import ReactDOM from 'react-dom'

      const Hello = ({name, age}) => {
        const bornYear = () => new Date().getFullYear() -age
        return (
          <div>
            <p>
              Hello {name}, you are {age} years old
            </p>
            <p>So you were probably born in {bornYear()}</p>
          </div>
        )
      }
      const App = () => {
        const name = 'Peter'
        const age = 22

        return(
          <div>
            <h1>Greetings</h1>
            <Hello name = 'Maya' age={26 + 10} />
            <Hello name = {name} age={age} />
          </div>
        )
      }

      ReactDOM.render(
        // React.createElement(App, null),
        <App />,
        document.getElementById('root')
      )
-------------------------------------------------------------------------

Eg2
======
      import React, { useState } from 'react'
      import ReactDOM from 'react-dom'

      const Button = (props) => {
        return (
          <button onClick={props.handleClick}>
            {props.text}
          </button>
        )
      }
      const Display = (props) => {
        return (
          <div>{props.counter}</div>
        )
      }
      const App = () => {
        const [ counter, setCounter ] = useState(0)

        const increaseByOne = () => setCounter(counter + 1)
        const decreaseByOne = () => setCounter(counter - 1)
        const setToZero = () => setCounter(0)

        return (
          <div>
            <Display counter={counter}/>
            <Button
              handleClick={increaseByOne}
              text='plus'
            />
            <Button
              handleClick={setToZero}
              text='zero'
            />     
            <Button
              handleClick={decreaseByOne}
              text='minus'
            />           
          </div>
        )
      }

      ReactDOM.render(
        // React.createElement(App, null),
        <App />,
        document.getElementById('root')
      )
-------------------------------------------------------------------------------------------------------
Eg.3
=====
      import React from 'react';
      class Item extends React.Component {
        render() {
          return (
            <li>
              {this.props.name},
              {this.props.price}
            </li>
          )
        }
      }
      class App extends React.Component {
        state = {
          items: [
            { id: 1, name: 'Apple', price: 0.99 },
            { id: 2, name: 'Orange', price: 0.89 }
          ]
        }
        nameRef = React.createRef();
        priceRef = React.createRef();
        add = () => {
            let id = this.state.items.length +1;
            let name = this.nameRef.current.value;
            let price = this.priceRef.current.value;
            this.setState({
            items: [
              ...this.state.items,
              { id, name, price }
            ]
            });

        }
        render() {
          return (
            <div>
              <h1>Hello React</h1>
              <ul>
                {this.state.items.map(i => {
                  return (
                    <Item id= {i.id} name={i.name} price={i.price} />
                  )
                })}
              </ul>
              <input type="text" ref={this.nameRef} /><br />
              <input type="text" ref={this.priceRef} /><br />
              <button onClick={this.add}>Add</button>
            </div>
          )
        }
      }


      export default App;

----------------------------------------------------
Eg.4
============

      import React from 'react';
      class Item extends React.Component {
        render() {
          return (
            <li>
              {this.props.name},
              {this.props.price}
            </li>
          )
        }
      }
      class AddForm extends React.Component {
        nameRef = React.createRef();
        priceRef = React.createRef();

        add = () => {
          let name = this.nameRef.current.value;
          let price = this.priceRef.current.value;
          this.props.add(name, price);
        }
        render() {
          return (
            <div>
              <input type="text" ref={this.nameRef} /> <br />
              <input type="text" ref={this.priceRef} /><br />
              <button onClick={this.add}>Add</button>
            </div>
          )
        }

      }
      class App extends React.Component {
        state = {
          items: [
            { id: 1, name: 'Apple', price: 0.99 },
            { id: 2, name: 'Orange', price: 0.89 }
          ]
        }

        add = (name,price) => {
          let id = this.state.items.length + 1;
          this.setState({
            items: [
              ...this.state.items,
              { id, name, price }
            ]
          });

        }
        render() {
          return (
            <div>
              <h1>Hello React</h1>
              <ul>
                {this.state.items.map(i => {
                  return (
                    <Item id={i.id} name={i.name} price={i.price} />
                  )
                })}
              </ul>
              <AddForm add={this.add}></AddForm>
            </div>
          )
        }
      }


      export default App;
 ---------------------------------------------------------------------------------
 Eg.5
 ======
       import React, {useState} from 'react';
      import ReactDom from 'react-dom';
      class Title extends React.Component{
        render(){
          return(
            <div>
              <h1 name={this.props.name}></h1>
            </div>
          )
        }
      }
      class Header extends React.Component{
        render(){
          return(
            <div>
              <Title name={this.props.name}></Title>
            </div>
          )
        }

      }
      class App extends React.Component{
        render(){
          return(
            <div>
              <Header name="App Name"></Header>
              how are you
            </div>
          )
        }
      }
      export default App;
      
      -------------------------------------------------
   Eg.6
  ============
      import React, { useState } from 'react';
      import ReactDom from 'react-dom';
      class Toolbar extends React.Component {
        render() {
          return (
            <div style={{ background: 'cyan', padding: 10 }}>
              {this.props.children}
            </div>
          )
        }
      }

      class App extends React.Component {
        render() {
          return (
            <div>
              <Toolbar>
                <h1>Hello React</h1>
                <h2>Hello Testing</h2>
              </Toolbar>
            </div>
          )
        }
      }
      export default App;
      ---------------------------------
  Eg7
 =====
      import React from 'react';
      const Item = props => {
          return (<li>
              {props.name}
              ${props.price}
          </li>
          )
      }
      const App = props => {
          return(
              <div>
                  <ul>
                      <Item name="apple" price="0.99">  </Item>
                      <Item name="orange" price="0.89"></Item>
                  </ul>
              </div>
          )

      }
      export default App;
      -----------------------------------
      
   Eg 8
   =======
      import React, { createRef, useState } from 'react';
      const Item = ({ name, price }) => (
        <li> {name}, ${price}</li>
      )

      const App = props => {
        let [items, setItems] = useState ([
          { id:1, name: 'Apple', price: 9.99 },
          { id:2, name: 'Orange', price: 9.59 },

        ])

        let nameRef = createRef();
        let priceRef = createRef();

        let add = () => {
          let id = items.length + 1 ;
          let name = nameRef.current.value;
          let price = priceRef.current.value;
          setItems([
            ...items,
            { id, name, price}
          ]);
        }

        return (
          <div>
            <ul>
              {items.map(i => (
                <Item key={i.id} name={i.name} price={i.price}></Item>
              ))}
            </ul>
            <input type="text" ref={nameRef} /><br />
            <input type="text" ref={priceRef} /><br />
            <button onClick={add}>Add</button>
          </div>
        )
      }
      export default App;
      -----------------------------

