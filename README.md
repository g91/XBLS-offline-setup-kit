# XBLS-offline-setup-kit
XBLS offline setup kit don't pay for online access 


hi im theDomo I want to share with you is the ability to last offline.
this is a kit to add it to any source that you currently have however are offline files will be released shortly fully functional.
 
https://github.com/g91/XBLS-offline-setup-kit/
join us on Discord: https://discord.gg/ZysePxQ
 
in your Initialize
 
add:
    xbox::Hvx::InitializeHvPeekPoke();
    xbox::Hvx::InitializeHvProc();
    xbox::Cleaning::Go_Clean_HV(FALSE);
 
in your XeKeysExecuteHook
 
add:
 
Buffer = CallXamExecuteChallenge(HvSalt);


example of how to properly build the challenge after the data has been added:
p.s. the source that you are using may not be set up in the same way you can look at our example client to find out how to get it corrected!
//=======================================================================================================
PXE_KEYS_BUFFER buff = (PXE_KEYS_BUFFER)Buffer;
//=======================================================================================================
XEKEYS_EXEC_HEADER header = (XEKEYS_EXEC_HEADER)buff->header;                               //  XEKEYS_EXEC_HEADER header; //0x0           
buff->result                = 0x0000000000000000;                                           //  QWORD result; //0x20
buff->HvMagic               = 0x4E4E;                                                       //  WORD HvMagic; //0x28
buff->HvVersion             = 0x4497;                                                       //  WORD HvVersion; //0x2A
buff->HvQfe                 = 0x0000;                                                       //  WORD HvQfe; //0x2C
buff->BldrFlags             = xbox::utilities::data::bldrFlags;                             //  WORD BldrFlags; //0x2E
buff->BaseKernelVersion     = 0x07600000;                                                   //  DWORD BaseKernelVersion; //0x30
buff->UpdateSequence        = xbox::utilities::data::updSeqFlags;                           //  DWORD UpdateSequence; //0x34
buff->HvStatusFlags         = xbox::utilities::data::hvStatusFlags;                         //  DWORD HvStatusFlags; //0x38
buff->ConsoleTypeSeqAllow   = xbox::utilities::data::ConsoleTypeSeqAllow;                   //  DWORD ConsoleTypeSeqAllow; //0x3C
buff->RTOC                  = 0x0000000200000000;                                           //  QWORD RTOC; //0x40
buff->HRMOR                 = 0x0000010000000000;                                           //  QWORD HRMOR; //0x48
                                                                                            //  BYTE HvECCDigest[XECRYPT_SHA_DIGEST_SIZE]; //0x50
memcpy(buff->CpuKeyDigest, xbox::utilities::data::cpuKeyDigest, XECRYPT_SHA_DIGEST_SIZE);   //  BYTE CpuKeyDigest[XECRYPT_SHA_DIGEST_SIZE]; //0x64
