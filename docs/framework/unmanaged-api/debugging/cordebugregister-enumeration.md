---
title: CorDebugRegister Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugRegister
helpviewer_keywords:
- CorDebugRegister enumeration [.NET Framework debugging]
ms.assetid: 003bb138-7960-4291-ac88-0d87e470ff70
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 177f191d5f438cef106d835b0b9d204a9b19d1f0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64616284"
---
# <a name="cordebugregister-enumeration"></a>CorDebugRegister Numaralandırması
Bir verilen işlemci mimarisi ile ilişkili olan kayıtları belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
typedef enum CorDebugRegister {  
  
    REGISTER_INSTRUCTION_POINTER = 0,  
    REGISTER_STACK_POINTER,  
    REGISTER_FRAME_POINTER,  
  
    REGISTER_X86_EIP = 0,  
    REGISTER_X86_ESP,  
    REGISTER_X86_EBP,  
  
    REGISTER_X86_EAX,  
    REGISTER_X86_ECX,  
    REGISTER_X86_EDX,  
    REGISTER_X86_EBX,  
  
    REGISTER_X86_ESI,  
    REGISTER_X86_EDI,  
  
    REGISTER_X86_FPSTACK_0,  
    REGISTER_X86_FPSTACK_1,  
    REGISTER_X86_FPSTACK_2,  
    REGISTER_X86_FPSTACK_3,  
    REGISTER_X86_FPSTACK_4,  
    REGISTER_X86_FPSTACK_5,  
    REGISTER_X86_FPSTACK_6,  
    REGISTER_X86_FPSTACK_7,  
  
    REGISTER_AMD64_RIP = 0,  
    REGISTER_AMD64_RSP,  
    REGISTER_AMD64_RBP,  
    REGISTER_AMD64_RAX,  
    REGISTER_AMD64_RCX,  
    REGISTER_AMD64_RDX,  
    REGISTER_AMD64_RBX,  
    REGISTER_AMD64_RSI,  
    REGISTER_AMD64_RDI,  
    REGISTER_AMD64_R8,  
    REGISTER_AMD64_R9,  
    REGISTER_AMD64_R10,  
    REGISTER_AMD64_R11,  
    REGISTER_AMD64_R12,  
    REGISTER_AMD64_R13,  
    REGISTER_AMD64_R14,  
    REGISTER_AMD64_R15,  
  
    REGISTER_AMD64_XMM0,  
    REGISTER_AMD64_XMM1,  
    REGISTER_AMD64_XMM2,  
    REGISTER_AMD64_XMM3,  
    REGISTER_AMD64_XMM4,  
    REGISTER_AMD64_XMM5,  
    REGISTER_AMD64_XMM6,  
    REGISTER_AMD64_XMM7,  
    REGISTER_AMD64_XMM8,  
    REGISTER_AMD64_XMM9,  
    REGISTER_AMD64_XMM10,  
    REGISTER_AMD64_XMM11,  
    REGISTER_AMD64_XMM12,  
    REGISTER_AMD64_XMM13,  
    REGISTER_AMD64_XMM14,  
    REGISTER_AMD64_XMM15,  
  
    REGISTER_IA64_BSP = REGISTER_FRAME_POINTER,  
    REGISTER_IA64_R0  = REGISTER_IA64_BSP + 1,  
    REGISTER_IA64_F0  = REGISTER_IA64_R0  + 128,  
    REGISTER_ARM_PC = 0,  
    REGISTER_ARM_SP,  
    REGISTER_ARM_R0,  
    REGISTER_ARM_R1,  
    REGISTER_ARM_R2,  
    REGISTER_ARM_R3,  
    REGISTER_ARM_R4,  
    REGISTER_ARM_R5,  
    REGISTER_ARM_R6,  
    REGISTER_ARM_R7,  
    REGISTER_ARM_R8,  
    REGISTER_ARM_R9,  
    REGISTER_ARM_R10,  
    REGISTER_ARM_R11,  
    REGISTER_ARM_R12,  
    REGISTER_ARM_LR,  
  
} CorDebugRegister;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`REGISTER_INSTRUCTION_POINTER`|Bir yönerge işaretçisini herhangi bir işlemci üzerinde kaydedin.|  
|`REGISTER_STACK_POINTER`|Yığın işaretçisi, herhangi bir işlemci üzerinde kaydedin.|  
|`REGISTER_FRAME_POINTER`|Çerçeve işaretçisini herhangi bir işlemci üzerinde kaydedin.|  
|`REGISTER_X86_EIP`|Yönerge işaretçisi kaydı x86 işlemci.|  
|`REGISTER_X86_ESP`|Yığın işaretçisi kaydı x86 işlemci.|  
|`REGISTER_X86_EBP`|Taban işaretçisi kaydı x86 işlemci.|  
|`REGISTER_X86_EAX`|Bir veri kaydetme üzerinde x86 işlemci.|  
|`REGISTER_X86_ECX`|C veri x86 kaydettirmek işlemci.|  
|`REGISTER_X86_EDX`|D verileri üzerinde x86 kaydı işlemci.|  
|`REGISTER_X86_EBX`|B veri kaydetme üzerinde x86 işlemci.|  
|`REGISTER_X86_ESI`|Kaynak dizin yazmacı x86 işlemci.|  
|`REGISTER_X86_EDI`|Hedef dizin yazmacı x86 işlemci.|  
|`REGISTER_X86_FPSTACK_0`|Yığın x86 kayan nokta (dp) kaydı 0 işlemci.|  
|`REGISTER_X86_FPSTACK_1`|#1 yığın FP işlemci üzerinde x86 kaydedin.|  
|`REGISTER_X86_FPSTACK_2`|#2 yığın FP işlemci üzerinde x86 kaydedin.|  
|`REGISTER_X86_FPSTACK_3`|#3 yığın FP işlemci üzerinde x86 kaydedin.|  
|`REGISTER_X86_FPSTACK_4`|#4 yığın FP işlemci üzerinde x86 kaydedin.|  
|`REGISTER_X86_FPSTACK_5`|#5 yığın FP işlemci üzerinde x86 kaydedin.|  
|`REGISTER_X86_FPSTACK_6`|#6 yığın FP işlemci üzerinde x86 kaydedin.|  
|`REGISTER_X86_FPSTACK_7`|#7 yığın FP işlemci üzerinde x86 kaydedin.|  
|`REGISTER_AMD64_RIP`|Yönerge işaretçisi AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_RSP`|Yığın işaretçisi AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_RBP`|Taban işaretçisi AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_RAX`|Bir veri AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_RCX`|C veri AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_RDX`|D veri AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_RBX`|B veri AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_RSI`|Kaynak dizini AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_RDI`|Hedef dizin AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_R8`|#8 veri AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_R9`|#9 veri AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_R10`|#10 veri AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_R11`|#11 veri AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_R12`|#12 veri AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_R13`|#13 veri AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_R14`|#14 veri AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_R15`|#15 veri AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_XMM0`|Multimedya #0 AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_XMM1`|Multimedya #1 AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_XMM2`|Multimedya #2 AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_XMM3`|Multimedya #3 AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_XMM4`|Multimedya #4 AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_XMM5`|Multimedya #5 AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_XMM6`|Multimedya #6 AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_XMM7`|Multimedya #7 AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_XMM8`|Multimedya #8 AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_XMM9`|Multimedya #9 AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_XMM10`|Multimedya #10 AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_XMM11`|Multimedya #11 AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_XMM12`|Multimedya #12 AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_XMM13`|Multimedya #13 AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_XMM14`|Multimedya #14 AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_AMD64_XMM15`|Multimedya #15 AMD64 işlemci üzerinde kaydedin.|  
|`REGISTER_IA64_BSP`|Yığın işaretçisi IA-64 işlemci üzerinde kaydedin.|  
|`REGISTER_IA64_R0`|#0 veri IA-64 işlemci kaydedin.|  
|`REGISTER_IA64_F0`|#0 FP veri IA-64 işlemci kaydedin.|  
|`REGISTER_ARM_PC`|Program sayacının ARM işlemci üzerinde (R15 kayıtları) kaydedin.|  
|`REGISTER_ARM_SP`|Yığın işaretçisi, ARM işlemci üzerinde (R13) kaydedin.|  
|`REGISTER_ARM_R0`|Veri R0 ARM işlemci üzerinde kaydedin.|  
|`REGISTER_ARM_R1`|Veri R1 ARM işlemci üzerinde kaydedin.|  
|`REGISTER_ARM_R2`|Veri R2 ARM işlemci üzerinde kaydedin.|  
|`REGISTER_ARM_R3`|Veri R3 ARM işlemci üzerinde kaydedin.|  
|`REGISTER_ARM_R4`|ARM işlemci üzerinde R4 kaydedin.|  
|`REGISTER_ARM_R5`|ARM işlemci üzerinde R5 kaydedin.|  
|`REGISTER_ARM_R6`|ARM işlemci üzerinde r6 kaydedin.|  
|`REGISTER_ARM_R7`|R7 kaydetme (Flash çerçeve işaretçisi) ARM işlemci üzerinde.|  
|`REGISTER_ARM_R8`|R8, ARM işlemci üzerinde kaydedin.|  
|`REGISTER_ARM_R9`|ARM işlemci üzerinde R9 kaydedin.|  
|`REGISTER_ARM_R10`|ARM işlemci üzerinde R10 kaydedin.|  
|`REGISTER_ARM_R11`|ARM işlemci çerçeve işaretçisi.|  
|`REGISTER_ARM_R12`|ARM işlemci üzerinde R12 kaydedin.|  
|`REGISTER_ARM_LR`|Bağlantı, ARM işlemci üzerinde (R14) kaydedin.|  
  
## <a name="remarks"></a>Açıklamalar  
 128 genel amaçlı veri kayıtları ve 128 kayan nokta veri kayıtları IA-64 işlemci, ancak yalnızca değerleri `REGISTER_IA64_R0` ve `REGISTER_IA64_F0` sağlanır. Diğer değerleri aşağıdaki gibi belirlenir:  
  
- Kayıt numarası eklemek `REGISTER_IA64_R0` değerleri `REGISTER_IA64_R1` aracılığıyla `REGISTER_IA64_R127`, karşılık IA-64 işlemci #127 verilerini kasayla aracılığıyla #1 veri kaydı.  
  
- Kayıt numarası eklemek `REGISTER_IA64_F0` değerleri `REGISTER_IA64_F1` aracılığıyla `REGISTER_IA64_F127`, hangi karşılık #1 FP veri register-#127 IA-64 işlemci FP veri kaydı.  
  
 Örneğin, #83 veri kaydı IA-64 işlemci üzerinde belirtmeniz gerekiyorsa, kullanın `REGISTER_IA64_R0` + 83.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
