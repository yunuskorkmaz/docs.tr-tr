---
title: Icordebughandlevalue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugHandleValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue
helpviewer_keywords:
- ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b8df7b46bf22fa1a3a8633cbad7ad1a6582b4860
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebughandlevalue-interface1"></a>Icordebughandlevalue Interface1
Hata ayıklayıcı çöp toplama için bir tanıtıcı oluşturduğu başvuru değeri temsil eden Icordebugreferencevalue sınıfıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Dispose Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|Bu tarafından başvurulan tanıtıcı serbest `ICorDebugHandleValue` açıkça arabirimi işaretçisi serbest olmadan nesnesi.|  
|[GetHandleType Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|Bu tarafından başvurulan tanıtıcı türünü tanımlayan bir CorDebugHandleType değeri alır `ICorDebugHandleValue`.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `ICorDebugReferenceValue` hata ayıklaması kod yürütmeyi aranın tarafından nesnesi geçersiz. Bir `ICorDebugHandleValue` açıkça serbest kadar sonları ve devamlılıklar, aracılığıyla kendi başvuru korur.  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
