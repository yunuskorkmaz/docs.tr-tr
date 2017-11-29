---
title: "Profil Oluşturma Numaralandırmaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- profiling enumerations [.NET Framework]
- enumerations [.NET Framework profiling]
- unmanaged enumerations [.NET Framework], profiling
ms.assetid: 8d5f9570-9853-4ce8-8101-df235d5b258e
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2e0b539c8e455040cc97f37f75476b0efe796abb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="profiling-enumerations"></a>Profil Oluşturma Numaralandırmaları
Bu bölümde, profil oluşturma API'si kullanan yönetilmeyen numaralandırmalar açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [COR_PRF_CLAUSE_TYPE numaralandırması](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)  
 Kod yalnızca geçtiğini özel durum yan tümcesi veya sol türünü belirtir.  
  
 [Cor_prf_codegen_flags sabit listesi](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)  
 İle ayarlayabilirsiniz kod oluşturma bayrakları tanımlar [Icorprofilerfunctioncontrol::setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) yöntemi.  
  
 [Cor_prf_fınalızer_flags numaralandırması](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)  
 Bir nesne için sonlandırıcıyı açıklar.  
  
 [Cor_prf_gc_generatıon numaralandırması](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)  
 Çöp koleksiyonu oluşturma tanımlar.  
  
 [COR_PRF_GC_REASON numaralandırması](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)  
 Çöp toplama oluştuğunu nedenini gösterir.  
  
 [COR_PRF_GC_ROOT_FLAGS numaralandırması](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)  
 Çöp toplayıcı kök özelliklerini gösterir.  
  
 [Cor_prf_gc_root_kınd numaralandırması](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)  
 Tarafından sunulan atık toplayıcı kök türünü gösteren [Icorprofilercallback2::rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) geri çağırma.  
  
 [Cor_prf_hıgh_monıtor numaralandırması](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)  
 Bulunan listelenenlere bayrakları sağlar [cor_prf_monıtor](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) profil oluşturucu belirtebilirsiniz numaralandırma [Icorprofilerınfo5::seteventmask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) onu yüklenirken yöntemi.  
  
 [Cor_prf_jıt_cache numaralandırması](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)  
 Önbelleğe alınan işlevi arama sonucu gösterir.  
  
 [Cor_prf_mısc numaralandırması](../../../../docs/framework/unmanaged-api/profiling/cor-prf-misc-enumeration.md)  
 Özel tanımlayıcılarını belirtmek sabit değerleri içerir.  
  
 [COR_PRF_MODULE_FLAGS numaralandırması](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)  
 Bir modül özelliklerini belirtir.  
  
 [Cor_prf_monıtor numaralandırması](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 Davranış, özellikleri, olayları için profil oluşturucu abone istediği veya belirtmek için kullanılan değerler içeriyor.  
  
 [Cor_prf_runtıme_type numaralandırması](../../../../docs/framework/unmanaged-api/profiling/cor-prf-runtime-type-enumeration.md)  
 Ortak dil çalışma zamanı sürümü belirtmek değerlerini içerir.  
  
 [Cor_prf_snapshot_ınfo numaralandırması](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)  
 Profil Oluşturucu'nın her çağrıda anlık görüntü yığını ile ne kadar veri geçirmek için geri belirtir `StackSnapshotCallback` işlevi.  
  
 [Cor_prf_statıc_type numaralandırması](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md)  
 Bir statik alandır ve varsa, statik kalite, alan için geçerli olup olmadığını gösterir.  
  
 [COR_PRF_SUSPEND_REASON numaralandırması](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md)  
 Çalışma zamanı askıya alındı nedenini gösterir.  
  
 [Cor_prf_transıtıon_reason numaralandırması](../../../../docs/framework/unmanaged-api/profiling/cor-prf-transition-reason-enumeration.md)  
 Yönetilmeyen kod için veya tersi yönetilen bir geçiş nedenini gösterir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Profil oluşturmaya genel bakış](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Profil oluşturma arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [Profil oluşturma genel statik işlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [Profil oluşturma yapıları](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
