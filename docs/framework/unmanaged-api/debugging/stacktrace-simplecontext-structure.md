---
title: StackTrace_SimpleContext Yapısı
ms.date: 03/30/2017
api_name:
- StackTrace_SimpleContext
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SimpleContext
helpviewer_keywords:
- SimpleContext structure [.NET Framework debugging]
- StackTrace_SimpleContext structure [.NET Framework debugging]
ms.assetid: d4cef11f-a8ca-49bc-a1b8-6631f9e28f3e
topic_type:
- apiref
ms.openlocfilehash: 45ae947cda5b4ddadfb10f5b2bdc78a95f031703
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420699"
---
# <a name="stacktrace_simplecontext-structure"></a>StackTrace_SimpleContext Yapısı
Tam bir yapının yerine kullanılabilecek basit bir bağlam sağlar `CONTEXT` .  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`StackOffset`|X86 platformlarında yığın işaretçisi veya yığın işaretçisi (ESP) girin.|  
|`FrameOffset`|Çerçeve kayması veya x86 platformlarında EBP kaydı.|  
|`InstructionOffset`|X86 platformlarında yönerge işaretçisi veya giriş yönergesi işaretçisi (EıP).|  
  
## <a name="remarks"></a>Açıklamalar  
 Yığın izleme işlevlerinin tipik olarak yalnızca adresi, çerçeve sapmasını ve yığın adresini döndürmesi gerektiğinden, `SimpleContext` büyük bir yapı yerine isteğe bağlı olarak yapıyı kullanabilirsiniz `CONTEXT` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** SOS_Stacktrace. h  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
