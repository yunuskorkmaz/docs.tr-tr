---
description: ': ICorDebugComObjectValue arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 3c071c371ae6e330431630cfb1934b538d62efe6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710822"
---
# <a name="icordebugcomobjectvalue-interface"></a>ICorDebugComObjectValue Arabirimi

Bir çalışma zamanı çağrılabilir sarmalayıcı (RCW) ile ilişkili bilgileri almak için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetCachedInterfacePointers Yöntemi](icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|Geçerli RCW 'da önbelleğe alınan ham arabirim işaretçilerini alır.|  
|[GetCachedInterfaceTypes Yöntemi](icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|Geçerli nesnenin küçük harf olarak kullanıldığı veya kullanıldığı arabirim türleri için bir Numaralandırıcı sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  

 "ICorDebugValue" arabiriminin bir örneğinin bir RCW 'yu temsil ettiğini denetlemek için, `QueryInterface` ile "ICorDebugValue" üzerinde bir hata ayıklayıcı çağırır `IID_ICorDebugComObjectValue` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
