---
title: Icordebughandlevalue Interface1
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed6ba8a738b4086b9150e0a1c7b300a519fa3092
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
