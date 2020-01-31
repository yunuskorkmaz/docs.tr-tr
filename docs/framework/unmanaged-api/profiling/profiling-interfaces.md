---
title: Profil Oluşturma Arabirimleri
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
ms.openlocfilehash: 8b6b9acff2945e2d8fd684bfa31e4af086ea5ab9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868154"
---
# <a name="profiling-interfaces"></a>Profil Oluşturma Arabirimleri
Bu bölümde, ortak dil çalışma zamanı (CLR) tarafından yürütülen bir programın profilini oluşturma olanağı sağlayan yönetilmeyen arabirimler açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [ICLRProfiling Arabirimi](iclrprofiling-interface.md)  
 Bir profil oluşturucunun çalışan bir işleme iliştirmesine olanak sağlayan [AttachProfiler](iclrprofiling-attachprofiler-method.md) yöntemini sağlar.  
  
 [ICorProfilerAssemblyReferenceProvider Arabirimi](icorprofilerassemblyreferenceprovider-interface.md)  
 Profiler 'ın [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) geri çağırması içinde ekleneceği derleme başvurularını clr 'ye bilgilendirmesini sağlar.  
  
 [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)  
 Profil oluşturucunun abone olduğu olaylar gerçekleştiğinde kod Profilcisi bildirmek için CLR tarafından kullanılan yöntemleri sağlar.  
  
 [ICorProfilerCallback2 Arabirimi](icorprofilercallback2-interface.md)  
 `ICorProfilerCallback` arabirimini .NET Framework 2,0 ve sonraki sürümlerde desteklenen geri çağırmalar ile genişletir.  
  
 [ICorProfilerCallback3 Arabirimi](icorprofilercallback3-interface.md)  
 CLR 'nin, bağlama ve ayırma durum bilgilerini profil oluşturucuya iletmek için kullandığı geri çağırma yöntemleri sağlar.  
  
 [ICorProfilerCallback4 Arabirimi](icorprofilercallback4-interface.md)  
 CLR 'nin bilgileri profil oluşturucuya iletmek için kullandığı geri çağırma yöntemleri sağlar.  
  
 [ICorProfilerCallback5 Arabirimi](icorprofilercallback5-interface.md)  
 Çöp toplama kökleri tarafından başvurulan nesnelerin geçişli kapanışını tanımlayan bir yöntem sağlar.  
  
 [ICorProfilerCallback6 Arabirimi](icorprofilercallback6-interface.md)  
 Bir derlemenin yüklendiği profil oluşturucuyu bilgilendirmek için CLR 'nin kullandığı bir geri çağırma yöntemi sağlar.  
  
 [ICorProfilerCallback7 Arabirimi](icorprofilercallback7-interface.md)  
 Ortak dil çalışma zamanının, bir bellek içi modülle ilişkili sembol akışının güncelleştirildiğini, profil oluşturucuyu bilgilendirmek için kullandığı bir geri arama yöntemi sağlar.  

[ICorProfilerCallback8 Arabirimi](icorprofilercallback8-interface.md)  
Ortak dil çalışma zamanının, dinamik bir yöntemin JıT derlemesinin başlatıldığını ve bittiğini bildiren profil oluşturucuyu bilgilendirmek için kullandığı geri çağırma yöntemleri sağlar.

[ICorProfilerCallback9 Arabirimi](icorprofilercallback9-interface.md)  
Ortak dil çalışma zamanının, dinamik bir yöntemin atık olarak toplandığını ve daha sonra kaldırılmadığını Profiler 'a bildirmek için kullandığı bir geri arama yöntemi sağlar.

 [ICorProfilerFunctionControl Arabirimi](icorprofilerfunctioncontrol-interface.md)  
 Bir kod profil oluşturucunun, belirli bir yöntemi yeniden oluştururken JıT derleyicisinin nasıl kod üretdiğini denetlemek için CLR ile iletişim kurmasına imkan tanıyan yöntemler sağlar.  
  
 [ICorProfilerFunctionEnum Arabirimi](icorprofilerfunctionenum-interface.md)  
 CLR içindeki işlevlerin bir koleksiyonu aracılığıyla sırayla yinelemek için yöntemler sağlar.  
  
 [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)  
 Olay izleme ve istek bilgilerini denetlemek için CLR ile iletişim kurmak üzere kod profil oluşturucular tarafından kullanılacak yöntemler sağlar.  
  
 [ICorProfilerInfo2 Arabirimi](icorprofilerinfo2-interface.md)  
 `ICorProfilerInfo` arabirimini .NET Framework 2,0 ve sonraki sürümlerde desteklenen yöntemlerle genişletir.  
  
 [ICorProfilerInfo3 Yöntemi](icorprofilerinfo3-interface.md)  
 `ICorProfilerInfo2` arabirimini .NET Framework 4 ve sonraki sürümlerde desteklenen yöntemlerle genişletir.  
  
 [ICorProfilerInfo4 Arabirimi](icorprofilerinfo4-interface.md)  
 Olay izlemeyi denetlemek ve bilgi istemek üzere CLR ile iletişim kurmak için kod profil oluşturucular kullanan yöntemler sağlar.  
  
 [ICorProfilerInfo5 Arabirimi](icorprofilerinfo5-interface.md)  
 Olay izlemeyi denetlemek için CLR ile iletişim kurmak üzere kod profil oluşturucular tarafından kullanılacak yöntemler sağlar.  
  
 [ICorProfilerInfo6 Arabirimi](icorprofilerinfo6-interface.md)  
 Belirli bir NGen modülüne ait olan ve belirli bir yöntemin gövdesinde satır içine alınmış tüm yöntemlere bir Numaralandırıcı sağlar.  
  
 [ICorProfilerInfo7 Arabirimi](icorprofilerinfo7-interface.md)  
 Bir modüle yeni tanımlanmış meta verileri uygulamak için bir yöntem sağlar ve bellek içi sembol akışına erişim sağlar.  
  
 [ICorProfilerModuleEnum Arabirimi](icorprofilermoduleenum-interface.md)  
 Uygulama veya profil oluşturucu tarafından yüklenen bir modül koleksiyonunda sırayla yinelemek için yöntemler sağlar.  
  
 [ICorProfilerObjectEnum Arabirimi](icorprofilerobjectenum-interface.md)  
 [Ngen. exe (yerel görüntü Oluşturucu)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)tarafından oluşturulan dondurulmuş nesneler koleksiyonunda sırayla yinelemek için yöntemler sağlar.  
  
 [ICorProfilerThreadEnum Arabirimi](icorprofilerthreadenum-interface.md)  
 CLR 'deki iş parçacığı koleksiyonunda sırayla yinelemek için yöntemler sağlar.  
  
 [IMethodMalloc Arabirimi](imethodmalloc-interface.md)  
 Yeni bir Microsoft ara dili (MSIL) işlev gövdesi için bellek ayırmak üzere [ayırma](imethodmalloc-alloc-method.md) yöntemi sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Profil Oluşturmaya Genel Bakış](profiling-overview.md)  
  
 [Profil Oluşturma Genel Statik İşlevleri](profiling-global-static-functions.md)  
  
 [Profil Oluşturma Sabit Listeleri](profiling-enumerations.md)  
  
 [Profil Oluşturma Yapıları](profiling-structures.md)
