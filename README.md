Repro issue with blazor debugger not sending cookies in request.

1. Start server running kestrel.
2. Open in chrome, note the static site won't load in the browser because the server requires cookie authentication.
3. Navigate to /SignIn that will give you a cookie.
4. Reload the site, the wasm application should now load.
5. Try the FetchData page of the wasm application - note it calls a webapi that requires authentication - it works because you have the cookie.
6. Alt shift D to open blazor debugging tools - you may want to place a breakpoint on the server project, in Startup.cs where the Debug.WriteLine is - you'll see requests incoming from the debugger, without any authentication cookies.

This bug makes it impossible to use the debugger if the static files are protected with cookie authentication.

