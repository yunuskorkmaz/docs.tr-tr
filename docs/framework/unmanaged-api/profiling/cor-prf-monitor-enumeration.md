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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dbb39eb768069a737f3f89c771bf02fd6bc0c3b4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102407"
---
# <a name="corprfmonitor-enumeration"></a>COR_PRF_MONITOR Numaralandırması
Davranış, özellikleri veya olayları profil oluşturucu abone olmak isteyen belirtmek için kullanılan değerleri içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
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
 Aşağıdaki bölümlerde liste `COR_PRF_MONITOR` numaralandırma üyelerini kategoriye göre. Kategorileri şunlardır:  
  
-   [Bayrak ayarlanmadı](#None)  
  
-   [Geri çağırma bayrakları](#Callback)  
  
-   [Özellik etkinleştirme bayrakları](#Feature)  
  
-   [Yapılandırma bayrakları](#Config)  
  
-   [Bileşik bayrakları](#Composite)  
  
<a name="None"></a>   
### <a name="no-flags-set"></a>Bayrak ayarlanmadı  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`COR_PRF_MONITOR_NONE`|Hiçbir bayrakları ayarlanmış.|  
  
<a name="Callback"></a>   
### <a name="callback-flags"></a>Geri çağırma bayrakları  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`COR_PRF_MONITOR_ALL`|Tüm geri çağırma olayları sağlar.|  
|`COR_PRF_MONITOR_APPDOMAIN_LOADS`|Denetimleri `AppDomainCreation*` ve `AppDomainShutdown*` içindeki geri çağırmalar [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) arabirimi.|  
|`COR_PRF_MONITOR_ASSEMBLY_LOADS`|Denetimleri `AssemblyLoad*` ve `AssemblyUnload*` içindeki geri çağırmalar [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) arabirimi.|  
|`COR_PRF_MONITOR_CACHE_SEARCHES`|Denetimleri `JITCachedFunctionSearch*` içindeki geri çağırmalar [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) arabirimi.<br /><br /> Bu bayrak davranışını .NET Framework 2.0 sürümünde değiştirilir.|  
|`COR_PRF_MONITOR_CCW`|Denetimleri `COMClassicVTable*` içindeki geri çağırmalar [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) arabirimi.|  
|`COR_PRF_MONITOR_CLASS_LOADS`|Denetimleri `ClassLoad*` ve `ClassUnload*` içindeki geri çağırmalar [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) arabirimi.|  
|`COR_PRF_MONITOR_CLR_EXCEPTIONS`|Denetimleri `ExceptionCLRCatcher*` içindeki geri çağırmalar [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) arabirimi.|  
|`COR_PRF_MONITOR_CODE_TRANSITIONS`|Denetimleri [UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) ve [ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) içindeki geri çağırmalar [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) arabirimi|  
|`COR_PRF_MONITOR_ENTERLEAVE`|Denetimleri `FunctionEnter*`, `FunctionLeave*`, ve `FunctionTailCall*` [profil oluşturma genel statik işlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md).|  
|`COR_PRF_MONITOR_EXCEPTIONS`|Denetimleri [ExceptionThrown](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md) geri çağırma ve `ExceptionSearch*`, `ExceptionOSHandler*`, `ExceptionUnwind*`, ve `ExceptionCatcher*` içindeki geri çağırmalar [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) arabirimi.|  
|`COR_PRF_MONITOR_FUNCTION_UNLOADS`|Denetimleri [FunctionUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md) geri [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) arabirimi.|  
|`COR_PRF_MONITOR_GC`|Denetimleri [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md), [MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md), [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md), [ SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md), [SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md), [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), [ObjectsAllocatedByClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md), [ RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md), [RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md), [HandleCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md), [HandleDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md), ve [FinalizeableObjectQueued ](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) içindeki geri çağırmalar `ICorProfilerCallback*` arabirimleri.|  
|`COR_PRF_MONITOR_JIT_COMPILATION`|Denetimleri `JITCompilation*`, [Jıtfunctionpitched](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md), ve [Jıtınlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) içindeki geri çağırmalar [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) arabirimi.|  
|`COR_PRF_MONITOR_MODULE_LOADS`|Denetimleri `ModuleLoad*`, `ModuleUnload*`, ve [ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) içindeki geri çağırmalar [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) arabirimi.|  
|`COR_PRF_MONITOR_OBJECT_ALLOCATED`|Denetimleri [ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md) geri [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) arabirimi.|  
|`COR_PRF_MONITOR_REMOTING`|Denetimleri `Remoting*` içindeki geri çağırmalar [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) arabirimi.|  
|`COR_PRF_MONITOR_REMOTING_ASYNC`|Denetimleri olmadığını `Remoting*` geri çağırmaları, zaman uyumsuz olaylarını izleyecek.|  
|`COR_PRF_MONITOR_REMOTING_COOKIE`|Bir tanımlama bilgisi için geçip geçmediğini denetler `Remoting*` geri çağırmalar.|  
|`COR_PRF_MONITOR_SUSPENDS`|Denetimleri `RuntimeSuspend*`, `RuntimeResume*`, [RuntimeThreadSuspended](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md), ve [RuntimeThreadResumed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md) içindeki geri çağırmalar [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) arabirimi.|  
|`COR_PRF_MONITOR_THREADS`|Denetimleri [ThreadCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md), [ThreadDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md), [ThreadAssignedToOSThread](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md), ve [ThreadNameChanged](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md) içinde geri çağırmaları [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) ve [Icorprofilercallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) arabirimleri.|  
  
<a name="Feature"></a>   
### <a name="feature-enabling-flags"></a>Özellik etkinleştirme bayrakları  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`COR_PRF_ENABLE_FRAME_INFO`|Bir tam alınmasını sağlayan `ClassID` çağırarak genel bir işlev için [Getfunctionınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) yöntemi ile bir `COR_PRF_FRAME_INFO` tarafından döndürülen değer [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) geri çağırma.|  
|`COR_PRF_ENABLE_FUNCTION_ARGS`|Etkinleştirir, izleme bağımsız değişkenini kullanarak [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) geri çağırma veya [Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) geri çağırma ve [Getfunctionenter3ınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) yöntemi.|  
|`COR_PRF_ENABLE_FUNCTION_RETVAL`|Dönüş değerleri kullanarak izlemeyi etkinleştirir [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) geri çağırma veya [Functionleave3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) geri çağırma ve [Getfunctionleave3ınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) yöntemi.|  
|`COR_PRF_ENABLE_INPROC_DEBUGGING`|Kullanım dışı.<br /><br /> İşlemde hata ayıklama desteklenmiyor. Bu bayrağın hiçbir etkisi olmaz.|  
|`COR_PRF_ENABLE_JIT_MAPS`|Kullanım dışı.<br /><br /> IL yerel eşlemeleri kullanarak almak profil oluşturucu sağlayan [Getıltonativemapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md). .NET Framework 2.0 ile başlayarak, çalışma zamanı her zaman bir IL yerel haritalar izler; Bu nedenle, bu bayrağı ayarlamak için her zaman değerlendirilir.|  
|`COR_PRF_ENABLE_OBJECT_ALLOCATED`|Çalışma zamanı, profil oluşturucu nesne ayırma bildirimleri isteyebilirsiniz bildirir. Bu bayrak, başlatma sırasında ayarlamanız gerekir. Daha sonra kullanmak profil oluşturucu sağlayan `COR_PRF_MONITOR_OBJECT_ALLOCATED` almak için bayrağı [ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md) geri çağırmalar.|  
|`COR_PRF_ENABLE_REJIT`|Çağrıları etkinleştirir [Requestrejıt](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) ve [RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) yöntemleri. Profil Oluşturucu Bu bayrak, başlangıçta ayarlamanız gerekir.  Profil Oluşturucu bu bayrağı belirtirse, bu da belirtmeniz gerekir `COR_PRF_DISABLE_ALL_NGEN_IMAGES`.|  
|`COR_PRF_ENABLE_STACK_SNAPSHOT`|Çağrıları etkinleştirir [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) yöntemi.|  
  
<a name="Config"></a>   
### <a name="configuration-flags"></a>Yapılandırma bayrakları  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`COR_PRF_DISABLE_ALL_NGEN_IMAGES`|(Profil oluşturucunun geliştirdiği Görüntüleriniz dahil) tüm yerel görüntüleri yüklenmesini engeller.  Varsa bu bayrağı ve `COR_PRF_USE_PROFILE_IMAGES` bayrağı her ikisi de belirtilirse, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` kullanılır.|  
|`COR_PRF_DISABLE_INLINING`|Tüm satır içi kullanım devre dışı bırakır.|  
|`COR_PRF_DISABLE_OPTIMIZATIONS`|Tüm kod iyileştirmeleri devre dışı bırakır.|  
|`COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST`|Just-ın-time (JIT) derleme ve sınıf tam güven derlemeleri için yükleme sırasında normal olarak yapılan güvenlik saydamlık denetimleri devre dışı bırakır. Bu bazı izleme gerçekleştirmek daha kolay hale getirebilirsiniz.|  
|`COR_PRF_USE_PROFILE_IMAGES`|Profil oluşturucunun geliştirdiği görüntüler için yerel görüntü arama neden olur. Profil oluşturucunun geliştirdiği görüntü için verilen bir derlemeye bulunursa, ortak dil çalışma zamanı JIT için o derleme için geri döner. Varsa bu bayrağı ve `COR_PRF_DISABLE_ALL_NGEN_IMAGES` bayrağı her ikisi de belirtilirse, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` kullanılır.|  
  
<a name="Composite"></a>   
### <a name="composite-flags"></a>Bileşik bayrakları  
  
|Üye|Açıklama|  
|------------|-----------------|  
|`COR_PRF_ALL`|Tüm gösteren `COR_PRF_MONITOR` bayrak değerleri.|  
|`COR_PRF_ALLOWABLE_AFTER_ATTACH`|Tüm gösteren `COR_PRF_MONITOR` profil oluşturucuyu çalışan bir uygulamaya bağlandıktan sonra ayarlanabilir bayrakları. Söz dizimi bölümünün bu bit maskesi içinde mevcut olan tek bayrakları belirtir.|  
|`COR_PRF_MONITOR_ALL`|Tüm geri çağırma olayları sağlar.|  
|`COR_PRF_MONITOR_IMMUTABLE`|Tüm gösteren `COR_PRF_MONITOR` yalnızca başlatma sırasında ayarlanabilir bayrakları. Başlatma döndürdükten sonra bu bayraklar hiçbirini değiştirilmeye çalışılırken bir `HRESULT` başarısızlığı gösteren değer.|  
|`COR_PRF_REQUIRE_PROFILE_IMAGE`|Tüm gösteren `COR_PRF_MONITOR` profili Gelişmiş görüntüleri gerektiren bayrakları.|  
  
## <a name="remarks"></a>Açıklamalar  
 A `COR_PRF_MONITOR` değeri ile kullanılan [Icorprofilerınfo::geteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) ve [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) ortak dil çalışma zamanı yapar olay bildirimleri tanımlamak için yöntemleri Profil Oluşturucu.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Sabit Listeleri](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [GetEventMask Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)
- [SetEventMask Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)
