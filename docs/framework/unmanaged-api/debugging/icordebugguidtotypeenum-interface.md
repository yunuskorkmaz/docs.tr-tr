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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22cd08154268bdf1e819a0ec0067b05a81d60b22
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025830"
---
# <a name="icordebugguidtotypeenum-interface"></a>ICorDebugGuidToTypeEnum Arabirimi
Icordebugtype örnekleri tarafından temsil edilen bunların karşılık gelen türlerine ve GUID'leri kümesi arasındaki eşlemeyi tanımlar bir numaralandırıcı sağlar. Bu arabirim yöntemleri Icordebugenum arabirimi devralır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Icordebugguidtotypeenum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|Belirtilen sayıda alır [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) bilgi GUID'leri harita örneği.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `ICorDebugGuidToTypeEnum` arabirimi nesnesi çağrılarak alınabilir [Icordebugappdomain3::getcachedwinrttypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) yöntemi. Bir hata ayıklayıcı bu arabirimi çağırabilir [sonraki](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) alınacak yöntemi [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) içinde yönetilen bir Windows çalışma zamanı türleri temsillerini eşleşmelerini temsil eden nesneleri yüklendi uygulama etki alanı için yapılan çağrının kullanılan [Icordebugappdomain3::getcachedwinrttypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Windows Çalışma Zamanı  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
