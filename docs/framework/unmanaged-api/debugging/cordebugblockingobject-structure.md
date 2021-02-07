---
description: 'Daha fazla bilgi edinin: CorDebugBlockingObject yapısı'
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
ms.openlocfilehash: 2b16af5eecb01067c2ee6811613f964af391f345
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712226"
---
# <a name="cordebugblockingobject-structure"></a>CorDebugBlockingObject Yapısı

Bir iş parçacığını engelleyen bir nesne ve iş parçacığının engellediği belirli bir nedeni tanımlar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Description|  
|------------|-----------------|  
|`pBlockingObject`|İş parçacığının engellediği nesne. Bu nesne yalnızca geçerli eşitlenmiş durumun süresi için geçerlidir. Aynı eşitlenmiş durum içindeki aynı nesnede iki iş parçacığı engellenirse, [ICorDebugValue:: GetAddress](icordebugvalue-getaddress-method.md) yönteminin aynı değeri döndürmesini beklemeniz gerekebilir. Ancak, arabirimler işaretçi eşdeğeri olabilir veya olmayabilir.|  
|`dwTimeout`|Engelleme işlemi zaman aşımına geçmeden önce geçen milisaniye sayısı veya sonsuz değeri, zaman aşımına gerekmediğini gösterir. Zaman aşımı değeri, hala kalan süre değil, engelleyici işlem için geçen sürenin toplam uzunluğunu belirtir.|  
|`blockingReason`|Bu nesne üzerinde iş parçacığının engellendiği neden.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Yapıları](debugging-structures.md)
- [Hata Ayıklama](index.md)
