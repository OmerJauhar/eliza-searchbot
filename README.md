# Eliza-Searchbot

This project utilizes the Eliza framework along with the Eliza web search plugin to develop a bot capable of searching the internet for a wide range of information, including the latest news updates.
## Steps Performed

1. Configured the OpenRouter API.
2. Created a character file for the search bot, located at `characters/searchbot.character.json`.
3. Configured the search bot character to use OpenRouter by specifying the model provider in the character file.
   ```json
   {
       "name": "searchbot",
       "clients": [],
       "modelProvider": "openrouter",
       "settings": {
           "secrets": {},
           "voice": {
               "model": "en_US-female-medium"
           }
       }
   }
   ```
4. Installed the web search plugin using the following command:
   ```
   pnpm install @elizaos/plugin-web-search
   ```
5. Set up the Travili API with the following environment variable:
   ```
   TAVILY_API_KEY=your_api_key    # Required: API key for search service
   ```
6. Configured the search bot character to utilize the web search plugin by adding it to the character file:
   ```json
   {
       "name": "searchbot",
       "clients": [],
       "modelProvider": "openrouter",
       "settings": {
           "secrets": {},
           "voice": {
               "model": "en_US-female-medium"
           }
       },
       "plugins": ["@elizaos/plugin-web-search"]
   }
   ```
7. Added custom code in the `agent/src/index.ts` file to enable the search bot to use the web search plugin in actions:
   ```typescript
   actions: [
       character.name === "searchbot" ? webSearchPlugin.actions.find(action => action.name === "WEB_SEARCH") : null,
   ],
   services: [],
   managers: [],
   ```

## Conclusion

With the setup complete, your Eliza search bot is now ready to perform web searches and provide the latest news updates. For further customization and enhancements, refer to the Eliza framework documentation.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Acknowledgments

Thanks to the Eliza framework and the contributors of the web search plugin for making this project possible.
