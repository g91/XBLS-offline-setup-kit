# XBLS-offline-setup-kit
XBLS offline setup kit don't pay for online access 


hi im theDomo I want to share with you is the ability to last offline.
this is a kit to add it to any source that you currently have however are offline files will be released shortly fully functional.


join us on Discord: https://discord.gg/ZysePxQ
 
in your Initialize
 
add:
    xbox::Hvx::InitializeHvPeekPoke();
    xbox::Hvx::InitializeHvProc();
    xbox::Cleaning::Go_Clean_HV(FALSE);
 
in your XeKeysExecuteHook
 
add:
 
Buffer = CallXamExecuteChallenge(HvSalt);
