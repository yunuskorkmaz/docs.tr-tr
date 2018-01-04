---
title: ICorDebugExceptionDebugEvent Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 97bbd9374b8a3f938f42b8ddd001049a2e7a324c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptiondebugevent-interface"></a>ICorDebugExceptionDebugEvent Arabirimi
Genişletir [Icordebugdebugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) özel durum olayları desteklemek için arabirim.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetFlags Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getflags-method.md)|Bir özel durum olup olmadığını gösteren bayrağı alır geçirilebilir.|  
|[GetNativeIP Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getnativeip-method.md)|Yerel arabirim işaretçisi için bu özel durum hata ayıklama olayı alır.|  
|[GetStackPointer Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)|Yığın işaretçisi için bu özel durum hata ayıklama olayı alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugExceptionDebugEvent` Arabirimi, aşağıdaki olay türlerine göre uygulanır:  
  
-   [MANAGED_EXCEPTION_FIRST_CHANCE](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [MANAGED_EXCEPTION_USER_FIRST_CHANCE](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [MANAGED_EXCEPTION_UNHANDLED](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
>  Arabirimi yalnızca .NET yerel ile kullanılabilir. Çağrı girişimi `QueryInterface` bir arabirim işaretçisi almak için döndürür `E_NOINTERFACE` .NET yerel dışında Icordebug senaryoları için.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
