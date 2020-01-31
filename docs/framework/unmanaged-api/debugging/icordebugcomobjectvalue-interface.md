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
ms.openlocfilehash: ed5b39ed4b2a14c071bf23fb04efbad6834e8a9d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783965"
---
# <a name="icordebugcomobjectvalue-interface"></a>ICorDebugComObjectValue Arabirimi
Bir çalışma zamanı çağrılabilir sarmalayıcı (RCW) ile ilişkili bilgileri almak için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetCachedInterfacePointers Yöntemi](icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|Geçerli RCW 'da önbelleğe alınan ham arabirim işaretçilerini alır.|  
|[GetCachedInterfaceTypes Yöntemi](icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|Geçerli nesnenin küçük harf olarak kullanıldığı veya kullanıldığı arabirim türleri için bir Numaralandırıcı sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir "ICorDebugValue" arabiriminin bir örneğinin bir RCW 'yu temsil ettiğini denetlemek için, hata ayıklayıcı `IID_ICorDebugComObjectValue`"ICorDebugValue" üzerinde `QueryInterface` çağırır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
