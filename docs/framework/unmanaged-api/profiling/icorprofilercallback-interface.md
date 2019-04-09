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
ms.openlocfilehash: e2f474317493b3aac421ca1270ff461b97cfe027
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125950"
---
# <a name="icorprofilercallback-interface"></a>ICorProfilerCallback Arabirimi
Ortak dil çalışma zamanı tarafından (CLR) profil oluşturucu abone olduğu olaylar meydana geldiğinde bir kod profil oluşturucu bildirmek için kullanılan yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[AppDomainCreationFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md)|Profil Oluşturucu, bir uygulama etki alanı oluşturulduğunu bildirir.|  
|[AppDomainCreationStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationstarted-method.md)|Profil Oluşturucu, bir uygulama etki alanı oluşturulduğunu bildirir.|  
|[AppDomainShutdownFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownfinished-method.md)|Profil Oluşturucu, bir uygulama etki alanı bir işlemden olduğunu bildirir.|  
|[AppDomainShutdownStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md)|Profil Oluşturucu, bir uygulama etki alanı bir işlemden boşaltılıyor bildirir.|  
|[AssemblyLoadFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md)|Profil Oluşturucu bir bütünleştirilmiş kod yükleme işleminin tamamlandığını bildirir.|  
|[AssemblyLoadStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadstarted-method.md)|Profil Oluşturucu, bir derlemenin yüklendiği bildirir.|  
|[AssemblyUnloadFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)|Profil Oluşturucu, bir derleme kaldırıldı bildirir.|  
|[AssemblyUnloadStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md)|Profil Oluşturucu, bir derleme boşaltılıyor bildirir.|  
|[ClassLoadFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)|Profil Oluşturucu, bir sınıf yükleme işleminin tamamlandığını bildirir.|  
|[ClassLoadStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)|Profil Oluşturucu, bir sınıf yüklü olduğunu bildirir.|  
|[ClassUnloadFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)|Profil Oluşturucu, bir sınıf kaldırma işleminin tamamlandığını bildirir.|  
|[ClassUnloadStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)|Profil Oluşturucu, bir sınıf boşaltılıyor bildirir.|  
|[COMClassicVTableCreated Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)|Profil Oluşturucu, belirtilen IID ve sınıf için bir çalışma zamanı çağrılabilir sarmalayıcı (RCW) oluşturulduğunu bildirir.|  
|[COMClassicVTableDestroyed Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)|Profil Oluşturucu bir RCW edildiğini bildirir.|  
|[ExceptionCatcherEnter Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)|Denetimi uygun geçirilen profil oluşturucu bildirir `catch` blok.|  
|[ExceptionCatcherLeave Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)|Denetimi uygun dışında geçirilen profil oluşturucu bildirir `catch` blok.|  
|[ExceptionCLRCatcherExecute Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)|.NET Framework 2.0 sürümünde Kullanımdan kalktı.|  
|[ExceptionCLRCatcherFound Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)|.NET Framework 2.0 Kullanımdan kalktı.|  
|[ExceptionOSHandlerEnter Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerenter-method.md)|Henüz uygulanmadı. Yönetilmeyen özel durum bilgisi gerektiren bir profil oluşturucu, diğer araçlarla bu bilgileri edinmeniz gerekir.|  
|[ExceptionOSHandlerLeave Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerleave-method.md)|Henüz uygulanmadı. Yönetilmeyen özel durum bilgisi gerektiren bir profil oluşturucu, diğer araçlarla bu bilgileri edinmeniz gerekir.|  
|[ExceptionSearchCatcherFound Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchcatcherfound-method.md)|Profil Oluşturucu, oluşturulan özel durum işleyicisi özel durum işleme arama aşaması bulunduğunu bildirir.|  
|[ExceptionSearchFilterEnter Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)|Profil Oluşturucu, kullanıcı filtresi yürütülmekte olan bildirir.|  
|[ExceptionSearchFilterLeave Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)|Profil Oluşturucu, kullanıcı filtresi yalnızca yürütme işleminin tamamlandığını bildirir.|  
|[ExceptionSearchFunctionEnter Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)|Profil Oluşturucu bir işlev özel durum işleme arama aşaması girdiğini bildirir.|  
|[ExceptionSearchFunctionLeave Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)|Profil Oluşturucu, özel durum işleme arama aşaması bir işlev arama işleminin tamamlandığını bildirir.|  
|[ExceptionThrown Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md)|Profil Oluşturucu, bir özel durum olduğunu bildirir.|  
|[ExceptionUnwindFinallyEnter Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)|İşleme özel durumu geriye doğru izleme aşamasına giriyor profil oluşturucu bildirir bir `finally` belirtilen işlevinde yan tümcesi.|  
|[ExceptionUnwindFinallyLeave Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)|İşleme özel durumu geriye doğru izleme aşaması ayrıldı profil oluşturucu bildirir bir `finally` yan tümcesi.|  
|[ExceptionUnwindFunctionEnter Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)|Profil Oluşturucu bir işlev özel durum işleme geriye doğru izleme aşaması girdiğini bildirir.|  
|[ExceptionUnwindFunctionLeave Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)|Profil Oluşturucu, özel durum işleme geriye doğru izleme aşaması bir işlevi geriye doğru izleme işleminin tamamlandığını bildirir.|  
|[FunctionUnloadStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md)|Profil Oluşturucu bir işlev kaldırmak çalışma zamanı başlatıldığını bildirir.|  
|[Initialize Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)|Yeni bir CLR uygulaması başlatıldığında profil oluşturucuyu başlatmak üzere çağrılır.|  
|[JITCachedFunctionSearchFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md)|Profil Oluşturucu, NGen.exe kullanarak önceden derlenen bir işlev için bir arama işleminin tamamlandığını bildirir.|  
|[JITCachedFunctionSearchStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md)|Profil Oluşturucu, NGen.exe kullanarak önceden derlenen bir işlev için bir arama başlatıldığını bildirir.|  
|[JITCompilationFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)|Profil Oluşturucu, JIT Derleyici bir işlevi derleme tamamlandığını bildirir.|  
|[JITCompilationStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)|Profil Oluşturucu, just-ın-time (JIT) derleyici bir işlevi derlemeye ne başlatıldığını bildirir.|  
|[JITFunctionPitched Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md)|Profil oluşturucunun JIT olarak derlenmiş bir işlev bellekten kaldırıldığını size bildirir.|  
|[JITInlining Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)|Profil Oluşturucu, JIT Derleyici hakkında başka bir işlevi satır içi işlev eklemek için olduğunu bildirir.|  
|[ManagedToUnmanagedTransition Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)|Profil Oluşturucu, yönetilen koddan yönetilmeyen koda geçiş oluştuğunu bildirir.|  
|[ModuleAttachedToAssembly Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md)|Profil Oluşturucu, bir modül, ana derlemeye bağlı olduğunu bildirir.|  
|[ModuleLoadFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)|Profil Oluşturucu, bir modül yükleme işleminin tamamlandığını bildirir.|  
|[ModuleLoadStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)|Profil Oluşturucu, bir modül yüklenmekte olduğuna dair bildirir.|  
|[ModuleUnloadFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)|Profil Oluşturucu, bir modül kaldırma işleminin tamamlandığını bildirir.|  
|[ModuleUnloadStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md)|Profil Oluşturucu, bir modül boşaltılıyor bildirir.|  
|[MovedReferences Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)|Profil oluşturucuyu çöp toplama sırasında taşınan nesne başvuruları hakkında bilgilendirir.|  
|[ObjectAllocated Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)|Bir nesne için bellek yığında ayrılan profil oluşturucu bildirir.|  
|[ObjectReferences Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)|Profil Oluşturucu belirtilen nesne tarafından başvurulan bellek nesneleri hakkında bilgilendirir.|  
|[ObjectsAllocatedByClass Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)|Profil Oluşturucu belirtilen her sınıf önceki çöp toplama işleminden itibaren oluşturulan örnek sayısını hakkında bilgilendirir.|  
|[RemotingClientInvocationFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)|Profil Oluşturucu bir çağrının sürebileceği istemcide tamamlanmak üzere çalıştırılmasını bildirir.|  
|[RemotingClientInvocationStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationstarted-method.md)|Profil Oluşturucu bir çağrının sürebileceği başlatıldığını bildirir.|  
|[RemotingClientReceivingReply Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)|Uzaktan iletişim çağrısı sunucu tarafı kısmı tamamlandı ve istemci artık alma profil oluşturucu bildirir ve yanıt işlenecek.|  
|[RemotingClientSendingMessage Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)|Profil Oluşturucu, istemci sunucuya istek göndermeden bildirir.|  
|[RemotingServerInvocationReturned Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md)|Profil Oluşturucu, bir uzak yöntem çağırma isteğine yanıt olarak bir yöntem çağırma işleminin tamamlandığını bildirir.|  
|[RemotingServerInvocationStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationstarted-method.md)|Profil Oluşturucu işlemi uzak yöntem çağırma isteğine yanıt olarak bir yöntemi çağıran olduğunu bildirir.|  
|[RemotingServerReceivingMessage Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md)|Profil Oluşturucu işlemin bir uzak yöntem çağırma veya etkinleştirme isteği aldığını bildirir.|  
|[RemotingServerSendingReply Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)|Profil Oluşturucu işlemi bir uzak yöntem çağırma isteği işlemeyi tamamladıktan ve yanıt bir kanal üzerinden iletilmek üzere olduğunu bildirir.|  
|[RootReferences Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)|Profil oluşturucuyu çöp toplamadan sonra kök başvuruları hakkındaki bilgileri ile bildirir.|  
|[RuntimeResumeFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumefinished-method.md)|Profil Oluşturucu çalışma zamanı tüm çalışma zamanı iş parçacığı devam ediyor ve normal çalışmasına geri döndürdü bildirir.|  
|[RuntimeResumeStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)|Profil Oluşturucu çalışma zamanı, tüm çalışma zamanı iş parçacığı sürdürülmekte bildirir.|  
|[RuntimeSuspendAborted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)|Profil Oluşturucu çalışma zamanı oluşan çalışma zamanı askıya alınması iptal edildiğini bildirir.|  
|[RuntimeSuspendFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)|Profil Oluşturucu çalışma zamanı, tüm çalışma zamanı iş parçacıkları askıya alınması tamamlandığını bildirir.|  
|[RuntimeSuspendStarted Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)|Profil Oluşturucu çalışma zamanı tüm çalışma zamanı iş parçacıklarını askıya almak olduğunu bildirir.|  
|[RuntimeThreadResumed Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)|Profil Oluşturucu, belirtilen iş parçacığını askıya sonra ettirdi bildirir.|  
|[RuntimeThreadSuspended Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)|Belirtilen iş parçacığı olan veya askıya için profil oluşturucu bildirir.|  
|[Shutdown Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)|Profil Oluşturucu, uygulamanın kapanacağını bildirir.|  
|[ThreadAssignedToOSThread Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)|Profil Oluşturucu, belirli bir işletim sistemi (OS) iş parçacığı kullanarak bir yönetilen iş parçacığı uygulanan olduğunu bildirir.|  
|[ThreadCreated Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)|Profil Oluşturucu, bir iş parçacığı oluşturulduğunu size bildirir.|  
|[ThreadDestroyed Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)|Profil Oluşturucu, bir iş parçacığı yok edildi bildirir.|  
|[UnmanagedToManagedTransition Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)|Profil Oluşturucu, yönetilmeyen koddan yönetilen koda geçiş oluştuğunu bildirir.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR bir yöntem çağrıları `ICorProfilerCallback` (veya [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) olduğu için profil oluşturucu abone, bir olay gerçekleştiğinde, profil oluşturucu bildirmek için arabirimi gerçekleşir. Bu, CLR kod Profil Oluşturucu ile iletişim kurar birincil geri çağırma arabirimidir.  
  
 Bir kod profil oluşturucu yöntemleri uygulamalıdır `ICorProfilerCallback` arabirimi. .NET Framework sürüm 2.0 veya üzeri için profil oluşturucu ayrıca uygulamalıdır `ICorProfilerCallback2` yöntemleri. Her yöntem uygulaması değeri başarılıysa S_OK HRESULT ya da E_FAIL hatası döndürmesi gerekir. Şu anda, CLR dışında her bir geri çağırma tarafından döndürülen HRESULT yoksayar [Icorprofilercallback::objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
 Microsoft Windows kayıt defterinde bir kod profil oluşturucu uygulayan kendi Bileşen Nesne Modeli (COM) nesne kaydetmelisiniz `ICorProfilerCallback` ve `ICorProfilerCallback2` arabirimleri. Bir kod profil oluşturucu, istediği çağırarak bildirim almak olaylara abone olur [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). Bu genellikle profil oluşturucunun uygulamasında yapılır [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Profil Oluşturucu ardından bir olayı gerçekleşmek üzere olduğunu veya sadece yürütülmekte olan bir çalışma zamanı işleminde oluştu çalışma zamanını şuradan bildirim almak kullanabilirsiniz.  
  
> [!NOTE]
>  Profil oluşturucuyu tek bir COM nesnesi kaydeder. Profil oluşturucuyu bir .NET Framework sürüm 1.0 veya 1.1, COM nesnesi yalnızca yöntemlerini uygulamak gereken hedeflediği `ICorProfilerCallback`. Bu .NET Framework 2.0 veya sonraki bir sürümü hedefliyorsa, COM nesnesinin yöntemlerini de uygulamalıdır `ICorProfilerCallback2`.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [ICorProfilerCallback3 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerCallback4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
