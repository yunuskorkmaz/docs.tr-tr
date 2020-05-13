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
ms.openlocfilehash: b00be90316598e458f01f6cd440d0ad0a2e79c50
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212366"
---
# <a name="icordebugmanagedcallback2-interface"></a>ICorDebugManagedCallback2 Arabirimi
Hata ayıklayıcı özel durum işlemesini ve yönetilen hata ayıklama yardımcılarını (MDA) desteklemek için yöntemler sağlar. `ICorDebugManagedCallback2`, [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) arabiriminin mantıksal uzantısıdır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ChangeConnection Yöntemi](icordebugmanagedcallback2-changeconnection-method.md)|Hata ayıklayıcısını, belirtilen bağlantıyla ilişkili görev kümesinin değiştiğini bildirir.|  
|[CreateConnection Yöntemi](icordebugmanagedcallback2-createconnection-method.md)|Hata ayıklayıcıya yeni bir bağlantı oluşturulduğunu bildirir.|  
|[DestroyConnection Metodu](icordebugmanagedcallback2-destroyconnection-method.md)|Hata ayıklayıcıyı belirtilen bağlantının sonlandırıldığını bildirir.|  
|[Exception Yöntemi](icordebugmanagedcallback2-exception-method.md)|Hata ayıklayıcıya bir özel durum işleyici aramasının başlatıldığını bildirir.|  
|[ExceptionUnwind Yöntemi](icordebugmanagedcallback2-exceptionunwind-method.md)|Özel durum geri sarma işlemi sırasında bir durum bildirimi sağlar.|  
|[FunctionRemapComplete Yöntemi](icordebugmanagedcallback2-functionremapcomplete-method.md)|Kod yürütmenin düzenlenmiş bir işlevin yeni bir sürümüne geçirildiği hata ayıklayıcıya bildirir.|  
|[FunctionRemapOpportunity Yöntemi](icordebugmanagedcallback2-functionremapopportunity-method.md)|Kod yürütmenin, düzenlenmiş bir işlevin daha eski bir sürümündeki bir sıra noktasına ulaştığı hata ayıklayıcıya bildirir.|  
|[MDANotification Yöntemi](icordebugmanagedcallback2-mdanotification-method.md)|Kod yürütmenin yönetilen hata ayıklama Yardımcısı (MDA) iletisiyle karşılaştığından bildirim sağlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugManagedCallback2`Arabirim, `ICorDebugManagedCallback` .NET Framework sürüm 2,0 ' de tanıtılan yeni hata ayıklama olaylarını işlemek için arabirimi genişletir.  
  
 Hata ayıklayıcı `ICorDebugManagedCallback2` .NET Framework 2,0 uygulamalarında hata ayıklaması durumunda uygulamanız gerekir. `ICorDebugManagedCallback`Veya örneği `ICorDebugManagedCallback2` [ICorDebug:: SetManagedHandler](icordebug-setmanagedhandler-method.md)öğesine geri çağırma nesnesi olarak geçirilir.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [ICorDebugManagedCallback Arabirimi](icordebugmanagedcallback-interface.md)
