---
title: CorDebugBlockingObject Yapısı
ms.date: 03/30/2017
api_name:
- CorDebugBlockingObject Structure
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingObject
helpviewer_keywords:
- CorDebugBlockingObject structure [.NET Framework debugging]
ms.assetid: 5944edd1-0914-4efa-aba0-d5a277c38b1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57de11c1c40c05befcf3c99c31c2e07e1ecaec5a
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273965"
---
# <a name="cordebugblockingobject-structure"></a>CorDebugBlockingObject Yapısı
Bir iş parçacığını engelleyen bir nesne ve iş parçacığının engellediği belirli bir nedeni tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`pBlockingObject`|İş parçacığının engellediği nesne. Bu nesne yalnızca geçerli eşitlenmiş durumun süresi için geçerlidir. Aynı eşitlenmiş durum içindeki aynı nesnede iki iş parçacığı engellenirse, [ICorDebugValue:: GetAddress](icordebugvalue-getaddress-method.md) yönteminin aynı değeri döndürmesini beklemeniz gerekebilir. Ancak, arabirimler işaretçi eşdeğeri olabilir veya olmayabilir.|  
|`dwTimeout`|Engelleme işlemi zaman aşımına geçmeden önce geçen milisaniye sayısı veya sonsuz değeri, zaman aşımına gerekmediğini gösterir. Zaman aşımı değeri, hala kalan süre değil, engelleyici işlem için geçen sürenin toplam uzunluğunu belirtir.|  
|`blockingReason`|Bu nesne üzerinde iş parçacığının engellendiği neden.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
