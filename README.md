# Component composition vs inheritance

See https://github.com/GavinJoyce/ember-component-composition-vs-inheritance/tree/master/app/components for some example components that use both inheritance and composition.

Reasons why composition is better:

 * There is much less coupling between the `<DataProvider>` component and the `<Report>` components. With inheritance, every detail of the component internals is available in the derived class. If the base class is a classic Ember component, the derived class must be too. Refactoring it to be a Glimmer component is tricky as any derived components must be migrated at the same time. In comparison, the components aren't coupled to the same degree with composition. We have specified the [`<DataLoader>` interface](https://github.com/GavinJoyce/ember-component-composition-vs-inheritance/blob/master/app/components/composition/data-loader.hbs) in its template, this is all consuming components need to know about this component. With composition, the `<DataLoader>` could be a classic component or a Glimmer component, consumers don't need to know.
  * Composition works with template only components, inheritance mandates a [derived JavaScript class](https://github.com/GavinJoyce/ember-component-composition-vs-inheritance/blob/master/app/components/inheritance/report1.js).
  * Due to the strong coupling, it's not possible to understand a derived component without also looking at its base classes. When making changes to the derived class, one must take care so not to inadvertently override base properties or actions. With composition, components are isolated from each other so this isn't a concern.
  * The coupling that comes with inheritance also means that duplicate tests are necessary to ensure that no unintended overriding of base behaviour has occurred. In contrast, the clean separation of composition means that tests can focus on testing just the higher level behaviour of a component, it's safer to assume that the sub components are behaving well (assuming that they too are separately tested themselves).

## Prerequisites

You will need the following things properly installed on your computer.

- [Git](https://git-scm.com/)
- [Node.js](https://nodejs.org/) (with npm)
- [Ember CLI](https://ember-cli.com/)
- [Google Chrome](https://google.com/chrome/)

## Installation

- `git clone <repository-url>` this repository
- `cd composition`
- `npm install`

## Running / Development

- `ember serve`
- Visit your app at [http://localhost:4200](http://localhost:4200).
- Visit your tests at [http://localhost:4200/tests](http://localhost:4200/tests).

### Code Generators

Make use of the many generators for code, try `ember help generate` for more details

### Running Tests

- `ember test`
- `ember test --server`

### Linting

- `npm run lint:hbs`
- `npm run lint:js`
- `npm run lint:js -- --fix`

### Building

- `ember build` (development)
- `ember build --environment production` (production)

### Deploying

Specify what it takes to deploy your app.

## Further Reading / Useful Links

- [ember.js](https://emberjs.com/)
- [ember-cli](https://ember-cli.com/)
- Development Browser Extensions
  - [ember inspector for chrome](https://chrome.google.com/webstore/detail/ember-inspector/bmdblncegkenkacieihfhpjfppoconhi)
  - [ember inspector for firefox](https://addons.mozilla.org/en-US/firefox/addon/ember-inspector/)
