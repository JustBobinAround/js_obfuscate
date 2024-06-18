# js_obfuscate

js_obfuscate is a tool that can encode JavaScript into zero width UTF-8
whitespace characters. This makes it so that when viewing the script in most
editor's the code will always appear to be the following:
```html
<script>
	var d=(a='',b=0,c=(a,b,e)=>e<8?(a[b]!='\uFEFF'?2**e:0)+c(a,b+1,e+1):0)=>a[b]?String.fromCharCode(c(a,b,0))+d(a,b+8):'';eval(d())
</script>
```

This is because `a=''` is where the actual code is stored at. It just doesn't get
rendered as anything because of the zero-width property of the characters. The rest
of the script is a minimalist decoder that recursively converts the encoding back
to normal characters and then a script that gets evaluated.

So even if you are using an editor that can see the characters, the code is in
reverse binary. So deciphering would be somewhat challenging. Of course the user
could just replace the `eval()` call with a `console.log()` if they want to see
what the code is. At the end of the day, this is really just a proof of concept.

If anyone can think of a way to shorten the decoder even more, I would love to see
it; PRs welcome!

### Disclaimer

This code is just a demonstration, please be
responsible and USE AT YOUR OWN RISK.
