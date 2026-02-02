## 🧪 Jest Unit Testing Setup (Vite + React)

Follow the steps below to configure **Jest + React Testing Library** in a Vite-based React project.

---

### ✅ 1. Create React App with Vite (if not created)

```bash
npm create vite@latest my-app
cd my-app
npm install
Choose:

React

JavaScript or TypeScript

✅ 2. Install Jest & Required Packages
npm install --save-dev \
jest \
@testing-library/react \
@testing-library/jest-dom \
babel-jest \
jest-environment-jsdom
If you use JSX, also install Babel presets:

npm install --save-dev @babel/preset-env @babel/preset-react
✅ 3. Create Babel Configuration
Create a file named babel.config.cjs in the project root:

module.exports = {
  presets: [
    ['@babel/preset-env', { targets: { node: 'current' } }],
    ['@babel/preset-react', { runtime: 'automatic' }],
  ],
};
✅ 4. Create Jest Configuration
Create a file named jest.config.cjs:

module.exports = {
  testEnvironment: "jsdom",
  setupFilesAfterEnv: ["<rootDir>/src/setupTests.js"],
  moduleNameMapper: {
    "\\.(css|scss|sass)$": "identity-obj-proxy"
  }
};
Install CSS mock dependency:

npm install --save-dev identity-obj-proxy
✅ 5. Setup Testing Library
Create the file src/setupTests.js:

import "@testing-library/jest-dom";
✅ 6. Add Test Script in package.json
"scripts": {
  "dev": "vite",
  "build": "vite build",
  "test": "jest"
}
✅ 7. Example Test
📄 src/App.jsx
function App() {
  return <h1>Hello Jainesh</h1>;
}

export default App;
📄 src/App.test.jsx
import { render, screen } from "@testing-library/react";
import App from "./App";

test("renders heading", () => {
  render(<App />);
  expect(screen.getByText("Hello Jainesh")).toBeInTheDocument();
});
✅ 8. Run Tests
npm test
or

npx jest
🖼 Image & Asset Mocking (Optional but Recommended)
🛠 Step 1: Create File Mock
Create this file in the project root:

📄 __mocks__/fileMock.js

module.exports = "test-file-stub";
Project structure:

my-app/
├── __mocks__/
│   └── fileMock.js
├── src/
├── babel.config.cjs
├── jest.config.cjs
└── package.json
🛠 Step 2: Update jest.config.cjs
Add image extension mappings:

module.exports = {
  testEnvironment: "jsdom",
  setupFilesAfterEnv: ["<rootDir>/src/setupTests.js"],
  moduleNameMapper: {
    "\\.(css|scss|sass)$": "identity-obj-proxy",
    "\\.(svg|png|jpg|jpeg|gif|webp)$": "<rootDir>/__mocks__/fileMock.js"
  }
};
✅ Result
After setup, running:

npm test
```
