---
title: "Profil Oluşturma Arabirimleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
caps.latest.revision: "31"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f8c2a5ce5e1231c55f598e48d14bec896a4b5f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="profiling-interfaces"></a>Profil Oluşturma Arabirimleri
Bu bölümde ortak dil çalışma zamanı tarafından (CLR) çalıştırılan bir program profil sağlayan yönetilmeyen arabirimler açıklanmaktadır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [ICLRProfiling Arabirimi](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 Sağlar [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) çalışan bir işlemi eklemek bir profil oluşturucu etkinleştirir yöntemi.  
  
 [ICorProfilerAssemblyReferenceProvider Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 Profil oluşturucu içinde ekleyeceksiniz derleme başvurularını CLR bildirmek profil oluşturucu etkinleştirir [Icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri çağırma.  
  
 [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 CLR tarafından profil oluşturucu abone olaylar meydana geldiğinde kod profil oluşturucu bildirmek için kullanılan yöntemleri sağlar.  
  
 [ICorProfilerCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 Genişletir `ICorProfilerCallback` .NET Framework 2.0 ve sonraki sürümlerinde desteklenen geri aramalar arabirimi.  
  
 [ICorProfilerCallback3 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 CLR iletişim kurmak için kullandığı geri arama yöntemleri ekleme ve durum bilgilerini profil oluşturucu için ayırma sağlar.  
  
 [ICorProfilerCallback4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 CLR Profil bilgilerini iletmek için kullandığı geri çağırma yöntemleri sağlar.  
  
 [ICorProfilerCallback5 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 Çöp toplama kökleri tarafından başvurulan nesne geçişli kapatma tanımlayan bir yöntem sağlar.  
  
 [ICorProfilerCallback6 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 Bir derlemesi yüklenirken bir profil oluşturucu bildirmek için CLR kullanan bir geri arama yöntemi sağlar.  
  
 [ICorProfilerCallback7 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 Profil Oluşturucu bir bellek içi modülü ile ilişkili simgesi akış güncelleştirilir bildirmek için ortak dil çalışma zamanı kullanan bir geri arama yöntemi sağlar.  
  
 [ICorProfilerFunctionControl Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 Kod profil oluşturucu nasıl JIT Derleyici kodu belirli bir yöntemi yeniden derlenmesi sırasında oluşturulmasına denetlemek için CLR ile iletişim kurmasına izin yöntemleri sağlar.  
  
 [ICorProfilerFunctionEnum Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 CLR işlevlerde koleksiyonu sırayla yinelemek için yöntemleri sağlar.  
  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 Kod profil oluşturucuları olayı izlemeyi denetlemek ve bilgi istemek için CLR ile iletişim kurmak için kullandığı için yöntemleri sağlar.  
  
 [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 Genişletir `ICorProfilerInfo` .NET Framework 2.0 ve sonraki sürümlerinde desteklenen yöntemleriyle arabirimi.  
  
 [ICorProfilerInfo3 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 Genişletir `ICorProfilerInfo2` desteklenen yöntemleri arabirimiyle [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] ve sonraki sürümler.  
  
 [ICorProfilerInfo4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 Kod profil oluşturucuları olayı izlemeyi denetlemek ve bilgi istemek için CLR ile iletişim kurmak için kullandıkları yöntemleri sağlar.  
  
 [ICorProfilerInfo5 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 Kod profil oluşturucuları olayı izlemeyi denetlemek için CLR ile iletişim kurmak için kullandığı için yöntemleri sağlar.  
  
 [ICorProfilerInfo6 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 Belirli bir NGen modüle ait olan ve belirli bir yöntemin gövdesine içermesinden tüm yöntemleri için bir numaralandırıcı sağlar.  
  
 [ICorProfilerInfo7 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 Yeni uygulamak için bir yöntem meta verileri bir modüle tanımlanmış ve bir bellek içi simgesi akışına erişim sağlayan sağlar.  
  
 [ICorProfilerModuleEnum Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 Uygulama veya profil oluşturucu tarafından yüklenen modülleri koleksiyonu sırayla yinelemek için yöntemleri sağlar.  
  
 [ICorProfilerObjectEnum Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 Bir koleksiyon tarafından üretilen dondurulmuş nesnelerin sırayla yinelemek için yöntemler sağlar [Ngen.exe (yerel Görüntü Oluşturucu)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
 [ICorProfilerThreadEnum Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 CLR iş parçacıkları koleksiyonu sırayla yinelemek için yöntemleri sağlar.  
  
 [IMethodMalloc Arabirimi](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 Sağlar [ayırma](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) yöntemi yeni bir Microsoft Ara dili (MSIL) işlev gövdesi için bellek ayrılamadı.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Profil Oluşturmaya Genel Bakış](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Profil Oluşturma Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [Profil Oluşturma Sabit Listeleri](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [Profil Oluşturma Yapıları](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
