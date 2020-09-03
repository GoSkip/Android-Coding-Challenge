# Skip Android Coding Challenge

Here at Skip we aim to create world-class app experiences for our customers. Skip takes great care in how we select members of our engineering team. This coding challenge will help us get an idea of how you would use software to solve problems for our end users.

We know that your time is valuable, so we’ve designed the challenge with that in mind. There's no specific amount of time that this challenge should take you to complete, as the level of effort will depend on how familiar you are with Android development, but we don't want it to take you more than an evening. With that in mind, please feel free to spend as much time as you’d like crafting your preferred solution and we hope you have fun building it!

## Challenge: Product Search with Check Digit validation!

Your challenge is to create a three-screen application that allows users to:
1. Search for products at Best Buy using the [Best Buy Products API](https://bestbuyapis.github.io/api-documentation/#products-api)
2. View their search results in a list
3. View the individual details of each product and validate that the check digit is correct (See the [Notes section](#what-is-a-check-digit) below for check digit details)

The first screen should display an input field that allows users to search for products (for example, “laptop”, “Cell Phone”, “Stainless Steel Ovens”, etc).  Upon executing a search, the next screen should display the results in a list. Clicking an item in the list should launch a details screen. The details screen should show the product's image and provide more details about the product.

### Requirements

1. The main screen should display a search input, and should perform a search against the Best Buy Product Search API when the user submits the query.
2. When a search returns results, these should be displayed in a list format. Each list item should provide, at a minimum:
    * Name of the product (e.g., Google - Pixelbook Pen - Midnight Blue)
    * Image from the response. 
3. Clicking a list item should launch the details screen for that product. The details screen for a product should include:
    * Name of the product (e.g., Google - Pixelbook Pen - Midnight Blue)
    * UPC of the product (e.g., 842776108302)
    * LongDescription of the product (e.g., Write and design with confidence with this Google Pixelbook pen. The responsive instrument can be used with Google Pixelbook or Google Assistant to make taking notes or creating art more efficient. The realistic feel of this Google Pixelbook pen helps you write and draw naturally so you can focus on your designs.)
    * Image of the product
    * Price of the product (e.g., $99.99)
    * The check digit that you have calculated (e.g., 2) (See the [Notes section](#how-do-i-calculate-a-check-digit) below for how this is calculated).
4. The user should be able to navigate between screens according to Android platform conventions.
5. Please zip up your project and email it to <jobs@getskip.com> with your first and last name.

Feel free to use any libraries you feel are appropriate to your needs.

### Notes

To be able to access the Best Buy API you will need an API key. This API key should have been sent to you already. If you have not received the API key, please email <jobs@getskip.com> with your name and the request for the API key.


#### What is a check digit?
Most products sold in retail have on them what's called a UPC-A barcode. UPC-A barcodes are a set of 12 digits. The first 11 digits are a product identifier, while the last digit is what's called a check digit. The check digit exists to ensure that the barcode was generated correctly. The products that are returned to you from Best Buy contain a UPC that is type UPC-A and already have a check digit. We need to ensure that the check digit returned in the UPC from Best Buy is correct.


#### How do I calculate a check digit?
Suppose that you want to find the check digit of UPC-A number `84277610830`.
1. From the right to the left assign an odd/even position to each digit, starting with odd.
2. Sum all digits in odd positions and multiply the result by 3: `(0+8+1+7+2+8)*3=78`
3. Sum all digits in even positions: `(3+0+6+7+4)=20`
4. Sum the results of step two and three: `78+20=98`
5. Divide the result of step four by 10. The check digit is the number which adds the remainder to 10.
In our case, divide 98 by 10 we get the remainder 8.
The check digit then is the result of 10-8=2.
If there is no remainder then the check digit equals zero.
http://www.azalea.com/white-papers/upc-barcode-check-digit/

#### Sample Query
A query to the Best Buy Product API could look something like:

```
curl "https://api.bestbuy.com/v1/products(search=pixel&search=pen)?format=json&show=name,upc,salePrice,image,longDescription&apiKey=INSERT_API_KEY"
```

#### Free Icons if Needed
For quick and easy icons if needed, consider using the [Material icons](https://material.io/icons/).

### Considerations

Your submission will be evaluated on:

(Based on order of importance)
1. Implementation of the stated requirements
2. Its resistance to crashing
3. The general quality of the code
4. Application Architecture
5. Your use of Android coding conventions
6. Knowledge and usage of Android libraries and SDKs
7. Clarity of communications in comments and other documentation
8. UI and UX -- while we don't want you to spend any time creating custom icons or other assets, the app should look clean and generally obey the Human Interface Guidelines

Coding challenge reviewers should be able to load your project into Android Studio and build an instance of your app into an emulator. If the reviewer needs to do any project configuration (i.e. add his/her own Best Buy API key) that is enough reason to reject your application.

Don’t worry if your app has personality or a sense of humor. We want you to have fun!


Sincerely,

Your Friends at Skip

### Sample Best Buy Response

For your convenience, below is a sample JSON response from the Best Buy Products Search API.

```
{
    "from": 1,
    "to": 8,
    "currentPage": 1,
    "total": 8,
    "totalPages": 1,
    "queryTime": "0.061",
    "totalTime": "0.070",
    "partial": false,
    "canonicalUrl": "/v1/products(search=\"pixel\"&search=\"pen\")?show=name,upc,salePrice,image,longDescription&format=json&apiKey=YOUR_API_KEY",
    "products": [
        {
            "name": "Google - Pixelbook Pen - Midnight Blue",
            "upc": "842776108302",
            "salePrice": 99.00,
            "image": "https://pisces.bbystatic.com/image2/BestBuy_US/images/products/6306/6306364_sa.jpg",
            "longDescription": "Write and design with confidence with this Google Pixelbook pen. The responsive instrument can be used with Google Pixelbook or Google Assistant to make taking notes or creating art more efficient. The realistic feel of this Google Pixelbook pen helps you write and draw naturally so you can focus on your designs."
        },
        {
            "name": "Apple Pencil (1st Generation) - White",
            "upc": "888462313674",
            "salePrice": 99.99,
            "image": "https://pisces.bbystatic.com/image2/BestBuy_US/images/products/4538/4538802_sa.jpg",
            "longDescription": "The new Multi-Touch subsystem in the new iPad 9.7\" and iPad Pro gives Apple Pencil striking capabilities alongside pixel perfect precision. Using incredibly sensitive pressure and tilt sensors, Apple Pencil instantly recognizes when you are pressing harder or shifting its angle. So you can vary line weight, create subtle shading, and produce a wide range of artistic effects &#8212; just like with a conventional pencil."
        },
        {
            "name": "Microsoft - Surface Go 2 - 10.5\" Touch-Screen - Intel Pentium Gold - 4GB - 64GB Storage - Platinum",
            "upc": "889842593549",
            "salePrice": 399.99,
            "image": "https://pisces.bbystatic.com/image2/BestBuy_US/images/products/6408/6408476_sa.jpg",
            "longDescription": "Your perfect everyday companion. New 10.5\" Surface Go 2 is perfect for keeping up and winding down - delivering tablet portability with laptop versatility, long battery life, a stunning touchscreen, and Windows security for the whole family. Browse, shop, and manage email with ease, relax with your favorite TV shows, and much more."
        },
        {
            "name": "Microsoft - Surface Go 2 - 10.5\" Touch-Screen - Intel Pentium Gold - 8GB - 128GB Storage - Platinum",
            "upc": "889842593686",
            "salePrice": 549.99,
            "image": "https://pisces.bbystatic.com/image2/BestBuy_US/images/products/6408/6408475_sa.jpg",
            "longDescription": "Your perfect everyday companion. New 10.5\" Surface Go 2 is perfect for keeping up and winding down - delivering tablet portability with laptop versatility, long battery life, a stunning touchscreen, and Windows security for the whole family. Browse, shop, and manage email with ease, relax with your favorite TV shows, and much more."
        },
        {
            "name": "Surface Pro X - 13\" Touch Screen - Microsoft SQ1 - 8GB Memory - 256GB SSD - WiFi+4G LTE - Keyboard+Slim Pen - Matte Black",
            "upc": "889842518801",
            "salePrice": 1569.98,
            "image": "https://pisces.bbystatic.com/image2/BestBuy_US/images/products/6375/6375053_sa.jpg",
            "longDescription": "You're always one step ahead. So is Surface Pro X. The sleek design and ultimate mobility combine with blazing-fast LTE&#178; Advanced Pro connectivity&#179; and an edge-to-edge 13\" touch screen with amazing graphics for creating, mobile gaming, and working away from your desk. For a premium laptop experience on the go, click Surface Pro X Signature Keyboard with Slim Pen (included) in place. The Pen stores securely and recharges in the keyboard, so it's always at your fingertips."
        },
        {
            "name": "Microsoft - Geek Squad Certified Refurbished Surface Go - 10\" Touch-Screen - Intel Pentium Gold - 4GB Memory - 64GB Storage - Silver",
            "upc": "400064103271",
            "salePrice": 323.99,
            "image": "https://pisces.bbystatic.com/image2/BestBuy_US/images/products/6410/6410327_sa.jpg",
            "longDescription": "Geek Squad&#174; Certified Refurbished products are thoroughly, painstakingly and lovingly tested, so you can be sure that your device will work right, right away. Learn more about Geek Squad&#174; Certified Refurbished products.Finish pending assignments on the go with this refurbished Microsoft Surface Go tablet. The 10-inch PixelSense multitouch display provides an interactive user experience, while the 64GB SSD offers vast media space and reduced load times. This Microsoft Surface Go tablet features an Intel Pentium Gold dual-core processor and 4GB of RAM for seamless multitasking."
        },
        {
            "name": "Knights of Pen and Paper Bundle - Nintendo Switch [Digital]",
            "upc": "400063215456",
            "salePrice": 22.49,
            "image": "https://pisces.bbystatic.com/image2/BestBuy_US/images/products/6321/6321545_sa.jpg",
            "longDescription": "Take on the roles of in-game players by taking on the roles of their characters in a traditional Pen and Paper RPG session in the ultimate meta role-playing experience.  This item cannot be returned or refunded, please visit Best Buy Return Policy to learn more."
        },
        {
            "name": "Knights of Pen & Paper 2 Deluxiest Edition - Nintendo Switch [Digital]",
            "upc": "400063215463",
            "salePrice": 12.99,
            "image": "https://pisces.bbystatic.com/image2/BestBuy_US/images/products/6321/6321546_sa.jpg",
            "longDescription": "Prepare to join Knights of Pen & Paper 2 in a turn-based, retro-style, pixel-art adventure full of danger, intrigue, and semi-appropriate cultural references.  This item cannot be returned or refunded, please visit Best Buy Return Policy to learn more."
        }
    ]
}
```
