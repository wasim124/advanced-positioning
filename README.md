# Advanced Positioning

## Topics of the day

1. Position Property
2. Position Static
3. Position Relative
4. Position Absolute
5. Position Fixed
6. Box-offset properties
7. Box offset properties for Relative elements
8. Box offset properties for Absolute elements
9. Box offset properties for fixed elements
10. Z-index property.

In the previous chapter, we learned how to position elements using floats and inline-block. With float, we can place element either to the left corner or right corner. The float also removes the element from its normal flow and creates some unwanted result. With the inline-block positioning method, we make the element come one after another and let them sit adjacent to each other. With all these methods we cannot place any element precisely. Sometime we may want to position an element very precisely anywhere in the window, may be exactly at the center of the window or top corner of the page or right bottom corner of the page. Sometimes we may want to fix the element somewhere in the window and it should not move as we scroll the page.

## 1. Position Property

For all these purposes we have position property in CSS to uniquely position the elements anywhere in our page or window. Position property accepts four different values and each value has its own use cases. With the position property, we can decide how we want to position an element in a page. The different values are: static, relative, absolute, and fixed. Based on these values of position property in CSS we can move elements either to the left or right or top or bottom of the page. Actually left, right, top, and the bottom is known as box-offset properties on which all the values of position property depends on except the static value. No worries, we will cover the box-offset properties at the end of position property, but for now, just understand we can move the element using these properties(left, right, top and bottom).

## 2. Position Static

This is the default value for the position property and this does not accept any box-offset property. It means each and every element in a page is a static element by default which cannot be moved using left, right, top, or bottom property.

The default static value can be overwritten using relative, absolute, and fixed.

## 3. Position Relative

The relative value is somewhat different from the static one because it accepts all the box-offset properties. We can move the relatively positioned element using box-offset properties.

```
  <div class="box">......</div>

  .box {
    position: relative;
    left: 60px;
    top: 60px;
  }
```

Now the box will move 60 pixels from left and 60px from down from its original position.

One important point for the relatively positioned element is that it will always remain in the normal flow of the page, unlike floated elements. If we position any relatively it's original position will be maintained, no elements can take its original position. As well as relatively positioned element won't disturb the other elements also, it will always move in its coordinates. A relatively positioned element may go on top or below the other elements but it will not push other elements either to the left, right, top, or bottom. Let's make this clear using an example. Suppose we have three boxes and the second box is relatively positioned then let's see how the second box will behave.

```
  <div class="box box-1">......</div>
  <div class="box box-2">......</div>
  <div class="box box-3">......</div>

  box {
    width: 100px;
    height: 100px;
    background: green;
  }
  .box-2 {
    position: relative;
    top: 60px;
  }
```

Here, we made the box-2 position relative but still, it is in the normal flow, therefore the third box won't take its position. Also, we shifted the second box from the top by 60 pixels, the box will move by 60 pixels and come on top of the third box. The third box position will not change due to changes in the position of the second box.

## 4. Position Absolute

Absolutely positioned elements accept all the box-offset properties. Similar to relative elements we can move the absolute elements in its coordinates. We can move either left or right or top or bottom to the absolutely positioned elements.

```
  <div class="box">......</div>

  .box {
    position: absolute;
    right: 60px;
    bottom: 60px;
  }
```

However, the absolute elements are different from the relatively positioned elements. Whenever we position any elements absolutely it goes out of the flow and it is removed from the normal flow of the page. That means its original position will be lost and the next upcoming element will take its position.

The display property is also changed if we position any element absolutely. A block level elements will start taking space according to the content it is wrapping inside. At the same time, an inline-level element may start accepting the box model properties(such as width and height).

If we don't provide any box-offset properties to absolute elements, the element will remain absolutely positioned in its original position but on Z-axis, its X and Y plane will be lost. Therefore the next element will take the original position of the absolute element and the absolute element will be on top of it.

```
  <div class="box box-1">......</div>
  <div class="box box-2">......</div>
  <div class="box box-3">......</div>

  box {
    width: 100px;
    height: 100px;
    background: green;
  }
  .box-2 {
    position: absolute;
  }
```

Here, the box-2 is absolutely positioned, so you'll see the original position of box-2 in the X-Y plane is taken by the box-3 and box-2 will be on top box-3.

We can position the absolute elements in two different ways. We can place them either relative to its parent in which it is wrapped or to the body of the page.

If we want to position the absolute element with relative to its parent then we need to position its parent relatively.

```
  <div class="box box-1">......</div>
  <section class="parent-box">
    <div class="box box-2">......</div>
  </section>
  <div class="box box-3">......</div>


  box {
    width: 100px;
    height: 100px;
    background: green;
  }
  .parent-box {
    position: relative;
  }
  .box-2 {
    position: absolute;
    right: 0;
    bottom: 0;
  }
```

Here, the box-2 is absolutely positioned with relative to its parent, because parent-box has been relatively positioned. Therefore the box-2 will sit at the right bottom corner of the parent-box.

Now, if we don't make its parent position relative then the box-offset property of the absolute element will work with relative to the body of the page.

```
  <div class="box box-1">......</div>
  <section class="parent-box">
    <div class="box box-2">......</div>
  </section>
  <div class="box box-3">......</div>

  box {
    width: 100px;
    height: 100px;
    background: green;
  }
  .box-2 {
    position: absolute;
    right: 0;
    bottom: 0;
  }
```

Here, the parent-box doesn't have any position relative property so the box-2 will sit at the right bottom corner of the body because it is positioned 0 pixels from right and 0 pixels from the bottom.

## 5. Position Fixed

Position fixed is similar to absolute positioning. The only difference is that fixed positioning always works with respect to window viewport and does not scroll with content as we scroll the page. It also accepts all the box-offset properties, so wherever we want we can fix the position of the element.

```
  <div class="box">......</div>

  .box {
    position: fixed;
    right: 60px;
    bottom: 60px;
  }
```

Similar to the absolute element, the display property for the fixed element is also changed. Fixed block-level elements will start taking space according to the content it is wrapping inside. At the same time, an inline-level element may start accepting the box model properties(such as width and height), if we fix the position.

## 6. Box offset properties

We have four box offset properties, top, right, bottom, and left. These box offset properties only work with a relative, absolute and fixed positioned elements. With static elements, box offset properties do not work.
Actually, the box properties specify how an element will be positioned or in which direction the element will move in a page. You might have got the idea from the above examples how the box offset properties work.

## 7. Box offset properties for Relative elements

For the relative elements if both the top and bottom box offset properties are defined at the same time, then the top property will take priority. And for the left and right properties, priority depends on the language in which the page is written. If it is in English, then left will be having more priority and if it is in Arabic then right offset property will be having more priority.

```
  <div class="box">......</div>

  .box {
    position: relative;
    top: 60px
    right: 60px;
    bottom: 60px;
    left: 60px;
  }
```

Here, in the vertical direction the box will move down by 60 pixels from the top because top offset property has high priority. In the horizontal direction, the box will move to the right by 60 pixels from left because it is written in the English language, and in the English language left offset property has more priority.

## 8. Box offset properties for Absolute elements

For the absolute elements, if the width and height are fixed then the box offset properties will work in a similar way as it works with the relative elements. Here also, between top and bottom, top offset property has higher priority and between left and right, priority goes according to the language in which the page is written.

But if the absolute elements do not have fixed width and height then the element will start all the end if all the box offset property is defined.

```
  <section class="parent-box">
      <div class="box">......</div>
  </section>

  .parent-box {
    position: relative;
    width: 1000px;
    height: 300px;
  }
  .box {
    background: green;
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
  }
```

Here, the absolute box does not have any fixed width and height, therefore it will start from the top left end of its parent and will go till up to the right bottom end of its parent. It means the size of the absolute box will span according to the size of its parents. The left and right box offset property are deciding the width of absolute elements and top and bottom offset property is deciding the height of the absolute elements.

If the parent is not a relative element then the reference point will be the body of the page.

## 9. Box offset properties for Fixed elements

All the box offset for fixed elements works similarly as it works for absolute elements.

## 10. Z-index property.

Normally all the elements in a page are displayed in X and Y plane. So whenever any element comes on a page it goes either top to bottom or one after another depending upon the display property of the element. However, we can make the element come in z-axis with position property. We can place the element on top of another.

To bring elements on the z-axis and place them on top of another we can make use of position property having values either relative, absolute, or fixed. Thereafter with box offset property, we can position the elements anywhere on the z-axis and if we need to place them on top of another we can do that. Now, if we place the elements on top of another, obviously one of them will be at the top and one them will be at the bottom.

However, we can decide the order that which element will be at the top and which will be at the bottom with 'z-index' property. The z-index property only works with relative,absolute and fixed elements. So to specify the z-index property we must have either relative, absolute, or fixed elements. By default, every element has 0 value for the z-index property. The element with the highest z-index value will appear on the top and with the lowest value will at the bottom.

```
  <section class="parent-box">
    <div class="box box-1">1</div>
    <div class="box box-2">2</div>
    <div class="box box-3">3</div>
  </section>

  .parent-box {
    height: 200px;
    background: #bada55;
    position: relative
  }
  .box {
    width: 100px;
    height: 100px;
    position: absolute;
  }
  .box-1 {
    left: 10px;
    top: 10px;
    background: red;
    z-index: 1;
  }
  .box-2 {
    left: 30px;
    top: 30px;
    background: blue;
    z-index: 2;
  }
  .box-3 {
    left: 50px;
    top: 50px;
    background: green;
    z-index: 3
  }
```

Here, the box-3 is having the highest z-index value, therefore, it will be on top and box-1 is having the lowest z-index value so it will be at the bottom.

## Answer the following questions

1. What are the different ways to uniquely position elements in a page?
2. We have a static element, can we position that element with box offset properties?
3. What are different offset properties and why do we use?
4. Suppose we have a span element and we made its position fixed. Can we fix its width and height?
5. What is z-index property in CSS? And how does it work?
6. To which element we can apply z-index property?

## Do the exercise 1

## Additional resources

1. https://learn.shayhowe.com/html-css/positioning-content/

2. https://learn.shayhowe.com/advanced-html-css/detailed-css-positioning/

- https://internetingishard.com/html-and-css/advanced-positioning/
