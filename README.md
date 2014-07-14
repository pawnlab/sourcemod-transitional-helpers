## SM Transitional API Helpers

A set of helper include files for cleverly (or abusively) working with the SM transitional API.

## Usage

Include thelpers:

```sourcepawn
#define GAME_TF2 // required to pull in tf2 related helpers
#include <thelpers/thelpers>
```
  
Go wild:

```sourcepawn
public void OnClientPutInServer( int client )
{
  CBasePlayer player = CBasePlayer( client );
  
  char steamId[ 128 ];
  player.GetSteamID( steamId, sizeof( steamId ) );
  
  PrintToServer( "%N's steam id: %s", player.Index, steamId );
  
  // do some tf2 specific stuff
  CTFPlayer tfPlayer = CTFPlayer:player;
  tfPlayer.SetClass( TFClassType_Medic );
  
  // we didn't like them anyway
  ServerCommand( "sm_kick #%d", player.UserID );
}
```

## Documentation

The include files themselves are highly documented with doxygen-like comments. Simply browse [around the tree](https://github.com/VoiDeD/sourcemod-transitional-helpers/tree/master/thelpers).

### Supported Games

The API aims to be game-agnostic where possible to support all possible games. However, it is possible to enable game specific features by `#defining GAME_X` before including the thelpers files.

Currently only TF2 specific additions have been implemented (enabled with the `GAME_TF2` define), but pull requests for other games are welcome!

## Considerations

- This library will be changing rapidly and often. Expect breaking changes.
- SM's transitional syntax is exerimental and thus has the potential to break us. Expect more breaking changes.
