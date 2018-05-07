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
ms.openlocfilehash: ed7db321b32657087b791758096c692f25f3d7f5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="cordebugblockingobject-structure"></a>CorDebugBlockingObject Yapısı
Bir iş parçacığı ve iş parçacığı engellendi belirli bir nedenle engelleyen bir nesneyi tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
|`pBlockingObject`|İş parçacığı engelleyen nesnesi. Bu nesne yalnızca geçerli eşitlenmiş durumuna süre için geçerli değil. İki iş parçacığı aynı eşitlenmiş durumuna içinde aynı nesne üzerinde engelliyorsanız bekleyebilir [Icordebugvalue::getaddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) yöntemi aynı değeri döndürür. Ancak, arabirimler olabilir veya eşdeğer işaretçisi olmayabilir.|  
|`dwTimeout`|Engelleme işleminden önce milisaniye sayısını zaman aşımı ya da onu olacağı zaman aşımına gösterir SONSUZ değeri görüntüler. Zaman aşımı değerini değil hala kalan zaman engelleme işlemi için toplam süreyi belirtir.|  
|`blockingReason`|İş parçacığı bu nesne üzerinde engellendi açıklaması.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Yapıları](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
