---
title: CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
ms.date: 03/30/2017
f1_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE
helpviewer_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT [.NET Framework profiling]
ms.assetid: f2fc441f-d62e-4f72-a011-354ea13c8c59
ms.openlocfilehash: 4d835f749a33d21a13be307e1524671e36496899
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440834"
---
# <a name="corprof_e_unsupported_call_sequence-hresult"></a>CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT .NET Framework sürüm 2,0 ' de tanıtılmıştı. .NET Framework 4, bu HRESULT 'yi iki senaryoda döndürür:  
  
- Bir ele geçiren profil oluşturucu, iş parçacığının kayıt bağlamını rastgele bir zamanda zorla sıfırladığında iş parçacığı tutarsız bir durumda olan yapılara erişmeye çalışır.  
  
- Bir profil oluşturucu çöp toplamayı yasaklıyor çöp toplamanın geri çağırma yönteminden tetikleyen bir bilgilendirici yöntemi çağırmayı denediğinde.  
  
 Bu iki senaryo aşağıdaki bölümlerde ele alınmıştır.  
  
## <a name="hijacking-profilers"></a>Ele geçirme profil oluşturucular  
 (Bu senaryo birincil olarak ele geçirme profil oluşturucular ile ilgili bir sorundur ve ele alınmayan profil oluşturucular bu HRESULT 'yi görebildiği durumlar olmasına rağmen).  
  
 Bu senaryoda, bir ele geçiren profil oluşturucu, iş parçacığının kayıt bağlamını rastgele bir zamanda zorla sıfırlar, böylece iş parçacığı profil oluşturucu kodu girebilir veya bir [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) yöntemi aracılığıyla ortak dil çalışma ZAMANıNı (CLR) yeniden girebilirler.  
  
 Profil oluşturma API 'sinin birçok kimliği, CLR 'deki veri yapılarına işaret verir. Birçok `ICorProfilerInfo` çağrı yalnızca bu veri yapılarındaki bilgileri okur ve geri geçirebilir. Ancak, CLR bu yapıların çalıştığı gibi herhangi bir şeyi değiştirebilir ve bunu yapmak için kilitleri kullanabilir. CLR 'nin iş parçacığını ele aldığı sırada bir kilidi zaten tutan (veya edinmeye çalışırken) bir kilit olduğunu varsayalım. İş parçacığı CLR 'yi yeniden girerse ve değiştirme sürecinde daha fazla kilit almaya veya yapıları incelemeye çalışırsa, bu yapılar tutarsız bir durumda olabilir. Kilitlenmeler ve erişim ihlalleri bu gibi durumlarda kolayca gerçekleşebilir.  
  
 Genel olarak, ele alınmayan bir profil oluşturucu kodu bir [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) yöntemi içinde yürütür ve geçerli parametrelerle bir `ICorProfilerInfo` yöntemi çağırıyorsa, kilitlenmemelidir veya bir erişim ihlali almamalıdır. Örneğin, [ICorProfilerCallback:: ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) yöntemi içinde çalışan profil oluşturucu kodu, [ICorProfilerInfo2:: GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) yöntemini çağırarak sınıf hakkında bilgi isteyebilir. Kod, bilgilerin kullanılamadığını belirten bir HRESULT CORPROF_E_DATAINCOMPLETE alabilir; Ancak, kilitlenmez veya bir erişim ihlali almaz. `ICorProfilerInfo` ' a çağrı sınıfı, bir `ICorProfilerCallback` yönteminden yapıldığından zaman uyumlu olarak adlandırılır.  
  
 Ancak, bir `ICorProfilerCallback` yöntemi içinde olmayan kodu yürüten yönetilen bir iş parçacığı, zaman uyumsuz bir çağrı yapmakta olduğu kabul edilir. .NET Framework sürüm 1 ' de, zaman uyumsuz bir çağrıda ne olabileceğini belirlemek zordur. Çağrı kilitlenme, kilitlenme veya geçersiz yanıt verebilir. .NET Framework sürüm 2,0, bu sorundan kaçınmanıza yardımcı olacak bazı basit denetimler sunmuştur. .NET Framework 2,0 ' de, güvenli olmayan bir `ICorProfilerInfo` işlevini zaman uyumsuz olarak çağırırsanız, bir CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT ile başarısız olur.  
  
 Genel olarak, zaman uyumsuz çağrılar güvenli değildir. Ancak, aşağıdaki yöntemler güvenlidir ve özellikle zaman uyumsuz çağrıları destekler:  
  
- [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)  
  
- [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)  
  
- [GetCurrentThreadID](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)  
  
- [GetThreadContext](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)  
  
- [GetThreadAppDomain](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)  
  
- [GetFunctionFromIP](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)  
  
- [GetFunctionInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)  
  
- [Getfunctionınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)  
  
- [GetCodeInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)  
  
- [Getcodeınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)  
  
- [GetModuleInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)  
  
- [GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)  
  
- [Getclassıdınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)  
  
- [IsArrayClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)  
  
- [SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
  
- [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
  
 Daha fazla bilgi için bkz. CLR profil oluşturma API bloguna [neden corprof_e_unsupported_call_sequence sahip olduğumuz](https://go.microsoft.com/fwlink/?LinkId=169156) girişi.  
  
## <a name="triggering-garbage-collections"></a>Çöp koleksiyonları tetikleniyor  
 Bu senaryo, bir geri çağırma yöntemi içinde çalışan bir profil Oluşturucu içerir (örneğin, `ICorProfilerCallback` yöntemlerinden biri) yasaklıyor çöp toplama. Profil Oluşturucu çöp toplama tetikleyebilen bir bilgilendirici yöntemi (örneğin, `ICorProfilerInfo` arabirimindeki bir yöntemi) çağırmaya çalışırsa, bilgilendirici yöntemi bir HRESULT CORPROF_E_UNSUPPORTED_CALL_SEQUENCE başarısız olur.  
  
 Aşağıdaki tabloda çöp koleksiyonları sağlayan geri çağırma yöntemleri ve çöp koleksiyonlarının tetikleyebileceğini bilgilendirici Yöntemler gösterilmektedir. Profil Oluşturucu listelenmiş geri çağırma yöntemlerinden birinin içinde yürütülüyorsa ve listelenen bilgilendirici yöntemlerden birini çağırırsa, bu bilgi yöntemi HRESULT CORPROF_E_UNSUPPORTED_CALL_SEQUENCE başarısız olur.  
  
|Çöp koleksiyonlarını sağlayan geri çağırma yöntemleri|Çöp koleksiyonları tetikleyen bilgilendirici Yöntemler|  
|------------------------------------------------------|------------------------------------------------------------|  
|[ThreadAssignedToOSThread](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)<br /><br /> [ExceptionUnwindFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)<br /><br /> [ExceptionUnwindFunctionLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)<br /><br /> [ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)<br /><br /> [ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)<br /><br /> [ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)<br /><br /> [RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)<br /><br /> [RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)<br /><br /> [RuntimeSuspendAborted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)<br /><br /> [RuntimeThreadSuspended](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)<br /><br /> [RuntimeThreadResumed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)<br /><br /> [MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)<br /><br /> [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)<br /><br /> [ObjectsAllocatedByClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)<br /><br /> [RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)<br /><br /> [HandleCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)<br /><br /> [HandleDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)<br /><br /> [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)<br /><br /> [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|[GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)<br /><br /> [SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)<br /><br /> [SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)<br /><br /> [ForceGC](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)<br /><br /> [GetClassFromToken](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)<br /><br /> [GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)<br /><br /> [GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)<br /><br /> [GetAppDomainInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)<br /><br /> [EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)<br /><br /> [RequestProfilerDetach](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)<br /><br /> [GetAppDomainsContainingModule](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getappdomainscontainingmodule-method.md)|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [ICorProfilerCallback3 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [ICorProfilerInfo3 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
