# Description of my meme

* ## Information about this meme

    _I want to express the scenario -- **the funny result from testing my first image classifier model.**_

* ## The motivation of creating this meme

    _This meme is making fun of me -- My first machine learning model did not work very well; it through some hilarious predictions when I tested the model._

* ## The format of this meme

    _The format of this meme is very generic. However, I create my meme from the sketch._

# Display the meme

![my meme](my_meme.png)

# Images I used to create it

1. The first images is a picture of [Muffine](https://www.biggerbolderbaking.com/lemon-blueberry-muffins/)
![Muffin](https://www.biggerbolderbaking.com/wp-content/uploads/2020/05/Bakery-Style-Lemon-Blueberry-Muffins-WS-Thumbnail.jpg)

2. The second images is a picture of [Chihuahua](https://www.google.com/imgres?imgurl=https%3A%2F%2Fwww.k9web.com%2Fwp-content%2Fuploads%2F2021%2F01%2Ffive-purebred-chihuahua-dogs.jpg&imgrefurl=https%3A%2F%2Fwww.k9web.com%2Fbreeds%2Fchihuahua%2F&tbnid=SSD1ONX1GftxFM&vet=12ahUKEwiYs4Wens_2AhUTRGwGHcbQBigQMygfegUIARCcAg..i&docid=qyHM89uCDkWzFM&w=1200&h=593&q=chihuahua&ved=2ahUKEwiYs4Wens_2AhUTRGwGHcbQBigQMygfegUIARCcAg)

![Chihuahua](https://www.k9web.com/wp-content/uploads/2021/01/five-purebred-chihuahua-dogs.jpg)


# R code I used to create it

```
library(magick)

# create a blank image and write text
image <- image_blank(400,
                     150,
                     color = "#000000") %>%
  image_annotate(text = "WHEN I TEST MY FIRST\nIMAGE CLASSIFIER MODEL",
                 color = "#FFFFFF",
                 size = 35,
                 font = "Impact",
                 gravity = "center")

# read a muffin image and write text
image_1 <- image_read(path = "https://www.biggerbolderbaking.com/wp-content/uploads/2020/05/Bakery-Style-Lemon-Blueberry-Muffins-WS-Thumbnail.jpg") %>%
  image_crop("700x700+200") %>%
  image_scale(200)%>%
  image_annotate(text = "CHIHUAHUA",
                 color = "#FF0000",
                 size = 30,
                 font = "Impact",
                 gravity = "southwest")

# read a chihuahua image and write text

image_2 <- image_read(path = "https://www.k9web.com/wp-content/uploads/2021/01/five-purebred-chihuahua-dogs.jpg") %>%
  image_crop("230x230+300") %>%
    image_scale(200) %>%
      image_annotate(text = "MUFFIN",
                     color = "#FF0000",
                     size = 30,
                     font = "Impact",
                     gravity = "southeast")

# combine two images in one row
second_row <- c(image_1, image_2) %>%
  image_append()


# create my meme
meme <- c(image, second_row) %>%
  image_append(stack = TRUE)

# write the image
image_write(meme, "my_meme.png")
```
