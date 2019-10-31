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
ms.openlocfilehash: d182476130e611e57df232c9652cda4bec002c31
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132770"
---
# <a name="cordebugregister-enumeration"></a>CorDebugRegister Numaralandırması
Belirli bir işlemci mimarisiyle ilişkili kayıtları belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
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
|`REGISTER_INSTRUCTION_POINTER`|Bir yönerge işaretçisi herhangi bir işlemciye kayıt kaydeder.|  
|`REGISTER_STACK_POINTER`|Yığın işaretçisi herhangi bir işlemciye kayıt kaydeder.|  
|`REGISTER_FRAME_POINTER`|Bir çerçeve işaretçisi herhangi bir işlemciye kayıt kaydeder.|  
|`REGISTER_X86_EIP`|Yönerge işaretçisi x86 işlemcisine kaydolun.|  
|`REGISTER_X86_ESP`|Yığın işaretçisi x86 işlemcisine kaydolun.|  
|`REGISTER_X86_EBP`|Temel işaretçi x86 işlemcisine kaydolun.|  
|`REGISTER_X86_EAX`|X86 işlemcisinde bir veri kaydı.|  
|`REGISTER_X86_ECX`|C verileri x86 işlemcisine kaydedilir.|  
|`REGISTER_X86_EDX`|D verileri x86 işlemcisinde kayıt.|  
|`REGISTER_X86_EBX`|B verileri x86 işlemcisinde kayıt.|  
|`REGISTER_X86_ESI`|Kaynak dizin, x86 işlemcide kayıt yaptırın.|  
|`REGISTER_X86_EDI`|Hedef dizin, x86 işlemcide kayıt yaptırın.|  
|`REGISTER_X86_FPSTACK_0`|Yığın, x86 kayan nokta (FP) işlemcisinde 0 ' ı kaydeder.|  
|`REGISTER_X86_FPSTACK_1`|#1 Stack, x86 FP işlemcisine kayıt kaydeder.|  
|`REGISTER_X86_FPSTACK_2`|#2 Stack, x86 FP işlemcisine kayıt kaydeder.|  
|`REGISTER_X86_FPSTACK_3`|#3 Stack, x86 FP işlemcisine kayıt kaydeder.|  
|`REGISTER_X86_FPSTACK_4`|#4 Stack, x86 FP işlemcisine kayıt kaydeder.|  
|`REGISTER_X86_FPSTACK_5`|#5 Stack, x86 FP işlemcisine kayıt kaydeder.|  
|`REGISTER_X86_FPSTACK_6`|#6 Stack, x86 FP işlemcisine kayıt kaydeder.|  
|`REGISTER_X86_FPSTACK_7`|#7 Stack, x86 FP işlemcisine kayıt kaydeder.|  
|`REGISTER_AMD64_RIP`|Yönerge işaretçisi AMD64 işlemcisine kaydolun.|  
|`REGISTER_AMD64_RSP`|Yığın işaretçisi AMD64 işlemcisine kaydolun.|  
|`REGISTER_AMD64_RBP`|Temel işaretçi AMD64 işlemcisine kaydolun.|  
|`REGISTER_AMD64_RAX`|AMD64 işlemcisinde bir veri kaydı.|  
|`REGISTER_AMD64_RCX`|C verileri AMD64 işlemcisine kaydedilir.|  
|`REGISTER_AMD64_RDX`|D verileri AMD64 işlemcisinde kayıt.|  
|`REGISTER_AMD64_RBX`|B verileri AMD64 işlemci üzerinde kayıt.|  
|`REGISTER_AMD64_RSI`|Kaynak dizini AMD64 işlemcide kaydolun.|  
|`REGISTER_AMD64_RDI`|Hedef dizin AMD64 işlemci üzerinde kayıt.|  
|`REGISTER_AMD64_R8`|#8 verileri AMD64 işlemcisinde kayıt.|  
|`REGISTER_AMD64_R9`|#9 verileri AMD64 işlemcisinde kayıt.|  
|`REGISTER_AMD64_R10`|#10 verileri AMD64 işlemcisinde kayıt.|  
|`REGISTER_AMD64_R11`|#11 verileri AMD64 işlemcisinde kayıt.|  
|`REGISTER_AMD64_R12`|#12 verileri AMD64 işlemcisinde kayıt.|  
|`REGISTER_AMD64_R13`|#13 verileri AMD64 işlemcisinde kayıt.|  
|`REGISTER_AMD64_R14`|#14 verileri AMD64 işlemcisinde kayıt.|  
|`REGISTER_AMD64_R15`|#15 verileri AMD64 işlemcisinde kayıt.|  
|`REGISTER_AMD64_XMM0`|#0 multimedyayı AMD64 işlemcisine kaydeder.|  
|`REGISTER_AMD64_XMM1`|#1 multimedyayı AMD64 işlemcisine kaydeder.|  
|`REGISTER_AMD64_XMM2`|#2 multimedyayı AMD64 işlemcisine kaydeder.|  
|`REGISTER_AMD64_XMM3`|#3 multimedyayı AMD64 işlemcisine kaydeder.|  
|`REGISTER_AMD64_XMM4`|#4 multimedyayı AMD64 işlemcisine kaydeder.|  
|`REGISTER_AMD64_XMM5`|#5 multimedyayı AMD64 işlemcisine kaydeder.|  
|`REGISTER_AMD64_XMM6`|#6 multimedyayı AMD64 işlemcisine kaydeder.|  
|`REGISTER_AMD64_XMM7`|#7 multimedyayı AMD64 işlemcisine kaydeder.|  
|`REGISTER_AMD64_XMM8`|#8 multimedyayı AMD64 işlemcisine kaydeder.|  
|`REGISTER_AMD64_XMM9`|#9 multimedyayı AMD64 işlemcisine kaydeder.|  
|`REGISTER_AMD64_XMM10`|#10 multimedyayı AMD64 işlemcisine kaydeder.|  
|`REGISTER_AMD64_XMM11`|#11 multimedyayı AMD64 işlemcisine kaydeder.|  
|`REGISTER_AMD64_XMM12`|#12 multimedyayı AMD64 işlemcisine kaydeder.|  
|`REGISTER_AMD64_XMM13`|#13 multimedyayı AMD64 işlemcisine kaydeder.|  
|`REGISTER_AMD64_XMM14`|#14 multimedyayı AMD64 işlemcisine kaydeder.|  
|`REGISTER_AMD64_XMM15`|#15 multimedyayı AMD64 işlemcisine kaydeder.|  
|`REGISTER_IA64_BSP`|Yığın işaretçisi, IA-64 işlemcisine kaydolun.|  
|`REGISTER_IA64_R0`|#0 veri, IA-64 işlemcisinde kayıt.|  
|`REGISTER_IA64_F0`|#0, IA-64 işlemcisinde FP veri kaydı.|  
|`REGISTER_ARM_PC`|ARM işlemcisinde program sayaç kaydı (R15).|  
|`REGISTER_ARM_SP`|Yığın işaretçisi, ARM işlemcisinde kayıt (R13).|  
|`REGISTER_ARM_R0`|ARM işlemcisinde veri kaydı R0.|  
|`REGISTER_ARM_R1`|ARM işlemcisinde veri kaydı R1.|  
|`REGISTER_ARM_R2`|ARM işlemcisinde veri kayıt R2.|  
|`REGISTER_ARM_R3`|ARM işlemcisinde veri kaydı R3.|  
|`REGISTER_ARM_R4`|ARM işlemcisine R4 kaydolun.|  
|`REGISTER_ARM_R5`|ARM işlemcisine R5 kaydolun.|  
|`REGISTER_ARM_R6`|ARM işlemcisine R6 kaydolun.|  
|`REGISTER_ARM_R7`|ARM işlemcisine R7 (THUMB kare işaretçisi) öğesini kaydettirin.|  
|`REGISTER_ARM_R8`|ARM işlemcisine R8 öğesini kaydettirin.|  
|`REGISTER_ARM_R9`|ARM işlemcisine R9 kaydolun.|  
|`REGISTER_ARM_R10`|ARM işlemcisine R10 kaydolun.|  
|`REGISTER_ARM_R11`|ARM işlemcisindeki çerçeve işaretçisi.|  
|`REGISTER_ARM_R12`|ARM işlemcisine R12 kaydolun.|  
|`REGISTER_ARM_LR`|ARM işlemcisinde bağlantı yazmacı (R14).|  
  
## <a name="remarks"></a>Açıklamalar  
 IA-64 işlemcisinde 128 genel amaçlı veri kayıtları ve 128 kayan nokta veri kayıtları bulunur, ancak yalnızca `REGISTER_IA64_R0` ve `REGISTER_IA64_F0` değerleri sağlanır. Diğer değerler aşağıdaki şekilde belirlenebilir:  
  
- `REGISTER_IA64_R0` `REGISTER_IA64_R1` değerler için kayıt numarasını, IA-64 işlemcisinde #127 veri kaydı aracılığıyla #1 veri kaydına karşılık gelen `REGISTER_IA64_R127`aracılığıyla ekleyin.  
  
- `REGISTER_IA64_F0` `REGISTER_IA64_F1` değerler için kayıt numarasını, IA-64 işlemcisindeki #127 FP veri kaydı aracılığıyla #1 FP veri kaydına karşılık gelen `REGISTER_IA64_F127`aracılığıyla ekleyin.  
  
 Örneğin, IA-64 işlemcisinde #83 veri kaydını belirtmeniz gerekiyorsa `REGISTER_IA64_R0` + 83 kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
