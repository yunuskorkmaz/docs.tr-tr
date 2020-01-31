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
ms.openlocfilehash: 43982ebb634843c0130c3321aa84c90b84e8c786
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793310"
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
 `ICorDebugManagedCallback2` arabirimi .NET Framework 2,0 sürümünde tanıtılan yeni hata ayıklama olaylarını işlemek için `ICorDebugManagedCallback` arabirimini genişletir.  
  
 Hata ayıklayıcı .NET Framework 2,0 uygulamalarında hata ayıklaması durumunda `ICorDebugManagedCallback2` uygulamalıdır. Bir `ICorDebugManagedCallback` veya `ICorDebugManagedCallback2` örneği [ICorDebug:: SetManagedHandler](icordebug-setmanagedhandler-method.md)öğesine geri çağırma nesnesi olarak geçirilir.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [ICorDebugManagedCallback Arabirimi](icordebugmanagedcallback-interface.md)
