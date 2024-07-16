# React Interview Questions and Answers

## Basic Level

1. **What is React?**
   - React is a JavaScript library for building user interfaces, developed by Facebook. It allows developers to create large web applications that can update and render efficiently in response to data changes.

2. **What are the major features of React?**
   - Declarative
   - Component-Based
   - Learn Once, Write Anywhere
   - Virtual DOM
   - One-Way Data Binding

3. **What is JSX?**
   - JSX stands for JavaScript XML. It is a syntax extension for JavaScript that looks similar to XML or HTML and is used with React to describe what the UI should look like.

4. **What is the Virtual DOM?**
   - The Virtual DOM is a lightweight copy of the actual DOM. React uses it to optimize updates to the real DOM by first performing updates in the virtual DOM and then syncing with the real DOM in the most efficient way.

5. **What are components in React?**
   - Components are the building blocks of a React application. They can be thought of as custom, reusable HTML elements that help in creating complex UIs.

6. **Explain the difference between state and props.**
   - **State**: A component's state is an object that holds some information that may change over the lifecycle of the component. It is managed within the component.
   - **Props**: Props (short for properties) are read-only attributes used to pass data from one component to another.

7. **How do you create a React component?**
   - You can create a React component as a function or a class.
     ```jsx
     function MyComponent() {
       return <div>Hello World</div>;
     }
     // or
     class MyComponent extends React.Component {
       render() {
         return <div>Hello World</div>;
       }
     }
     ```

8. **What is the purpose of the render() method in React?**
   - The `render()` method is used to return the JSX that should be rendered to the DOM. It is required for class components.

9. **What are React lifecycle methods?**
   - Lifecycle methods are special methods in class components that allow you to run code at specific points in a component's lifecycle, such as `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount`.

10. **How do you handle events in React?**
    - Events in React are handled using camelCase syntax and passing a function as an event handler.
      ```jsx
      function handleClick() {
        alert('Button clicked!');
      }

      <button onClick={handleClick}>Click me</button>
      ```

## Intermediate Level

11. **What are controlled and uncontrolled components?**
    - **Controlled Components**: Components where form data is handled by a React component's state.
    - **Uncontrolled Components**: Components where form data is handled by the DOM itself, using refs to access form values.

12. **How do you pass data between React components?**
    - Data can be passed from a parent component to a child component using props.
      ```jsx
      <ChildComponent propName={value} />
      ```

13. **What is the context API and when would you use it?**
    - The Context API is a way to pass data through the component tree without having to pass props down manually at every level. It is useful for global settings or themes.

14. **What are higher-order components (HOC)?**
    - HOCs are functions that take a component and return a new component with additional props or functionality.
      ```jsx
      function withExtraProp(WrappedComponent) {
        return function EnhancedComponent(props) {
          return <WrappedComponent extraProp="value" {...props} />;
        };
      }
      ```

15. **How do you optimize performance in a React application?**
    - Techniques include using React.memo, PureComponent, lazy loading components, code splitting, and avoiding unnecessary re-renders.

16. **Explain React hooks and provide examples of useState and useEffect.**
    - Hooks are functions that let you use state and other React features in functional components.
      ```jsx
      import { useState, useEffect } from 'react';

      function ExampleComponent() {
        const [count, setCount] = useState(0);

        useEffect(() => {
          document.title = `Count: ${count}`;
        }, [count]);

        return (
          <div>
            <p>Count: {count}</p>
            <button onClick={() => setCount(count + 1)}>Increment</button>
          </div>
        );
      }
      ```

17. **What is the difference between functional and class components?**
    - Functional components are simpler and use hooks to manage state and lifecycle methods, while class components use ES6 classes and lifecycle methods.

18. **How do you manage state in a React application?**
    - State can be managed using useState, useReducer, or state management libraries like Redux or MobX.

19. **What are React fragments and why would you use them?**
    - Fragments let you group a list of children without adding extra nodes to the DOM.
      ```jsx
      <React.Fragment>
        <Child1 />
        <Child2 />
      </React.Fragment>
      // or the shorthand
      <>
        <Child1 />
        <Child2 />
      </>
      ```

20. **Explain the use of keys in React.**
    - Keys help React identify which items have changed, are added, or are removed. They should be given to the elements inside an array to give elements a stable identity.

## Advanced Level

21. **What are React portals?**
    - Portals provide a way to render children into a DOM node that exists outside the DOM hierarchy of the parent component.
      ```jsx
      ReactDOM.createPortal(
        <div>Portal Content</div>,
        document.getElementById('portal-root')
      );
      ```

22. **How does server-side rendering (SSR) work in React?**
    - SSR involves rendering React components on the server and sending the HTML to the client, which improves performance and SEO. Frameworks like Next.js facilitate SSR in React.

23. **What is the difference between client-side rendering (CSR) and server-side rendering (SSR)?**
    - **CSR**: The browser downloads a minimal HTML file, then loads JavaScript to render the content.
    - **SSR**: The server renders the full HTML for a page, which is sent to the browser. This can be faster for initial load and better for SEO.

24. **What is React Fiber?**
    - React Fiber is the new reconciliation algorithm in React 16, which improves the ability to handle animations, gestures, and other updates.

25. **Explain the concept of reconciliation in React.**
    - Reconciliation is the process of updating the DOM to match the React elements. React uses the diffing algorithm to compare the new and old virtual DOM trees and update the necessary parts of the DOM.

26. **What are render props and how do you use them?**
    - Render props are a technique for sharing code between React components using a prop whose value is a function.
      ```jsx
      <DataProvider render={data => (
        <SomeComponent data={data} />
      )} />
      ```

27. **How do you handle error boundaries in React?**
    - Error boundaries are React components that catch JavaScript errors in their child component tree, log those errors, and display a fallback UI.
      ```jsx
      class ErrorBoundary extends React.Component {
        state = { hasError: false };

        static getDerivedStateFromError(error) {
          return { hasError: true };
        }

        componentDidCatch(error, errorInfo) {
          // Log the error
        }

        render() {
          if (this.state.hasError) {
            return <h1>Something went wrong.</h1>;
          }

          return this.props.children; 
        }
      }
      ```

28. **What is lazy loading and how do you implement it in React?**
    - Lazy loading delays loading of non-essential resources at page load time.
      ```jsx
      const LazyComponent = React.lazy(() => import('./LazyComponent'));

      function App() {
        return (
          <Suspense fallback={<div>Loading...</div>}>
            <LazyComponent />
          </Suspense>
        );
      }
      ```

29. **Explain the useReducer hook and provide an example.**
    - `useReducer` is a hook that is used for managing complex state logic.
      ```jsx
      const initialState = { count: 0 };

      function reducer(state, action) {
        switch (action.type) {
          case 'increment':
            return { count: state.count + 1 };
          case 'decrement':
            return { count: state.count - 1 };
          default:
            throw new Error();
        }
      }

      function Counter() {
        const [state, dispatch] = useReducer(reducer, initialState);

        return (
          <>
            Count: {state.count}
            <button onClick={() => dispatch({ type: 'increment' })}>+</button>
            <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
          </>
        );
      }
      ```

30. **What is React.memo and when would you use it?**
    - `React.memo` is a higher order component that prevents re-rendering of a component if its props have not changed.
      ```jsx
      const MyComponent = React.memo(function MyComponent(props) {
        /* render using
