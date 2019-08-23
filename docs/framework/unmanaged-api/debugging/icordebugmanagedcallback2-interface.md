---
title: ICorDebugManagedCallback2 Arabirimi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca33436d98edf5844a5ca27c9ac89648f10ec0c5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909977"
---
# <a name="icordebugmanagedcallback2-interface"></a>ICorDebugManagedCallback2 Arabirimi
Hata ayıklayıcı özel durum işlemesini ve yönetilen hata ayıklama yardımcılarını (MDA) desteklemek için yöntemler sağlar. `ICorDebugManagedCallback2`, [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) arabiriminin mantıksal uzantısıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ChangeConnection Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|Hata ayıklayıcısını, belirtilen bağlantıyla ilişkili görev kümesinin değiştiğini bildirir.|  
|[CreateConnection Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|Hata ayıklayıcıya yeni bir bağlantı oluşturulduğunu bildirir.|  
|[DestroyConnection Metodu](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|Hata ayıklayıcıyı belirtilen bağlantının sonlandırıldığını bildirir.|  
|[Exception Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|Hata ayıklayıcıya bir özel durum işleyici aramasının başlatıldığını bildirir.|  
|[ExceptionUnwind Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|Özel durum geri sarma işlemi sırasında bir durum bildirimi sağlar.|  
|[FunctionRemapComplete Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|Kod yürütmenin düzenlenmiş bir işlevin yeni bir sürümüne geçirildiği hata ayıklayıcıya bildirir.|  
|[FunctionRemapOpportunity Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|Kod yürütmenin, düzenlenmiş bir işlevin daha eski bir sürümündeki bir sıra noktasına ulaştığı hata ayıklayıcıya bildirir.|  
|[MDANotification Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|Kod yürütmenin yönetilen hata ayıklama Yardımcısı (MDA) iletisiyle karşılaştığından bildirim sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Arabirim, .NET Framework sürüm `ICorDebugManagedCallback` 2,0 ' de tanıtılan yeni hata ayıklama olaylarını işlemek için arabirimi genişletir. `ICorDebugManagedCallback2`  
  
 Hata ayıklayıcı .NET Framework 2,0 `ICorDebugManagedCallback2` uygulamalarında hata ayıklaması durumunda uygulamanız gerekir. `ICorDebugManagedCallback` Veya`ICorDebugManagedCallback2` örneği [ICorDebug:: SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)öğesine geri çağırma nesnesi olarak geçirilir.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ICorDebugManagedCallback Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
