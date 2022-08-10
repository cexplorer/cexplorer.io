# Ada Handle implementation

We are supporting ADA Handle ( https://adahandle.com/ )

## This includes

- searching in handles
- displaying special badge for txs which contains handle´s policy
- onchain handle validation page: https://cexplorer.io/handle 
- translating addresses to handles [reverse-usecase] (this part is daily updated) - we are choosing the oldest handle sitting on specified account (address for enterprises)

## Disclaimer

- Address/Account to handle recognition are cached (delayed; daily update. Translations handle to address are always onchain instant.
- For various reasons the correct translation may be delayed (database synchronization, data processing, db-sync failure, caching). 
- Always check that the translated address is the same as the one you have.
- Translations are without guarantee and may contain errors or inaccuracies. We are not responsible for incorrect translations.
