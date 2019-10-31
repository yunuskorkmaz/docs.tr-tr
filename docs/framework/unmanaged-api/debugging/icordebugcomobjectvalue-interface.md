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
ms.openlocfilehash: 4ff5c0d470e6eb84eb8b526f5e8f74e5e1a8118a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125481"
---
# <a name="icordebugcomobjectvalue-interface"></a>ICorDebugComObjectValue Arabirimi
Bir çalışma zamanı çağrılabilir sarmalayıcı (RCW) ile ilişkili bilgileri almak için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetCachedInterfacePointers Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|Geçerli RCW 'da önbelleğe alınan ham arabirim işaretçilerini alır.|  
|[GetCachedInterfaceTypes Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|Geçerli nesnenin küçük harf olarak kullanıldığı veya kullanıldığı arabirim türleri için bir Numaralandırıcı sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir "ICorDebugValue" arabiriminin bir örneğinin bir RCW 'yu temsil ettiğini denetlemek için, hata ayıklayıcı `IID_ICorDebugComObjectValue`"ICorDebugValue" üzerinde `QueryInterface` çağırır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
