---
title: ICorDebugComObjectValue Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugComObjectValue
helpviewer_keywords:
- ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3387985ebf6027b9cd9dee372190da65939dbae3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749703"
---
# <a name="icordebugcomobjectvalue-interface"></a>ICorDebugComObjectValue Arabirimi
Bir çalışma zamanı çağrılabilir sarmalayıcı (RCW) ile ilgili bilgileri almak için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetCachedInterfacePointers Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|Geçerli RCW üzerinde önbelleğe ham arabirim işaretçisi alır.|  
|[GetCachedInterfaceTypes Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|Bir numaralandırıcı, geçerli nesne için büyük/küçük harfleri veya bırakıldığı olarak kullanılan, arabirim türlerinde sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 "ICorDebugValue" arabiriminin bir örneği bir RCW temsil edip etmediğini denetlemek için bir hata ayıklayıcı çağırır `QueryInterface` ile "Icordebugvalue" üzerinde `IID_ICorDebugComObjectValue`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
