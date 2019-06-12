---
title: CorDebugGuidToTypeMapping Yapısı
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugGuidToTypeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGuidToTypeMapping
helpviewer_keywords:
- CorDebugGuidToTypeMapping structure [.NET Framework debugging]
ms.assetid: 57dbccd9-b16d-4da3-ae25-7a2cf9adf679
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38e1b19d6340f559e6f8b7e0f7bc042a10df16c3
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025993"
---
# <a name="cordebugguidtotypemapping-structure"></a>CorDebugGuidToTypeMapping Yapısı
Bir Windows çalışma zamanı GUID, karşılık gelen Icordebugtype nesnesine eşler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`iid`|Önbelleğe alınan Windows çalışma zamanı türü GUİD'si.|  
|`pType`|Önbelleğe alınan türü hakkında bilgi sağlayan Icordebugtype nesne işaretçisi.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Windows çalışma zamanı.  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
