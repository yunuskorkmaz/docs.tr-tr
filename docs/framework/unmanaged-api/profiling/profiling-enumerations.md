---
title: Profil Oluşturma Numaralandırmaları
ms.date: 03/30/2017
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
ms.openlocfilehash: bc90743fb348c31bd2f7487c1573ec38a43bd3af
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447454"
---
# <a name="profiling-enumerations"></a>Profil Oluşturma Numaralandırmaları
Bu bölümde profil oluşturma API 'sinin kullandığı yönetilmeyen numaralandırmalar açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [COR_PRF_CLAUSE_TYPE Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)  
 Kodun yalnızca girdiği veya solundaki özel durum yan tümcesinin türünü gösterir.  
  
 [COR_PRF_CODEGEN_FLAGS Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)  
 [ICorProfilerFunctionControl:: SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) yöntemiyle ayarlanabilmesi için kod oluşturma bayraklarını tanımlar.  
  
 [COR_PRF_FINALIZER_FLAGS Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)  
 Bir nesne için sonlandırıcıyı açıklar.  
  
 [COR_PRF_GC_GENERATION Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)  
 Çöp toplama oluşturmayı tanımlar.  
  
 [COR_PRF_GC_REASON Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)  
 Çöp toplamanın oluşma nedenini gösterir.  
  
 [COR_PRF_GC_ROOT_FLAGS Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)  
 Çöp toplayıcı kökünün özelliklerini gösterir.  
  
 [COR_PRF_GC_ROOT_KIND Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)  
 [ICorProfilerCallback2:: RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) geri çağırması tarafından sunulan çöp toplayıcı kökünün türünü gösterir.  
  
 [COR_PRF_HIGH_MONITOR Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)  
 , Profil oluşturucunun, yüklenirken [ICorProfilerInfo5:: SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metoduna belirtmesinin [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) numaralandırmasında bulunanlara ek olarak bayraklar sağlar.  
  
 [COR_PRF_JIT_CACHE Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)  
 Önbelleğe alınmış işlev aramasının sonucunu gösterir.  
  
 [COR_PRF_MISC Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-misc-enumeration.md)  
 Özel tanımlayıcılar belirten sabit değerleri içerir.  
  
 [COR_PRF_MODULE_FLAGS Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)  
 Modülün özelliklerini belirtir.  
  
 [COR_PRF_MONITOR Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 Profil oluşturucunun abone olması için davranış, özellik veya olay belirlemek için kullanılan değerleri içerir.  
  
 [COR_PRF_RUNTIME_TYPE Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-runtime-type-enumeration.md)  
 Ortak dil çalışma zamanının sürümünü gösteren değerleri içerir.  
  
 [COR_PRF_SNAPSHOT_INFO Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)  
 Profiler 'ın `StackSnapshotCallback` işlevine yapılan her çağrıda bir yığın anlık görüntüsüne ne kadar veri geçirileceğini belirtir.  
  
 [COR_PRF_STATIC_TYPE Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)  
 Bir alanın statik olup olmadığını ve bu durumda alan için geçerli olan statik kaliteyi gösterir.  
  
 [COR_PRF_SUSPEND_REASON Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md)  
 Çalışma zamanının askıya alınma nedenini gösterir.  
  
 [COR_PRF_TRANSITION_REASON Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)  
 Yönetilmesinin yönetilmeyen koda veya tam tersi bir geçişin sebebini gösterir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Profil Oluşturmaya Genel Bakış](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [Profil Oluşturma Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [Profil Oluşturma Yapıları](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
