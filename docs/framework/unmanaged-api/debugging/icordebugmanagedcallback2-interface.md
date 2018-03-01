---
title: ICorDebugManagedCallback2 Arabirimi
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
- ICorDebugManagedCallback2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2
helpviewer_keywords:
- ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: cf7b7cfa-1c4b-4d8c-be70-4f9ed15a788b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2a46e8e4f23c57391877d8cb6ba6b35d50de151b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2-interface"></a>ICorDebugManagedCallback2 Arabirimi
Hata ayıklayıcı özel durum işlemesini ve yönetilen hata ayıklama yardımcılarını (MDA) desteklemek için yöntemler sağlar. `ICorDebugManagedCallback2`mantıksal bir uzantısıdır ve [Icordebugmanagedcallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) arabirimi.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ChangeConnection Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|Hata ayıklayıcı belirtilen bağlantı ile ilişkili görevlerin değiştiğini bildirir.|  
|[CreateConnection Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|Hata ayıklayıcı yeni bir bağlantı oluşturulduğunu size bildirir.|  
|[DestroyConnection Metodu](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|Hata ayıklayıcı belirtilen bağlantı sonlandırıldı bildirir.|  
|[Exception Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|Hata ayıklayıcı bir özel durum işleyici için bir arama başlatıldı bildirir.|  
|[ExceptionUnwind Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|Özel durum unwinding işlemi sırasında bir durum bildirim sağlar.|  
|[FunctionRemapComplete Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|Hata ayıklayıcı kod yürütmeyi düzenlenen işlevi yeni bir sürüme geçirdi bildirir.|  
|[FunctionRemapOpportunity Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|Hata ayıklayıcı kod yürütmeyi bir dizi noktası düzenlenen işlevi daha eski bir sürümünde ulaştı bildirir.|  
|[MDANotification Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|Kod yürütmeyi yönetilen hata ayıklama Yardımcısı (MDA) ileti karşılaştı bildirim sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugManagedCallback2` Arabirimi genişletiyor `ICorDebugManagedCallback` .NET Framework 2.0 sürümünde sunulan yeni hata ayıklama olayları işlemek için arabirim.  
  
 Bir hata ayıklayıcısı uygulamalıdır `ICorDebugManagedCallback2` .NET Framework 2.0 uygulamaları hata ayıklama durumunda. Örneği `ICorDebugManagedCallback` veya `ICorDebugManagedCallback2` geri çağırma nesnesi olarak geçirilen [Icordebug::setmanagedhandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
