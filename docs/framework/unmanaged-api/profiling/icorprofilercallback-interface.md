---
title: ICorProfilerCallback Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback
helpviewer_keywords: ICorProfilerCallback interface [.NET Framework profiling]
ms.assetid: 4bae06f7-94d7-4ba8-b250-648b2da78674
topic_type: apiref
caps.latest.revision: "29"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3370dade937d67aa40be263faf3a433d142d932c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback-interface"></a>ICorProfilerCallback Arabirimi
Ortak dil çalışma zamanı tarafından (CLR) profil oluşturucu abone olaylar meydana geldiğinde kod profil oluşturucu bildirmek için kullanılan yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[AppDomainCreationFinished yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md)|Profil Oluşturucu uygulama etki alanı oluşturulduğunu size bildirir.|  
|[AppDomainCreationStarted yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationstarted-method.md)|Profil Oluşturucu uygulama etki alanı oluşturulduğunu size bildirir.|  
|[AppDomainShutdownFinished yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownfinished-method.md)|Profil Oluşturucu uygulama etki alanı bir işlemden kaldırıldı bildirir.|  
|[AppDomainShutdownStarted yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md)|Profil Oluşturucu uygulama etki alanı bir işlemden yüklenmemiş olduğunu bildirir.|  
|[AssemblyLoadFinished yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md)|Profil Oluşturucu bütünleştirilmiş yüklenmesini tamamladı bildirir.|  
|[AssemblyLoadStarted yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadstarted-method.md)|Profil Oluşturucu bütünleştirilmiş yüklendiği bildirir.|  
|[AssemblyUnloadFinished yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)|Profil Oluşturucu bütünleştirilmiş kaldırıldı bildirir.|  
|[AssemblyUnloadStarted yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md)|Profil Oluşturucu bütünleştirilmiş yüklenmemiş olduğunu bildirir.|  
|[ClassLoadFinished yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)|Profil Oluşturucu bir sınıf yükleme tamamlandığını bildirir.|  
|[ClassLoadStarted yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)|Profil Oluşturucu bir sınıf yüklü olduğunu bildirir.|  
|[ClassUnloadFinished yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)|Profil Oluşturucu bir sınıf kaldırılması tamamlandığını bildirir.|  
|[ClassUnloadStarted yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)|Profil Oluşturucu bir sınıf yüklenmemiş olduğunu bildirir.|  
|[COMClassicVTableCreated yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)|Profil Oluşturucu, belirtilen IID ve sınıf için bir çalışma zamanı aranabilir sarmalayıcısı (RCW) oluşturulduğunu size bildirir.|  
|[COMClassicVTableDestroyed yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)|Profil Oluşturucu bir RCW yok olduğunu bildirir.|  
|[ExceptionCatcherEnter yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)|Denetim uygun geçirilmiş profil oluşturucu bildirir `catch` bloğu.|  
|[ExceptionCatcherLeave yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)|Denetim uygun dışında geçirilmiş profil oluşturucu bildirir `catch` bloğu.|  
|[ExceptionCLRCatcherExecute yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)|.NET Framework 2.0 sürümünde Kullanımdan kalktı.|  
|[ExceptionCLRCatcherFound yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)|.NET Framework 2.0 Kullanımdan kalktı.|  
|[ExceptionOSHandlerEnter yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerenter-method.md)|Henüz uygulanmadı. Yönetilmeyen özel durum bilgileri gerektiren bir profil oluşturucu arasında başka yollarla bu bilgileri edinmeniz gerekir.|  
|[ExceptionOSHandlerLeave yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerleave-method.md)|Henüz uygulanmadı. Yönetilmeyen özel durum bilgileri gerektiren bir profil oluşturucu arasında başka yollarla bu bilgileri edinmeniz gerekir.|  
|[ExceptionSearchCatcherFound yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchcatcherfound-method.md)|Profil Oluşturucu, özel durum işleme arama aşaması oluşturulan özel durum işleyicisi bulunduğunu bildirir.|  
|[ExceptionSearchFilterEnter yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)|Profil Oluşturucu kullanıcı filtresi yürütülmekte olan bildirir.|  
|[ExceptionSearchFilterLeave yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)|Profil Oluşturucu yürütülmesi kullanıcı filtresi yalnızca tamamlandı bildirir.|  
|[ExceptionSearchFunctionEnter yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)|Profil Oluşturucu, özel durum işleme arama aşaması işlevi girdiğini bildirir.|  
|[ExceptionSearchFunctionLeave yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)|Profil Oluşturucu, özel durum işleme arama aşaması işlevi aramayı bitirdi bildirir.|  
|[ExceptionThrown yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md)|Profil Oluşturucu bir özel durum bildirir.|  
|[ExceptionUnwindFinallyEnter yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)|Özel durum geriye doğru izleme aşaması işleme girme profil oluşturucu bildirir bir `finally` belirtilen işlevinde yan tümcesi.|  
|[ExceptionUnwindFinallyLeave yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)|Özel durum geriye doğru izleme aşaması işleme ayrıldı profil oluşturucu bildirir bir `finally` yan tümcesi.|  
|[ExceptionUnwindFunctionEnter yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)|Profil Oluşturucu, özel durum işleme bırakma aşaması işlevi girdiğini bildirir.|  
|[ExceptionUnwindFunctionLeave yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)|Profil Oluşturucu, özel durum işleme bırakma aşaması işlevi geriye doğru izleme tamamlandığını bildirir.|  
|[FunctionUnloadStarted yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md)|Profil oluşturucu işlevi kaldırmak çalışma zamanı başlatıldı bildirir.|  
|[Initialize yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)|Yeni bir CLR uygulaması başlatıldığında profil oluşturucu başlatmak üzere çağrılır.|  
|[Jıtcachedfunctionsearchfinished yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md)|Profil Oluşturucu, arama NGen.exe kullanarak önceden derlenen bir işlev için tamamlandığını bildirir.|  
|[Jıtcachedfunctionsearchstarted yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md)|Profil Oluşturucu, arama NGen.exe kullanarak önceden derlenen bir işlev için başlatıldı bildirir.|  
|[Jıtcompilationfinished yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)|Profil Oluşturucu JIT Derleyici bir işlev derleme tamamlandığını bildirir.|  
|[Jıtcompilationstarted yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)|Profil Oluşturucu tam zamanında (JIT) derleyici bir işlev derlemek başlatıldı bildirir.|  
|[Jıtfunctionpitched yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md)|Profil Oluşturucu JIT derlenmiş bir işlev bellekten kaldırıldığını bildirir.|  
|[Jıtınlining yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)|Profil Oluşturucu JIT Derleyici hakkında başka bir işlev uygun olarak bir işlev eklemek için olduğunu bildirir.|  
|[ManagedToUnmanagedTransition yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)|Profil Oluşturucu yönetilen koddan yönetilmeyen koda geçiş oluştuğunu bildirir.|  
|[ModuleAttachedToAssembly yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md)|Profil Oluşturucu bir modül kendi üst derlemeye bağlı olduğunu bildirir.|  
|[ModuleLoadFinished yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)|Profil Oluşturucu bir modül yüklenmesini tamamladı bildirir.|  
|[ModuleLoadStarted yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)|Profil Oluşturucu bir modül yüklendiği bildirir.|  
|[ModuleUnloadFinished yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)|Profil Oluşturucu bir modül kaldırılması tamamlandığını bildirir.|  
|[ModuleUnloadStarted yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md)|Profil Oluşturucu modülü yüklenmemiş olduğunu bildirir.|  
|[MovedReferences yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)|Profil Oluşturucu çöp toplama sırasında taşınan nesne başvuruları hakkında uyarır.|  
|[ObjectAllocated yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)|Bellek öbek içinde bir nesne için ayrılan profil oluşturucu bildirir.|  
|[ObjectReferences yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)|Profil Oluşturucu belirtilen nesne tarafından başvurulan bellek nesneleri hakkında uyarır.|  
|[ObjectsAllocatedByClass yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)|Profil Oluşturucu önceki çöp toplamadan beri oluşturulan her belirtilen sınıf örneklerini sayısı hakkında uyarır.|  
|[Remotingclientınvocationfinished yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)|Profil Oluşturucu uzaktan iletişim çağrısı, istemcide tamamlanıncaya kadar çalıştırıldığını bildirir.|  
|[Remotingclientınvocationstarted yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationstarted-method.md)|Profil Oluşturucu uzaktan iletişim çağrısı başlatıldı bildirir.|  
|[RemotingClientReceivingReply yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)|Uzaktan iletişim çağrısı sunucu tarafı kısmı tamamlandı ve istemci şimdi alma profil oluşturucu bildirir ve yanıtı işlemek üzere.|  
|[RemotingClientSendingMessage yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)|Profil Oluşturucu istemci sunucuya istek gönderilirken bildirir.|  
|[Remotingserverınvocationreturned yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md)|Profil Oluşturucu uzak yöntem çağırma isteğine yanıt olarak bir yöntemi çağırma işlemi tamamlandığını bildirir.|  
|[Remotingserverınvocationstarted yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationstarted-method.md)|Profil Oluşturucu işlemi uzak yöntem çağırma isteğine yanıt olarak bir yönteminin çağrılması gerektiğini bildirir.|  
|[RemotingServerReceivingMessage yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md)|Profil Oluşturucu işlemi bir uzak yöntem çağırma veya etkinleştirme isteği aldığını bildirir.|  
|[RemotingServerSendingReply yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)|Profil Oluşturucu işlemi bir uzak yöntem çağırma isteği işlemi tamamladı ve yanıt bir kanal üzerinden iletilmek üzere olduğunu bildirir.|  
|[RootReferences yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)|Profil Oluşturucu çöp toplamadan sonra kök başvurular hakkındaki bilgilerle bildirir.|  
|[RuntimeResumeFinished yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumefinished-method.md)|Profil Oluşturucu çalışma zamanı tüm çalışma zamanı iş parçacıklarını sürdürdü ve normal çalışmasına geri döndü bildirir.|  
|[RuntimeResumeStarted yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)|Profil Oluşturucu çalışma zamanı tüm çalışma zamanı iş parçacıklarını sürdürme olduğunu bildirir.|  
|[RuntimeSuspendAborted yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)|Profil Oluşturucu çalışma zamanı meydana çalışma zamanı askıya durdurdu bildirir.|  
|[RuntimeSuspendFinished yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)|Profil Oluşturucu çalışma zamanı tüm çalışma zamanı iş parçacıklarını askıya tamamlandığını bildirir.|  
|[RuntimeSuspendStarted yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)|Profil Oluşturucu çalışma zamanı hakkında tüm çalışma zamanı iş parçacıklarını askıya alma olduğunu bildirir.|  
|[RuntimeThreadResumed yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)|Profil Oluşturucu, belirtilen iş parçacığı askıya sonra sürdürdü bildirir.|  
|[RuntimeThreadSuspended yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)|Profil Oluşturucu, belirtilen iş parçacığı bırakıldı veya hakkında askıya alınmasına olduğunu bildirir.|  
|[Shutdown yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)|Profil Oluşturucu uygulamanın kapanacağını bildirir.|  
|[ThreadAssignedToOSThread yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)|Profil Oluşturucu, belirli bir işletim sistemi (OS) iş parçacığı kullanan bir yönetilen iş parçacığı uygulanan olduğunu bildirir.|  
|[ThreadCreated yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)|Profil Oluşturucu bir iş parçacığı oluşturulduğunu size bildirir.|  
|[ThreadDestroyed yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)|Profil Oluşturucu, bir iş parçacığı yok olduğunu bildirir.|  
|[UnmanagedToManagedTransition yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)|Profil Oluşturucu yönetilmeyen koddan yönetilen koda geçiş oluştuğunu bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR bir yöntem çağrıları `ICorProfilerCallback` (veya [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) için profil oluşturucu abone, bir olay gerçekleştiğinde, profil oluşturucu bildirmek için arabirimi oluşur. Üzerinden CLR kod Profil Oluşturucu ile iletişim kurar birincil geri çağırma arabirimidir.  
  
 Kod profil oluşturucu yöntemlerinin uygulamalıdır `ICorProfilerCallback` arabirimi. .NET Framework sürüm 2.0 veya üstü için profil oluşturucu ayrıca uygulamalıdır `ICorProfilerCallback2` yöntemleri. Her yöntem uygulaması başarılı S_OK değerine sahip bir HRESULT veya E_FAIL hatası döndürmesi gerekir. Şu anda, CLR dışında her geri çağırma tarafından döndürülen HRESULT yoksayar [Icorprofilercallback::objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
 Microsoft Windows Kayıt Defteri'nde kod profil oluşturucu uygular, Bileşen Nesne Modeli (COM) nesne kaydetmeniz gerekir `ICorProfilerCallback` ve `ICorProfilerCallback2` arabirimleri. Kod profil oluşturucu için istediği bildirim arayarak almak olayları abone [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). Bu genellikle Profil Oluşturucu'nın uygulamasında yapılır [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Profil Oluşturucu sonra bir olay gerçekleşmek üzere olduğunda veya yalnızca yürütülen bir çalışma zamanı işleminde oluştu çalışma zamanını şuradan bildirim almak mümkün olur.  
  
> [!NOTE]
>  Profil Oluşturucu tek bir COM nesnesi kaydeder. Profil oluşturucuyu bir .NET Framework sürüm 1.0 veya 1.1, COM nesnesi yalnızca yöntemlerini uygulamak gereken hedeflediği `ICorProfilerCallback`. .NET Framework sürüm 2.0 veya sonraki sürümünü hedefleme, COM nesnesi de yöntemlerinin uygulamalıdır `ICorProfilerCallback2`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil oluşturma arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Icorprofilercallback2 arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [Icorprofilercallback3 arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 [Icorprofilercallback4 arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
