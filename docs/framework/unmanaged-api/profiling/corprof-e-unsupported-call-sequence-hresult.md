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
ms.openlocfilehash: a8c65ec6acc5ff87501392eb41909fcd6ebf1e3f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59092147"
---
# <a name="corprofeunsupportedcallsequence-hresult"></a>CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT .NET Framework 2.0 sürümünde kullanıma sunulmuştur. [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] İki senaryoda Bu HRESULT döndürür:  
  
-   Geçirme profil oluşturucu bir iş parçacığının zorla sıfırlar. böylece iş parçacığı tutarsız bir durumda olan yapılarına erişmeye bağlam rastgele bir zaman kaydedersiniz.  
  
-   Bir geri çağırma yönteminden atık toplama işlemini tetikleyen bilgilendirici bir yöntemi çağırmak bir profil oluşturucu çalıştığında, çöp toplama engelliyor.  
  
 Bu iki senaryo, aşağıdaki bölümlerde ele alınmıştır.  
  
## <a name="hijacking-profilers"></a>Profil oluşturucular ele geçirme  
 (Bu senaryoda geçirme olmayan profil oluşturucular Bu HRESULT görebileceğiniz durumları olsa, profil oluşturucular ele geçirme ile öncelikle bir sorundur.)  
  
 İş parçacığı profil oluşturucu kodu girin veya ortak dil çalışma zamanı (CLR) yeniden girmeniz Bu senaryoda, geçirme profil oluşturucu zorla bir iş parçacığının kayıt bağlam rastgele bir zaman aracılığıyla sıfırlar ve böylece bir [Icorprofilerınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) yöntemi.  
  
 Çoğu kimlikleri profil oluşturma API'ın CLR veri yapılarını noktası sağlar. Birçok `ICorProfilerInfo` çağrıları yalnızca bu veri yapılarının bilgileri okuyun ve bunları geri geçirin. Ancak, CLR çalıştırır ve bunu yapmak için kilit kullanabilirsiniz Bu yapıları şeyler değişebilir. CLR zaten bulunduran (veya alma girişimi olduğunu varsayın) bir kilit zaman profil oluşturucu iş parçacığı ele. Bu yapılar, iş parçacığı CLR yeniden girer ve daha fazla kilitler veya değiştiren sürecinde olan yapıları İnceleme çalışırsa, tutarsız bir durumda olabilir. Kilitlenmeler ve erişim İhlallerinde kolayca bu gibi durumlarda gerçekleşebilir.  
  
 Genel olarak, ne zaman geçirme profil oluşturucu yürütür kod içinde bir [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) yöntemi ve çağırıyor bir `ICorProfilerInfo` yöntemi geçerli parametrelerle, kilitlenmeye veya gerekir bir erişim ihlali alıyorsunuz. Örneğin, içinde çalışan kod profil oluşturucu [Icorprofilercallback::classloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) yöntemi isteyebilir sınıfı hakkında daha fazla bilgi için çağırarak [Icorprofilerınfo2::getclassıdınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) yöntem. Kod bilgilerinin kullanılabilir olduğunu belirtmek için CORPROF_E_DATAINCOMPLETE HRESULT alabilirsiniz; Ancak, görüntülenecektir değil kilitlenme veya erişim ihlali alırsınız. Bu sınıfı çağırıyor `ICorProfilerInfo` gelen gerçekleştirildiğinden zaman uyumlu olarak adlandırılan bir `ICorProfilerCallback` yöntemi.  
  
 Ancak, bir yönetilen iş parçacığı, yürütür içinde olmayan kodu bir `ICorProfilerCallback` yöntemi zaman uyumsuz bir çağrı yapmak için olarak kabul edilir. .NET Framework sürüm 1'da, ne zaman uyumsuz bir çağrı içinde gerçekleşebilir belirlemek zor oluyordu. Çağrı yüklenemedi, kilitlenme, kilitlenme veya geçersiz bir yanıt verin. .NET Framework 2.0 sürümünde bu sorunu önlemek için bazı basit denetimler kullanıma sunuldu. .NET Framework güvenli olmayan bir çağırırsanız 2.0, `ICorProfilerInfo` zaman uyumsuz işlev, CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT ile başarısız olur.  
  
 Genel olarak, zaman uyumsuz çağrıları güvenli değildir. Ancak, aşağıdaki yöntemlerden güvenlidir ve özellikle zaman uyumsuz çağrıları destekler:  
  
-   [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)  
  
-   [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)  
  
-   [Getcurrentthreadıd](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)  
  
-   [GetThreadContext](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)  
  
-   [GetThreadAppDomain](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)  
  
-   [GetFunctionFromIP](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)  
  
-   [GetFunctionInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)  
  
-   [GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)  
  
-   [Getcodeınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)  
  
-   [Getcodeınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)  
  
-   [Getmoduleınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)  
  
-   [GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)  
  
-   [GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)  
  
-   [Isarrayclass](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)  
  
-   [Setfunctionıdmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
  
-   [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
  
 Giriş ek bilgi için bkz. [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE sahibiz neden](https://go.microsoft.com/fwlink/?LinkId=169156) CLR Profil oluşturma API blogunda.  
  
## <a name="triggering-garbage-collections"></a>Tetikleyici çöp koleksiyonları  
 Bu senaryo, bir geri çağırma yöntemi içinde çalışan bir profil oluşturucu içerir (örneğin, biri `ICorProfilerCallback` yöntemleri), çöp toplama engelliyor. Profil Oluşturucu bilgi yöntemi çağırmak çalışırsa (örneğin, bir yöntem `ICorProfilerInfo` arabirimi) çöp toplama tetikleyen, bilgi yöntemi ile bir CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT başarısız olur.  
  
 Aşağıdaki tabloda, atık toplamaları yasaklayabilme geri çağırma yöntemleri ve atık toplamaları tetikleyebilir bilgilendirici yöntemleri görüntüler. Profil Oluşturucu listelenen geri çağırma yöntemlerine biri içinde yürütür ve listelenen bilgilendirici yöntemi çağıran bir CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT bu bilgi yöntemi başarısız olur.  
  
|Atık toplama yasaklayabilme geri çağırma yöntemleri|Çöp toplama tetikleyen bilgilendirici yöntemleri|  
|------------------------------------------------------|------------------------------------------------------------|  
|[ThreadAssignedToOSThread](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)<br /><br /> [ExceptionUnwindFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)<br /><br /> [ExceptionUnwindFunctionLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)<br /><br /> [ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)<br /><br /> [ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)<br /><br /> [ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)<br /><br /> [RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)<br /><br /> [RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)<br /><br /> [RuntimeSuspendAborted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)<br /><br /> [RuntimeThreadSuspended](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)<br /><br /> [RuntimeThreadResumed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)<br /><br /> [MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)<br /><br /> [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)<br /><br /> [ObjectsAllocatedByClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)<br /><br /> [RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)<br /><br /> [HandleCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)<br /><br /> [HandleDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)<br /><br /> [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)<br /><br /> [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|[GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)<br /><br /> [Setılfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)<br /><br /> [Setılınstrumentedcodemap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)<br /><br /> [ForceGC](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)<br /><br /> [GetClassFromToken](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)<br /><br /> [GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)<br /><br /> [GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)<br /><br /> [GetAppDomainInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)<br /><br /> [EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)<br /><br /> [RequestProfilerDetach](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)<br /><br /> [GetAppDomainsContainingModule](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getappdomainscontainingmodule-method.md)|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [ICorProfilerCallback3 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [ICorProfilerInfo3 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
