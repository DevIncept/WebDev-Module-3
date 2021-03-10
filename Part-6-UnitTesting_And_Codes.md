# Unit Testing

## What is unit testing :question:

Writing automated tests is very important in any real world project, but it can been notoriously difficult
to figure out especially in the frontend world. Unit testing is a level of software testing where individual units/components of a software are tested. 
In the React world this means testing an individual React Component or pure functions.

## Why should We test :question:

Testing is essential to guarantee a stable application. Unit testing in particular is possibly the most important part of testing. 
1. They are very fast to run allowing us to very quickly understand if there is anything broken in our app.
2. They bring great value with the least amount of effort as they are very easy to write compared to other more complicated tests.
3. If they fail it is very easy to know where the error is because they only concentrate on small units of code.

## How can we do it :question:

In order to do our unit testing we will use two very popular libraries namely **Jest** and **Enzyme**.

## What are Jest and Enzyme :question:

- Jest is a testing tool from Facebook that makes it easy to perform unit testing in JavaScript. 
- Enzyme on the other hand, is React specific. It provides a bunch of helpful methods that enhance how we test React components.
- REACT-TESTING-LIBRARY is the new tool for unit testing in React ,and it is comparitively more easy to work with.

<br>
<br>

## How can we do Unit Testing 

#### This is a small code example to explain how unit testing is done:
1. ##### We will test a component whose only purpose is to render a paragraph with some text.
```
import React from 'react'

const Paragraph = ({ children }) => (
  <p>{ children }</p>
)

export default Paragraph
```
2. ##### The only thing we want to test here is that the children passed to this component are rendered inside a <p> tag.
```
/* Dependencies */
import React from 'react'
import Enzyme, { shallow } from 'enzyme'
import Adapter from 'enzyme-adapter-react-16'

/* Components */
import Paragraph from './'

// Configure enzyme for react 16
Enzyme.configure({ adapter: new Adapter() })

describe('Paragraph', () => {
  it('should render children inside a p tag', () => {
    const wrapper = shallow(<Paragraph>This is my first test</Paragraph>)
    const paragraph = wrapper.find('p')
    expect(paragraph).toHaveLength(1)
    expect(paragraph.text()).toEqual('This is my first test')
  })
})
```
3. ##### We can test this by running `npm test` It looks for all test files and tests them. 
