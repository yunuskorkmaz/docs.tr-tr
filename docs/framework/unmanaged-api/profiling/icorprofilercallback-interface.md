---
title: ICorProfilerCallback Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback
helpviewer_keywords:
- ICorProfilerCallback interface [.NET Framework profiling]
ms.assetid: 4bae06f7-94d7-4ba8-b250-648b2da78674
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3119818934df765a8bbd9c05caaee04f9476069f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963519"
---
# <a name="icorprofilercallback-interface"></a>ICorProfilerCallback Arabirimi
Profil oluşturucunun abone olduğu olaylar gerçekleştiğinde, bir kod Profilcisi bildirmek için ortak dil çalışma zamanı (CLR) tarafından kullanılan yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[AppDomainCreationFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md)|Profil oluşturucuyu bir uygulama etki alanının oluşturulduğunu bildirir.|  
|[AppDomainCreationStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationstarted-method.md)|Profil oluşturucuyu bir uygulama etki alanının oluşturulduğunu bildirir.|  
|[AppDomainShutdownFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownfinished-method.md)|Profil oluşturucuyu bir uygulama etki alanının bir işlemden kaldırılmış olduğunu bildirir.|  
|[AppDomainShutdownStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md)|Profil Oluşturucu bir uygulama etki alanının bir işlemden kaldırılmakta olduğunu bildirir.|  
|[AssemblyLoadFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md)|Profiler 'ın bir derlemenin yüklemeyi bitirmiş olduğunu bildirir.|  
|[AssemblyLoadStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadstarted-method.md)|Profiler 'ın bir derlemenin yüklenmekte olduğunu bildirir.|  
|[AssemblyUnloadFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)|Profiler öğesine bir derlemenin kaldırılmış olduğunu bildirir.|  
|[AssemblyUnloadStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md)|Profiler öğesine bir derlemenin kaldırılmakta olduğunu bildirir.|  
|[ClassLoadFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)|Profil oluşturucuyu bir sınıfın yükleme tamamlandığını bildirir.|  
|[ClassLoadStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)|Profil oluşturucuyu bir sınıfın yüklenmekte olduğunu bildirir.|  
|[ClassUnloadFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)|Profil oluşturucuyu bir sınıfın kaldırmayı tamamladığını bildirir.|  
|[ClassUnloadStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)|Profil oluşturucuyu bir sınıfın kaldırılmakta olduğunu bildirir.|  
|[COMClassicVTableCreated Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)|Profil oluşturucuya, belirtilen IID ve sınıf için bir çalışma zamanı çağrılabilir sarmalayıcı (RCW) oluşturulduğunu bildirir.|  
|[COMClassicVTableDestroyed Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)|Profil oluşturucuyu bir RCW 'ın yok edildiğini bildirir.|  
|[ExceptionCatcherEnter Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)|Profil oluşturucuyu denetimin uygun `catch` bloğa geçtiğini bildirir.|  
|[ExceptionCatcherLeave Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)|Profil oluşturucuyu denetimin uygun `catch` bloktan geçirilmekte olduğunu bildirir.|  
|[ExceptionCLRCatcherExecute Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)|.NET Framework sürüm 2,0 ' de kullanılmıyor.|  
|[ExceptionCLRCatcherFound Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)|.NET Framework 2,0 ' de kullanılmıyor.|  
|[ExceptionOSHandlerEnter Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerenter-method.md)|Uygulanmadı. Yönetilmeyen özel durum bilgisine ihtiyacı olan bir profil oluşturucu, bu bilgileri diğer yollarla almalıdır.|  
|[ExceptionOSHandlerLeave Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerleave-method.md)|Uygulanmadı. Yönetilmeyen özel durum bilgisine ihtiyacı olan bir profil oluşturucu, bu bilgileri diğer yollarla almalıdır.|  
|[ExceptionSearchCatcherFound Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchcatcherfound-method.md)|Profil oluşturucuya özel durum işlemenin arama aşamasının oluşturulan özel durum için bir işleyici bulunduğunu bildirir.|  
|[ExceptionSearchFilterEnter Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)|Profil oluşturucuyu Kullanıcı filtresinin yürütüldüğü konusunda bilgilendirir.|  
|[ExceptionSearchFilterLeave Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)|Profil oluşturucuyu bir Kullanıcı filtresinin yürütmeyi bitirmekte olduğunu bildirir.|  
|[ExceptionSearchFunctionEnter Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)|Profil oluşturucuyu özel durum işlemenin arama aşamasının bir işlev girdiği hakkında bilgilendirir.|  
|[ExceptionSearchFunctionLeave Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)|Profil oluşturucuya özel durum işlemenin arama aşamasının bir işlev aramayı bitirmediğini bildirir.|  
|[ExceptionThrown Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md)|Profiler öğesine bir özel durum gerçekleştiğini bildirir.|  
|[ExceptionUnwindFinallyEnter Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)|Profil oluşturucuya özel durum işlemenin geriye doğru izleme aşamasının belirtilen işlevde içerilen bir `finally` yan tümce girdiğini bildirir.|  
|[ExceptionUnwindFinallyLeave Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)|Profil oluşturucuya özel durum işlemenin geriye doğru izleme aşamasının bir `finally` yan tümce kaldığını bildirir.|  
|[ExceptionUnwindFunctionEnter Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)|Profil oluşturucuyu, özel durum işlemenin geriye doğru izleme aşamasının bir işlev girdiği hakkında bilgilendirir.|  
|[ExceptionUnwindFunctionLeave Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)|Profil oluşturucuyu, özel durum işlemenin geri sarma aşamasının bir işlevi geriye doğru izlemeyi tamamladığını bildirir.|  
|[FunctionUnloadStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md)|Profil oluşturucuyu, çalışma zamanının bir işlevi kaldırmak için başlatıldığını bildirir.|  
|[Initialize Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)|Her yeni CLR uygulaması başlatıldığında profil oluşturucuyu başlatmak için çağırılır.|  
|[JITCachedFunctionSearchFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md)|Profiler öğesine, daha önce NGen. exe kullanılarak derlenen bir işlev için bir aramanın tamamlandığını bildirir.|  
|[JITCachedFunctionSearchStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md)|Profil oluşturucuyu, daha önce NGen. exe kullanılarak derlenen bir işlev için bir aramanın başlatıldığını bildirir.|  
|[JITCompilationFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)|Profiler öğesine JıT derleyicisinin bir işlevi derlemeyi tamamladığını bildirir.|  
|[JITCompilationStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)|Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin bir işlevi derlemek için başlatıldığını bildirir.|  
|[JITFunctionPitched Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md)|Profiler öğesine JıT derlenmiş bir işlevin bellekten kaldırıldığını bildirir.|  
|[JITInlining Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)|Profiler öğesine JıT derleyicisinin başka bir işlevle satıra bir işlev eklemek üzere olduğunu bildirir.|  
|[ManagedToUnmanagedTransition Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)|Profil oluşturucuyu yönetilen koddan yönetilmeyen koda geçişin oluştuğunu bildirir.|  
|[ModuleAttachedToAssembly Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md)|Profil oluşturucuyu bir modülün üst derlemesine iliştirilmekte olduğunu bildirir.|  
|[ModuleLoadFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)|Profiler 'ın bir modülün yüklemeyi bitirdiğinden emin olduğunu bildirir.|  
|[ModuleLoadStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)|Profil oluşturucuyu bir modülün yüklenmekte olduğunu bildirir.|  
|[ModuleUnloadFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)|Profil oluşturucuyu bir modülün kaldırmayı bitirmediğini bildirir.|  
|[ModuleUnloadStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md)|Profil oluşturucuyu bir modülün kaldırılmakta olduğunu bildirir.|  
|[MovedReferences Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)|Çöp toplama sırasında taşınan nesne başvuruları hakkında profil oluşturucuyu bilgilendirir.|  
|[ObjectAllocated Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)|Profil oluşturucuya, yığın içindeki belleğin bir nesne için ayrıldığını bildirir.|  
|[ObjectReferences Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)|Belirtilen nesne tarafından başvurulan bellekteki nesneler hakkında profil oluşturucuyu bilgilendirir.|  
|[ObjectsAllocatedByClass Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)|Önceki çöp toplamadan bu yana oluşturulan her bir sınıfın örnek sayısı hakkında profil oluşturucuyu bilgilendirir.|  
|[RemotingClientInvocationFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)|Bir uzaktan iletişim çağrısının istemci üzerinde tamamlanmasının çalıştırıldığı profil oluşturucuyu bildirir.|  
|[RemotingClientInvocationStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationstarted-method.md)|Profil oluşturucuyu, uzaktan iletişim çağrısının başlatıldığını bildirir.|  
|[RemotingClientReceivingReply Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)|Profil oluşturucuya, uzaktan iletişim çağrısının sunucu tarafı bölümünün tamamlandığını ve istemcinin artık yanıtı aldığını ve yanıt işlemesini bildirir.|  
|[RemotingClientSendingMessage Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)|Profil oluşturucuyu istemcinin sunucuya bir istek gönderdiğini bildirir.|  
|[RemotingServerInvocationReturned Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md)|Profil oluşturucuyu, işlemin bir uzak yöntem çağırma isteğine yanıt olarak bir yöntemi çağırma işlemini tamamladığını bildirir.|  
|[RemotingServerInvocationStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationstarted-method.md)|Profil oluşturucuyu, işlemin uzak yöntem çağırma isteğine yanıt olarak bir yöntemi çağırdığını bildirir.|  
|[RemotingServerReceivingMessage Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md)|Profil oluşturucuya işlemin uzak yöntem çağırma veya etkinleştirme isteği aldığını bildirir.|  
|[RemotingServerSendingReply Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)|Profil oluşturucuya işlemin uzak yöntem çağırma isteğini işlemeyi tamamladığını ve yanıtı bir kanaldan iletmek üzere olduğunu bildirir.|  
|[RootReferences Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)|Çöp toplama işleminden sonra kök başvuruları hakkındaki bilgilerle profil oluşturucuyu bilgilendirir.|  
|[RuntimeResumeFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumefinished-method.md)|Profil oluşturucuyu çalışma zamanının tüm çalışma zamanı iş parçacıklarını sürdürdüğünü ve normal işleme döndürüldüğünü bildirir.|  
|[RuntimeResumeStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)|Profil oluşturucuyu çalışma zamanının tüm çalışma zamanı iş parçacıklarını sürdürmeye devam etgeldiğini bildirir.|  
|[RuntimeSuspendAborted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)|Profil oluşturucuyu, çalışma zamanının gerçekleşen çalışma zamanı askıya alma süresini durdurduğu konusunda bilgilendirir.|  
|[RuntimeSuspendFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)|Profil oluşturucuyu çalışma zamanının tüm çalışma zamanı iş parçacıklarının askıya alınma tamamlandığını bildirir.|  
|[RuntimeSuspendStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)|Profil oluşturucuyu çalışma zamanının tüm çalışma zamanı iş parçacıklarını askıya almak üzere olduğunu bildirir.|  
|[RuntimeThreadResumed Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)|Profil oluşturucuyu, belirtilen iş parçacığının askıya alındıktan sonra devam ettirmekte olduğunu bildirir.|  
|[RuntimeThreadSuspended Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)|Profil oluşturucuya belirtilen iş parçacığının olduğunu veya askıya alınmayı bildirir.|  
|[Shutdown Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)|Profil oluşturucuyu uygulamanın kapandığını bildirir.|  
|[ThreadAssignedToOSThread Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)|Profil oluşturucuyu yönetilen bir iş parçacığının belirli bir işletim sistemi (OS) iş parçacığı kullanılarak uygulandığını bildirir.|  
|[ThreadCreated Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)|Profil oluşturucuyu bir iş parçacığının oluşturulduğunu bildirir.|  
|[ThreadDestroyed Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)|Profiler öğesine bir iş parçacığının yok edildiğini bildirir.|  
|[UnmanagedToManagedTransition Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)|Profil oluşturucuyu yönetilmeyen koddan yönetilen koda geçiş olduğunu bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, profil oluşturucunun abone olduğu bir `ICorProfilerCallback` olay olduğunda profil oluşturucuyu bilgilendirmek için (veya [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) arabirimindeki bir yöntemi çağırır. Bu, CLR 'nin kod Profilcisi ile iletişim kurduğu birincil geri çağırma arabirimidir.  
  
 Bir kod profil oluşturucu `ICorProfilerCallback` arabirimin yöntemlerini uygulamalıdır. .NET Framework sürüm 2,0 veya üzeri için, profil oluşturucunun de `ICorProfilerCallback2` yöntemleri uygulaması gerekir. Her yöntem uygulamasının hata durumunda Success veya E_FAıL değeri için S_OK değerine sahip bir HRESULT döndürmesi gerekir. Şu anda CLR [ICorProfilerCallback:: ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)hariç her geri çağırma tarafından döndürülen HRESULT 'yi yoksayar.  
  
 Microsoft Windows kayıt defterinde, bir kod Profilleyicisi, `ICorProfilerCallback` ve `ICorProfilerCallback2` arabirimlerini uygulayan bileşen nesne modeli (com) nesnesine kaydolmalıdır. Bir kod profil oluşturucu, [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)çağırarak bildirim almak istediği olaylara abone olur. Bu genellikle profil oluşturucunun [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)uygulamasında yapılır. Profil Oluşturucu daha sonra bir olay gerçekleşmekte olduğu veya yürütülmekte olan bir çalışma zamanı işleminde gerçekleştiyse çalışma zamanından bildirim alabilir.  
  
> [!NOTE]
> Profil Oluşturucu tek bir COM nesnesi kaydeder. Profiler .NET Framework sürüm 1,0 veya 1,1 ' i hedefliyorsanız, söz konusu COM nesnesinin yalnızca yöntemini `ICorProfilerCallback`uygulaması gerekir. .NET Framework sürüm 2,0 veya sonraki bir `ICorProfilerCallback2`sürümü HEDEFLIYORSANıZ, com nesnesinin yöntemlerini de uygulaması gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorProf. IDL, CorProf. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [ICorProfilerCallback3 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerCallback4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
