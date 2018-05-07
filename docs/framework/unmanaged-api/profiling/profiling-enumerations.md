---
title: Profil Oluşturma Numaralandırmaları
ms.date: 03/30/2017
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 996352637f34b0b6c0d12e611a6d9e70ab85230e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="profiling-enumerations"></a>Profil Oluşturma Numaralandırmaları
Bu bölümde, profil oluşturma API'si kullanan yönetilmeyen numaralandırmalar açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [COR_PRF_CLAUSE_TYPE Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)  
 Kod yalnızca geçtiğini özel durum yan tümcesi veya sol türünü belirtir.  
  
 [COR_PRF_CODEGEN_FLAGS Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)  
 İle ayarlayabilirsiniz kod oluşturma bayrakları tanımlar [Icorprofilerfunctioncontrol::setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) yöntemi.  
  
 [COR_PRF_FINALIZER_FLAGS Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)  
 Bir nesne için sonlandırıcıyı açıklar.  
  
 [COR_PRF_GC_GENERATION Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)  
 Çöp koleksiyonu oluşturma tanımlar.  
  
 [COR_PRF_GC_REASON Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)  
 Çöp toplama oluştuğunu nedenini gösterir.  
  
 [COR_PRF_GC_ROOT_FLAGS Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)  
 Çöp toplayıcı kök özelliklerini gösterir.  
  
 [COR_PRF_GC_ROOT_KIND Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)  
 Tarafından sunulan atık toplayıcı kök türünü gösteren [Icorprofilercallback2::rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) geri çağırma.  
  
 [COR_PRF_HIGH_MONITOR Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)  
 Bulunan listelenenlere bayrakları sağlar [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) profil oluşturucu belirtebilirsiniz numaralandırma [Icorprofilerınfo5::seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) onu yüklenirken yöntemi.  
  
 [COR_PRF_JIT_CACHE Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)  
 Önbelleğe alınan işlevi arama sonucu gösterir.  
  
 [COR_PRF_MISC Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-misc-enumeration.md)  
 Özel tanımlayıcılarını belirtmek sabit değerleri içerir.  
  
 [COR_PRF_MODULE_FLAGS Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)  
 Bir modül özelliklerini belirtir.  
  
 [COR_PRF_MONITOR Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 Davranış, özellikleri, olayları için profil oluşturucu abone istediği veya belirtmek için kullanılan değerler içeriyor.  
  
 [COR_PRF_RUNTIME_TYPE Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-runtime-type-enumeration.md)  
 Ortak dil çalışma zamanı sürümü belirtmek değerlerini içerir.  
  
 [COR_PRF_SNAPSHOT_INFO Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)  
 Profil Oluşturucu'nın her çağrıda anlık görüntü yığını ile ne kadar veri geçirmek için geri belirtir `StackSnapshotCallback` işlevi.  
  
 [COR_PRF_STATIC_TYPE Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)  
 Bir statik alandır ve varsa, statik kalite, alan için geçerli olup olmadığını gösterir.  
  
 [COR_PRF_SUSPEND_REASON Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md)  
 Çalışma zamanı askıya alındı nedenini gösterir.  
  
 [COR_PRF_TRANSITION_REASON Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)  
 Yönetilmeyen kod için veya tersi yönetilen bir geçiş nedenini gösterir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Profil Oluşturmaya Genel Bakış](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [Profil Oluşturma Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [Profil Oluşturma Yapıları](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
