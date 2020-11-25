---
title: Profil Oluşturma Numaralandırmaları
ms.date: 03/30/2017
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
ms.openlocfilehash: 8956a09cf76aa54452e8c020239e650e55d8a0d1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701620"
---
# <a name="profiling-enumerations"></a>Profil Oluşturma Numaralandırmaları

Bu bölümde profil oluşturma API 'sinin kullandığı yönetilmeyen numaralandırmalar açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [COR_PRF_CLAUSE_TYPE Numaralandırması](cor-prf-clause-type-enumeration.md)  
 Kodun yalnızca girdiği veya solundaki özel durum yan tümcesinin türünü gösterir.  
  
 [COR_PRF_CODEGEN_FLAGS Sabit Listesi](cor-prf-codegen-flags-enumeration.md)  
 [ICorProfilerFunctionControl:: SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) yöntemiyle ayarlanabilmesi için kod oluşturma bayraklarını tanımlar.  
  
 [COR_PRF_FINALIZER_FLAGS Numaralandırması](cor-prf-finalizer-flags-enumeration.md)  
 Bir nesne için sonlandırıcıyı açıklar.  
  
 [COR_PRF_GC_GENERATION Numaralandırması](cor-prf-gc-generation-enumeration.md)  
 Çöp toplama oluşturmayı tanımlar.  
  
 [COR_PRF_GC_REASON Numaralandırması](cor-prf-gc-reason-enumeration.md)  
 Çöp toplamanın oluşma nedenini gösterir.  
  
 [COR_PRF_GC_ROOT_FLAGS Numaralandırması](cor-prf-gc-root-flags-enumeration.md)  
 Çöp toplayıcı kökünün özelliklerini gösterir.  
  
 [COR_PRF_GC_ROOT_KIND Numaralandırması](cor-prf-gc-root-kind-enumeration.md)  
 [ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) geri çağırması tarafından sunulan çöp toplayıcı kökünün türünü gösterir.  
  
 [COR_PRF_HIGH_MONITOR Numaralandırması](cor-prf-high-monitor-enumeration.md)  
 , Profil oluşturucunun, yüklenirken [ICorProfilerInfo5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) metoduna belirtmesinin [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) numaralandırmasında bulunanlara ek olarak bayraklar sağlar.  
  
 [COR_PRF_JIT_CACHE Numaralandırması](cor-prf-jit-cache-enumeration.md)  
 Önbelleğe alınmış işlev aramasının sonucunu gösterir.  
  
 [COR_PRF_MISC Numaralandırması](cor-prf-misc-enumeration.md)  
 Özel tanımlayıcılar belirten sabit değerleri içerir.  
  
 [COR_PRF_MODULE_FLAGS Numaralandırması](cor-prf-module-flags-enumeration.md)  
 Modülün özelliklerini belirtir.  
  
 [COR_PRF_MONITOR Numaralandırması](cor-prf-monitor-enumeration.md)  
 Profil oluşturucunun abone olması için davranış, özellik veya olay belirlemek için kullanılan değerleri içerir.  
  
 [COR_PRF_RUNTIME_TYPE Numaralandırması](cor-prf-runtime-type-enumeration.md)  
 Ortak dil çalışma zamanının sürümünü gösteren değerleri içerir.  
  
 [COR_PRF_SNAPSHOT_INFO Numaralandırması](cor-prf-snapshot-info-enumeration.md)  
 Profil oluşturucunun işlevine yapılan her çağrıda bir yığın anlık görüntüsüne ne kadar veri geçirileceğini belirtir `StackSnapshotCallback` .  
  
 [COR_PRF_STATIC_TYPE Numaralandırması](cor-prf-static-type-enumeration.md)  
 Bir alanın statik olup olmadığını ve bu durumda alan için geçerli olan statik kaliteyi gösterir.  
  
 [COR_PRF_SUSPEND_REASON Numaralandırması](cor-prf-suspend-reason-enumeration.md)  
 Çalışma zamanının askıya alınma nedenini gösterir.  
  
 [COR_PRF_TRANSITION_REASON Numaralandırması](cor-prf-transition-reason-enumeration.md)  
 Yönetilmesinin yönetilmeyen koda veya tam tersi bir geçişin sebebini gösterir.  
  
## <a name="related-sections"></a>İlgili Bölümler  

 [Profil Oluşturmaya Genel Bakış](profiling-overview.md)  
  
 [Profil Oluşturma Arabirimleri](profiling-interfaces.md)  
  
 [Profil Oluşturma Genel Statik İşlevleri](profiling-global-static-functions.md)  
  
 [Profil Oluşturma Yapıları](profiling-structures.md)
