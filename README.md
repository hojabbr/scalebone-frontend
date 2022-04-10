# ScaleBone Frontend - Next.js Edition

## Introduction

This repository is an implementing of the [ScaleBone](https://github.com/hojabbr/scalebone) application / authentication
starter kit frontend in [Next.js](https://nextjs.org). All of the authentication boilerplate is already written for you

- powered by [Laravel Sanctum](https://laravel.com/docs/sanctum), allowing you to quickly begin pairing your beautiful
  Next.js frontend with a powerful ScaleBone Laravel backend.

## Official Documentation

### Installation

First, create a Next.js compatible ScaleBone backend by cloning and
installing [ScaleBone](https://github.com/hojabbr/scalebone) from and installing ScaleBone's API scaffolding:

Next, ensure that your application's `APP_URL` and `FRONTEND_URL` environment variables are set
to `http://localhost:8000` and `http://localhost:3000`, respectively.

After defining the appropriate environment variables, you may serve the ScaleBone application using the `serve` Artisan
command or use sail:

```bash
# Serve the application...
php artisan serve
```

```bash
# Serve the application...
sail up
```

Next, clone this repository and install its dependencies with `yarn install` or `npm install`. Then, copy
the `.env.example` file to `.env.local` and supply the URL of your backend:

```
NEXT_PUBLIC_BACKEND_URL=http://localhost:8000
```

Finally, run the application via `npm run dev`. The application will be available at `http://localhost:3000`:

```
npm run dev
```

> Note: Currently, we recommend using `localhost` during local development of your backend and frontend to avoid CORS "Same-Origin" issues.

### Authentication Hook

This Next.js application contains a custom `useAuth` React hook, designed to abstract all authentication logic away from
your pages. In addition, the hook can be used to access the currently authenticated user:

```js
const ExamplePage = () => {
    const { logout, user } = useAuth({ middleware: 'auth' })

    return (
        <>
            <p>{user?.name}</p>

            <button onClick={logout}>Sign out</button>
        </>
    )
}

export default ExamplePage
```

> Note: You will need to use [optional chaining](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Optional_chaining) (`user?.name` instead of `user.name`) when accessing properties on the user object to account for Next.js's initial server-side render.

## License

Laravel Breeze Next is open-sourced software licensed under the [MIT license](LICENSE.md).
