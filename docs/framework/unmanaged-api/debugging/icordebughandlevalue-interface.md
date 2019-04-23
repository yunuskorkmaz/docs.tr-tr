---
title: ICorDebugHandleValue Arabirimi
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
ms.openlocfilehash: 9a9eb63e681b47f058901b0ff002015baffe6048
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59117450"
---
# <a name="icordebughandlevalue-interface"></a>ICorDebugHandleValue Arabirimi

Icordebugreferencevalue için hata ayıklayıcı çöp toplama işlemi için bir tanıtıcı oluşturduğu bir başvuru değeri temsil eden bir alt sınıfı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Dispose Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|Bu tarafından başvurulan tanıtıcıyı serbest `ICorDebugHandleValue` açıkça arabirim işaretçisi serbest olmadan nesne.|  
|[GetHandleType Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|Bu tarafından başvurulan tanıtıcı türü tanımlayan CorDebugHandleType değeri alır `ICorDebugHandleValue`.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `ICorDebugReferenceValue` Nesne geçersiz hata ayıklanan kod yürütülmesi içindeki bir ara. Bir `ICorDebugHandleValue` açıkça serbest bırakılıncaya kadar sonu ve devamlılıklar, aracılığıyla, bir başvuru tutar.  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
