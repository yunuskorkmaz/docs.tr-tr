---
title: Profil Oluşturma Genel Statik İşlevleri
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8bb5d93c91de857ebbee63009cad73fba7e1d284
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461841"
---
# <a name="profiling-global-static-functions"></a>Profil Oluşturma Genel Statik İşlevleri
Bu bölümde, profil oluşturma API'si kullanan yönetilmeyen API işlevleri açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
## <a name="net-framework-version-1-profiling-functions"></a>.NET framework sürüm 1 profil işlevleri  
 [FunctionEnter İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)  
 Profil Oluşturucu denetim bir işlevine geçirilen olduğunu bildirir. .NET Framework 2.0 kullanım dışı.  
  
 [FunctionLeave İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)  
 Profil Oluşturucu çağırana hakkında bilgi döndürmek için bir işlevi olduğunu bildirir. .NET Framework 2.0 kullanım dışı.  
  
 [FunctionTailcall İşlevi](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md)  
 Profil Oluşturucu şu anda yürütülen işlevi başka bir işlevine bir kuyruk çağrısı gerçekleştirmek üzere olduğunu bildirir. .NET Framework 2.0 kullanım dışı.  
  
## <a name="net-framework-version-2-profiling-functions"></a>.NET framework sürüm 2 profil işlevleri  
 [FunctionIDMapper İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)  
 Profil oluşturucu işlevi verilen tanıtıcısı kullanılmak üzere bir alternatif kimlik eşlenmesine bildirir [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), ve [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) bu işlev için geri çağırmaları. Ayrıca, bu işlevin geri aramalar almak istediği olup olmadığını belirtmek profil oluşturucu sağlar  
  
 [FunctionEnter2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 Profil Oluşturucu denetim bir işlevine geçirilen ve çerçeve ve işlev bağımsız değişkenleri yığını hakkında bilgi sağlayan bildirir. İçinde kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [FunctionLeave2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 Profil oluşturucu işlevi çağırana hakkında bilgi döndürmek için ve yığın çerçevesi ve işlevi dönüş değeri hakkında bilgi sağlar bildirir. İçinde kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [FunctionTailcall2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 Profil Oluşturucu şu anda yürütülen işlevi başka bir işlevine bir kuyruk çağrısı gerçekleştirmek üzere ve yığın çerçevesi hakkında bilgi sağlar bildirir. İçinde kullanım dışı [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StackSnapshotCallback İşlevi](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)  
 Profil Oluşturucu bilgiler her yönetilen çerçeve ve her çalışma yönetilmeyen çerçeve yığında tarafından başlatılan bir yığın ilerlemesi sırasında verir [Icorprofilerınfo2::dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) yöntemi.  
  
## <a name="net-framework-version-4-profiling-functions"></a>.NET framework sürüm 4 profil işlevleri  
 [FunctionIDMapper2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 Profil oluşturucu işlevi verilen tanıtıcısı kullanılmak üzere bir alternatif kimlik eşlenmesine bildirir [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), ve [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), veya[Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [Functionleave3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), ve [Functiontailcall3withınfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) bu işlev için geri çağırmaları. Ayrıca, bu işlevin geri aramalar almak istediği olup olmadığını belirtmek profil oluşturucu sağlar.  
  
 `FunctionIDMapper2` genişletir [Functionıdmapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) ile işlev bir `clientData` parametresi profil oluşturucular çalışma zamanları arasında belirsizliğini ortadan kaldırmak için kullanabilirsiniz.  
  
 [FunctionEnter3 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 Profil Oluşturucu denetim bir işlevine geçirilen olduğunu bildirir.  
  
 [FunctionEnter3WithInfo İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 Profil Oluşturucu denetim bir işlevine geçirilen olduğunu bildirir ve için geçirilen tanıtıcı sağlar [Icorprofilerınfo3::getfunctionenter3ınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) yığın çerçevesi ve işlev bağımsız değişkenleri alınamadı.  
  
 [FunctionLeave3 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 Profil Oluşturucu denetim bir işlevinden döndürülen olduğunu bildirir.  
  
 [FunctionLeave3WithInfo İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 Profil Oluşturucu denetim bir işlevinden döndürülen olduğunu bildirir ve için geçirilen tanıtıcı sağlar [Icorprofilerınfo3::getfunctionleave3ınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) yığın çerçevesi ve dönüş değeri alınamadı.  
  
 [FunctionTailcall3 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 Profil Oluşturucu şu anda yürütülen işlevi başka bir işlevine bir kuyruk çağrısı gerçekleştirmek üzere olduğunu bildirir.  
  
 [FunctionTailcall3WithInfo İşlevi](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 Başka bir işlevine bir kuyruk çağrısı gerçekleştirmek üzere şu anda yürütülen işlevidir profil oluşturucu bildirir ve için geçirilen tanıtıcı sağlar [Icorprofilerınfo3::getfunctiontailcall3ınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) yığın çerçevesi alınamadı.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Profil Oluşturmaya Genel Bakış](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [Profil Oluşturma Sabit Listeleri](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [Profil Oluşturma Yapıları](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
