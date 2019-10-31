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
ms.openlocfilehash: 1cd3c34fc292e4a050fa8a75078283e34425fc8f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139126"
---
# <a name="stacktrace_simplecontext-structure"></a>StackTrace_SimpleContext Yapısı
Tam `CONTEXT` yapısının yerine kullanılabilecek basit bir bağlam sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
 Yığın izleme işlevlerinin genellikle yalnızca adresi, çerçeve sapmasını ve yığın adresini döndürmesi gerektiğinden, büyük bir `CONTEXT` yapısı yerine isteğe bağlı olarak `SimpleContext` yapısını kullanabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** SOS_Stacktrace. h  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
