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
ms.openlocfilehash: b6c3dc78b9c503747c7a2d404706eb797790b931
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175206"
---
# <a name="cor_prf_monitor-enumeration"></a>COR_PRF_MONITOR Numaralandırması
Profiloluşturucunun abone olmak istediği davranışları, yetenekleri veya olayları belirtmek için kullanılan değerleri içerir.  
  
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
 Aşağıdaki bölümlerde `COR_PRF_MONITOR` numaralandırma üyeleri kategoriye göre listeleneb.) Kategoriler şunlardır:  
  
- [Bayrak lar ayarlı değil](#None)  
  
- [Geri arama bayrakları](#Callback)  
  
- [Özellik etkinleştirme bayrakları](#Feature)  
  
- [Yapılandırma bayrakları](#Config)  
  
- [Bileşik bayraklar](#Composite)  
  
<a name="None"></a>
### <a name="no-flags-set"></a>Bayrak lar ayarlı değil  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`COR_PRF_MONITOR_NONE`|Bayrak lar ayarlı değil.|  
  
<a name="Callback"></a>
### <a name="callback-flags"></a>Geri arama bayrakları  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`COR_PRF_MONITOR_ALL`|Tüm geri arama olaylarını etkinleştirir.|  
|`COR_PRF_MONITOR_APPDOMAIN_LOADS`|`AppDomainCreation*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki geri aramaları ve `AppDomainShutdown*` geri aramaları denetler.|  
|`COR_PRF_MONITOR_ASSEMBLY_LOADS`|`AssemblyLoad*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki geri aramaları ve `AssemblyUnload*` geri aramaları denetler.|  
|`COR_PRF_MONITOR_CACHE_SEARCHES`|`JITCachedFunctionSearch*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki geri aramaları denetler.<br /><br /> Bu bayrağın davranışı .NET Framework sürüm 2.0'da değiştirilir.|  
|`COR_PRF_MONITOR_CCW`|`COMClassicVTable*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki geri aramaları denetler.|  
|`COR_PRF_MONITOR_CLASS_LOADS`|`ClassLoad*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki geri aramaları ve `ClassUnload*` geri aramaları denetler.|  
|`COR_PRF_MONITOR_CLR_EXCEPTIONS`|`ExceptionCLRCatcher*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki geri aramaları denetler.|  
|`COR_PRF_MONITOR_CODE_TRANSITIONS`|[ICorProfilerCallback](icorprofilercallback-interface.md) arabiriminde [YönetilmeyenToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) ve [ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) geri aramaları denetler|  
|`COR_PRF_MONITOR_ENTERLEAVE`|Genel `FunctionEnter*`statik `FunctionLeave*`işlevleri `FunctionTailCall*`ve [profil oluşturmayı denetler.](profiling-global-static-functions.md)|  
|`COR_PRF_MONITOR_EXCEPTIONS`|[ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki `ExceptionUnwind*` [ExceptionThrown](icorprofilercallback-exceptionthrown-method.md) geri aramasını ve `ExceptionSearch*` `ExceptionOSHandler*` `ExceptionCatcher*` geri aramaları denetler.|  
|`COR_PRF_MONITOR_FUNCTION_UNLOADS`|[ICorProfilerCallback](icorprofilercallback-interface.md) arabiriminde [FunctionUnloadStarted](icorprofilercallback-functionunloadstarted-method.md) geri çağırmasını denetler.|  
|`COR_PRF_MONITOR_GC`|Çöp Toplama Başlatıldı `ICorProfilerCallback*` , [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionstarted-method.md), [MovedReferences](icorprofilercallback-movedreferences-method.md), [MovedReferences2](icorprofilercallback4-movedreferences2-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) [SurvivingReferences2](icorprofilercallback2-survivingreferences-method.md), [ObjectReferences](icorprofilercallback-objectreferences-method.md), [ObjectsAllocatedByClass](icorprofilercallback-objectsallocatedbyclass-method.md), [RootReferences](icorprofilercallback-rootreferences-method.md), [RootReferences2](icorprofilercallback2-rootreferences2-method.md), [HandleCreated](icorprofilercallback2-handlecreated-method.md), [HandleDestroyed](icorprofilercallback2-handledestroyed-method.md), ve [FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) aramaları arayüzlerde. [SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md) Tahsis `COR_PRF_MONITOR_GC` edildiğinde, eşzamanlı çöp toplama kapatılır.|  
|`COR_PRF_MONITOR_JIT_COMPILATION`|`JITCompilation*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabiriminde [JITFunctionPitched](icorprofilercallback-jitfunctionpitched-method.md)ve [JITInlining](icorprofilercallback-jitinlining-method.md) geri aramaları denetler.|  
|`COR_PRF_MONITOR_MODULE_LOADS`|`ModuleLoad*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki [ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) geri aramalarını denetler. `ModuleUnload*`|  
|`COR_PRF_MONITOR_OBJECT_ALLOCATED`|[ICorProfilerCallback](icorprofilercallback-interface.md) arabiriminde [ObjectAllocated](icorprofilercallback-objectallocated-method.md) geri aramasını denetler.|  
|`COR_PRF_MONITOR_REMOTING`|`Remoting*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabirimindeki geri aramaları denetler.|  
|`COR_PRF_MONITOR_REMOTING_ASYNC`|Geri aramaların `Remoting*` eşzamanlı olayları izleyip izlemeyeceğini denetler.|  
|`COR_PRF_MONITOR_REMOTING_COOKIE`|Bir çerezin `Remoting*` geri aramalara geçirilip geçirilemeyeceğini denetler.|  
|`COR_PRF_MONITOR_SUSPENDS`|`RuntimeSuspend*` [ICorProfilerCallback](icorprofilercallback-interface.md) arabiriminde [RuntimeThreadSuspended](icorprofilercallback-runtimethreadsuspended-method.md)ve [RuntimeThreadResumed](icorprofilercallback-runtimethreadresumed-method.md) geri aramaları denetler. `RuntimeResume*`|  
|`COR_PRF_MONITOR_THREADS`|[ICorProfilerCallback ve ICorProfilerCallback2](icorprofilercallback-interface.md) arayüzlerinde [ThreadCreated](icorprofilercallback-threadcreated-method.md), [ICorProfilerCallback2](icorprofilercallback2-interface.md) [ThreadAssignedToOSThread](icorprofilercallback-threadassignedtoosthread-method.md)ve [ThreadNameChanged](icorprofilercallback2-threadnamechanged-method.md) geri aramaları kontrol eder. [ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md)|  
  
<a name="Feature"></a>
### <a name="feature-enabling-flags"></a>Özellik etkinleştirme bayrakları  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`COR_PRF_ENABLE_FRAME_INFO`|[FunctionEnter2](functionenter2-function.md) geri çağırması tarafından `ClassID` döndürülen bir değerle [GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) `COR_PRF_FRAME_INFO` yöntemini arayarak genel bir işlev için tam bir işlev alınmasını sağlar.|  
|`COR_PRF_ENABLE_FUNCTION_ARGS`|[FunctionEnter2](functionenter2-function.md) geri çağırma veya [FunctionEnter3WithInfo](functionenter3withinfo-function.md) geri arama ve [GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) yöntemini kullanarak bağımsız değişken izleme sağlar.|  
|`COR_PRF_ENABLE_FUNCTION_RETVAL`|[FunctionLeave2](functionleave2-function.md) geri çağırma veya [FunctionLeave3WithInfo](functionleave3withinfo-function.md) geri arama ve [GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) yöntemini kullanarak iade değerlerinin izlenmesini sağlar.|  
|`COR_PRF_ENABLE_INPROC_DEBUGGING`|Kullanım dışı.<br /><br /> İşlemde hata ayıklama desteklenmez. Bu bayrağın bir etkisi yok.|  
|`COR_PRF_ENABLE_JIT_MAPS`|Kullanım dışı.<br /><br /> Profiloluşturucunun [GetILToNativeMapping'i](icorprofilerinfo-getiltonativemapping-method.md)kullanarak IL-to-native haritaları elde etmesini sağlar. .NET Framework 2.0 ile başlayarak, çalışma zamanı her zaman IL-to-native haritaları izler; bu nedenle, bu bayrak her zaman ayarlanmış olarak kabul edilir.|  
|`COR_PRF_ENABLE_OBJECT_ALLOCATED`|Profil oluşturucunun nesne ayırma bildirimleri isteyebileceğini çalışma saatini bildirir. Bu bayrak başlatma sırasında ayarlanmalıdır. Profiloluşturucunun objectallocated geri `COR_PRF_MONITOR_OBJECT_ALLOCATED` aramaları [ObjectAllocated](icorprofilercallback-objectallocated-method.md) almak için bayrağı daha sonra kullanmasına olanak tanır.|  
|`COR_PRF_ENABLE_REJIT`|[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) ve [RequestRevert](icorprofilerinfo4-requestrevert-method.md) yöntemlerine çağrı yapılmasını sağlar. Profil oluşturucu bu bayrağı başlangıç üzerine ayarlamalıdır.  Profil oluşturucu bu bayrağı belirtirse, `COR_PRF_DISABLE_ALL_NGEN_IMAGES`bunu da belirtmesi gerekir.|  
|`COR_PRF_ENABLE_STACK_SNAPSHOT`|[DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) yöntemine çağrı yapılmasını sağlar.|  
  
<a name="Config"></a>
### <a name="configuration-flags"></a>Yapılandırma bayrakları  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`COR_PRF_DISABLE_ALL_NGEN_IMAGES`|Tüm yerel görüntülerin (profil oluşturucutarafından geliştirilmiş görüntüler dahil) yüklenmesiengellenir.  Bu bayrak ve `COR_PRF_USE_PROFILE_IMAGES` bayrak her `COR_PRF_DISABLE_ALL_NGEN_IMAGES` ikisi de belirtilirse, kullanılır.|  
|`COR_PRF_DISABLE_INLINING`|Tüm inlining devre dışı kılabilir.|  
|`COR_PRF_DISABLE_OPTIMIZATIONS`|Tüm kod optimizasyonlarını devre dışı kılabilir.|  
|`COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST`|Tam güven derlemeleri için normalde tam zamanında (JIT) derleme ve sınıf yüklemesi sırasında yapılan güvenlik saydamlık denetimlerini devre dışı bırakır. Bu, bazı enstrümantasyon gerçekleştirmeyi kolaylaştırabilir.|  
|`COR_PRF_USE_PROFILE_IMAGES`|Yerel görüntü aramasının profil oluşturucutarafından geliştirilmiş görüntüler aramasına neden olur. Belirli bir derleme için profil oluşturucu tarafından geliştirilmiş görüntü bulunmazsa, ortak dil çalışma süresi bu derleme için JIT'ye geri döner. Bu bayrak ve `COR_PRF_DISABLE_ALL_NGEN_IMAGES` bayrak her `COR_PRF_DISABLE_ALL_NGEN_IMAGES` ikisi de belirtilirse, kullanılır.|  
  
<a name="Composite"></a>
### <a name="composite-flags"></a>Bileşik bayraklar  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`COR_PRF_ALL`|Tüm `COR_PRF_MONITOR` bayrak değerlerini temsil eder.|  
|`COR_PRF_ALLOWABLE_AFTER_ATTACH`|Profil `COR_PRF_MONITOR` oluşturucu çalışan bir uygulamaya iliştirildikten sonra ayarlanabilecek tüm bayrakları temsil eder. Sözdizimi bölümü, bu bitmaskesinde bulunan tek tek bayrakları gösterir.|  
|`COR_PRF_MONITOR_ALL`|Tüm geri arama olaylarını etkinleştirir.|  
|`COR_PRF_MONITOR_IMMUTABLE`|Yalnızca `COR_PRF_MONITOR` başlatma sırasında ayarlanabilen tüm bayrakları temsil eder. Başlatmadan sonra bu bayraklardan herhangi `HRESULT` birini değiştirmeye çalışmak, başarısızlığı gösteren bir değer döndürür.|  
|`COR_PRF_REQUIRE_PROFILE_IMAGE`|Profille `COR_PRF_MONITOR` geliştirilmiş görüntüler gerektiren tüm bayrakları temsil eder.|  
  
## <a name="remarks"></a>Açıklamalar  
 `COR_PRF_MONITOR` [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) ve [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemleri, ortak dil çalışma süresinin profil oluşturucuya yaptığı olay bildirimlerini tanımlamak için kullanılır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorProf.idl, CorProf.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Sabit Listeleri](profiling-enumerations.md)
- [GetEventMask Yöntemi](icorprofilerinfo-geteventmask-method.md)
- [SetEventMask Yöntemi](icorprofilerinfo-seteventmask-method.md)
