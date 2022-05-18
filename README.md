# Amazon-scraper-API
### Features
- product details
- product reviews
- product offers
- search results

### Development
```
npm install express request-promise request nodemon
```
#### link
https://valamazonscraper.herokuapp.com
### API Endpoints
#### SEARCH(GET)

**Product details Request**
https://valamazonscraper.herokuapp.com/products/B08N5KWB9H?api_key= **add your scraper api here**

**response**
![image](https://user-images.githubusercontent.com/61587290/169061561-d3beef0f-576d-4665-a083-3c444eabafdc.png)

**Product reviews Request**
https://valamazonscraper.herokuapp.com/products/B08N5KWB9H/reviews?api_key=**add your scraper api here**

**response**
![image](https://user-images.githubusercontent.com/61587290/169062403-f548e8a4-d10d-4dee-a054-eb8e64a3d8c5.png)

**product offers Request**
https://valamazonscraper.herokuapp.com/products/B08N5KWB9H/offers?api_key=**add your scraper api here**

**response**
![image](https://user-images.githubusercontent.com/61587290/169062873-ea170df8-067b-4151-89ce-b007d6dc1f73.png)

**search results request**
https://valamazonscraper.herokuapp.com/search/macbook%20air?api_key= **add your scraper api here**
**response**
![image](https://user-images.githubusercontent.com/61587290/169064027-e46fde9d-7680-444f-82a8-d9c31d5671e0.png)

#### suggestions
> you can add your scrapper api key to your code for you not to keep adding it in your link
add the following code for that 
```js
const express = require('express');
const request = require('request-promise');
const app = express();

const apiKey='//your scrapper api key';
 const baseUrl =`http://api.scraperapi.com?api_key=${apiKey}&autoparse=true`;
const PORT = process.env. PORT || 5000;

app.use(express.json());
app.get('/', (req, res) => {
 res.send('Welcome to Amazon Scraper API.');
});

// Get product reviews
//follow the following format for your other api endpoints
app.get('/products/:productId/reviews', async (req, res) => {
   const { productId } = req.params;
 
   try {
       const response = await request(`${baseUrl}&url=https://www.amazon.com/product-reviews/${productId}`);
      
       res.json(JSON.parse(response));
   } catch (error) {
       res.json(error);
   }
});

app.listen(PORT, () => console.Log('Server running on port ${ PORT}'));


```
#### Run your app locally
`npm run dev`
port:5000

#### Reference
javascript mastery 

Happy learning!
