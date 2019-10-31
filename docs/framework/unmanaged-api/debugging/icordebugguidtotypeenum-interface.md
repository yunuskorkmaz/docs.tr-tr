---
title: ICorDebugGuidToTypeEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum
helpviewer_keywords:
- ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: aa32b12b-05fc-4ea8-a904-adae25034269
topic_type:
- apiref
ms.openlocfilehash: da921644c4d967efb0d88060ada0332c5eb63965
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138526"
---
# <a name="icordebugguidtotypeenum-interface"></a>ICorDebugGuidToTypeEnum Arabirimi
ICorDebugType örnekleri tarafından temsil edilen bir GUID kümesi ve bunlara karşılık gelen türleri arasındaki eşlemeyi tanımlayan bir Numaralandırıcı sağlar. Bu arabirim, ıcorıcertificate Genum arabiriminden gelen yöntemleri devralır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ICorDebugGuidToTypeEnum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|GUID 'Leri tür bilgilerine eşleyen, belirtilen [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) örneklerinin sayısını alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 [ICorDebugAppDomain3:: GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) yöntemi çağırarak bir `ICorDebugGuidToTypeEnum` arabirimi nesnesi alınabilir. Bir hata ayıklayıcı, [](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) [](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) [Bu arabirimin bir sonraki yöntemini çağırmak için kullanılan uygulama etki alanında yüklü Windows çalışma zamanı türlerinin yönetilen gösterimlerinden eşlemelerini temsil eden CorDebugGuidToTypeMapping nesneleri elde edebilir. ICorDebugAppDomain3:: Getcachedwınrttypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) metodu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Windows Çalışma Zamanı  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
