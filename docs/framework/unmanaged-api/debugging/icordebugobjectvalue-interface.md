---
title: ICorDebugObjectValue Arabirimi
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
ms.openlocfilehash: b782207503a2c3f739a30f68d509e6b481d2b6a4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129759"
---
# <a name="icordebugobjectvalue-interface"></a>ICorDebugObjectValue Arabirimi

Bir nesnesi içeren bir değeri temsil eden "ICorDebugValue" öğesinin bir alt sınıfı.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetClass Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|Bu `ICorDebugObjectValue` başvurduğu nesnenin ortak dil çalışma zamanı (CLR) <xref:System.Type> için bir arabirim işaretçisi alır.|  
|[GetContext Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|Uygulanmadı.|  
|[GetFieldValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|Belirtilen sınıftaki belirtilen alanın değerini temsil eden bir [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) için bir arabirim işaretçisi alır.|  
|[GetManagedCopy Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|Kullanımdan kalktı. Bu yöntemi çağırmayın.|  
|[GetVirtualMethod Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|Uygulanmadı.|  
|[IsValueClass Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|Bu `ICorDebugObjectValue` başvurduğu nesnenin bir değer türü olup olmadığını gösteren bir değer alır.|  
|[SetFromManagedCopy Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|Kullanımdan kalktı. Bu yöntemi çağırmayın.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklamakta olan işlem devam edene kadar `ICorDebugObjectValue` geçerli kalır.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
