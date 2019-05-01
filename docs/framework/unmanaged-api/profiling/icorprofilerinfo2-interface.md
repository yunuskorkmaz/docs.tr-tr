---
title: ICorProfilerInfo2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2
helpviewer_keywords:
- ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: 91bd49b6-4d12-494f-a8f1-2f251e8c65e3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3476a338191a4af9cc01b7e44456f1bd20f52a10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796552"
---
# <a name="icorprofilerinfo2-interface"></a>ICorProfilerInfo2 Arabirimi
İstek bilgilerini ve ortak dil çalışma zamanı olayı izlemeyi denetlemek için (CLR) ile iletişim kurmak için kod profil oluşturucuları kullanmak için yöntemler sağlar. `ICorProfilerInfo2` Arabirimi uzantısıdır [Icorprofilerınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) arabirimi. Diğer bir deyişle, .NET Framework sürüm 2.0 ve sonraki sürümlerinde desteklenen yeni yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[DoStackSnapshot Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)|Yönetilen çağrı çerçeveler için profil oluşturucu rapor için belirtilen iş parçacığı yığını gösterecektir.|  
|[EnumModuleFrozenObjects Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)|Belirtilen modüldeki donmuş nesneler üzerinde yineleme sağlayan bir numaralandırıcıyı alır.|  
|[GetAppDomainStaticAddress Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getappdomainstaticaddress-method.md)|Belirtilen uygulama etki alanı kapsamı içinde belirtilen uygulama etki alanı statik alanı adresini alır.|  
|[GetArrayObjectInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getarrayobjectinfo-method.md)|Bir dizi nesnesi hakkında ayrıntılı bilgiler alır.|  
|[GetBoxClassLayout Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getboxclasslayout-method.md)|Kutulanmaz belirtilen değer türü için sınıf düzeni hakkındaki bilgileri alır.|  
|[GetClassFromTokenAndTypeArgs Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)|Alır `ClassID` belirtilen meta veri belirteci kullanarak türü ve `ClassID` herhangi bir değer türü bağımsız değişkenler.|  
|[GetClassIDInfo2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)|Üst modülü belirtilen genel sınıfının, sınıf için meta veri belirteci alır `ClassID` kendi üst sınıfın ve `ClassID` her tür bağımsız değişkeni, sınıfın varsa.|  
|[GetClassLayout Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclasslayout-method.md)|Belirtilen sınıf tarafından tanımlanan alanların bellekte Düzen hakkında bilgi alır. Diğer bir deyişle, bu yöntem, sınıfın alanlarının uzaklıkları alır.|  
|[GetCodeInfo2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)|Yerel kod belirtilen ile ilişkili kapsam alır `FunctionID`.|  
|[GetContextStaticAddress Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcontextstaticaddress-method.md)|Belirtilen bağlamı kapsamında belirtilen bağlam statik alanı adresini alır.|  
|[GetFunctionFromTokenAndTypeArgs Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)|Alır `FunctionID` sınıf içeren belirtilen meta veri belirteci kullanarak bir işlevin ve `ClassID` herhangi bir değer türü bağımsız değişkenler.|  
|[GetFunctionInfo2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)|Üst sınıfın, meta veri belirteci alır ve `ClassID` işlevinin varsa, her tür bağımsız değişkeninin.|  
|[GetGenerationBounds Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md)|Nesil atık olarak toplanmış yığınla yapmak bellek bölgeleri (yığın kesimlerini) alır.|  
|[GetNotifiedExceptionClauseInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)|Özel durum yan tümcesinin yerel adres ve çerçeve bilgilerini alır (`catch`/`finally`/`filter`) hakkında çalıştırılacak veya yalnızca çalıştırın.|  
|[GetObjectGeneration Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md)|Belirtilen nesneyi içeren yığın kesimini alır.|  
|[GetRVAStaticAddress Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getrvastaticaddress-method.md)|Belirtilen göreli sanal adres (RVA) adresini alır-statik alan.|  
|[GetStaticFieldInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstaticfieldinfo-method.md)|Belirtilen alan statik kapsamı alır.|  
|[GetStringLayout Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md)|Bir dize nesnesinin düzeni hakkındaki bilgileri alır.|  
|[GetThreadAppDomain Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)|İçinde belirtilen iş parçacığı şu anda kod yürüttüğünü uygulama etki alanı Kimliğini alır.|  
|[GetThreadStaticAddress Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md)|Belirtilen iş parçacığı kapsamında belirtilen statik iş parçacığı alanı adresini alır.|  
|[SetEnterLeaveFunctionHooks2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)|Profil Oluşturucu uygulanan işlevleri "enter", "Ayrıl" ve "tailcall" hooks yönetilen işlevlerin çağrılmasına belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir profil oluşturucu bir yöntem çağrıları `ICorProfilerInfo2` olayı izlemeyi denetlemek ve bilgi istemek için CLR ile iletişim kurmak için arabirim.  
  
 Yöntemlerinin `ICorProfilerInfo2` arabirimi serbest iş parçacıklı modelini kullanarak CLR tarafından uygulanır. Her yöntem başarısı veya başarısızlığı göstermek için HRESULT döndürür. Olası dönüş kodları listesi için CorError.h dosyasına bakın.  
  
 CLR geçirmeden bir `ICorProfilerInfo2` profil oluşturucu uygulamasını kullanarak her kod profil oluşturucu başlatma sırasında arabirimine [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Bir kod profil oluşturucu ardından yöntemlerini çağırabilirsiniz `ICorProfilerInfo2` CLR denetimi altında yürütülmekte olan yönetilen kodu hakkında bilgi almak için arabirim.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
