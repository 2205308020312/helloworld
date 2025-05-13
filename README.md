# Hello World
Assignment

## Installation and Deployment Instructions

### Environment Preparation
Ensure the following tools are installed locally:
- **Node.js** (Recommended version >= 16.x)
- **npm** (Comes with Node.js) or **yarn**

### Dependency Installation
1. **Clone the project repository**:
   ```bash
   git clone https://github.com/your-repo/books-management-system.git
   cd books-management-system
   ```

2. **Install project dependencies**:
   ```bash
   npm install
   ```

### Starting the Development Environment
1. **Start the development server**:
   ```bash
   npm run serve
   ```

2. **Access the application**:
   Open a browser and visit [http://localhost:8080](http://localhost:8080).
   The development server supports hot updates, and the page will automatically refresh after modifying the code.

### Production Environment Deployment
1. **Build the production environment code**:
   ```bash
   npm run build
   ```

2. **Explanation of build artifacts**:
   - The static files after building will be generated in the `dist` directory.
   - Include HTML, CSS, JavaScript, images and other resources.
   - All resources have been compressed and optimized.

3. **Deploy to the Web server**:
   Copy all the files in the `dist` directory to the root directory of your Web server, for example:
   - **Nginx**
   - **Apache**
   - **Cloud service providers** (such as AWS S3, Alibaba Cloud OSS)

---

## Configuration Instructions

### Environment Variables
The project uses `.env` files to configure environment variables:
- `.env.development`: Development environment configuration
- `.env.production`: Production environment configuration

#### Modify the API Interface Address
If you need to modify the API interface address, you can modify the `VUE_APP_API_BASE_URL` variable in the `.env` file.

---

## Frequently Asked Questions

### 1. Network issues when installing dependencies
**Problem phenomenon**: Downloading dependencies fails during `npm install` or `yarn install`.
**Solutions**:
- Use a domestic mirror source:
  ```bash
  npm install --registry=https://registry.npmmirror.com
  ```
- Or configure the npm mirror:
  ```bash
  npm config set registry https://registry.npmmirror.com
  ```

### 2. Failure to start the development server
**Problem phenomenon**: The browser cannot access [http://localhost:8080](http://localhost:8080) after executing `npm run serve`.
**Solutions**:
- Check if the port is occupied:
  ```bash
  netstat -ano | findstr :8080
  ```
- Modify the port: Add the following configuration in `vue.config.js`:
  ```javascript
  module.exports = {
    devServer: {
      port: 8081 // Modify to another port
    }
  }
  ```

### 3. Blank page after building
**Problem phenomenon**: The page is blank and there are errors in the console after deploying to the production environment.
**Solutions**:
- Check if the `publicPath` configuration in `vue.config.js` is correct:
  ```javascript
  module.exports = {
    publicPath: process.env.NODE_ENV === 'production' ? '/' : '/'
  }
  ```
- Ensure that the server configuration is correct and supports single-page application routing.

### 4. Dependency version conflicts
**Problem phenomenon**: Version conflict errors occur when installing dependencies.
**Solutions**:
- Delete `node_modules` and `package-lock.json` (or `yarn.lock`):
  ```bash
  rm -rf node_modules package-lock.json
  ```
- Reinstall the dependencies:
  ```bash
  npm install
  ```

### 5. ESLint check fails
**Problem phenomenon**: The code fails to pass the ESLint check during development.
**Solutions**:
- Automatically fix the fixable errors:
  ```bash
  npm run lint -- --fix
  ```
- Modify the `.eslintrc.js` configuration file to adjust the rules. 