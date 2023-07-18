***Mechanical Translation through Google Translate***

### what is
 Based on the mobile terminal debugging tool eruda, it is a UI high-precision restoration auxiliary tool, which is a powerful tool for designers to accept pages.

 The principle is to insert the design drawing into the page to reduce the transparency of the design drawing.  Then compare.
 #### The design drawing given by the designer
 ![image.png](https://i.postimg.cc/YG8wx6Lr/File-20230718-054416-1.jpg)

 #### After the development, the actual effect will be realized
 ![image.png](https://i.postimg.cc/T5wvNKnr/File-20230718-054649-2.jpg)
 #### After using the eruda-pixel tool, develop self-inspection and design acceptance effect

 ![image.png](https://i.postimg.cc/PNrH5R0P/File-20230718-054721-3.jpg)

 ### Demo experience
 [Experience URL](https://faithree.github.io/eruda-pixel/)

 ### Install
 #### npm install

 ```bash

 npm install eruda eruda-pixel -D
 ```

 ```javascript
 eruda.init();
 eruda.add(erudaPixel);
 ```
 #### cdn installation

 ```typescript
 const loadOneJS = (url, callback) => {
   const script = document. createElement('script');
   const fn = callback || (() => {});

   script.type = 'text/javascript';

   script.onload = () => {
     fn();
   };

   script.src = url;

   document.getElementsByTagName('head')[0].appendChild(script);
 };
 const loadJS = (urls, callback) => {
   let i = 0;
   const fn = callback || (() => {});

   urls. forEach((url) => {
     loadOneJS(url, () => {
       i = 1 + i;
       if (urls. length === i) {
         fn();
       }
     });
   });
 };

 loadJS(
   [
     '//cdn.bootcdn.net/ajax/libs/eruda/2.4.1/eruda.min.js',
     '//unpkg.com/eruda-pixel@1.0.13/eruda-pixel.js',
   ],
   () => {
     const eruda = window.eruda;
     if (typeof eruda !== 'undefined') {
       eruda.init();
       eruda. add(window. erudaPixel);
     }
   },
 );
 ```

 ### Function
 Click on the pixel panel and upload the ui design (the picture is stored in the page memory and will not be uploaded anywhere).

 ![image.png](https://i.postimg.cc/N0bzg0B7/File-20230718-055443-4.jpg)

 1. Freeze: the design diagram cannot be dragged to prevent some mouse events affecting the page
 2. Coordinate axis: based on the upper left corner
 3. Mode: Support multiple modes, find out the difference of the page
 3. Refresh the page to keep the design
 4. Only a single design drawing is supported, re-uploading will overwrite the previous design drawing

 ### Advantage
 1. It is convenient and fast, supports npm and cdn installation, and can even inject plugins into a certain website through a packet capture tool like the demo above
 2. Support mobile phone real machine debugging
 3. The plugin uses shadow dom + iframe, without DOM, JavaScript, CSS polluting the real page
 4. Although it is a mobile terminal debugging tool, it is also applicable to the PC terminal
