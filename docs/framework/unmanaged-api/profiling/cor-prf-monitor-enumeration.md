---
title: COR_PRF_MONITOR Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_MONITOR
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MONITOR
helpviewer_keywords:
- COR_PRF_MONITOR enumeration [.NET Framework profiling]
ms.assetid: 9294d702-b4e5-441c-a930-e63d27b86bfd
topic_type:
- apiref
ms.openlocfilehash: 1ff167121a5bb752c70edd2c5901133503326bea
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500812"
---
# <a name="cor_prf_monitor-enumeration"></a>COR_PRF_MONITOR Numaralandırması
Profil oluşturucunun abone olması için davranış, özellik veya olay belirlemek için kullanılan değerleri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
typedef enum {  
    COR_PRF_MONITOR_NONE                = 0x00000000,  
    COR_PRF_MONITOR_FUNCTION_UNLOADS    = 0x00000001,  
    COR_PRF_MONITOR_CLASS_LOADS         = 0x00000002,  
    COR_PRF_MONITOR_MODULE_LOADS        = 0x00000004,  
    COR_PRF_MONITOR_ASSEMBLY_LOADS      = 0x00000008,  
    COR_PRF_MONITOR_APPDOMAIN_LOADS     = 0x00000010,  
    COR_PRF_MONITOR_JIT_COMPILATION     = 0x00000020,  
    COR_PRF_MONITOR_EXCEPTIONS          = 0x00000040,  
    COR_PRF_MONITOR_GC                  = 0x00000080,  
    COR_PRF_MONITOR_OBJECT_ALLOCATED    = 0x00000100,  
    COR_PRF_MONITOR_THREADS             = 0x00000200,  
    COR_PRF_MONITOR_REMOTING            = 0x00000400,  
    COR_PRF_MONITOR_CODE_TRANSITIONS    = 0x00000800,  
    COR_PRF_MONITOR_ENTERLEAVE          = 0x00001000,  
    COR_PRF_MONITOR_CCW                 = 0x00002000,  
    COR_PRF_MONITOR_REMOTING_COOKIE     = 0x00004000 |
                                          COR_PRF_MONITOR_REMOTING,  
    COR_PRF_MONITOR_REMOTING_ASYNC      = 0x00008000 |
                                          COR_PRF_MONITOR_REMOTING,  
    COR_PRF_MONITOR_SUSPENDS            = 0x00010000,  
    COR_PRF_MONITOR_CACHE_SEARCHES      = 0x00020000,  
    COR_PRF_ENABLE_REJIT                = 0x00040000,  
    COR_PRF_ENABLE_INPROC_DEBUGGING     = 0x00080000,  
    COR_PRF_ENABLE_JIT_MAPS             = 0x00100000,  
    COR_PRF_DISABLE_INLINING            = 0x00200000,  
    COR_PRF_DISABLE_OPTIMIZATIONS       = 0x00400000,  
    COR_PRF_ENABLE_OBJECT_ALLOCATED     = 0x00800000,  
    COR_PRF_MONITOR_CLR_EXCEPTIONS      = 0x01000000,  
    COR_PRF_MONITOR_ALL                 = 0x0107FFFF,  
    COR_PRF_ENABLE_FUNCTION_ARGS        = 0X02000000,  
    COR_PRF_ENABLE_FUNCTION_RETVAL      = 0X04000000,  
    COR_PRF_ENABLE_FRAME_INFO           = 0X08000000,  
    COR_PRF_ENABLE_STACK_SNAPSHOT       = 0X10000000,  
    COR_PRF_USE_PROFILE_IMAGES          = 0x20000000,  
    COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST  
                                        = 0x40000000,  
    COR_PRF_DISABLE_ALL_NGEN_IMAGES     = 0x80000000,  
    COR_PRF_ALL                         = 0x8FFFFFFF,  
    COR_PRF_REQUIRE_PROFILE_IMAGE       = COR_PRF_USE_PROFILE_IMAGES |
                                          COR_PRF_MONITOR_CODE_TRANSITIONS |
                                          COR_PRF_MONITOR_ENTERLEAVE,  
    COR_PRF_ALLOWABLE_AFTER_ATTACH      = COR_PRF_MONITOR_THREADS |  
                                          COR_PRF_MONITOR_MODULE_LOADS |  
                                          COR_PRF_MONITOR_ASSEMBLY_LOADS |  
                                          COR_PRF_MONITOR_APPDOMAIN_LOADS |  
                                          COR_PRF_ENABLE_STACK_SNAPSHOT |  
                                          COR_PRF_MONITOR_GC |  
                                          COR_PRF_MONITOR_SUSPENDS |  
                                          COR_PRF_MONITOR_CLASS_LOADS |  
                                          COR_PRF_MONITOR_JIT_COMPILATION,  
    COR_PRF_MONITOR_IMMUTABLE           = COR_PRF_MONITOR_CODE_TRANSITIONS |  
                                          COR_PRF_MONITOR_REMOTING |  
                                          COR_PRF_MONITOR_REMOTING_COOKIE |  
                                          COR_PRF_MONITOR_REMOTING_ASYNC |  
                                          COR_PRF_ENABLE_REJIT |  
                                          COR_PRF_ENABLE_INPROC_DEBUGGING |  
                                          COR_PRF_ENABLE_JIT_MAPS |  
                                          COR_PRF_DISABLE_OPTIMIZATIONS |  
                                          COR_PRF_DISABLE_INLINING |  
                                          COR_PRF_ENABLE_OBJECT_ALLOCATED |  
                                          COR_PRF_ENABLE_FUNCTION_ARGS |  
                                          COR_PRF_ENABLE_FUNCTION_RETVAL |  
                                          COR_PRF_ENABLE_FRAME_INFO |  
                                          COR_PRF_USE_PROFILE_IMAGES |  
                     COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST |  
                                          COR_PRF_DISABLE_ALL_NGEN_IMAGES  
} COR_PRF_MONITOR;  
```  
  
## <a name="members"></a>Üyeler  
 Aşağıdaki bölümlerde `COR_PRF_MONITOR` kategoriye göre numaralandırma üyeleri listelenmiştir. Kategoriler şunlardır:  
  
- [Bayrak ayarlanmadı](#None)  
  
- [Geri çağırma bayrakları](#Callback)  
  
- [Özellik etkinleştirme bayrakları](#Feature)  
  
- [Yapılandırma bayrakları](#Config)  
  
- [Bileşik bayraklar](#Composite)  
  
<a name="None"></a>
### <a name="no-flags-set"></a>Bayrak ayarlanmadı  
  
|Üye|Description|  
|------------|-----------------|  
|`COR_PRF_MONITOR_NONE`|Hiçbir bayrak ayarlanmadı.|  
  
<a name="Callback"></a>
### <a name="callback-flags"></a>Geri çağırma bayrakları  
  
|Üye|Description|  
|------------|-----------------|  
|`COR_PRF_MONITOR_ALL`|Tüm geri çağırma olaylarını etkinleştirilir.|  
|`COR_PRF_MONITOR_APPDOMAIN_LOADS`|`AppDomainCreation*` `AppDomainShutdown*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki ve geri çağırmaları denetler.|  
|`COR_PRF_MONITOR_ASSEMBLY_LOADS`|`AssemblyLoad*` `AssemblyUnload*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki ve geri çağırmaları denetler.|  
|`COR_PRF_MONITOR_CACHE_SEARCHES`|`JITCachedFunctionSearch*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki geri çağırmaları denetler.<br /><br /> Bu bayrağın davranışı .NET Framework sürüm 2,0 ' de değiştirilir.|  
|`COR_PRF_MONITOR_CCW`|`COMClassicVTable*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki geri çağırmaları denetler.|  
|`COR_PRF_MONITOR_CLASS_LOADS`|`ClassLoad*` `ClassUnload*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki ve geri çağırmaları denetler.|  
|`COR_PRF_MONITOR_CLR_EXCEPTIONS`|`ExceptionCLRCatcher*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki geri çağırmaları denetler.|  
|`COR_PRF_MONITOR_CODE_TRANSITIONS`|[ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki [UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) ve [ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) geri çağırmaları denetler|  
|`COR_PRF_MONITOR_ENTERLEAVE`|`FunctionEnter*`, `FunctionLeave*` Ve `FunctionTailCall*` [profil oluşturma genel statik işlevlerini](profiling-global-static-functions.md)denetler.|  
|`COR_PRF_MONITOR_EXCEPTIONS`|[ExceptionThrown](icorprofilercallback-exceptionthrown-method.md) `ExceptionSearch*` `ExceptionOSHandler*` `ExceptionUnwind*` `ExceptionCatcher*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki exceptionatılan geri aramayı ve,, ve geri çağırmaları denetler.|  
|`COR_PRF_MONITOR_FUNCTION_UNLOADS`|[ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki [FunctionUnloadStarted](icorprofilercallback-functionunloadstarted-method.md) geri çağrısını denetler.|  
|`COR_PRF_MONITOR_GC`|Arabirimlerinizde, [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md), [MovedReferences](icorprofilercallback-movedreferences-method.md), [MovedReferences2](icorprofilercallback4-movedreferences2-method.md), [acil vınreferences](icorprofilercallback2-survivingreferences-method.md), [SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md), [ObjectReferences](icorprofilercallback-objectreferences-method.md), [ObjectsAllocatedByClass](icorprofilercallback-objectsallocatedbyclass-method.md), [RootReferences](icorprofilercallback-rootreferences-method.md), [RootReferences2](icorprofilercallback2-rootreferences2-method.md), [HandleCreated](icorprofilercallback2-handlecreated-method.md), [handleınalına](icorprofilercallback2-handledestroyed-method.md)ve [finalizeableobjectkuyruklanmış](icorprofilercallback2-finalizeableobjectqueued-method.md) geri çağırmaları kontrol eder `ICorProfilerCallback*` . `COR_PRF_MONITOR_GC`Ayrılan zaman, eşzamanlı atık toplama kapalıdır.|  
|`COR_PRF_MONITOR_JIT_COMPILATION`|`JITCompilation*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki, [jıtfunction,](icorprofilercallback-jitfunctionpitched-method.md)ve [jınkıtıl](icorprofilercallback-jitinlining-method.md) geri çağırmaları denetler.|  
|`COR_PRF_MONITOR_MODULE_LOADS`|`ModuleLoad*` `ModuleUnload*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki,, ve [ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) geri çağırmaları denetler.|  
|`COR_PRF_MONITOR_OBJECT_ALLOCATED`|[ICorProfilerCallback](icorprofilercallback-interface.md) arabiriminde [objectalchanged](icorprofilercallback-objectallocated-method.md) geri çağırma işlemini denetler.|  
|`COR_PRF_MONITOR_REMOTING`|`Remoting*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki geri çağırmaları denetler.|  
|`COR_PRF_MONITOR_REMOTING_ASYNC`|`Remoting*`Geri çağırmaların zaman uyumsuz olayları izleyip izmeyeceğini denetler.|  
|`COR_PRF_MONITOR_REMOTING_COOKIE`|Bir tanımlama bilgisinin geri çağırmaların geçirilip geçirilmediğini denetler `Remoting*` .|  
|`COR_PRF_MONITOR_SUSPENDS`|`RuntimeSuspend*` `RuntimeResume*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki,, [runtimethreadaskıya alındı](icorprofilercallback-runtimethreadsuspended-method.md)ve [runtimethreadsürdürülme](icorprofilercallback-runtimethreadresumed-method.md) geri çağırmaları denetler.|  
|`COR_PRF_MONITOR_THREADS`|[ICorProfilerCallback](icorprofilercallback-interface.md) ve [ICorProfilerCallback2](icorprofilercallback2-interface.md) arabirimlerindeki [ThreadCreated](icorprofilercallback-threadcreated-method.md), [threadyok](icorprofilercallback-threaddestroyed-method.md), [ThreadAssignedToOSThread](icorprofilercallback-threadassignedtoosthread-method.md)ve [ThreadNameChanged](icorprofilercallback2-threadnamechanged-method.md) geri çağırmaları denetler.|  
  
<a name="Feature"></a>
### <a name="feature-enabling-flags"></a>Özellik etkinleştirme bayrakları  
  
|Üye|Description|  
|------------|-----------------|  
|`COR_PRF_ENABLE_FRAME_INFO`|, `ClassID` [Getfunctionınfo2](icorprofilerinfo2-getfunctioninfo2-method.md) yöntemini `COR_PRF_FRAME_INFO` [FunctionEnter2](functionenter2-function.md) geri çağırması tarafından döndürülen bir değerle çağırarak genel bir işlev için tam olarak alınmasını mümkün bir şekilde sunar.|  
|`COR_PRF_ENABLE_FUNCTION_ARGS`|[FunctionEnter2](functionenter2-function.md) callback veya [FunctionEnter3WithInfo](functionenter3withinfo-function.md) geri çağırması ile [GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) yöntemini kullanarak bağımsız değişken izlemeyi mümkün.|  
|`COR_PRF_ENABLE_FUNCTION_RETVAL`|[FunctionLeave2](functionleave2-function.md) callback veya [Functionleave3withınfo](functionleave3withinfo-function.md) callback ve [GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) yöntemini kullanarak dönüş değerlerinin izlenmesini mümkün.|  
|`COR_PRF_ENABLE_INPROC_DEBUGGING`|Kullanım dışı.<br /><br /> İşlem hata ayıklaması desteklenmiyor. Bu bayrağın bir etkisi yoktur.|  
|`COR_PRF_ENABLE_JIT_MAPS`|Kullanım dışı.<br /><br /> Profiler 'ın [Getiltonativemapping](icorprofilerinfo-getiltonativemapping-method.md)kullanarak Il 'den yerel haritalar almasına izin verir. .NET Framework 2,0 ' den başlayarak, çalışma zamanı her zaman Il 'nin yerel haritalarını izler; Bu nedenle, bu bayrak her zaman ayarlanmış olarak değerlendirilir.|  
|`COR_PRF_ENABLE_OBJECT_ALLOCATED`|Çalışma zamanına, profil oluşturucunun nesne ayırma bildirimlerini isteyebilir bildirir. Bu bayrağın başlatma sırasında ayarlanması gerekir. Profil oluşturucunun, `COR_PRF_MONITOR_OBJECT_ALLOCATED` [Objectalkonumlandırılan](icorprofilercallback-objectallocated-method.md) geri çağırmaları almak için bayrağını daha sonra kullanmasına izin verir.|  
|`COR_PRF_ENABLE_REJIT`|[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) ve [requestdöndürülüyor](icorprofilerinfo4-requestrevert-method.md) yöntemlerine çağrıları sağlar. Profil oluşturucunun bu bayrağı başlangıçta ayarlaması gerekir.  Profil Oluşturucu bu bayrağı belirtiyorsa, Ayrıca belirtmeniz gerekir `COR_PRF_DISABLE_ALL_NGEN_IMAGES` .|  
|`COR_PRF_ENABLE_STACK_SNAPSHOT`|[DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) metoduna çağrıları sağlar.|  
  
<a name="Config"></a>
### <a name="configuration-flags"></a>Yapılandırma bayrakları  
  
|Üye|Description|  
|------------|-----------------|  
|`COR_PRF_DISABLE_ALL_NGEN_IMAGES`|Tüm yerel görüntülerin (Profil Oluşturucu gelişmiş görüntüler dahil) yüklenmesini engeller.  Bu bayrak ve `COR_PRF_USE_PROFILE_IMAGES` bayrak her ikisi de belirtildiyse, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` kullanılır.|  
|`COR_PRF_DISABLE_INLINING`|Tüm satır dışı bırakır.|  
|`COR_PRF_DISABLE_OPTIMIZATIONS`|Tüm kod iyileştirmelerini devre dışı bırakır.|  
|`COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST`|Tam zamanında (JıT) derleme sırasında ve tam güven derlemeleri için sınıf yüklenirken normalde gerçekleştirilen güvenlik saydamlığı denetimlerini devre dışı bırakır. Bu, bazı izleme işlemlerini daha kolay hale getirir.|  
|`COR_PRF_USE_PROFILE_IMAGES`|Yerel görüntü aramasının profil oluşturucu gelişmiş görüntüleri aramasına neden olur. Belirli bir derleme için profil oluşturucu gelişmiş görüntü bulunamazsa, ortak dil çalışma zamanı bu derleme için JıT 'e geri döner. Bu bayrak ve `COR_PRF_DISABLE_ALL_NGEN_IMAGES` bayrak her ikisi de belirtildiyse, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` kullanılır.|  
  
<a name="Composite"></a>
### <a name="composite-flags"></a>Bileşik bayraklar  
  
|Üye|Description|  
|------------|-----------------|  
|`COR_PRF_ALL`|Tüm `COR_PRF_MONITOR` bayrak değerlerini temsil eder.|  
|`COR_PRF_ALLOWABLE_AFTER_ATTACH`|`COR_PRF_MONITOR`Profil Oluşturucu çalışan bir uygulamaya eklendikten sonra ayarlanmayacak tüm bayrakları temsil eder. Söz dizimi bölümü, bu bit maskesi içinde bulunan bireysel bayrakları gösterir.|  
|`COR_PRF_MONITOR_ALL`|Tüm geri çağırma olaylarını etkinleştirilir.|  
|`COR_PRF_MONITOR_IMMUTABLE`|`COR_PRF_MONITOR`Yalnızca başlatma sırasında ayarlanabilir tüm bayrakları temsil eder. Başlatma işleminden sonra bu bayrakların herhangi birini değiştirme girişimi, `HRESULT` hatayı gösteren bir değer döndürür.|  
|`COR_PRF_REQUIRE_PROFILE_IMAGE`|`COR_PRF_MONITOR`Profil ile geliştirilmiş görüntüler gerektiren tüm bayrakları temsil eder.|  
  
## <a name="remarks"></a>Açıklamalar  
 `COR_PRF_MONITOR`Ortak dil çalışma zamanının profil oluşturucuya yaptığı olay bildirimlerini tanımlamak Için [ICorProfilerInfo:: GetEventMask](icorprofilerinfo-geteventmask-method.md) ve [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemleriyle bir değer kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Sabit Listeleri](profiling-enumerations.md)
- [GetEventMask Yöntemi](icorprofilerinfo-geteventmask-method.md)
- [SetEventMask Yöntemi](icorprofilerinfo-seteventmask-method.md)
