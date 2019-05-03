#

- Single-page application written in an Angular6 frontend with Typescript
- Uses Firebase's Cloud Storage to store larger files such as pictures.
    - Routes with photos that are stored in the cloud have their URLs pre-fetched using a service implementing Angular's <code>Resolve<></code> interface.
    - The URLs are loaded asynchronously using Angular's <code>async</code> pipe.
- Animations used to liven up pages include:
    - Loading indicator when pre-fetching data
    - Route animations and child animations upon page load
- Uses complex angular routing features
  - data transfer with route parameters
  - asynchronous picture loading with Firebase Storage
  - route resolvers
  - lazy loading
- RxJS usage for asynchronous data handling
    - During development, I also migrated from RxJS5 to RxJS6 to keep up-to-date.

