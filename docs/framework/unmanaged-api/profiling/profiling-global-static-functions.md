---
title: Profil Oluşturma Genel Statik İşlevleri
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
ms.openlocfilehash: 20ee2a9e045d839aa8ac043e035c438986b987ef
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76860872"
---
# <a name="profiling-global-static-functions"></a>Profil Oluşturma Genel Statik İşlevleri
Bu bölümde profil oluşturma API 'sinin kullandığı yönetilmeyen API işlevleri açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
## <a name="net-framework-version-1-profiling-functions"></a>.NET Framework sürüm 1 profil oluşturma Işlevleri  
 [FunctionEnter İşlevi](functionenter-function.md)  
 Profil oluşturucuya denetimin bir işleve geçtiğini bildirir. .NET Framework 2,0 ' de kullanımdan kaldırılmıştır.  
  
 [FunctionLeave İşlevi](functionleave-function.md)  
 Profiler öğesine bir işlevin çağırana dönmek üzere olduğunu bildirir. .NET Framework 2,0 ' de kullanımdan kaldırılmıştır.  
  
 [FunctionTailcall İşlevi](functiontailcall-function.md)  
 Profil oluşturucuyu Şu anda yürütülmekte olan işlevin başka bir işleve tail çağrısı gerçekleştirmek üzere olduğunu bildirir. .NET Framework 2,0 ' de kullanımdan kaldırılmıştır.  
  
## <a name="net-framework-version-2-profiling-functions"></a>.NET Framework sürüm 2 profil oluşturma Işlevleri  
 [FunctionIDMapper İşlevi](functionidmapper-function.md)  
 Profil oluşturucuyu, bir işlevin verilen tanımlayıcısının, bu işlev için [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md)ve [FunctionTailcall2](functiontailcall2-function.md) geri ÇAĞıRMALAR içinde kullanılacak alternatif bir kimliğe yeniden eşlenilebileceği konusunda bilgilendirir. Ayrıca, profil oluşturucunun bu işlev için geri çağırmaları almak isteyip istemediğini belirtmek için izin sağlar  
  
 [FunctionEnter2 İşlevi](functionenter2-function.md)  
 Profil oluşturucuyu denetimin bir işleve geçtiğini ve yığın çerçevesi ve işlev bağımsız değişkenleri hakkında bilgi sağladığını bildirir. .NET Framework 4 ' te kullanım dışıdır.  
  
 [FunctionLeave2 İşlevi](functionleave2-function.md)  
 Profil oluşturucuya bir işlevin çağırana dönmek üzere olduğunu bildirir ve yığın çerçevesi ve işlev dönüş değeri hakkında bilgi sağlar. .NET Framework 4 ' te kullanım dışıdır.  
  
 [FunctionTailcall2 İşlevi](functiontailcall2-function.md)  
 Şu anda yürütülmekte olan işlevin başka bir işleve bir tail çağrısı gerçekleştirmek üzere olduğunu ve yığın çerçevesi hakkında bilgi sağladığını bildiren Profiler öğesine bildirir. .NET Framework 4 ' te kullanım dışıdır.  
  
 [StackSnapshotCallback İşlevi](stacksnapshotcallback-function.md)  
 , Profil oluşturucuyu her yönetilen çerçeve ve yığın üzerinde her yönetilmeyen çerçeve, [ICorProfilerInfo2::D oStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) yöntemi tarafından başlatılan bir yığın ilerleme durumuyla ilgili bilgilerle birlikte sağlar.  
  
## <a name="net-framework-version-4-profiling-functions"></a>.NET Framework sürüm 4 profil oluşturma Işlevleri  
 [FunctionIDMapper2 İşlevi](functionidmapper2-function.md)  
 Profil oluşturucuyu, bir işlevin verilen tanımlayıcısının, bu işlev için [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)ve [FunctionTailcall3](functiontailcall3-function.md)veya[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)ve [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) geri çağırmalar içinde kullanılacak alternatif bir kimliğe yeniden eşlenilebileceği konusunda bilgilendirir. Ayrıca, profil oluşturucunun bu işlev için geri çağırmaları almak isteyip istemediğini belirtmek için de olanak sağlar.  
  
 `FunctionIDMapper2` [FunctionIDMapper](functionidmapper-function.md) işlevini bir `clientData` parametresiyle genişleterek, bu, çalışma zamanları arasında belirsizliği ortadan kaldırmak için kullanılabilir.  
  
 [FunctionEnter3 İşlevi](functionenter3-function.md)  
 Profil oluşturucuya denetimin bir işleve geçtiğini bildirir.  
  
 [FunctionEnter3WithInfo İşlevi](functionenter3withinfo-function.md)  
 Denetim oluşturucuyu denetimin bir işleve geçtiğini bildirir ve yığın çerçevesini ve işlev bağımsız değişkenlerini almak için [ICorProfilerInfo3:: GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) öğesine geçirilebilecek bir tanıtıcı sağlar.  
  
 [FunctionLeave3 İşlevi](functionleave3-function.md)  
 Denetim oluşturucuyu, denetimin bir işlevden döndürülmekte olduğunu bildirir.  
  
 [FunctionLeave3WithInfo İşlevi](functionleave3withinfo-function.md)  
 Denetim oluşturucuyu denetimin bir işlevden döndürülmekte olduğunu bildirir ve yığın çerçevesini ve dönüş değerini almak için [ICorProfilerInfo3:: GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) öğesine geçirilebilecek bir tanıtıcı sağlar.  
  
 [FunctionTailcall3 İşlevi](functiontailcall3-function.md)  
 Profil oluşturucuyu Şu anda yürütülmekte olan işlevin başka bir işleve tail çağrısı gerçekleştirmek üzere olduğunu bildirir.  
  
 [FunctionTailcall3WithInfo İşlevi](functiontailcall3withinfo-function.md)  
 Profiler 'ın Şu anda yürütülmekte olan işlevin başka bir işleve tail çağrısı gerçekleştirmek üzere olduğunu bildirir ve yığın çerçevesini almak için [ICorProfilerInfo3:: GetFunctionTailcall3Info](icorprofilerinfo3-getfunctiontailcall3info-method.md) öğesine geçirilebilecek bir tanıtıcı sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Profil Oluşturmaya Genel Bakış](profiling-overview.md)  
  
 [Profil Oluşturma Arabirimleri](profiling-interfaces.md)  
  
 [Profil Oluşturma Sabit Listeleri](profiling-enumerations.md)  
  
 [Profil Oluşturma Yapıları](profiling-structures.md)
