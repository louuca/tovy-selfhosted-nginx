# Modifying the port on Tovy
OS used for documentation: **Ubuntu Server 22.04**

Questions? Ask in discord.gg/tovy or Lucalicious#7961

### Explanation
Hosting on NGINX or any other service like Apache is relatively simple but due to the nature of this app using the most universal port, **3000**, we must change that. This fork shows you how.

**Note:** The repository should already reflect the changes given in this documentation, so you can go over there and take a look at it. However, the repo does not include the NGINX site-configuration files.

# Create a Javascript start file _(ex: prod-start.js)_
Paste this code: 
```require('dotenv').config(); // require dotenv
const cli = require('next/dist/cli/next-start');

cli.nextStart(['-p', process.env.PORT || 3000]);
```
* Run `npm i dotenv` to make sure the app can read the .env used to store the port.

# Set your port in .env
Open your `.env` file and insert this:
```PORT=3000```
* Replace `3000` with any port number you'd like, that's available.


# Modify `package.json` for starting parameters.
Find `scripts` > `start` and replace `next start` with:

```node prod-start.js```
or with the file name you've given your start file.

# Final
To finish off, run `npm start` and you should see your port in the starting message!
### Congratulations! You made customizing your port on Tovy available! If you have any improvements, feel free to make a PR or message me!
