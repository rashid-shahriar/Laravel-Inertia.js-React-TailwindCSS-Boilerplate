## Laravel with Inertia.js and React Setup Guide

Follow the steps below to set up a Laravel project with Inertia.js, React, and TailwindCSS

#### 1\. **Install Laravel**

-   Install Laravel using either:

    ```
    Laravel new project-name
    ```
    OR

     ```
    composer create-project laravel/laravel project-name
     ```

-   Follow the official Laravel [installation documentation](https://laravel.com/docs/11.x/installation).

#### 2\. **Install React and Vite Plugin**

-   Install React and React DOM:

    ```
    npm install react react-dom
    ```

-   Install the Vite plugin for React:

    ```
    npm install --save-dev @vitejs/plugin-react
    ```

    Refer to the [Laravel Vite documentation](https://laravel.com/docs/11.x/vite#react) for additional details.

* * * * *

### Inertia.js Setup

#### 3\. **Server-Side Setup**

-   Install the Inertia.js server-side package:

    ```
    composer require inertiajs/inertia-laravel
    ```

    Refer to the [Inertia.js server-side setup](https://inertiajs.com/server-side-setup) documentation.

-   Rename the `welcome.blade.php` file to `app.blade.php`:

    ```
    mv resources/views/welcome.blade.php resources/views/app.blade.php
    ```

-   Add the root template in the `app.blade.php` file: Follow the example in the [Inertia.js server-side setup](https://inertiajs.com/server-side-setup).

-   Generate the Inertia middleware:
    ```
    php artisan inertia:middleware
    ```

    Refer to the [middleware section](https://inertiajs.com/server-side-setup) of the documentation.

-   Add the middleware in `bootstrap/app.php`: Open `bootstrap/app.php` and register the middleware according to the instructions in the [Inertia.js server-side setup](https://inertiajs.com/server-side-setup).

#### 4\. **Client-Side Setup**

-   Install Inertia.js for React:

    ```
    npm install @inertiajs/react
    ```

    Refer to the [Inertia.js client-side setup](https://inertiajs.com/client-side-setup).

-   Rename `app.js` to `app.jsx`:
    ```
    mv resources/js/app.js resources/js/app.jsx
    ```

-   Initialize the Inertia app in `app.jsx`: Follow the example from the [Inertia.js client-side setup](https://inertiajs.com/client-side-setup).

-   Modify `vite.config.js` to add support for React:
    ```
    import { defineConfig } from 'vite';
    import react from '@vitejs/plugin-react';

    export default defineConfig({
        plugins: [react()],
        input: "resources/js/app.jsx",
    });
    ```

-   In `app.blade.php`, add:

    ```
    @viteReactRefresh
    ```

-   In `routes/web.php`, define a route for Inertia:

    ```
    Route::get('/', function () {
        return inertia('Home');
    });
    ```

* * * * *

### TailwindCSS Setup

#### 5\. **Install TailwindCSS**

-   Follow the [TailwindCSS Laravel guide](https://tailwindcss.com/docs/guides/laravel).

-   Install the required dependencies:
    ```
    npm install -D tailwindcss postcss autoprefixer
    ```

-   Initialize the Tailwind configuration:
    ```
    npx tailwindcss init -p
    ```

-   Modify `tailwind.config.js` as per the TailwindCSS guide: Refer to the [official documentation](https://tailwindcss.com/docs/guides/laravel) for guidance.

-   Update `app.css` or use a pre-defined Tailwind setup: You can use the [Tailwind classes](https://github.com/JonVadar/YouTube_videos/blob/main/tailwind_classes.css) from GitHub as an example.

-   Import `app.css` in `app.jsx`:

    ```
    import "../css/app.css";
    ```

* * * * *

### Running the Application

#### 6\. **Run Laravel and Vite**

-   Start the Laravel server:

    ```
    php artisan serve
    ```

-   Run the Vite development server:
    ```
    npm run dev
    ```

Now your Laravel application with Inertia.js, React, and TailwindCSS is ready to run.
