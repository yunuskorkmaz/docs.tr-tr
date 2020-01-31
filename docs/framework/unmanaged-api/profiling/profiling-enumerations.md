---
title: Profil Oluşturma Numaralandırmaları
ms.date: 03/30/2017
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
ms.openlocfilehash: 1a9781fa1b4b608152faa7d5edc80bd4866f0c81
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868141"
---
# <a name="profiling-enumerations"></a>Profil Oluşturma Numaralandırmaları
Bu bölümde profil oluşturma API 'sinin kullandığı yönetilmeyen numaralandırmalar açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [COR_PRF_CLAUSE_TYPE Sabit Listesi](cor-prf-clause-type-enumeration.md)  
 Kodun yalnızca girdiği veya solundaki özel durum yan tümcesinin türünü gösterir.  
  
 [COR_PRF_CODEGEN_FLAGS Sabit Listesi](cor-prf-codegen-flags-enumeration.md)  
 [ICorProfilerFunctionControl:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) yöntemiyle ayarlanabilmesi için kod oluşturma bayraklarını tanımlar.  
  
 [COR_PRF_FINALIZER_FLAGS Sabit Listesi](cor-prf-finalizer-flags-enumeration.md)  
 Bir nesne için sonlandırıcıyı açıklar.  
  
 [COR_PRF_GC_GENERATION Sabit Listesi](cor-prf-gc-generation-enumeration.md)  
 Çöp toplama oluşturmayı tanımlar.  
  
 [COR_PRF_GC_REASON Sabit Listesi](cor-prf-gc-reason-enumeration.md)  
 Çöp toplamanın oluşma nedenini gösterir.  
  
 [COR_PRF_GC_ROOT_FLAGS Sabit Listesi](cor-prf-gc-root-flags-enumeration.md)  
 Çöp toplayıcı kökünün özelliklerini gösterir.  
  
 [COR_PRF_GC_ROOT_KIND Sabit Listesi](cor-prf-gc-root-kind-enumeration.md)  
 [ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) geri çağırması tarafından sunulan çöp toplayıcı kökünün türünü gösterir.  
  
 [COR_PRF_HIGH_MONITOR Sabit Listesi](cor-prf-high-monitor-enumeration.md)  
 , Profil oluşturucunun, yüklenirken [ICorProfilerInfo5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) metoduna belirtmesinin [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) numaralandırmasında bulunanlara ek olarak bayraklar sağlar.  
  
 [COR_PRF_JIT_CACHE Sabit Listesi](cor-prf-jit-cache-enumeration.md)  
 Önbelleğe alınmış işlev aramasının sonucunu gösterir.  
  
 [COR_PRF_MISC Sabit Listesi](cor-prf-misc-enumeration.md)  
 Özel tanımlayıcılar belirten sabit değerleri içerir.  
  
 [COR_PRF_MODULE_FLAGS Sabit Listesi](cor-prf-module-flags-enumeration.md)  
 Modülün özelliklerini belirtir.  
  
 [COR_PRF_MONITOR Sabit Listesi](cor-prf-monitor-enumeration.md)  
 Profil oluşturucunun abone olması için davranış, özellik veya olay belirlemek için kullanılan değerleri içerir.  
  
 [COR_PRF_RUNTIME_TYPE Sabit Listesi](cor-prf-runtime-type-enumeration.md)  
 Ortak dil çalışma zamanının sürümünü gösteren değerleri içerir.  
  
 [COR_PRF_SNAPSHOT_INFO Sabit Listesi](cor-prf-snapshot-info-enumeration.md)  
 Profiler 'ın `StackSnapshotCallback` işlevine yapılan her çağrıda bir yığın anlık görüntüsüne ne kadar veri geçirileceğini belirtir.  
  
 [COR_PRF_STATIC_TYPE Sabit Listesi](cor-prf-static-type-enumeration.md)  
 Bir alanın statik olup olmadığını ve bu durumda alan için geçerli olan statik kaliteyi gösterir.  
  
 [COR_PRF_SUSPEND_REASON Sabit Listesi](cor-prf-suspend-reason-enumeration.md)  
 Çalışma zamanının askıya alınma nedenini gösterir.  
  
 [COR_PRF_TRANSITION_REASON Sabit Listesi](cor-prf-transition-reason-enumeration.md)  
 Yönetilmesinin yönetilmeyen koda veya tam tersi bir geçişin sebebini gösterir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Profil Oluşturmaya Genel Bakış](profiling-overview.md)  
  
 [Profil Oluşturma Arabirimleri](profiling-interfaces.md)  
  
 [Profil Oluşturma Genel Statik İşlevleri](profiling-global-static-functions.md)  
  
 [Profil Oluşturma Yapıları](profiling-structures.md)
