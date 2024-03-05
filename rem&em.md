## An example of em

Say you had the following HTML.

    <style>
      html {
        font-size: 8px;
      }
      div {
        font-size: 1.5em;
      }
    </style>
    <div id="outer">
      This is some div text
      <div id="nested">
        This is some nested div text
        <div id="doubly-nested">
          This is doubly nested text
        </div>
      </div>
    </div>

When that renders, the browser gets to the first `div` (that is, `#outer`) and says to itself, "Hey! This needs to be `1.5em`, that is, 1.5 times the size of the font that it would normally be. The browser checks and notices that it would normally be "8px" tall (as specified by the CSS rule for the `html` element). Therefore, it calculates that the text for that needs to be `1.5 * 8px = 12px`. The text "This is some div text" gets drawn at 12 pixels tall.

Then, it gets to `#nested` which is a `div`. The browser says, "Hey! this needs to be `1.5em`, that is, 1.5 times the size of the font that it would normally be." Right now, the browser is drawing its text at `12px` from the previous calculation (it's still in `#outer`), so it calculates a new font size of `1.5 * 12px = 18px`. The text "This is some nested div text" gets drawn 18 pixels tall.

Finally, it gets to the innermost `div`, `#doubly-nested`. It does the same calculation as before, multiplying 1.5 by the size that it's currently drawing text. That's 18 pixels, right now. Thus, the text "This is doubly nested text" gets drawn at `1.5 * 18px = 27px` tall.

![Example of em sizing](https://appacademy-open-assets.s3-us-west-1.amazonaws.com/Module-Responsive-Design/attributes/assets/properties-em-font-size.png)

## An example of rem

Say you had the same HTML with one vital difference: the `1.5em` from the previous example is changed to `1.5rem`.

    <style>
      html {
        font-size: 8px;
      }
      div {
        /* Here's the change */
        font-size: 1.5rem;
      }
    </style>
    <div id="outer">
      This is some div text
      <div id="nested">
        This is some nested div text
        <div id="doubly-nested">
          This is doubly nested text
        </div>
      </div>
    </div>

Now, every time the browser gets to a `div`, it asks itself, "What is 1.5 times the root element's font size?" That answer is the same, every time, because the root element's font size doesn't change. It's just `8px` set right there in the `html` rule. So, it doesn't matter that the `div` elements are nested; all of the text just gets drawn at `1.5 * 8px = 12px`.

![Example of rem sizing](https://appacademy-open-assets.s3-us-west-1.amazonaws.com/Module-Responsive-Design/attributes/assets/properties-rem-font-size.png)
