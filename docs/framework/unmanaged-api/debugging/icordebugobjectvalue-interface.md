---
title: Icordebugobjectvalue arabirimi1
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue
helpviewer_keywords:
- ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5cd991049c159b96a0f0717b31d6a2834b250f70
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632000"
---
# <a name="icordebugobjectvalue-interface1"></a>Icordebugobjectvalue arabirimi1
"Bir nesne içeren bir değeri temsil eden Icordebugvalue" öğesinin.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetClass Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|Ortak dil çalışma zamanı (CLR) bir arabirim işaretçisi alır <xref:System.Type> nesnenin bu `ICorDebugObjectValue` başvuruları.|  
|[GetContext Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|Henüz uygulanmadı.|  
|[GetFieldValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|Bir arabirim işaretçisi alır bir [Icordebugvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) , belirtilen sınıfın belirtilen alanın değerini temsil eder.|  
|[GetManagedCopy Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|Kullanımdan kalktı. Bu yöntemi çağırmanız gerekmez.|  
|[GetVirtualMethod Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|Henüz uygulanmadı.|  
|[IsValueClass Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|Bu tarafından başvurulan nesne olup olmadığını gösteren bir değer alır `ICorDebugObjectValue` bir değer türüdür.|  
|[SetFromManagedCopy Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|Kullanımdan kalktı. Bu yöntemi çağırmanız gerekmez.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir `ICorDebugObjectValue` ayıklanan işlemin devam kadar geçerli kalır.  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

