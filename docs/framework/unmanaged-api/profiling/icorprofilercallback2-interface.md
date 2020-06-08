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
ms.openlocfilehash: 3b0e60602d2f36552c3e0e85ec51205b4128486b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499772"
---
# <a name="icorprofilercallback2-interface"></a>ICorProfilerCallback2 Arabirimi
Profil oluşturucunun abone olduğu olaylar gerçekleştiğinde, bir kod Profilcisi bildirmek için ortak dil çalışma zamanı (CLR) tarafından kullanılan yöntemleri sağlar. `ICorProfilerCallback2`Arabirim, [ICorProfilerCallback](icorprofilercallback-interface.md) arabiriminin bir uzantısıdır. Diğer bir deyişle, .NET Framework sürüm 2,0 ' de tanıtılan yeni geri çağrılar sağlar.  
  
> [!NOTE]
> Her yöntem uygulamasının başarılı veya E_FAIL hata durumunda S_OK değerine sahip bir HRESULT döndürmesi gerekir. Şu anda CLR [ICorProfilerCallback:: ObjectReferences](icorprofilercallback-objectreferences-method.md)hariç her geri çağırma tarafından döndürülen HRESULT 'yi yoksayar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Description|  
|------------|-----------------|  
|[FinalizeableObjectQueued Yöntemi](icorprofilercallback2-finalizeableobjectqueued-method.md)|Kod Profilcisi, sonlandırıcısı olan bir nesnenin, yönteminin yürütülmesi için Sonlandırıcı iş parçacığına sıraya alınmış olduğunu bildirir `Finalize` .|  
|[GarbageCollectionFinished Yöntemi](icorprofilercallback2-garbagecollectionfinished-method.md)|Profiler öğesine bir çöp toplamanın tamamlandığını ve tüm çöp toplama geri çağırmaları için verildiğini bildirir.|  
|[GarbageCollectionStarted Yöntemi](icorprofilercallback2-garbagecollectionstarted-method.md)|Kod Profilcisi bir çöp toplamanın başlatıldığını bildirir.|  
|[HandleCreated Yöntemi](icorprofilercallback2-handlecreated-method.md)|Kod Profilcisi bir çöp toplama tutamacının oluşturulduğunu bildirir.|  
|[HandleDestroyed Yöntemi](icorprofilercallback2-handledestroyed-method.md)|Kod Profilcisi bir çöp toplama tanıtıcısının yok edildiğini bildirir.|  
|[RootReferences2 Yöntemi](icorprofilercallback2-rootreferences2-method.md)|Çöp toplama gerçekleştirildikten sonra profil oluşturucuyu kök başvuruları hakkında bilgilendirir. Bu yöntem [ICorProfilerCallback:: RootReferences](icorprofilercallback-rootreferences-method.md) yönteminin bir uzantısıdır.|  
|[SurvivingReferences Yöntemi](icorprofilercallback2-survivingreferences-method.md)|Bir atık toplamayı daha fazla kullanan nesne başvuruları hakkında profil oluşturucuyu bilgilendirir.|  
|[ThreadNameChanged Yöntemi](icorprofilercallback2-threadnamechanged-method.md)|Kod Profilcisi bir iş parçacığı adının değiştiğini bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, profil oluşturucunun `ICorProfilerCallback` `ICorProfilerCallback2` abone olduğu bir olay olduğunda profil oluşturucuyu bilgilendirmek için (veya) arabirimindeki bir yöntemi çağırır. Bu, CLR 'nin kod Profilcisi ile iletişim kurduğu birincil geri çağırma arabirimidir.  
  
 Bir kod profil oluşturucu arabirimin yöntemlerini uygulamalıdır `ICorProfilerCallback` . .NET Framework 2,0 ve sonraki sürümlerinde, profil oluşturucunun de yöntemleri uygulaması gerekir `ICorProfilerCallback2` . Her yöntem uygulamasının başarılı veya E_FAIL hata durumunda S_OK değerine sahip bir HRESULT döndürmesi gerekir. Şu anda CLR [ICorProfilerCallback:: ObjectReferences](icorprofilercallback-objectreferences-method.md)hariç her geri çağırma tarafından döndürülen HRESULT 'yi yoksayar.  
  
 Bir kod Profilcisi, ve arabirimlerini uygulayan COM nesnesine Microsoft Windows kayıt defteri 'ne kaydolmalıdır `ICorProfilerCallback` `ICorProfilerCallback2` . Bir kod profil oluşturucu, [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md)çağırarak bildirim almak istediği olaylara abone olur. Bu genellikle profil oluşturucunun [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md)uygulamasında yapılır. Profil Oluşturucu daha sonra bir olay gerçekleşmekte olduğu veya yürütülmekte olan bir çalışma zamanı işleminde gerçekleştiyse çalışma zamanından bildirim alabilir.  
  
> [!NOTE]
> Profil Oluşturucu tek bir COM nesnesi kaydeder. Profiler .NET Framework sürüm 1,0 veya 1,1 ' i hedefliyorsanız, bu COM nesnesi yalnızca ' nin yöntemlerini uygular `ICorProfilerCallback` . .NET Framework sürüm 2,0 ve üzeri hedefleniyorsa, COM nesnesinin yöntemlerini de uygulaması gerekir `ICorProfilerCallback2` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ICorProfilerCallback3 Arabirimi](icorprofilercallback3-interface.md)
- [ICorProfilerCallback4 Arabirimi](icorprofilercallback4-interface.md)
