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
ms.openlocfilehash: 4480fefa51eec2f2751bd71910db87b72a1c32cf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496736"
---
# <a name="icorprofilerinfo2-interface"></a>ICorProfilerInfo2 Arabirimi
Olay izlemeyi ve istek bilgilerini denetlemek için ortak dil çalışma zamanı (CLR) ile iletişim kurmak üzere kod profil oluşturucular kullanan yöntemler sağlar. `ICorProfilerInfo2`Arabirim, [ICorProfilerInfo](icorprofilerinfo-interface.md) arabiriminin bir uzantısıdır. Diğer bir deyişle, .NET Framework sürüm 2,0 ve sonraki sürümlerde desteklenen yeni yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Description|  
|------------|-----------------|  
|[DoStackSnapshot Yöntemi](icorprofilerinfo2-dostacksnapshot-method.md)|Profil oluşturucuya yönetilen çağrı çerçevelerini raporlamak için belirtilen iş parçacığının yığınını gösterir.|  
|[EnumModuleFrozenObjects Yöntemi](icorprofilerinfo2-enummodulefrozenobjects-method.md)|Belirtilen modüldeki dondurulmuş nesneler üzerinde yinelemeye izin veren bir Numaralandırıcı alır.|  
|[GetAppDomainStaticAddress Yöntemi](icorprofilerinfo2-getappdomainstaticaddress-method.md)|Belirtilen uygulama etki alanının kapsamındaki belirtilen uygulama etki alanı-statik alanının adresini alır.|  
|[GetArrayObjectInfo Yöntemi](icorprofilerinfo2-getarrayobjectinfo-method.md)|Bir dizi nesnesi hakkında ayrıntılı bilgi alır.|  
|[GetBoxClassLayout Yöntemi](icorprofilerinfo2-getboxclasslayout-method.md)|Kutulanmış belirtilen değer türünün sınıf düzeni hakkında bilgi alır.|  
|[GetClassFromTokenAndTypeArgs Yöntemi](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)|`ClassID`Belirtilen meta veri belirtecini ve `ClassID` tür bağımsız değişkenlerinin değerlerini kullanarak bir türün türünü alır.|  
|[GetClassIDInfo2 Yöntemi](icorprofilerinfo2-getclassidinfo2-method.md)|Belirtilen genel sınıfın üst modülünü, sınıfının meta veri belirtecini, `ClassID` üst sınıfını ve varsa `ClassID` sınıfının her tür bağımsız değişkenini alır.|  
|[GetClassLayout Yöntemi](icorprofilerinfo2-getclasslayout-method.md)|Belirtilen sınıf tarafından tanımlanan alanların bellek olarak düzeni hakkında bilgi alır. Diğer bir deyişle, bu yöntem sınıfın alanlarının uzaklıklarını alır.|  
|[GetCodeInfo2 Yöntemi](icorprofilerinfo2-getcodeinfo2-method.md)|Belirtilen yerel kod kapsamlarını alır, bununla ilişkili `FunctionID` .|  
|[GetContextStaticAddress Yöntemi](icorprofilerinfo2-getcontextstaticaddress-method.md)|Belirtilen bağlamın kapsamındaki belirtilen context-static alanının adresini alır.|  
|[GetFunctionFromTokenAndTypeArgs Yöntemi](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)|`FunctionID`Belirtilen meta veri belirtecini, sınıfını ve `ClassID` tür bağımsız değişkenlerinin değerlerini kullanarak bir işlevi alır.|  
|[GetFunctionInfo2 Yöntemi](icorprofilerinfo2-getfunctioninfo2-method.md)|Bir işlevin varsa, üst sınıfı, meta veri belirtecini ve `ClassID` her tür bağımsız değişkenini alır.|  
|[GetGenerationBounds Yöntemi](icorprofilerinfo2-getgenerationbounds-method.md)|Atık toplanan yığının nesini oluşturan bellek bölgelerini (yığının kesimleri) alır.|  
|[GetNotifiedExceptionClauseInfo Yöntemi](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)|`catch` / `finally` / `filter` Çalıştırılmak üzere olan veya yalnızca çalıştırılmış olan özel durum yan tümcesinin () yerel adresini ve çerçeve bilgilerini alır.|  
|[GetObjectGeneration Yöntemi](icorprofilerinfo2-getobjectgeneration-method.md)|Belirtilen nesneyi içeren yığının segmentini alır.|  
|[GetRVAStaticAddress Yöntemi](icorprofilerinfo2-getrvastaticaddress-method.md)|Belirtilen göreli sanal adres (RVA)-statik alanının adresini alır.|  
|[GetStaticFieldInfo Yöntemi](icorprofilerinfo2-getstaticfieldinfo-method.md)|Belirtilen alanın statik olduğu kapsamı alır.|  
|[GetStringLayout Yöntemi](icorprofilerinfo2-getstringlayout-method.md)|Bir dize nesnesinin yerleşimi hakkında bilgi alır.|  
|[GetThreadAppDomain Yöntemi](icorprofilerinfo2-getthreadappdomain-method.md)|Belirtilen iş parçacığının kodu çalıştırmakta olduğu uygulama etki alanının KIMLIĞINI alır.|  
|[GetThreadStaticAddress Yöntemi](icorprofilerinfo2-getthreadstaticaddress-method.md)|Belirtilen iş parçacığının kapsamındaki belirtilen thread-static alanının adresini alır.|  
|[SetEnterLeaveFunctionHooks2 Yöntemi](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)|Yönetilen işlevlerin "Enter", "Leave" ve "cloncall" kancalarında çağrılacak Profil Oluşturucu uygulanmış işlevleri belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Profil Oluşturucu, `ICorProfilerInfo2` olay izleme ve istek bilgilerini denetlemek üzere clr ile iletişim kurmak için arabirimdeki bir yöntemi çağırır.  
  
 Arabirim yöntemleri, `ICorProfilerInfo2` clr tarafından ücretsiz iş parçacıklı model kullanılarak uygulanır. Her yöntem, başarılı veya başarısız olduğunu göstermek için bir HRESULT döndürür. Olası dönüş kodlarının listesi için CorError. h dosyasına bakın.  
  
 CLR, `ICorProfilerInfo2` başlatma sırasında, profil oluşturucunun [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md)uygulamasını kullanarak her kod profil oluşturucuya bir arabirim geçirir. Kod Profilcisi daha sonra, `ICorProfilerInfo2` clr denetimi altında yürütülen yönetilen kod hakkında bilgi almak için arabirimin yöntemlerini çağırabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
