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
ms.openlocfilehash: 149c5b09639c8809e736ade09566e7b1b530e3eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705728"
---
# <a name="icordebugguidtotypeenum-interface"></a>ICorDebugGuidToTypeEnum Arabirimi

ICorDebugType örnekleri tarafından temsil edilen bir GUID kümesi ve bunlara karşılık gelen türleri arasındaki eşlemeyi tanımlayan bir Numaralandırıcı sağlar. Bu arabirim, ıcorıcertificate Genum arabiriminden gelen yöntemleri devralır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ICorDebugGuidToTypeEnum:: Next](icordebugguidtotypeenum-next-method.md)|GUID 'Leri tür bilgilerine eşleyen, belirtilen [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) örneklerinin sayısını alır.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bir `ICorDebugGuidToTypeEnum` arabirim nesnesi, [ICorDebugAppDomain3:: GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) yöntemi çağırarak alınabilir. Bir hata ayıklayıcı, [ICorDebugAppDomain3:: GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) yöntemine yapılan çağrı için kullanılan uygulama etki alanında yüklü Windows çalışma zamanı türlerinin yönetilen gösterimlerinden eşlemelerini temsil eden [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) nesnelerini almak için bu arabirimin [sonraki](icordebugguidtotypeenum-next-method.md) metodunu çağırabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Windows Çalışma Zamanı  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
