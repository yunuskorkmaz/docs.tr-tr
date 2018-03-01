---
title: ICorProfilerCallback2 Arabirimi
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7927d3b4d41731c9b69154fa8895a8f698f53e31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback2-interface"></a>ICorProfilerCallback2 Arabirimi
Ortak dil çalışma zamanı tarafından (CLR) profil oluşturucu abone olaylar meydana geldiğinde kod profil oluşturucu bildirmek için kullanılan yöntemleri sağlar. `ICorProfilerCallback2` Arabirimi uzantısıdır [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) arabirimi. Diğer bir deyişle, .NET Framework 2.0 sürümünde sunulan yeni geri aramalar sağlar.  
  
> [!NOTE]
>  Her yöntem uygulaması değerini S_OK başarı veya E_FAIL hatasında sahip bir HRESULT döndürmesi gerekir. Şu anda, CLR dışında her geri çağırma tarafından döndürülen HRESULT yoksayar [Icorprofilercallback::objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[FinalizeableObjectQueued Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md)|Kod profil oluşturucu bir sonlandırıcı sahip bir nesne yürütülmesi için sonlandırıcıyı iş parçacığı için sıraya bildirir, `Finalize` yöntemi.|  
|[GarbageCollectionFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|Profil Oluşturucu çöp toplama tamamlandı ve tüm atık toplama geri aramalar için verilmiş bildirir.|  
|[GarbageCollectionStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)|Kod profil oluşturucu çöp toplama başlatıldı bildirir.|  
|[HandleCreated Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)|Kod profil oluşturucu bir atık toplama tanıtıcı oluşturulduğunu size bildirir.|  
|[HandleDestroyed Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)|Kod profil oluşturucu bir atık toplama tanıtıcı yok bildirir.|  
|[RootReferences2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)|Çöp toplama gerçekleştikten sonra Profil Oluşturucu kök başvurular hakkında uyarır. Bu yöntem uzantısıdır [Icorprofilercallback::rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) yöntemi.|  
|[SurvivingReferences Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)|Profil Oluşturucu çöp toplama derdi bitti nesne başvuruları hakkında uyarır.|  
|[ThreadNameChanged Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md)|Kod profil oluşturucu, bir iş parçacığı adına değiştiğini bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR bir yöntem çağrıları `ICorProfilerCallback` (veya `ICorProfilerCallback2`) için profil oluşturucu abone, bir olay gerçekleştiğinde, profil oluşturucu bildirmek için arabirimi oluşur. Üzerinden CLR kod Profil Oluşturucu ile iletişim kurar birincil geri çağırma arabirimidir.  
  
 Kod profil oluşturucu yöntemlerinin uygulamalıdır `ICorProfilerCallback` arabirimi. .NET Framework 2.0 ve sonraki sürümler için profil oluşturucu ayrıca uygulamalıdır `ICorProfilerCallback2` yöntemleri. Her yöntem uygulaması değerini S_OK başarı veya E_FAIL hatasında sahip bir HRESULT döndürmesi gerekir. Şu anda, CLR dışında her geri çağırma tarafından döndürülen HRESULT yoksayar [Icorprofilercallback::objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
 Kod profil oluşturucu Microsoft Windows kayıt defterinde uygular, COM nesnesi kaydettirmelisiniz `ICorProfilerCallback` ve `ICorProfilerCallback2` arabirimleri. Kod profil oluşturucu için istediği bildirim arayarak almak olayları abone [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). Bu genellikle Profil Oluşturucu'nın uygulamasında yapılır [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Profil Oluşturucu sonra bir olay gerçekleşmek üzere olduğunda veya yalnızca yürütülen bir çalışma zamanı işleminde oluştu çalışma zamanını şuradan bildirim almak mümkün olur.  
  
> [!NOTE]
>  Profil Oluşturucu tek bir COM nesnesi kaydeder. Profil Oluşturucu .NET Framework sürüm 1.0 veya 1.1 hedefliyorsa, bu COM nesnesinin yöntemlerinin yalnızca uygulamak zorunda `ICorProfilerCallback`. .NET Framework sürüm 2.0 hedefleme ve daha sonra COM nesnesi yöntemleri de uygulamalıdır `ICorProfilerCallback2`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback3 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 [ICorProfilerCallback4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
