---
title: Profil Oluşturma Arabirimleri
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d97960a43e1d7ce625d96755a7c597a0425d0911
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457466"
---
# <a name="profiling-interfaces"></a>Profil Oluşturma Arabirimleri
Bu bölümde, ortak dil çalışma zamanı tarafından (CLR) yürütülen bir programın profilini olanak tanıyan yönetilmeyen arabirimler açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [ICLRProfiling Arabirimi](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 Sağlar [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) yöntemi bir profil oluşturucunun bir çalışan işleme sağlar.  
  
 [ICorProfilerAssemblyReferenceProvider Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 CLR, profil oluşturucu ekler derleme başvuruları bildirmek profil oluşturucu sağlar [Icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri çağırma.  
  
 [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 Profil Oluşturucu abone olduğu olaylar meydana geldiğinde bir kod profil oluşturucu bildirmek için CLR tarafından kullanılan yöntemleri sağlar.  
  
 [ICorProfilerCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 Genişletir `ICorProfilerCallback` arabirimi ile .NET Framework 2.0 ve sonraki sürümlerinde desteklenen geri çağırmalar.  
  
 [ICorProfilerCallback3 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 CLR iletişim kurmak için kullandığı geri çağırma yöntemleri ekleme ve ayırma profil oluşturucu için durum bilgilerini sağlar.  
  
 [ICorProfilerCallback4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 CLR Profil Oluşturucu bilgiler iletmek için kullandığı geri çağırma yöntemleri sağlar.  
  
 [ICorProfilerCallback5 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 Çöp toplama kökleri tarafından başvurulan nesneleri geçişli kapatılmasını tanımlayan bir yöntem sağlar.  
  
 [ICorProfilerCallback6 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 Bir derleme yüklenen bir profil oluşturucu bildirmek için CLR kullanan bir geri arama yöntemi sağlar.  
  
 [ICorProfilerCallback7 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 Profil Oluşturucu bir bellek içi modül ile ilişkili simge akışı güncelleştirilmiş olduğunu bildirmek için ortak dil çalışma zamanı kullanan bir geri arama yöntemi sağlar.  

[ICorProfilerCallback8 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-interface.md)  
Dinamik bir yöntem JIT derlemesi başladı ve tamamlanmış olan profil oluşturucu bildirmek için ortak dil çalışma zamanı kullanan bir geri çağırma yöntemleri sağlar.

[ICorProfilerCallback9 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback9-interface.md)  
Toplanan ve daha sonra kaldırıldığında çöp dinamik bir yöntem olan profil oluşturucu bildirmek için ortak dil çalışma zamanı kullanan bir geri arama yöntemi sağlar.

 [ICorProfilerFunctionControl Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 Bir kod profil oluşturucu nasıl JIT Derleyici kodu belirli bir yöntem yeniden derlemeden oluşturmasını denetlemek için CLR ile iletişim kurmasına izin vermek için yöntemler sağlar.  
  
 [ICorProfilerFunctionEnum Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 Sıralı olarak CLR işlevler koleksiyonu üzerinden yineleme yapmak için yöntemler sağlar.  
  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 Olay İzleme Denetim ve bilgi istemek için CLR ile iletişim kurmak için kod profil Oluşturucuları tarafından kullanım için yöntemler sağlar.  
  
 [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 Genişletir `ICorProfilerInfo` arabirim yöntemleriyle .NET Framework 2.0 ve sonraki sürümlerinde desteklenir.  
  
 [ICorProfilerInfo3 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 Genişletir `ICorProfilerInfo2` arabirim yöntemleriyle .NET Framework 4 ve sonraki sürümlerinde desteklenir.  
  
 [ICorProfilerInfo4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 Olay İzleme denetlemek ve bilgi istemek için CLR ile iletişim kurmak için kod profil oluşturucuları kullanmak için yöntemler sağlar.  
  
 [ICorProfilerInfo5 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 Olay İzleme denetlemek için CLR ile iletişim kurmak için kod profil Oluşturucuları tarafından kullanım için yöntemler sağlar.  
  
 [ICorProfilerInfo6 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 Belirli bir NGen modüle ait olan ve belirli bir yöntemin gövdesinde satır içine alınmış olan tüm yöntemleri için bir numaralandırıcı sağlar.  
  
 [ICorProfilerInfo7 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 Yeni uygulamak için bir yöntem bir modül için meta verileri tanımlanmış ve bir bellek içi sembol akışına erişim sağlayan sağlar.  
  
 [ICorProfilerModuleEnum Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 Sıralı olarak uygulama veya profil oluşturucu tarafından yüklenen modülleri koleksiyonu üzerinden yineleme yapmak için yöntemler sağlar.  
  
 [ICorProfilerObjectEnum Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 Tarafından oluşturulan donmuş nesneler koleksiyonunu sırayla yinelemek için yöntemler sağlar [Ngen.exe (yerel Görüntü Oluşturucu)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
 [ICorProfilerThreadEnum Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 CLR iş parçacıklarının koleksiyonunu sırayla yinelemek için yöntemler sağlar.  
  
 [IMethodMalloc Arabirimi](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 Sağlar [ayırma](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) yöntemi yeni bir Microsoft Ara dili (MSIL) işlev gövdesi için bellek ayrılamadı.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Profil Oluşturmaya Genel Bakış](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Profil Oluşturma Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [Profil Oluşturma Sabit Listeleri](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [Profil Oluşturma Yapıları](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
