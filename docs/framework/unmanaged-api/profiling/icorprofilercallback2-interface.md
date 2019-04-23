---
title: ICorProfilerCallback2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2
helpviewer_keywords:
- ICorProfilerCallback2 interface [.NET Framework profiling]
ms.assetid: 4a261dba-450d-4f1f-8d98-865b58bfc992
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83c72704ccb01baf68a3cacb6252367e07909fa8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179003"
---
# <a name="icorprofilercallback2-interface"></a>ICorProfilerCallback2 Arabirimi
Ortak dil çalışma zamanı tarafından (CLR) profil oluşturucu abone olduğu olaylar meydana geldiğinde bir kod profil oluşturucu bildirmek için kullanılan yöntemleri sağlar. `ICorProfilerCallback2` Arabirimi uzantısıdır [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) arabirimi. Diğer bir deyişle, .NET Framework 2.0 sürümünde tanıtılan yeni geri çağırmaları sağlar.  
  
> [!NOTE]
>  Her yöntem uygulaması, bir HRESULT değerini S_OK başarı veya E_FAIL başarısız olması döndürmesi gerekir. Şu anda, CLR dışında her bir geri çağırma tarafından döndürülen HRESULT yoksayar [Icorprofilercallback::objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[FinalizeableObjectQueued Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md)|Bir sonlandırıcı içeren bir nesne Sonlandırıcı iş parçacığı yürütülmesi için kuyruğa kod profil oluşturucu bildirir, `Finalize` yöntemi.|  
|[GarbageCollectionFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|Profil Oluşturucu, çöp toplama tamamlandı ve tüm çöp toplama geri aramaları için verilmiş bildirir.|  
|[GarbageCollectionStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)|Kod profil oluşturucu, çöp toplama başlatıldı bildirir.|  
|[HandleCreated Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)|Kod profil oluşturucu, çöp toplama tanıtıcı oluşturulduğunu bildirir.|  
|[HandleDestroyed Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)|Kod profil oluşturucu, çöp toplama tanıtıcısı yok edildi bildirir.|  
|[RootReferences2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)|Bir çöp toplama işlemi gerçekleştirildikten sonra Profil Oluşturucu kök başvurular hakkında bilgilendirir. Bu yöntem bir uzantısıdır [Icorprofilercallback::rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) yöntemi.|  
|[SurvivingReferences Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)|Profil Oluşturucu bir çöp toplamadan kurtulan nesne başvuruları hakkında bilgilendirir.|  
|[ThreadNameChanged Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md)|Kod profil oluşturucu, bir iş parçacığı adı değiştiğini bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR bir yöntem çağrıları `ICorProfilerCallback` (veya `ICorProfilerCallback2`) bildirmek için profil oluşturucu abone, bir olay gerçekleştiğinde, profil oluşturucu için arabirimi gerçekleşir. Bu, CLR kod Profil Oluşturucu ile iletişim kurar birincil geri çağırma arabirimidir.  
  
 Bir kod profil oluşturucu yöntemleri uygulamalıdır `ICorProfilerCallback` arabirimi. .NET Framework 2.0 ve sonraki sürümleri için profil oluşturucu ayrıca uygulamalıdır `ICorProfilerCallback2` yöntemleri. Her yöntem uygulaması, bir HRESULT değerini S_OK başarı veya E_FAIL başarısız olması döndürmesi gerekir. Şu anda, CLR dışında her bir geri çağırma tarafından döndürülen HRESULT yoksayar [Icorprofilercallback::objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
 Bir kod profil oluşturucu, Microsoft Windows kayıt defterinde uygulayan kendi COM Nesne kaydetmelisiniz `ICorProfilerCallback` ve `ICorProfilerCallback2` arabirimleri. Bir kod profil oluşturucu, istediği çağırarak bildirim almak olaylara abone olur [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). Bu genellikle profil oluşturucunun uygulamasında yapılır [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Profil Oluşturucu ardından bir olayı gerçekleşmek üzere olduğunu veya sadece yürütülmekte olan bir çalışma zamanı işleminde oluştu çalışma zamanını şuradan bildirim almak kullanabilirsiniz.  
  
> [!NOTE]
>  Profil oluşturucuyu tek bir COM nesnesi kaydeder. Profil Oluşturucu .NET Framework sürüm 1.0 veya 1.1 hedefliyorsa, bu COM nesnesi yalnızca yöntemlerini uygulamak zorunda `ICorProfilerCallback`. .NET Framework sürüm 2.0 hedeflediği ve daha sonra COM nesnesinin yöntemlerini de uygulamalıdır `ICorProfilerCallback2`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback3 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerCallback4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
