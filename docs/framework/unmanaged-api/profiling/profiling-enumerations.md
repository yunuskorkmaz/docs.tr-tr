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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757579"
---
# <a name="profiling-enumerations"></a>Profil Oluşturma Numaralandırmaları
Bu bölümde, profil oluşturma API'SİNİN kullandığı yönetilmeyen numaralandırmaları açıklar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [COR_PRF_CLAUSE_TYPE Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)  
 Kodu girdiğiniz özel durum yan tümcesi veya sol türünü belirtir.  
  
 [COR_PRF_CODEGEN_FLAGS Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)  
 Ayarlanabilir kod oluşturma bayraklarını tanımlayan [Icorprofilerfunctioncontrol::setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) yöntemi.  
  
 [COR_PRF_FINALIZER_FLAGS Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)  
 Bir nesnenin Sonlandırıcısı açıklar.  
  
 [COR_PRF_GC_GENERATION Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)  
 Bir çöp toplama nesil tanımlar.  
  
 [COR_PRF_GC_REASON Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)  
 Çöp toplama oluştuğu nedenini gösterir.  
  
 [COR_PRF_GC_ROOT_FLAGS Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)  
 Çöp toplayıcı kök özelliklerini gösterir.  
  
 [COR_PRF_GC_ROOT_KIND Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)  
 Tarafından sunulan çöp toplayıcı kök türünü belirten [Icorprofilercallback2::rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) geri çağırma.  
  
 [COR_PRF_HIGH_MONITOR Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)  
 Bulunan listelenenlere bayrakları sağlar [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) Profiler'ı için belirtebileceğiniz numaralandırma [Icorprofilerınfo5::seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) , yüklenirken yöntemi.  
  
 [COR_PRF_JIT_CACHE Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)  
 Önbelleğe alınan işlevi arama sonucu gösterir.  
  
 [COR_PRF_MISC Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-misc-enumeration.md)  
 Özel tanımlayıcılardır belirten sabit değerleri içerir.  
  
 [COR_PRF_MODULE_FLAGS Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)  
 Bir modül özelliklerini belirtir.  
  
 [COR_PRF_MONITOR Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 Davranış, özellikleri veya olayları profil oluşturucu abone olmak isteyen belirtmek için kullanılan değerleri içerir.  
  
 [COR_PRF_RUNTIME_TYPE Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-runtime-type-enumeration.md)  
 Ortak dil çalışma zamanı sürümünü gösteren değerleri içerir.  
  
 [COR_PRF_SNAPSHOT_INFO Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)  
 Ne kadar bir yığın profil oluşturucunun her çağrıda anlık görüntü ile geçirilecek veriler geri belirtir `StackSnapshotCallback` işlevi.  
  
 [COR_PRF_STATIC_TYPE Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)  
 Bir statik alandır ve statik kalite bu durumda, alana uygulanan olup olmadığını gösterir.  
  
 [COR_PRF_SUSPEND_REASON Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md)  
 Çalışma zamanı askıya alındı nedenini gösterir.  
  
 [COR_PRF_TRANSITION_REASON Sabit Listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)  
 Yönetilmeyen kod veya tam tersi yönetilen bir geçiş nedenini gösterir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Profil Oluşturmaya Genel Bakış](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [Profil Oluşturma Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [Profil Oluşturma Yapıları](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
