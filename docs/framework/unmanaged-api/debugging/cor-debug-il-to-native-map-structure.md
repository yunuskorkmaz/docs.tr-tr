---
title: COR_DEBUG_IL_TO_NATIVE_MAP Yapısı
ms.date: 03/30/2017
api_name:
- COR_DEBUG_IL_TO_NATIVE_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: 06f3b504-085f-4142-934a-25381fe23d4c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: babb1ace1385c241b782691f22bfb4fbb689e310
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274069"
---
# <a name="cor_debug_il_to_native_map-structure"></a>COR_DEBUG_IL_TO_NATIVE_MAP Yapısı
Microsoft ara dili (MSIL) kodunu yerel kodla eşlemek için kullanılan uzaklıkları içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`ilOffset`|MSIL kodunun boşluğu.|  
|`nativeStartOffset`|Yerel kodun başlangıcının boşluğu.|  
|`nativeEndOffset`|Yerel kodun sonundaki fark.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** CorProf. IDL, CorDebug. IDL  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [GetILToNativeMapping Yöntemi](../profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [GetILToNativeMapping Yöntemi](icordebugcode-getiltonativemapping-method.md)
- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
