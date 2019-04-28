---
title: CorDebugBlockingReason Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugBlockingReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingReason
helpviewer_keywords:
- CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54652727b4684d71068a19eb5eeb2e862f413f25
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609262"
---
# <a name="cordebugblockingreason-enumeration"></a>CorDebugBlockingReason Numaralandırması
Belirli bir nesne üzerinde bir iş parçacığı neden engellenmiş duruma nedenlerini belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a>Üyeler  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`BLOCKING_NONE`|Yalnızca iç kullanım.|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|Bir iş parçacığı, bir nesne izleme kilidi ile ilişkili olan kritik bölümü almaya çalışıyor. Biri çağırdığınızda genelde böyle <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> veya <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> yöntemleri.|  
|`BLOCKING_MONITOR_EVENT`|Bir iş parçacığı, bir nesne için İzleyici kilit ile ilişkili olay bekleniyor. Biri çağırdığınızda genelde böyle <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` yöntemleri.|  
  
## <a name="remarks"></a>Açıklamalar  
 Zaman `BLOCKING_MONITOR_CRITICAL_SECTION` veya `BLOCKING_MONITOR_EVENT` üyesi kullanılan bir [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapısını `pBlockingObject` yapısı noktalarına giriliyor nesnesini temsil eden bir "ICorDebugValue" arabirim üyesi . Uygulamak için de garanti [Icordebugheapvalue3](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) arabirimi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Sabit Listeleri](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
