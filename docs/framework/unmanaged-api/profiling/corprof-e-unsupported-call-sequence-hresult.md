---
title: CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
ms.date: 03/30/2017
f1_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE
helpviewer_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT [.NET Framework profiling]
ms.assetid: f2fc441f-d62e-4f72-a011-354ea13c8c59
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6cce181037ee4f4db3a828f98cc3e07dfb45aff3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461636"
---
# <a name="corprofeunsupportedcallsequence-hresult"></a>CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT .NET Framework sürüm 2.0 sunulmuştur. [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] İki senaryoda Bu HRESULT döndürür:  
  
-   Bir iş parçacığının zorla ele geçirme profil oluşturucu sıfırlandıktan sonra bağlamı iş parçacığı tutarsız bir durumda yapıları erişmeye rasgele bir zaman kaydettiğiniz.  
  
-   Çöp toplama bir geri çağırma yönteminden tetikler bilgilendirici bir yöntemi çağırmak bir profil oluşturucu çalıştığında, atık toplama engelliyor.  
  
 Bu iki senaryo aşağıdaki bölümlerde ele alınmıştır.  
  
## <a name="hijacking-profilers"></a>Profil oluşturucular ele geçirme  
 (Bu senaryo vardır, ancak bu HRESULT geçirme olmayan profil oluşturucular görebileceğiniz durumlarda profil oluşturucular ele geçirme ile öncelikle bir sorundur.)  
  
 İş parçacığı profil oluşturucu kodu girin veya ortak dil çalışma zamanı (CLR) yeniden girmeniz Bu senaryoda, geçirme profil oluşturucu zorla bir iş parçacığının kayıt bağlamını rastgele bir zaman aracılığıyla sıfırlar ve böylece bir [Icorprofilerınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) yöntemi.  
  
 Çoğu profil oluşturma API CLR veri yapılarını noktasıdır kimlikleri. Birçok `ICorProfilerInfo` çağrıları yalnızca bu veri yapıları bilgileri okuyun ve geri geçirin. Ancak, CLR çalıştırır ve bunu yapmak için kilitler kullanabilir şey bu yapılarında değişebilir. CLR zaten bulunduran (veya alma girişimi varsayın) bir kilit zaman profil oluşturucu iş parçacığı sağlayarak. İş parçacığı CLR yeniden girer ve daha fazla kilitleri alın veya değiştirilen sürecinde olan yapıları incelemek çalışırsa, bu yapıları tutarsız bir durumda olabilir. Kilitlenmeler ve erişim ihlalleri kolayca bu gibi durumlarda oluşabilir.  
  
 Genel olarak, ne zaman geçirme olmayan profil oluşturucu yürütür kod içinde bir [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) yöntemi ve çağrılar bir `ICorProfilerInfo` yöntemi geçerli parametrelerle, kilitlenme veya gerekir bir erişim ihlali alıyorsunuz. Örneğin, içinde çalışan Profil Oluşturucu kod [Icorprofilercallback::classloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) yöntemi isteyin sınıfı hakkında bilgi için çağırarak [Icorprofilerınfo2::getclassıdınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) yöntem. Bilgi kullanılamaz olduğunu belirtmek için bir CORPROF_E_DATAINCOMPLETE HRESULT kodu alabilirsiniz; Ancak, bunu değil kilitlenme veya erişim ihlali alırsınız. Bu çağrılar sınıfının `ICorProfilerInfo` gelen yapıldığı için zaman uyumlu olarak adlandırılan bir `ICorProfilerCallback` yöntemi.  
  
 Ancak, yönetilen bir iş parçacığı yürütmelerinin içinde değil kod bir `ICorProfilerCallback` yöntemi zaman uyumsuz bir çağrı yapmak için değerlendirilir. .NET Framework sürüm 1'da, ne zaman uyumsuz bir çağrının gerçekleşebilir belirlemek zordur. Çağrı, kilitlenme, kilitlenme veya geçersiz bir yanıt verin. .NET Framework sürüm 2.0, bu sorunu önlemenize yardımcı olmak üzere bazı basit denetimleri sunmuştur. .NET Framework güvenli olmayan bir çağırırsanız 2.0, `ICorProfilerInfo` zaman uyumsuz olarak işlev, CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT ile başarısız olur.  
  
 Genel olarak, zaman uyumsuz çağrılar güvenli değildir. Ancak, aşağıdaki yöntemlerden güvenli ve özellikle zaman uyumsuz çağrılar destekler:  
  
-   [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)  
  
-   [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)  
  
-   [Getcurrentthreadıd](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)  
  
-   [GetThreadContext](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)  
  
-   [GetThreadAppDomain](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)  
  
-   [Getfunctionfromıp](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)  
  
-   [Getfunctionınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)  
  
-   [Getfunctionınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)  
  
-   [Getcodeınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)  
  
-   [Getcodeınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)  
  
-   [Getmoduleınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)  
  
-   [Getclassıdınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)  
  
-   [Getclassıdınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)  
  
-   [Isarrayclass](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)  
  
-   [Setfunctionıdmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
  
-   [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
  
 Ek bilgi için bkz: Giriş [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE sahibiz neden](http://go.microsoft.com/fwlink/?LinkId=169156) CLR Profil oluşturma API Web günlüğündeki.  
  
## <a name="triggering-garbage-collections"></a>Tetikleyici çöp koleksiyonları  
 Bu senaryo bir geri çağırma yöntemi içinde çalışan bir profil oluşturucu içerir (örneğin, aşağıdakilerden birini `ICorProfilerCallback` yöntemleri) çöp toplama engelliyor. Profil Oluşturucu bilgilendirici bir yöntemi çağırmak çalışırsa (örneğin, bir yöntem `ICorProfilerInfo` arabirimi) çöp toplama tetikleyin, bilgilendirici yöntem CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT başarısız olur.  
  
 Aşağıdaki tabloda çöp koleksiyonları yasaklamaz geri arama yöntemleri ve çöp koleksiyonları tetikleyebilir bilgilendirme yöntemleri görüntüler. Profil Oluşturucu listelenen geri çağırma yöntemlerden birini içinde yürütür ve listelenen bilgilendirme yöntemlerden birini çağırır bilgilendirme yöntem CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT başarısız olur.  
  
|Çöp koleksiyonlarının yasaklamaz geri arama yöntemleri|Çöp koleksiyonlarının tetiklemek bilgilendirme yöntemleri|  
|------------------------------------------------------|------------------------------------------------------------|  
|[ThreadAssignedToOSThread](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)<br /><br /> [ExceptionUnwindFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)<br /><br /> [ExceptionUnwindFunctionLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)<br /><br /> [ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)<br /><br /> [ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)<br /><br /> [ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)<br /><br /> [RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)<br /><br /> [RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)<br /><br /> [RuntimeSuspendAborted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)<br /><br /> [RuntimeThreadSuspended](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)<br /><br /> [RuntimeThreadResumed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)<br /><br /> [MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)<br /><br /> [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)<br /><br /> [ObjectsAllocatedByClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)<br /><br /> [RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)<br /><br /> [HandleCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)<br /><br /> [HandleDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)<br /><br /> [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)<br /><br /> [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|[Getılfunctionbodyallocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)<br /><br /> [Setılfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)<br /><br /> [Setılınstrumentedcodemap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)<br /><br /> [ForceGC](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)<br /><br /> [GetClassFromToken](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)<br /><br /> [GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)<br /><br /> [GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)<br /><br /> [Getappdomainınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)<br /><br /> [EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)<br /><br /> [RequestProfilerDetach](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)<br /><br /> [GetAppDomainsContainingModule](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getappdomainscontainingmodule-method.md)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [ICorProfilerCallback3 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [ICorProfilerInfo3 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
