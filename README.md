# NWCX Public Api Docs

## What is this

Hi! This repo's documentation for anyone who wants to interface with the [NWCX](https://finance.nwconifer.net) in a more automated way.

## The Api

[Route Documentation](API_ROUTES.md)

`https://api.finance.nwconifer.net` is our API, this is where all the business logic for the exchange lives, the "official" frontend uses it, and it's also partly publicly accessible.

_"Umm, whaddya mean, 'partly'? And why can't I submit trades through here?"_

Ah yeah, so the API has an authentication system currently, but I'm not super happy with it, so while I think up new solutions, the only thing allowed to use it is the [front](https://finance.nwconifer.net)[end](https://github.com/nwconifer-technical/nwc-trade-frontend), however that is open so you can always figure it out if you want, the only routes listed here are the ones that don't require authentication.
