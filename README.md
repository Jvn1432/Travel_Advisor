# Google Map Companion
[demo](https://kushaj-google-map.vercel.app/)

![](assets/demo_image.png)

Fully-responsive travel companion and weather checking app built by combining Google Maps API, Travel Advisor API and WeatherAPI.com. Built using Next.js and TypeScript, this app can be used to search for places, fetch restaurant, hotels and attractions based on location.

## Table of Contents
- [Demo Videos](#demo-videos)
    - as
- [Dependencies](#dependencies)
- [Local Setup](#local-setup)
- [License](#license)

## Demo Videos


## Dependencies
- [React](https://reactjs.org/)
- [Next.js](https://nextjs.org/)
- [TypeScript](https://www.typescriptlang.org/)
- [MUI](https://mui.com/)
- [google-map-react](https://github.com/google-map-react/google-map-react)
- [@react-google-maps/api](https://react-google-maps-api-docs.netlify.app/)
- [Axios](https://axios-http.com/docs/intro)

## Local Setup

### Node.js and respository setup
**Step 1**. Setup Node.js v16.17.1. [nvm](https://github.com/nvm-sh/nvm) can be used to quickly setup Node.js (and you can also have multiple versions of Node.js).
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
nvm install 16.17.1
```

**Step 2**. Clone the repository and install all the dependencies.
```
git clone https://github.com/KushajveerSingh/google_map_companion
cd google_map_companion
npm install --legacy-peer-deps
```

`--legacy-peer-deps` would install the exact packages as used in the repository. The repository already includes VSCode and Prettier setup, and you can modify the default behavior in `.vscode/settings.json` and `.prettierrc` respectively.

**Step 3**. Create `.env.local` and copy the contents from `.env.example` to `.env.local`.
- `NEXT_PUBLIC_BASE_URL` - set to `http://localhost:3000/` during development and when you deploy the project on Vercel, set it to the domain where the project is hosted.

### Travel Advisor API setup
**Step 1**. Goto [RapidAPI](https://rapidapi.com/hub) and create an account if not already.

**Step 2**. Goto [Travel Advisor](https://rapidapi.com/apidojo/api/travel-advisor) API and click **Subscribe to Test** and this would generate the API key for you.

**Step 3**. Copy the **X-RapidAPI-Key** key to `.env.local` under `NEXT_PUBLIC_TRAVEL_ADVISOR_KEY`.

Some tips when working with the API
- On the free tier only 500 requests are allowed per month. So for devlopment, I would suggest to create a secondary account on RapidAPI and use that instead.
- Because the request limit is low, I have added a Dialog box that pops up when a user visits the site and the request limit is reached. A screenshot of how the dialog box looks is attached below.
- Even when the limit is reached, you can still search for places and check the weather.

![](assets/travel_advisor_limit.png)

### Weather API setup

**Step 1**. Similar to above, goto [WeatherAPI.com](https://rapidapi.com/weatherapi/api/weatherapi-com) and click **Subscribe to Test**.

**Step 2**. Copy the **X-RapidAPI-Key** key to `.env.local` under `NEXT_PUBLIC_WEATHER_API_KEY`. If you are using the same account for both Travel Advisor and Weather API, then the keys would be same.

To show the weather, 5 random positions (plus the center) are chosen on the map. The logic for it is in `src/api.ts` and you can change the limit or the logic of getting the random places.

### Google Maps Setup

Note some things
- You will be setting up an account on [Google Cloud Platform](https://cloud.google.com/) and for that you need to provide credit card information.
- For this project, we do not have to setup any cloud instances and thus there would be no charges related to that.
- Google Maps provide a free montly quota, and if you go over that you will have to pay for that (you will not be autocharged). I still have $0 in billing.
- I have perosnlly set up a $5 alert on my account in case I ever get charged.

**Step 1**. Goto [Google Cloud Platform](https://cloud.google.com/) and create an account. Provide the bank information and claim the free joining credits.

**Step 2**. Goto Console -> New Project and provide all the necessary details. Select the billing associated with your credit card, that you setup in Step 1.

![](assets/google_cloud_new_project.png)

**Step 3**. On the left-hand sidebar of your project, click **APIs & Services** -> **Library**.

![](assets/google_cloud_library.png)

**Step 4**. Search for **Maps JavaScript API** and enable it. After enabling it, click on **Manage**.

**Step 5**. On the left-hand sidebar, click **Credentials** and then **Create Credentials** in the top.

**Step 6**. Copy the API key to `.env.local` under `NEXT_PUBLIC_GOOGLE_MAP_API_KEY`.

A video demo of the above is shown below.

https://user-images.githubusercontent.com/24699564/204116954-4e37a274-6639-4160-8086-3ca8d6ab2d8a.mp4

### Development and deployment instructions
**Step 1**. Run `make run dev` to start the local development server at `localhost:3000`. Now you can customize the application as per your needs.

**Step 2**. After making the desired changes, you can push your project to GitHub and you are ready for deployment on [Vercel](https://vercel.com/)

**Step 3**. Create an account on [Vercel](https://vercel.com/) and then click **Add New...** -> **Project** and choose your github repository.

And that is it. You have successfully deployed your custom google map companion website to Vercel.

## License
This application has Apache License Version 2.0, as found in the [LICENSE](./LICENSE) file.
