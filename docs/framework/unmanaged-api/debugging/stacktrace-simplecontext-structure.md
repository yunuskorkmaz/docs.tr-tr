---
description: 'Daha fazla bilgi edinin: StackTrace_SimpleContext yapısı'
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
ms.openlocfilehash: 22a0acada5ef2d392dfdef5326953be137280d7f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800571"
---
# <a name="stacktrace_simplecontext-structure"></a>StackTrace_SimpleContext Yapısı

Tam bir yapının yerine kullanılabilecek basit bir bağlam sağlar `CONTEXT` .  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
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
