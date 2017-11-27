---
title: "Profil Oluşturma Genel Statik İşlevleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4da4509a6e8b87490cee076b403f3fa525de91e0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="profiling-global-static-functions"></a>Profil Oluşturma Genel Statik İşlevleri
Bu bölümde, profil oluşturma API'si kullanan yönetilmeyen API işlevleri açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
## <a name="net-framework-version-1-profiling-functions"></a>.NET framework sürüm 1 profil işlevleri  
 [FunctionEnter işlevi](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)  
 Profil Oluşturucu denetim bir işlevine geçirilen olduğunu bildirir. .NET Framework 2.0 kullanım dışı.  
  
 [FunctionLeave işlevi](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)  
 Profil Oluşturucu çağırana hakkında bilgi döndürmek için bir işlevi olduğunu bildirir. .NET Framework 2.0 kullanım dışı.  
  
 [FunctionTailcall işlevi](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md)  
 Profil Oluşturucu şu anda yürütülen işlevi başka bir işlevine bir kuyruk çağrısı gerçekleştirmek üzere olduğunu bildirir. .NET Framework 2.0 kullanım dışı.  
  
## <a name="net-framework-version-2-profiling-functions"></a>.NET framework sürüm 2 profil işlevleri  
 [Functionıdmapper işlevi](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)  
 Profil oluşturucu işlevi verilen tanıtıcısı kullanılmak üzere bir alternatif kimlik eşlenmesine bildirir [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), ve [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) bu işlev için geri çağırmaları. Ayrıca, bu işlevin geri aramalar almak istediği olup olmadığını belirtmek profil oluşturucu sağlar  
  
 [FunctionEnter2 işlevi](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 Profil Oluşturucu denetim bir işlevine geçirilen ve çerçeve ve işlev bağımsız değişkenleri yığını hakkında bilgi sağlayan bildirir. İçinde kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [FunctionLeave2 işlevi](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 Profil oluşturucu işlevi çağırana hakkında bilgi döndürmek için ve yığın çerçevesi ve işlevi dönüş değeri hakkında bilgi sağlar bildirir. İçinde kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [FunctionTailcall2 işlevi](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 Profil Oluşturucu şu anda yürütülen işlevi başka bir işlevine bir kuyruk çağrısı gerçekleştirmek üzere ve yığın çerçevesi hakkında bilgi sağlar bildirir. İçinde kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StackSnapshotCallback işlevi](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)  
 Profil Oluşturucu bilgiler her yönetilen çerçeve ve her çalışma yönetilmeyen çerçeve yığında tarafından başlatılan bir yığın ilerlemesi sırasında verir [Icorprofilerınfo2::dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) yöntemi.  
  
## <a name="net-framework-version-4-profiling-functions"></a>.NET framework sürüm 4 profil işlevleri  
 [Functionıdmapper2 işlevi](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 Profil oluşturucu işlevi verilen tanıtıcısı kullanılmak üzere bir alternatif kimlik eşlenmesine bildirir [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), ve [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), veya[Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [Functionleave3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), ve [Functiontailcall3withınfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) bu işlev için geri çağırmaları. Ayrıca, bu işlevin geri aramalar almak istediği olup olmadığını belirtmek profil oluşturucu sağlar.  
  
 `FunctionIDMapper2`genişletir [Functionıdmapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) ile işlev bir `clientData` parametresi profil oluşturucular çalışma zamanları arasında belirsizliğini ortadan kaldırmak için kullanabilirsiniz.  
  
 [FunctionEnter3 işlevi](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 Profil Oluşturucu denetim bir işlevine geçirilen olduğunu bildirir.  
  
 [Functionenter3withınfo işlevi](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 Profil Oluşturucu denetim bir işlevine geçirilen olduğunu bildirir ve için geçirilen tanıtıcı sağlar [Icorprofilerınfo3::getfunctionenter3ınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) yığın çerçevesi ve işlev bağımsız değişkenleri alınamadı.  
  
 [FunctionLeave3 işlevi](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 Profil Oluşturucu denetim bir işlevinden döndürülen olduğunu bildirir.  
  
 [Functionleave3withınfo işlevi](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 Profil Oluşturucu denetim bir işlevinden döndürülen olduğunu bildirir ve için geçirilen tanıtıcı sağlar [Icorprofilerınfo3::getfunctionleave3ınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) yığın çerçevesi ve dönüş değeri alınamadı.  
  
 [FunctionTailcall3 işlevi](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 Profil Oluşturucu şu anda yürütülen işlevi başka bir işlevine bir kuyruk çağrısı gerçekleştirmek üzere olduğunu bildirir.  
  
 [Functiontailcall3withınfo işlevi](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 Başka bir işlevine bir kuyruk çağrısı gerçekleştirmek üzere şu anda yürütülen işlevidir profil oluşturucu bildirir ve için geçirilen tanıtıcı sağlar [Icorprofilerınfo3::getfunctiontailcall3ınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) yığın çerçevesi alınamadı.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Profil oluşturmaya genel bakış](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Profil oluşturma arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [Profil oluşturma numaralandırmaları](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [Profil oluşturma yapıları](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
