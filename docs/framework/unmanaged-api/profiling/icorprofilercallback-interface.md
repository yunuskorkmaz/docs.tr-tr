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
ms.openlocfilehash: 6a53b9b1b061c2ca07a469abc78c07ed9e710069
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500097"
---
# <a name="icorprofilercallback-interface"></a>ICorProfilerCallback Arabirimi
Profil oluşturucunun abone olduğu olaylar gerçekleştiğinde, bir kod Profilcisi bildirmek için ortak dil çalışma zamanı (CLR) tarafından kullanılan yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Description|  
|------------|-----------------|  
|[AppDomainCreationFinished Yöntemi](icorprofilercallback-appdomaincreationfinished-method.md)|Profil oluşturucuyu bir uygulama etki alanının oluşturulduğunu bildirir.|  
|[AppDomainCreationStarted Yöntemi](icorprofilercallback-appdomaincreationstarted-method.md)|Profil oluşturucuyu bir uygulama etki alanının oluşturulduğunu bildirir.|  
|[AppDomainShutdownFinished Yöntemi](icorprofilercallback-appdomainshutdownfinished-method.md)|Profil oluşturucuyu bir uygulama etki alanının bir işlemden kaldırılmış olduğunu bildirir.|  
|[AppDomainShutdownStarted Yöntemi](icorprofilercallback-appdomainshutdownstarted-method.md)|Profil Oluşturucu bir uygulama etki alanının bir işlemden kaldırılmakta olduğunu bildirir.|  
|[AssemblyLoadFinished Yöntemi](icorprofilercallback-assemblyloadfinished-method.md)|Profiler 'ın bir derlemenin yüklemeyi bitirmiş olduğunu bildirir.|  
|[AssemblyLoadStarted Yöntemi](icorprofilercallback-assemblyloadstarted-method.md)|Profiler 'ın bir derlemenin yüklenmekte olduğunu bildirir.|  
|[AssemblyUnloadFinished Yöntemi](icorprofilercallback-assemblyunloadfinished-method.md)|Profiler öğesine bir derlemenin kaldırılmış olduğunu bildirir.|  
|[AssemblyUnloadStarted Yöntemi](icorprofilercallback-assemblyunloadstarted-method.md)|Profiler öğesine bir derlemenin kaldırılmakta olduğunu bildirir.|  
|[ClassLoadFinished Yöntemi](icorprofilercallback-classloadfinished-method.md)|Profil oluşturucuyu bir sınıfın yükleme tamamlandığını bildirir.|  
|[ClassLoadStarted Yöntemi](icorprofilercallback-classloadstarted-method.md)|Profil oluşturucuyu bir sınıfın yüklenmekte olduğunu bildirir.|  
|[ClassUnloadFinished Yöntemi](icorprofilercallback-classunloadfinished-method.md)|Profil oluşturucuyu bir sınıfın kaldırmayı tamamladığını bildirir.|  
|[ClassUnloadStarted Yöntemi](icorprofilercallback-classunloadstarted-method.md)|Profil oluşturucuyu bir sınıfın kaldırılmakta olduğunu bildirir.|  
|[COMClassicVTableCreated Yöntemi](icorprofilercallback-comclassicvtablecreated-method.md)|Profil oluşturucuya, belirtilen IID ve sınıf için bir çalışma zamanı çağrılabilir sarmalayıcı (RCW) oluşturulduğunu bildirir.|  
|[COMClassicVTableDestroyed Yöntemi](icorprofilercallback-comclassicvtabledestroyed-method.md)|Profil oluşturucuyu bir RCW 'ın yok edildiğini bildirir.|  
|[ExceptionCatcherEnter Yöntemi](icorprofilercallback-exceptioncatcherenter-method.md)|Profil oluşturucuyu denetimin uygun bloğa geçtiğini bildirir `catch` .|  
|[ExceptionCatcherLeave Yöntemi](icorprofilercallback-exceptioncatcherleave-method.md)|Profil oluşturucuyu denetimin uygun bloktan geçirilmekte olduğunu bildirir `catch` .|  
|[ExceptionCLRCatcherExecute Yöntemi](icorprofilercallback-exceptionclrcatcherexecute-method.md)|.NET Framework sürüm 2,0 ' de kullanılmıyor.|  
|[ExceptionCLRCatcherFound Yöntemi](icorprofilercallback-exceptionclrcatcherfound-method.md)|.NET Framework 2,0 ' de kullanılmıyor.|  
|[ExceptionOSHandlerEnter Yöntemi](icorprofilercallback-exceptionoshandlerenter-method.md)|Uygulanmaz. Yönetilmeyen özel durum bilgisine ihtiyacı olan bir profil oluşturucu, bu bilgileri diğer yollarla almalıdır.|  
|[ExceptionOSHandlerLeave Yöntemi](icorprofilercallback-exceptionoshandlerleave-method.md)|Uygulanmaz. Yönetilmeyen özel durum bilgisine ihtiyacı olan bir profil oluşturucu, bu bilgileri diğer yollarla almalıdır.|  
|[ExceptionSearchCatcherFound Yöntemi](icorprofilercallback-exceptionsearchcatcherfound-method.md)|Profil oluşturucuya özel durum işlemenin arama aşamasının oluşturulan özel durum için bir işleyici bulunduğunu bildirir.|  
|[ExceptionSearchFilterEnter Yöntemi](icorprofilercallback-exceptionsearchfilterenter-method.md)|Profil oluşturucuyu Kullanıcı filtresinin yürütüldüğü konusunda bilgilendirir.|  
|[ExceptionSearchFilterLeave Yöntemi](icorprofilercallback-exceptionsearchfilterleave-method.md)|Profil oluşturucuyu bir Kullanıcı filtresinin yürütmeyi bitirmekte olduğunu bildirir.|  
|[ExceptionSearchFunctionEnter Yöntemi](icorprofilercallback-exceptionsearchfunctionenter-method.md)|Profil oluşturucuyu özel durum işlemenin arama aşamasının bir işlev girdiği hakkında bilgilendirir.|  
|[ExceptionSearchFunctionLeave Yöntemi](icorprofilercallback-exceptionsearchfunctionleave-method.md)|Profil oluşturucuya özel durum işlemenin arama aşamasının bir işlev aramayı bitirmediğini bildirir.|  
|[ExceptionThrown Yöntemi](icorprofilercallback-exceptionthrown-method.md)|Profiler öğesine bir özel durum gerçekleştiğini bildirir.|  
|[ExceptionUnwindFinallyEnter Yöntemi](icorprofilercallback-exceptionunwindfinallyenter-method.md)|Profil oluşturucuya özel durum işlemenin geriye doğru izleme aşamasının `finally` belirtilen işlevde içerilen bir yan tümce girdiğini bildirir.|  
|[ExceptionUnwindFinallyLeave Yöntemi](icorprofilercallback-exceptionunwindfinallyleave-method.md)|Profil oluşturucuya özel durum işlemenin geriye doğru izleme aşamasının bir `finally` yan tümce kaldığını bildirir.|  
|[ExceptionUnwindFunctionEnter Yöntemi](icorprofilercallback-exceptionunwindfunctionenter-method.md)|Profil oluşturucuyu, özel durum işlemenin geriye doğru izleme aşamasının bir işlev girdiği hakkında bilgilendirir.|  
|[ExceptionUnwindFunctionLeave Yöntemi](icorprofilercallback-exceptionunwindfunctionleave-method.md)|Profil oluşturucuyu, özel durum işlemenin geri sarma aşamasının bir işlevi geriye doğru izlemeyi tamamladığını bildirir.|  
|[FunctionUnloadStarted Yöntemi](icorprofilercallback-functionunloadstarted-method.md)|Profil oluşturucuyu, çalışma zamanının bir işlevi kaldırmak için başlatıldığını bildirir.|  
|[Initialize Yöntemi](icorprofilercallback-initialize-method.md)|Her yeni CLR uygulaması başlatıldığında profil oluşturucuyu başlatmak için çağırılır.|  
|[JITCachedFunctionSearchFinished Yöntemi](icorprofilercallback-jitcachedfunctionsearchfinished-method.md)|Profiler öğesine, daha önce NGen. exe kullanılarak derlenen bir işlev için bir aramanın tamamlandığını bildirir.|  
|[JITCachedFunctionSearchStarted Yöntemi](icorprofilercallback-jitcachedfunctionsearchstarted-method.md)|Profil oluşturucuyu, daha önce NGen. exe kullanılarak derlenen bir işlev için bir aramanın başlatıldığını bildirir.|  
|[JITCompilationFinished Yöntemi](icorprofilercallback-jitcompilationfinished-method.md)|Profiler öğesine JıT derleyicisinin bir işlevi derlemeyi tamamladığını bildirir.|  
|[JITCompilationStarted Yöntemi](icorprofilercallback-jitcompilationstarted-method.md)|Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin bir işlevi derlemek için başlatıldığını bildirir.|  
|[JITFunctionPitched Yöntemi](icorprofilercallback-jitfunctionpitched-method.md)|Profiler öğesine JıT derlenmiş bir işlevin bellekten kaldırıldığını bildirir.|  
|[JITInlining Yöntemi](icorprofilercallback-jitinlining-method.md)|Profiler öğesine JıT derleyicisinin başka bir işlevle satıra bir işlev eklemek üzere olduğunu bildirir.|  
|[ManagedToUnmanagedTransition Yöntemi](icorprofilercallback-managedtounmanagedtransition-method.md)|Profil oluşturucuyu yönetilen koddan yönetilmeyen koda geçişin oluştuğunu bildirir.|  
|[ModuleAttachedToAssembly Yöntemi](icorprofilercallback-moduleattachedtoassembly-method.md)|Profil oluşturucuyu bir modülün üst derlemesine iliştirilmekte olduğunu bildirir.|  
|[ModuleLoadFinished Yöntemi](icorprofilercallback-moduleloadfinished-method.md)|Profiler 'ın bir modülün yüklemeyi bitirdiğinden emin olduğunu bildirir.|  
|[ModuleLoadStarted Yöntemi](icorprofilercallback-moduleloadstarted-method.md)|Profil oluşturucuyu bir modülün yüklenmekte olduğunu bildirir.|  
|[ModuleUnloadFinished Yöntemi](icorprofilercallback-moduleunloadfinished-method.md)|Profil oluşturucuyu bir modülün kaldırmayı bitirmediğini bildirir.|  
|[ModuleUnloadStarted Yöntemi](icorprofilercallback-moduleunloadstarted-method.md)|Profil oluşturucuyu bir modülün kaldırılmakta olduğunu bildirir.|  
|[MovedReferences Yöntemi](icorprofilercallback-movedreferences-method.md)|Çöp toplama sırasında taşınan nesne başvuruları hakkında profil oluşturucuyu bilgilendirir.|  
|[ObjectAllocated Yöntemi](icorprofilercallback-objectallocated-method.md)|Profil oluşturucuya, yığın içindeki belleğin bir nesne için ayrıldığını bildirir.|  
|[ObjectReferences Yöntemi](icorprofilercallback-objectreferences-method.md)|Belirtilen nesne tarafından başvurulan bellekteki nesneler hakkında profil oluşturucuyu bilgilendirir.|  
|[ObjectsAllocatedByClass Yöntemi](icorprofilercallback-objectsallocatedbyclass-method.md)|Önceki çöp toplamadan bu yana oluşturulan her bir sınıfın örnek sayısı hakkında profil oluşturucuyu bilgilendirir.|  
|[RemotingClientInvocationFinished Yöntemi](icorprofilercallback-remotingclientinvocationfinished-method.md)|Bir uzaktan iletişim çağrısının istemci üzerinde tamamlanmasının çalıştırıldığı profil oluşturucuyu bildirir.|  
|[RemotingClientInvocationStarted Yöntemi](icorprofilercallback-remotingclientinvocationstarted-method.md)|Profil oluşturucuyu, uzaktan iletişim çağrısının başlatıldığını bildirir.|  
|[RemotingClientReceivingReply Yöntemi](icorprofilercallback-remotingclientreceivingreply-method.md)|Profil oluşturucuya, uzaktan iletişim çağrısının sunucu tarafı bölümünün tamamlandığını ve istemcinin artık yanıtı aldığını ve yanıt işlemesini bildirir.|  
|[RemotingClientSendingMessage Yöntemi](icorprofilercallback-remotingclientsendingmessage-method.md)|Profil oluşturucuyu istemcinin sunucuya bir istek gönderdiğini bildirir.|  
|[RemotingServerInvocationReturned Yöntemi](icorprofilercallback-remotingserverinvocationreturned-method.md)|Profil oluşturucuyu, işlemin bir uzak yöntem çağırma isteğine yanıt olarak bir yöntemi çağırma işlemini tamamladığını bildirir.|  
|[RemotingServerInvocationStarted Yöntemi](icorprofilercallback-remotingserverinvocationstarted-method.md)|Profil oluşturucuyu, işlemin uzak yöntem çağırma isteğine yanıt olarak bir yöntemi çağırdığını bildirir.|  
|[RemotingServerReceivingMessage Yöntemi](icorprofilercallback-remotingserverreceivingmessage-method.md)|Profil oluşturucuya işlemin uzak yöntem çağırma veya etkinleştirme isteği aldığını bildirir.|  
|[RemotingServerSendingReply Yöntemi](icorprofilercallback-remotingserversendingreply-method.md)|Profil oluşturucuya işlemin uzak yöntem çağırma isteğini işlemeyi tamamladığını ve yanıtı bir kanaldan iletmek üzere olduğunu bildirir.|  
|[RootReferences Yöntemi](icorprofilercallback-rootreferences-method.md)|Çöp toplama işleminden sonra kök başvuruları hakkındaki bilgilerle profil oluşturucuyu bilgilendirir.|  
|[RuntimeResumeFinished Yöntemi](icorprofilercallback-runtimeresumefinished-method.md)|Profil oluşturucuyu çalışma zamanının tüm çalışma zamanı iş parçacıklarını sürdürdüğünü ve normal işleme döndürüldüğünü bildirir.|  
|[RuntimeResumeStarted Yöntemi](icorprofilercallback-runtimeresumestarted-method.md)|Profil oluşturucuyu çalışma zamanının tüm çalışma zamanı iş parçacıklarını sürdürmeye devam etgeldiğini bildirir.|  
|[RuntimeSuspendAborted Yöntemi](icorprofilercallback-runtimesuspendaborted-method.md)|Profil oluşturucuyu, çalışma zamanının gerçekleşen çalışma zamanı askıya alma süresini durdurduğu konusunda bilgilendirir.|  
|[RuntimeSuspendFinished Yöntemi](icorprofilercallback-runtimesuspendfinished-method.md)|Profil oluşturucuyu çalışma zamanının tüm çalışma zamanı iş parçacıklarının askıya alınma tamamlandığını bildirir.|  
|[RuntimeSuspendStarted Yöntemi](icorprofilercallback-runtimesuspendstarted-method.md)|Profil oluşturucuyu çalışma zamanının tüm çalışma zamanı iş parçacıklarını askıya almak üzere olduğunu bildirir.|  
|[RuntimeThreadResumed Yöntemi](icorprofilercallback-runtimethreadresumed-method.md)|Profil oluşturucuyu, belirtilen iş parçacığının askıya alındıktan sonra devam ettirmekte olduğunu bildirir.|  
|[RuntimeThreadSuspended Yöntemi](icorprofilercallback-runtimethreadsuspended-method.md)|Profil oluşturucuya belirtilen iş parçacığının olduğunu veya askıya alınmayı bildirir.|  
|[Shutdown Yöntemi](icorprofilercallback-shutdown-method.md)|Profil oluşturucuyu uygulamanın kapandığını bildirir.|  
|[ThreadAssignedToOSThread Yöntemi](icorprofilercallback-threadassignedtoosthread-method.md)|Profil oluşturucuyu yönetilen bir iş parçacığının belirli bir işletim sistemi (OS) iş parçacığı kullanılarak uygulandığını bildirir.|  
|[ThreadCreated Yöntemi](icorprofilercallback-threadcreated-method.md)|Profil oluşturucuyu bir iş parçacığının oluşturulduğunu bildirir.|  
|[ThreadDestroyed Yöntemi](icorprofilercallback-threaddestroyed-method.md)|Profiler öğesine bir iş parçacığının yok edildiğini bildirir.|  
|[UnmanagedToManagedTransition Yöntemi](icorprofilercallback-unmanagedtomanagedtransition-method.md)|Profil oluşturucuyu yönetilmeyen koddan yönetilen koda geçiş olduğunu bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, profil oluşturucunun `ICorProfilerCallback` abone olduğu bir olay olduğunda profil oluşturucuyu bilgilendirmek için (veya [ICorProfilerCallback2](icorprofilercallback2-interface.md)) arabirimindeki bir yöntemi çağırır. Bu, CLR 'nin kod Profilcisi ile iletişim kurduğu birincil geri çağırma arabirimidir.  
  
 Bir kod profil oluşturucu arabirimin yöntemlerini uygulamalıdır `ICorProfilerCallback` . .NET Framework sürüm 2,0 veya üzeri için, profil oluşturucunun de yöntemleri uygulaması gerekir `ICorProfilerCallback2` . Her yöntem uygulamasının başarılı veya hatalı E_FAIL S_OK değerine sahip bir HRESULT döndürmesi gerekir. Şu anda CLR [ICorProfilerCallback:: ObjectReferences](icorprofilercallback-objectreferences-method.md)hariç her geri çağırma tarafından döndürülen HRESULT 'yi yoksayar.  
  
 Microsoft Windows kayıt defterinde, bir kod Profilleyicisi, ve arabirimlerini uygulayan bileşen nesne modeli (COM) nesnesine kaydolmalıdır `ICorProfilerCallback` `ICorProfilerCallback2` . Bir kod profil oluşturucu, [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md)çağırarak bildirim almak istediği olaylara abone olur. Bu genellikle profil oluşturucunun [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md)uygulamasında yapılır. Profil Oluşturucu daha sonra bir olay gerçekleşmekte olduğu veya yürütülmekte olan bir çalışma zamanı işleminde gerçekleştiyse çalışma zamanından bildirim alabilir.  
  
> [!NOTE]
> Profil Oluşturucu tek bir COM nesnesi kaydeder. Profiler .NET Framework sürüm 1,0 veya 1,1 ' i hedefliyorsanız, söz konusu COM nesnesinin yalnızca yöntemini uygulaması gerekir `ICorProfilerCallback` . .NET Framework sürüm 2,0 veya sonraki bir sürümü hedefliyorsanız, COM nesnesinin yöntemlerini de uygulaması gerekir `ICorProfilerCallback2` .  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerCallback2 Arabirimi](icorprofilercallback2-interface.md)
- [ICorProfilerCallback3 Arabirimi](icorprofilercallback3-interface.md)
- [ICorProfilerCallback4 Arabirimi](icorprofilercallback4-interface.md)
