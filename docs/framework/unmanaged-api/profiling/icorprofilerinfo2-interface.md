---
title: ICorProfilerInfo2 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2
helpviewer_keywords: ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: 91bd49b6-4d12-494f-a8f1-2f251e8c65e3
topic_type: apiref
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cbc0b4ad46c6a49313a42c4c232873988e7f4e99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2-interface"></a>ICorProfilerInfo2 Arabirimi
Kod profil oluşturucuları ortak dil çalışma zamanı (CLR) olayı izlemeyi denetlemek için ve istek bilgileri ile iletişim kurmak için kullandığı yöntemlerini sağlar. `ICorProfilerInfo2` Arabirimi uzantısıdır [Icorprofilerınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) arabirimi. Diğer bir deyişle, .NET Framework sürüm 2.0 ve sonraki sürümlerinde desteklenen yeni yöntemleri sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[DoStackSnapshot yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)|Yönetilen çağrı çerçeveler için profil oluşturucu bildirmek için belirtilen iş parçacığı yığınını anlatılmaktadır.|  
|[EnumModuleFrozenObjects yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)|Belirtilen modül dondurulmuş nesneleri üzerinden yineleme sağlayan bir numaralandırıcı alır.|  
|[GetAppDomainStaticAddress yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getappdomainstaticaddress-method.md)|Belirtilen uygulama etki alanı kapsamında belirtilen uygulama etki alanı statik alan adresini alır.|  
|[Getarrayobjectınfo yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getarrayobjectinfo-method.md)|Bir dizi nesnesi hakkında ayrıntılı bilgi alır.|  
|[GetBoxClassLayout yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getboxclasslayout-method.md)|Sınıf Düzen hakkında bilgi için Kutulu bir belirtilen değer türü alır.|  
|[GetClassFromTokenAndTypeArgs yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)|Alır `ClassID` belirtilen meta veri simgesi kullanarak bir türde ve `ClassID` değerleri herhangi tür bağımsız değişkenleri.|  
|[Getclassıdınfo2 yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)|Üst modülü belirtilen genel sınıfının sınıfı için meta veri simgesi alır `ClassID` kendi üst sınıfın ve `ClassID` sınıfının varsa, her türü değişkeni.|  
|[GetClassLayout yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclasslayout-method.md)|Belirtilen sınıf tarafından tanımlanan alanların bellekte düzeni hakkındaki bilgileri alır. Diğer bir deyişle, bu yöntem sınıfın alanları uzaklıklarını alır.|  
|[Getcodeınfo2 yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)|Yerel kod belirtilen ile ilişkili kapsam alır `FunctionID`.|  
|[GetContextStaticAddress yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcontextstaticaddress-method.md)|Belirtilen bağlamı kapsamında belirtilen bağlam statik alan adresini alır.|  
|[GetFunctionFromTokenAndTypeArgs yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)|Alır `FunctionID` sınıfı içeren belirtilen meta veri simgesi kullanarak bir işlevin ve `ClassID` değerleri herhangi tür bağımsız değişkenleri.|  
|[Getfunctionınfo2 yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)|Üst sınıf, meta veri simgesi alır ve `ClassID` işlevinin varsa, her tür bağımsız değişkenin.|  
|[GetGenerationBounds yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md)|Çöp toplanan yığın nesli yapmak bellek bölümlerinin (öbek kesimleri) alır.|  
|[Getnotifiedexceptionclauseınfo yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)|Özel durum yan tümcesi için yerel adres ve çerçeve bilgilerini alır (`catch`/`finally`/`filter`) hakkında çalıştırılacak veya yalnızca çalıştırın.|  
|[GetObjectGeneration yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md)|Belirtilen nesne içeren öbek kesimini alır.|  
|[GetRVAStaticAddress yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getrvastaticaddress-method.md)|Belirtilen göreli sanal adres (RVA) adresini alır-static alan.|  
|[Getstaticfieldınfo yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstaticfieldinfo-method.md)|Belirtilen alan statiktir kapsamı alır.|  
|[GetStringLayout yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md)|Bir dize nesnesi düzeni hakkındaki bilgileri alır.|  
|[GetThreadAppDomain yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)|İçinde belirtilen iş parçacığı kod şu anda yürütüyor uygulama etki alanı Kimliğini alır.|  
|[GetThreadStaticAddress yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md)|Belirtilen iş parçacığı kapsamında belirtilen statik iş parçacığı alan adresini alır.|  
|[SetEnterLeaveFunctionHooks2 yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)|Profil Oluşturucu uygulanan işlevler "girin", "bırakın" ve "tailcall" kancaları yönetilen işlevlerin çağrılacak belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir profil oluşturucu bir yöntem çağrıları `ICorProfilerInfo2` olayı izlemeyi denetlemek ve bilgi istemek için CLR ile iletişim kurmak için arabirim.  
  
 Yöntemlerinin `ICorProfilerInfo2` arabirimi kullanarak ücretsiz iş parçacıklı model CLR tarafından uygulanır. Her yöntem, başarı veya hata durumunu göstermek için bir HRESULT döndürür. Olası dönüş kodları listesi için CorError.h dosyasına bakın.  
  
 CLR geçirmeden bir `ICorProfilerInfo2` Profil Oluşturucu'nın uygulaması kullanarak her kod profil oluşturucu başlatma sırasında arabirimine [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Kod profil oluşturucu sonra yöntemlerini çağırın `ICorProfilerInfo2` CLR denetiminde yürütülmekte olan yönetilen kodu hakkında bilgi almak için arabirim.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil oluşturma arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Icorprofilerınfo arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
