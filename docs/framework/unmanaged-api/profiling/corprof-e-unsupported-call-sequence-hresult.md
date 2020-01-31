---
title: CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
ms.date: 03/30/2017
f1_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE
helpviewer_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT [.NET Framework profiling]
ms.assetid: f2fc441f-d62e-4f72-a011-354ea13c8c59
ms.openlocfilehash: b4ab5c8f7cdca1303cb4fbbc4fa39db3c5977c15
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867015"
---
# <a name="corprof_e_unsupported_call_sequence-hresult"></a>CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT

CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT .NET Framework sürüm 2,0 ' de tanıtılmıştı. .NET Framework 4, bu HRESULT 'yi iki senaryoda döndürür:  
  
- Bir ele geçiren profil oluşturucu, iş parçacığının kayıt bağlamını rastgele bir zamanda zorla sıfırladığında iş parçacığı tutarsız bir durumda olan yapılara erişmeye çalışır.  
  
- Bir profil oluşturucu çöp toplamayı yasaklıyor çöp toplamanın geri çağırma yönteminden tetikleyen bir bilgilendirici yöntemi çağırmayı denediğinde.  
  
Bu iki senaryo aşağıdaki bölümlerde ele alınmıştır.  
  
## <a name="hijacking-profilers"></a>Ele geçirme profil oluşturucular  

  (Bu senaryo birincil olarak ele geçirme profil oluşturucular ile ilgili bir sorundur, ancak ele alınmayan profil oluşturucular bu HRESULT 'yi görebildiği durumlar olabilir.)  
  
 Bu senaryoda, bir ele geçiren profil oluşturucu, iş parçacığının kayıt bağlamını rastgele bir zamanda zorla sıfırlar, böylece iş parçacığı profil oluşturucu kodu girebilir veya bir [ICorProfilerInfo](icorprofilerinfo-interface.md) yöntemi aracılığıyla ortak dil çalışma ZAMANıNı (CLR) yeniden girebilirler.  
  
 Profil oluşturma API 'sinin birçok kimliği, CLR 'deki veri yapılarına işaret verir. Birçok `ICorProfilerInfo` çağrı yalnızca bu veri yapılarındaki bilgileri okur ve geri geçirebilir. Ancak, CLR bu yapıların çalıştığı gibi herhangi bir şeyi değiştirebilir ve bunu yapmak için kilitleri kullanabilir. CLR 'nin iş parçacığını ele aldığı sırada bir kilidi zaten tutan (veya edinmeye çalışırken) bir kilit olduğunu varsayalım. İş parçacığı CLR 'ye yeniden girerse ve değiştirme sürecinde daha fazla kilit almaya veya yapıları incelemeye çalışırsa, bu yapılar tutarsız bir durumda olabilir. Kilitlenmeler ve erişim ihlalleri bu gibi durumlarda kolayca gerçekleşebilir.  
  
 Genel olarak, ele alınmayan bir profil oluşturucu kodu bir [ICorProfilerCallback](icorprofilercallback-interface.md) yöntemi içinde yürütür ve geçerli parametrelerle bir `ICorProfilerInfo` yöntemi çağırıyorsa, kilitlenmemelidir veya bir erişim ihlali almamalıdır. Örneğin, [ICorProfilerCallback:: ClassLoadFinished](icorprofilercallback-classloadfinished-method.md) yöntemi içinde çalışan profil oluşturucu kodu, [ICorProfilerInfo2:: GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md) yöntemini çağırarak sınıf hakkında bilgi isteyebilir. Kod, bilgilerin kullanılamadığını göstermek için bir HRESULT CORPROF_E_DATAINCOMPLETE alabilir. Ancak, kilitlenmez veya bir erişim ihlali almaz. Bu `ICorProfilerInfo` çağrısı, `ICorProfilerCallback` yönteminden yapıldığından zaman uyumlu olarak değerlendirilir.  
  
 Ancak, bir `ICorProfilerCallback` yöntemi içinde olmayan kodu yürüten yönetilen bir iş parçacığı, zaman uyumsuz bir çağrı yapmakta olduğu kabul edilir. .NET Framework sürüm 1 ' de, zaman uyumsuz bir çağrıda ne olabileceğini belirlemek zordur. Çağrı kilitlenme, kilitlenme veya geçersiz yanıt verebilir. .NET Framework sürüm 2,0, bu sorundan kaçınmanıza yardımcı olacak bazı basit denetimler sunmuştur. .NET Framework 2,0 ' de, güvenli olmayan bir `ICorProfilerInfo` işlevini zaman uyumsuz olarak çağırırsanız, bir CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT ile başarısız olur.  
  
 Genel olarak, zaman uyumsuz çağrılar güvenli değildir. Ancak, aşağıdaki yöntemler güvenlidir ve özellikle zaman uyumsuz çağrıları destekler:  
  
- [GetEventMask](icorprofilerinfo-geteventmask-method.md)  
  
- [SetEventMask](icorprofilerinfo-seteventmask-method.md)  
  
- [GetCurrentThreadID](icorprofilerinfo-getcurrentthreadid-method.md)  
  
- [GetThreadContext](icorprofilerinfo-getthreadcontext-method.md)  
  
- [GetThreadAppDomain](icorprofilerinfo2-getthreadappdomain-method.md)  
  
- [GetFunctionFromIP](icorprofilerinfo-getfunctionfromip-method.md)  
  
- [GetFunctionInfo](icorprofilerinfo-getfunctioninfo-method.md)  
  
- [Getfunctionınfo2](icorprofilerinfo2-getfunctioninfo2-method.md)  
  
- [GetCodeInfo](icorprofilerinfo-getcodeinfo-method.md)  
  
- [Getcodeınfo2](icorprofilerinfo2-getcodeinfo2-method.md)  
  
- [GetModuleInfo](icorprofilerinfo-getmoduleinfo-method.md)  
  
- [GetClassIDInfo](icorprofilerinfo-getclassidinfo-method.md)  
  
- [Getclassıdınfo2](icorprofilerinfo2-getclassidinfo2-method.md)  
  
- [IsArrayClass](icorprofilerinfo-isarrayclass-method.md)  
  
- [SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)  
  
- [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md)  
  
 Daha fazla bilgi için bkz. CLR profil oluşturma API 'SI blogda [neden corprof_e_unsupported_call_sequence sahip olduğumuz](https://docs.microsoft.com/archive/blogs/davbr/why-we-have-corprof_e_unsupported_call_sequence) girişi.  
  
## <a name="triggering-garbage-collections"></a>Çöp koleksiyonları tetikleniyor  
 Bu senaryo, bir geri çağırma yöntemi içinde çalışan bir profil Oluşturucu içerir (örneğin, `ICorProfilerCallback` yöntemlerinden biri) yasaklıyor çöp toplama. Profil Oluşturucu çöp toplama tetikleyebilen bir bilgilendirici yöntemi (örneğin, `ICorProfilerInfo` arabirimindeki bir yöntemi) çağırmaya çalışırsa, bilgilendirici yöntemi bir HRESULT CORPROF_E_UNSUPPORTED_CALL_SEQUENCE başarısız olur.  
  
 Aşağıdaki tabloda çöp koleksiyonları sağlayan geri çağırma yöntemleri ve çöp koleksiyonlarının tetikleyebileceğini bilgilendirici Yöntemler gösterilmektedir. Profil Oluşturucu listelenmiş geri çağırma yöntemlerinden birinin içinde yürütülüyorsa ve listelenen bilgilendirici yöntemlerden birini çağırırsa, bu bilgi yöntemi HRESULT CORPROF_E_UNSUPPORTED_CALL_SEQUENCE başarısız olur.  
  
|Çöp koleksiyonlarını sağlayan geri çağırma yöntemleri|Çöp koleksiyonları tetikleyen bilgilendirici Yöntemler|  
|------------------------------------------------------|------------------------------------------------------------|  
|[ThreadAssignedToOSThread](icorprofilercallback-threadassignedtoosthread-method.md)<br /><br /> [ExceptionUnwindFunctionEnter](icorprofilercallback-exceptionunwindfunctionenter-method.md)<br /><br /> [ExceptionUnwindFunctionLeave](icorprofilercallback-exceptionunwindfunctionleave-method.md)<br /><br /> [ExceptionUnwindFinallyEnter](icorprofilercallback-exceptionunwindfinallyenter-method.md)<br /><br /> [ExceptionUnwindFinallyLeave](icorprofilercallback-exceptionunwindfinallyleave-method.md)<br /><br /> [ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md)<br /><br /> [RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md)<br /><br /> [RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md)<br /><br /> [RuntimeSuspendAborted](icorprofilercallback-runtimesuspendaborted-method.md)<br /><br /> [RuntimeThreadSuspended](icorprofilercallback-runtimethreadsuspended-method.md)<br /><br /> [RuntimeThreadResumed](icorprofilercallback-runtimethreadresumed-method.md)<br /><br /> [MovedReferences](icorprofilercallback-movedreferences-method.md)<br /><br /> [ObjectReferences](icorprofilercallback-objectreferences-method.md)<br /><br /> [ObjectsAllocatedByClass](icorprofilercallback-objectsallocatedbyclass-method.md)<br /><br /> [RootReferences2](icorprofilercallback-rootreferences-method.md)<br /><br /> [HandleCreated](icorprofilercallback2-handlecreated-method.md)<br /><br /> [HandleDestroyed](icorprofilercallback2-handledestroyed-method.md)<br /><br /> [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md)<br /><br /> [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)|[GetILFunctionBodyAllocator](icorprofilerinfo-getilfunctionbodyallocator-method.md)<br /><br /> [SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md)<br /><br /> [SetILInstrumentedCodeMap](icorprofilerinfo-setilinstrumentedcodemap-method.md)<br /><br /> [ForceGC](icorprofilerinfo-forcegc-method.md)<br /><br /> [GetClassFromToken](icorprofilerinfo-getclassfromtoken-method.md)<br /><br /> [GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)<br /><br /> [GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)<br /><br /> [GetAppDomainInfo](icorprofilerinfo-getappdomaininfo-method.md)<br /><br /> [EnumModules](icorprofilerinfo3-enummodules-method.md)<br /><br /> [RequestProfilerDetach](icorprofilerinfo3-requestprofilerdetach-method.md)<br /><br /> [GetAppDomainsContainingModule](icorprofilerinfo3-getappdomainscontainingmodule-method.md)|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ICorProfilerCallback2 Arabirimi](icorprofilercallback2-interface.md)
- [ICorProfilerCallback3 Arabirimi](icorprofilercallback3-interface.md)
- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](icorprofilerinfo2-interface.md)
- [ICorProfilerInfo3 Yöntemi](icorprofilerinfo3-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
