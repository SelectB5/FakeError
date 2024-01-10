# FakeError
A bookmarklet that displays a fake error on most webpages, it's designed for an iPad using safari.
You can use it by dragging [FakeEorror](javascript:(function()%7B
  var newContent = `
    <div id="error-message" style="text-align: center; font-size: x-large; margin-top: 20%; color: #858585;">
      <p>Safari can’t open the page "${window.location.href}"<br>because an error has occurred.</p>
    </div>`;

  document.body.innerHTML = newContent;
  document.title = "Can't Open Page";
  document.body.style.backgroundColor = 'black';


  function invert(o, t) {
    var r = o.split("("),
        n = r[1].split(")")[0].split(",");

    n.forEach(function (o, r) {
      if (r < 3) {
        n[r] = (t === 'color' && 255 - parseInt(o) < 50) ? 120 : 255 - parseInt(o);
      }
    });

    n = n.join(",");
    return r[0] + "(" + n + ")";
  }

  document.querySelectorAll('*:not([invTouch])').forEach(function (o) {
    document.body.style.backgroundColor = 'black';
    var t = window.getComputedStyle(o);
    o.style.backgroundColor = invert(t.backgroundColor, 'back');
    o.style.color = invert(t.color, 'color');
    o.setAttribute('invTouch', 'true');
  });

  for (i = 0; i < document.styleSheets.length; i++) {
    void (document.styleSheets.item(i).disabled = true);
  }

  el = document.querySelectorAll('*:not([invTouch])');

  for (i = 0; i < el.length; i++) {
    el[i].style.cssText = '';
  }
})();) into your bookmarklets.
