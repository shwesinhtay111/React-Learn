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
