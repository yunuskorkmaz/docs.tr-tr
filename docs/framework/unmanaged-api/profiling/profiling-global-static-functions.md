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
ms.openlocfilehash: 3ea65c06871d9762fa6daac229a568594b4c4479
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457480"
---
# <a name="profiling-global-static-functions"></a>Profil Oluşturma Genel Statik İşlevleri
Bu bölümde, profil oluşturma API'SİNİN kullandığı yönetilmeyen API işlevleri açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
## <a name="net-framework-version-1-profiling-functions"></a>.NET framework sürüm 1 profil oluşturma işlevleri  
 [FunctionEnter İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)  
 Profil Oluşturucu, denetim bir işleve geçirilen olduğunu bildirir. .NET Framework 2.0 kullanım dışı.  
  
 [FunctionLeave İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)  
 Profil Oluşturucu bir işlev hakkında çağırana döndürmesi olduğunu bildirir. .NET Framework 2.0 kullanım dışı.  
  
 [FunctionTailcall İşlevi](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md)  
 Profil Oluşturucu, yürütülmekte olan işlevin başka bir işleve bir kuyruk çağrısı gerçekleştirmek üzere olduğunu bildirir. .NET Framework 2.0 kullanım dışı.  
  
## <a name="net-framework-version-2-profiling-functions"></a>.NET framework sürüm 2 profil oluşturma işlevleri  
 [FunctionIDMapper İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)  
 Profil Oluşturucu bir işlev, verilen tanımlayıcıya için kullanılmak üzere diğer Kimliğe yeniden eşlenebileceğini bildirir [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), ve [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) söz konusu işlev için geri çağırmaları. Ayrıca profil oluşturucunun söz konusu işlev için geri çağırmaları almak isteyip istemediğini göstermesini sağlar  
  
 [FunctionEnter2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 Profil Oluşturucu bildirir: denetim bir işleve geçirilir ve çerçeve ve işlev bağımsız değişkenleri yığın hakkında bilgi sağlar. .NET Framework 4 içinde kullanım dışı.  
  
 [FunctionLeave2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 Profil Oluşturucu bildirir: bir işlev hakkında çağırana döndürmesi için ve yığın çerçeve ve işlev dönüş değeri hakkında bilgi sağlar. .NET Framework 4 içinde kullanım dışı.  
  
 [FunctionTailcall2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 Profil Oluşturucu bildirir: yürütülmekte olan işlevin başka bir işleve bir kuyruk çağrısı gerçekleştirmek üzere olduğunu ve yığın çerçevesi hakkında bilgi sağlar. .NET Framework 4 içinde kullanım dışı.  
  
 [StackSnapshotCallback İşlevi](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)  
 Profil Oluşturucu yönetilen her çerçeve ve her bir çalıştırmanın yönetilmeyen çerçeveler hakkında tarafından başlatılan bir yığın ilerlemesi sırasında bilgileri yığında sağlar [Icorprofilerınfo2::dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) yöntemi.  
  
## <a name="net-framework-version-4-profiling-functions"></a>.NET framework sürüm 4'ün profil oluşturma işlevleri  
 [FunctionIDMapper2 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 Profil Oluşturucu bir işlev, verilen tanımlayıcıya için kullanılmak üzere diğer Kimliğe yeniden eşlenebileceğini bildirir [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), ve [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), veya[Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [Functionleave3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), ve [Functiontailcall3withınfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) söz konusu işlev için geri çağırmaları. Ayrıca, profil oluşturucunun söz konusu işlev için geri çağırmaları almak isteyip istemediğini göstermesini sağlar.  
  
 `FunctionIDMapper2` genişletir [Functionıdmapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) işleviyle bir `clientData` parametresini profil Oluşturucular, çalışma zamanları arasındaki belirsizliğini ortadan kaldırmak için kullanabilirsiniz.  
  
 [FunctionEnter3 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 Profil Oluşturucu, denetim bir işleve geçirilen olduğunu bildirir.  
  
 [FunctionEnter3WithInfo İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 Denetim bir işleve geçirilen profil oluşturucu bildirir ve geçirilebilir bir tanıtıcı sağlar [Icorprofilerınfo3::getfunctionenter3ınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) yığın çerçeve ve işlev bağımsız değişkenlerini almak için.  
  
 [FunctionLeave3 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 Profil Oluşturucu denetimi bir işlevden döndürülen uyarır.  
  
 [FunctionLeave3WithInfo İşlevi](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 Profil Oluşturucu denetimi bir işlevden döndürülen uyarır ve geçirilebilir bir tanıtıcı sağlar [Icorprofilerınfo3::getfunctionleave3ınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) yığın çerçevesi ve dönüş değeri alınamıyor.  
  
 [FunctionTailcall3 İşlevi](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 Profil Oluşturucu, yürütülmekte olan işlevin başka bir işleve bir kuyruk çağrısı gerçekleştirmek üzere olduğunu bildirir.  
  
 [FunctionTailcall3WithInfo İşlevi](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 Yürütülmekte olan işlevin başka bir işleve bir kuyruk çağrısı gerçekleştirmek üzere olan profil oluşturucu bildirir ve geçirilebilir bir tanıtıcı sağlar [Icorprofilerınfo3::getfunctiontailcall3ınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) yığın çerçevesi alınamadı.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Profil Oluşturmaya Genel Bakış](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [Profil Oluşturma Sabit Listeleri](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [Profil Oluşturma Yapıları](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
