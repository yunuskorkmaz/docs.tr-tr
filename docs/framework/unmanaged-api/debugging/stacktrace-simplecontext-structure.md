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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc0fc18e31b89b22ffd30d99a8b079ed7b87fa1b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752496"
---
# <a name="stacktracesimplecontext-structure"></a>StackTrace_SimpleContext Yapısı
Tam yerine kullanılabilecek basit bir bağlam sağlar `CONTEXT` yapısı.  
  
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
|`StackOffset`|Yığın işaretçisi veya x86 enter yığın işaretçisi (ESP) platformları.|  
|`FrameOffset`|Çerçeve uzaklığı veya x86 EBP kayıt platformlar.|  
|`InstructionOffset`|Yönerge işaretçisi veya x86 enter yönerge işaretçisi (EIP) platformları.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yığın izleme işlevleri genellikle yalnızca adresi, çerçeve uzaklığı ve yığın adresi döndürülecek gerektiğinden, isteğe bağlı olarak kullanabileceğiniz `SimpleContext` yapısı yerine büyük `CONTEXT` yapısı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** SOS_Stacktrace.h  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
