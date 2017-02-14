# Omastar
The Advanced Pokemon GO API
![alt text](http://assets.pokemon.com/assets/cms2/img/pokedex/full/139.png "Omastar (Pokemon)")

Description
======
Omastar is a Pokemon GO API that allows you to communicate with the PoGO servers in complex ways. This allows for programs such as maps.

Basics
======
If you've ever used [POGOLib](https://github.com/AeonLucid/POGOLib/tree/develop), the syntax is basically the same.
Login
------
Here is a basic login script, that logs in PTC/Google.

```csharp
var loginProviderStr = "ptc";
            var usernameStr = "Your username here";
            var passwordStr = "Your password here"; // Your PTC password

            // Login
            ILoginProvider loginProvider;

            switch (loginProviderStr)
            {
                case "Google":
                    loginProvider = new GoogleLoginProvider(username, password);
                    break;
                case "PTC":
                    loginProvider = new PtcLoginProvider(username, password);
                    break;
                default:
                    throw new ArgumentException("Login provider must be either \"google\" or \"ptc\".");
            }

            var locRandom = new Random();
            var latitude = 0 + locRandom.NextDouble(-0.000030, 0.000030);
            var longitude = 0 + locRandom.NextDouble(-0.000030, 0.000030);
            var session = await APIHelper.GetSession(loginProvider, latitude, longitude, true);

            APIHelper.SaveAccessToken(session.AccessToken);
```
