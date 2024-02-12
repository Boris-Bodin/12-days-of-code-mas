# Day 2: Two Turtle Doves (Creating the Homepage)

Welcome back to the "12 Days of Code-mas" series! On Day 2, we dive into the heart of our Holiday Countdown App by creating a festive and inviting homepage. This chapter will guide you through setting up your Angular project and designing a homepage that exudes holiday cheer.

## Setting Up the Angular Project

First, let's initialize our Angular project. Ensure you have Angular CLI installed (as covered on Day 1). Open your terminal and follow these steps:

```bash
# Create a new Angular project named 'holiday-countdown'
ng new holiday-countdown --package-manager=yarn
# For this project, we'll use the following settings :
# - Which stylesheet format would you like to use? SCSS
# - Do you want to enable Server-Side Rendering (SSR) and Static Site Generation (SSG/Prerendering)? No

# Navigate into your project directory
cd holiday-countdown

# Start the development server
ng serve
```

Visit `http://localhost:4200/` in your browser. You should see the default Angular welcome page.

For this project, we'll skip the configuration of the tsconfig.json file.
But usually, you would want to set for example the following options:
- `"strict": true` to enable strict type checking
- `"noImplicitAny": true` to disallow implicit `any` types

## Understanding Angular Components and Routing

Before we start coding, let's understand some key Angular concepts:

- Components: Think of components as the building blocks of an Angular app. They control what you see on the screen, which in Angular terms is called a view. Our 'homepage' component will manage all content on the homepage.
- Routing: This is how we navigate between different views or components in Angular. It's like creating a pathway for users to move through different parts of our app.

## Designing the Homepage Layout

### Creating a New Component

Every Angular application is made up of components. Let's create a new component for our homepage:

```bash
ng generate component homepage
```

This command creates a new folder `src/app/homepage` with four files. Open `homepage.component.html` and replace its content with the following basic HTML structure:

```html
<div class="homepage">
    <h1>Welcome to the Holiday Countdown!</h1>
    <p>Counting down to a joyful and festive holiday season.</p>
</div>
```

### Styling the Homepage

Open `homepage.component.scss` (or `.css`, depending on your setup) and add some festive styling:

```scss
.homepage {
    text-align: center;
    color: #2e1503; /* Warm brown color */
    background-color: #f8d7a9; /* Light, festive background */
    padding: 20px;
    border-radius: 15px;
    margin-top: 20px;

    h1 {
        color: #c0392b; /* Holiday red */
        text-shadow: 2px 2px 2px #fff;
    }
    
    p {
        text-shadow: 1px 1px 1px #fff;
    }
}
```

Feel free to adjust the colors and styles to fit your holiday theme.

### Adding Festive Flair

To add a festive touch, consider importing a holiday-themed font from Google Fonts and use holiday images. 
For example, you could use a font like 'Mountains of Christmas'.

```html
<link href="https://fonts.googleapis.com/css?family=Mountains+of+Christmas&display=swap" rel="stylesheet">
```

```scss
.homepage {
    font-family: 'Mountains of Christmas', cursive;
}
```

And include a header image of a winter landscape.

```html
<img src="assets/winter-landscape.png" alt="Winter landscape">
```

```scss
img {
  width: 100%;
  border-radius: 15px;
  margin-bottom: 20px;
}

```

### Keeping Our App Accessible

When designing, ensure good color contrasts and readable fonts. This makes your app enjoyable for everyone, including those with visual impairments.

## Implementing Basic Navigation

To navigate through your app, you need to set up routing.

### Setting Up Angular Routing

In your `app-routing.module.ts`, import the `HomepageComponent` and define a route:

```typescript
import { HomepageComponent } from './homepage/homepage.component';

export const routes: Routes = [
    { path: '', component: HomepageComponent },
    // Other routes will go here
];
```

This configuration makes `HomepageComponent` the default landing page of your application.

Replace the content of `app.component.html` with the following:

```html
<router-outlet></router-outlet>
```

## Incorporating Angular Material

Angular Material offers a wide range of UI components. Let's add a button to our homepage.

### Adding Angular Material

Install Angular Material in your project:

```bash
ng add @angular/material
```

Choose a custom theme and set up typography and animations as prompted.

The theme will be applied to all Angular Material components.

We'll configure the theme in our `styles.scss`:

```scss
$holiday-countdown-primary: mat.define-palette(mat.$red-palette);
$holiday-countdown-accent: mat.define-palette(mat.$blue-palette, A200, A100, A400);

$holiday-countdown-warn: mat.define-palette(mat.$orange-palette);

$holiday-countdown-theme: mat.define-light-theme((
        color: (
                primary: $holiday-countdown-primary,
                accent: $holiday-countdown-accent,
                warn: $holiday-countdown-warn,
        ),
        typography: mat.define-typography-config(
                $font-family: 'Mountains of Christmas, cursive',
        ),
        density: 0,
));
```

### Using a Material Button

In `homepage.component.html`, add a Material button:

```html
<button mat-raised-button color="primary">Explore</button>
```

Remember to import `MatButtonModule` in your `homepage.component.ts`.


## Troubleshooting

If your homepage doesn’t appear as expected:
- Ensure the development server is running (`ng serve`).
- Check for any typos or errors in your code.
- Make sure all necessary modules are imported in `app.module.ts`.

## Conclusion

Congratulations on completing Day 2! Your Holiday Countdown App now has a welcoming and festive homepage. On Day 3, we'll add user authentication to bring personalized experiences to our app. See you then for more Angular exploration! 🌟🎄