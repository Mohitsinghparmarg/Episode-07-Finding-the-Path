
## 
  - if No Dependency array => useEffect is called on every render
      useEffect(()=>
         {
            console.log("useEffect is called");
         });

  - if Dependency array is empty = [] => useEffect is called on initial render(just once)
     useEffect(()=>
         {
            console.log("useEffect is called");
         },[]);

 - if Dependency array is [btnNameReact] => called everytime btnNameReact is updated
        useEffect(() => 
         {
            console.log("useEffect is called");
         },[btnNameReact]);


## 
   - Always call your Hooks(useState,useEffect) in the component.
     - useState has its own purpose ,it is used to create local state variables inside functional component.
  - Always try to use Hooks above(higher level or first level) in the functional component.
  - never use Hooks in if-else.
  - never use Hooks inside the for loop.

##
  - rafce provides automatically a component.
##
  - RouterProvider provides routing configuration to our App.
  - react-router-dom provides a Hook which is useRouteError(provides more generic Error) in terms of Error.

  - Outlet is like a tunnel in which children of AppLayout come over in this according to the path and filled in Outlet.

  - when you are using React and you want to route some other page ,never ever use the anchor tag(because it reloads the page ). so always use Link Component which is also a super power Component provided by react-router-dom.Link tag exacty works as anchor tag but it does not reload the page again(directly reach to that link page) which is a good thing.we write to instead of href in Link tag.


## 2 Types of Routing in Web Apps
  - Client Side Routing
  - Serevr Side Routing




  ## What would happen if we do console.log(useState())?

        
    Using console.log(useState()) in a React component will display the result of invoking the useState hook without any arguments. useState is a Hook that lets you add React state to function components.

    When called, useState returns an array with two elements:

    1. The current state value.
    2. A function that allows you to update this value.

      If you call useState() without any arguments, it initializes the state with undefined because you haven't provided an initial state.

       Initialization: By calling useState() without any argument, you initialize the state variable with undefined.

       Console Output: When you console.log(useState()), it will log an array where:

       The first element is the current state value, which is undefined in this case because no initial value was provided.
       The second element is a function that you can use to update the state.


  ## How will useEffect behave if we don't add a dependency array ?

     In React, the useEffect hook is used to perform side effects in function components. When you use useEffect without specifying a dependency array, it means that the effect will run after every render. This is because React will not have any dependencies to compare with the previous render, so it will always consider the effect as needing to be run.

       Here's what happens when you use useEffect without a dependency array:

          Initial Render: 
             The effect will run after the initial render of the component.
          Subsequent Renders: 
             After each subsequent render, React will compare the effect's dependencies (which are none in this case) to the previous render's dependencies. Since there are no dependencies, React will always consider the effect as needing to be run.
          Cleanup:
             If the effect returns a cleanup function, that cleanup function will run before the effect runs again (on the next render).

      It's important to note that using useEffect without a dependency array can lead to performance issues if the effect is doing expensive computations or causing unnecessary re-renders. In such cases, it's recommended to specify the dependencies in the dependency array to control when the effect should run.




  ## What is SPA?

     Single-Page Application (SPA) is a web application or website that interacts with the user by dynamically rewriting the current page rather than loading entire new pages from the server. This approach avoids interruption of the user experience between successive pages, making the application behave more like a desktop application.

      Characteristics of SPAs
            User Experience (UX): SPAs offer a more fluid and faster experience, as users do not see the page reloads that typically occur in a traditional web application. Interactions are smoother, which can lead to a perception of a faster site and a more app-like experience.
            AJAX: SPAs heavily rely on AJAX (Asynchronous JavaScript and XML) to fetch data from the server. Only data, not HTML, is exchanged with the server, which means pages do not need to be reloaded from scratch.
            Client-Side Rendering: The rendering of the page content is primarily done in the browser using JavaScript. While this can speed up page transitions and reduce server load, it also means that the initial load might take longer as the browser has to load the framework and the initial content.
            Routing: SPAs handle routing differently from traditional multi-page applications. The routing is handled internally by the JavaScript loaded on the page, without the need for server-side routing to intervene. This can make URLs in SPAs look different, often using hash (#) symbols or the HTML5 History API to manage navigation.
            Challenges: Despite their advantages, SPAs face challenges such as SEO optimization, as search engines historically had difficulty indexing content loaded asynchronously. However, modern solutions like server-side rendering (SSR) and static site generation (SSG) have helped overcome these limitations. Additionally, SPAs can have implications for performance on the initial load and may require more careful consideration of architectural decisions.


## What is difference between Client Side Routing and Server Side Routing?
    
       Server-Side Routing :

        Definition:
            Server-side routing is the traditional way of handling routing in web applications. Every time a user requests a new page, the browser makes a request to the server, and the server responds with a new document. This process involves a full page refresh.
        Performance: 
            Initially, it can be slower for the user, especially on slower networks, because each navigation requires a round trip to the server, and the entire page must be reloaded.
        SEO Optimization: 
            It is inherently SEO-friendly because each page is a new document from the server, making it easier for search engines to crawl and index them.
        Scalability: 
             Handling routing on the server can be more demanding on server resources, especially with a large number of requests.
        User Experience: 
            Users may experience a flicker or delay as the entire page reloads with each navigation.
        Examples of Use:
             Traditional multi-page applications (MPAs) where each page is a separate HTML document.


        Client-Side Routing

           Definition: 
               Client-side routing is a modern approach used primarily in single-page applications (SPAs). It leverages JavaScript to manage routing. When a user navigates to a different part of the application, no request is made to the server for a new page. Instead, the current page is dynamically updated to display new content, usually leveraging frameworks/libraries like React, Vue, or Angular.
            Performance:
                It can offer a faster and smoother experience after the initial load, as only the necessary content is updated, and there's no full page refresh.
            SEO Optimization: 
                 Traditionally seen as less SEO-friendly, although advancements and practices such as server-side rendering (SSR) and static site generation (SSG) have significantly improved SEO capabilities of SPAs.
            Scalability: 
                Less taxing on the server after the initial load, as most resources (HTML, CSS, JavaScript) are loaded once. Subsequent navigations require minimal to no server communication.
            User Experience: 
                Provides a smoother and more app-like experience, as there's no full page reload. Transitions between pages can be animated, improving perceived performance.
            Examples of Use:
                Single-page applications (SPAs) where the application runs within a single HTML document, and content is dynamically changed through JavaScript.

            Key Differences

               Navigation and Loading:

                    Server-side: 
                        Full page reloads for each navigation, with content being served directly from the server.
                    Client-side:
                        Navigation does not involve page reloads; content is dynamically replaced using JavaScript.

                    Resource Requests:

                    Server-side: 
                        Each navigation results in a new HTTP request to the server for a full page.
                    Client-side: 
                         Most resources are loaded once, with only data or partial content being fetched as needed.


                    Performance and User Experience:

                    Server-side: 
                         Can be slower due to full page reloads, affecting user experience on slow connections.
                    Client-side: 
                         Generally offers a faster, smoother experience after the initial load.


                    SEO:

                    Server-side:
                         More straightforward for search engines to index.
                    Client-side:
                          Requires additional considerations, though modern techniques have mitigated many SEO concerns.
                




## 
 React Router DOM - https://reactrouter.com/en/main

## 
   Client Side Routing - https://reactrouter.com/en/main/start/overview

## 
    Formik - https://formik.org/