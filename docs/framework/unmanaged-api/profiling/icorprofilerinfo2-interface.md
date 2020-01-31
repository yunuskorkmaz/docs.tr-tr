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
ms.openlocfilehash: 23fd44a6865b0487296f3ade37c1219e8feba288
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862587"
---
# <a name="icorprofilerinfo2-interface"></a>ICorProfilerInfo2 Arabirimi
Olay izlemeyi ve istek bilgilerini denetlemek için ortak dil çalışma zamanı (CLR) ile iletişim kurmak üzere kod profil oluşturucular kullanan yöntemler sağlar. `ICorProfilerInfo2` arabirimi [ICorProfilerInfo](icorprofilerinfo-interface.md) arabiriminin bir uzantısıdır. Diğer bir deyişle, .NET Framework sürüm 2,0 ve sonraki sürümlerde desteklenen yeni yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[DoStackSnapshot Yöntemi](icorprofilerinfo2-dostacksnapshot-method.md)|Profil oluşturucuya yönetilen çağrı çerçevelerini raporlamak için belirtilen iş parçacığının yığınını gösterir.|  
|[EnumModuleFrozenObjects Yöntemi](icorprofilerinfo2-enummodulefrozenobjects-method.md)|Belirtilen modüldeki dondurulmuş nesneler üzerinde yinelemeye izin veren bir Numaralandırıcı alır.|  
|[GetAppDomainStaticAddress Yöntemi](icorprofilerinfo2-getappdomainstaticaddress-method.md)|Belirtilen uygulama etki alanının kapsamındaki belirtilen uygulama etki alanı-statik alanının adresini alır.|  
|[GetArrayObjectInfo Yöntemi](icorprofilerinfo2-getarrayobjectinfo-method.md)|Bir dizi nesnesi hakkında ayrıntılı bilgi alır.|  
|[GetBoxClassLayout Yöntemi](icorprofilerinfo2-getboxclasslayout-method.md)|Kutulanmış belirtilen değer türünün sınıf düzeni hakkında bilgi alır.|  
|[GetClassFromTokenAndTypeArgs Yöntemi](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)|Tür bağımsız değişkenlerinin belirtilen meta veri belirtecini ve `ClassID` değerlerini kullanarak bir türün `ClassID` alır.|  
|[GetClassIDInfo2 Yöntemi](icorprofilerinfo2-getclassidinfo2-method.md)|Belirtilen genel sınıfın üst modülünü, sınıf için meta veri belirtecini, üst sınıfının `ClassID` ve varsa sınıfının her tür bağımsız değişkeni için `ClassID` alır.|  
|[GetClassLayout Yöntemi](icorprofilerinfo2-getclasslayout-method.md)|Belirtilen sınıf tarafından tanımlanan alanların bellek olarak düzeni hakkında bilgi alır. Diğer bir deyişle, bu yöntem sınıfın alanlarının uzaklıklarını alır.|  
|[GetCodeInfo2 Yöntemi](icorprofilerinfo2-getcodeinfo2-method.md)|Belirtilen `FunctionID`ilişkili yerel kod kapsamlarını alır.|  
|[GetContextStaticAddress Yöntemi](icorprofilerinfo2-getcontextstaticaddress-method.md)|Belirtilen bağlamın kapsamındaki belirtilen context-static alanının adresini alır.|  
|[GetFunctionFromTokenAndTypeArgs Yöntemi](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)|Belirtilen meta veri belirtecini kullanarak bir işlevin `FunctionID` alır, sınıfı ve tür bağımsız değişkenlerinin `ClassID` değerlerini.|  
|[GetFunctionInfo2 Yöntemi](icorprofilerinfo2-getfunctioninfo2-method.md)|Bir işlevin varsa, üst sınıfı, meta veri belirtecini ve her tür bağımsız değişkeninin `ClassID` alır.|  
|[GetGenerationBounds Yöntemi](icorprofilerinfo2-getgenerationbounds-method.md)|Atık toplanan yığının nesini oluşturan bellek bölgelerini (yığının kesimleri) alır.|  
|[GetNotifiedExceptionClauseInfo Yöntemi](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)|Çalıştırılmak üzere olan veya yalnızca çalıştırılmış olan Exception yan tümcesinin (`catch`/`finally`/`filter`) yerel adresini ve çerçeve bilgilerini alır.|  
|[GetObjectGeneration Yöntemi](icorprofilerinfo2-getobjectgeneration-method.md)|Belirtilen nesneyi içeren yığının segmentini alır.|  
|[GetRVAStaticAddress Yöntemi](icorprofilerinfo2-getrvastaticaddress-method.md)|Belirtilen göreli sanal adres (RVA)-statik alanının adresini alır.|  
|[GetStaticFieldInfo Yöntemi](icorprofilerinfo2-getstaticfieldinfo-method.md)|Belirtilen alanın statik olduğu kapsamı alır.|  
|[GetStringLayout Yöntemi](icorprofilerinfo2-getstringlayout-method.md)|Bir dize nesnesinin yerleşimi hakkında bilgi alır.|  
|[GetThreadAppDomain Yöntemi](icorprofilerinfo2-getthreadappdomain-method.md)|Belirtilen iş parçacığının kodu çalıştırmakta olduğu uygulama etki alanının KIMLIĞINI alır.|  
|[GetThreadStaticAddress Yöntemi](icorprofilerinfo2-getthreadstaticaddress-method.md)|Belirtilen iş parçacığının kapsamındaki belirtilen thread-static alanının adresini alır.|  
|[SetEnterLeaveFunctionHooks2 Yöntemi](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)|Yönetilen işlevlerin "Enter", "Leave" ve "cloncall" kancalarında çağrılacak Profil Oluşturucu uygulanmış işlevleri belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Profil Oluşturucu, olay izleme ve istek bilgilerini denetlemek üzere CLR ile iletişim kurmak için `ICorProfilerInfo2` arabirimindeki bir yöntemi çağırır.  
  
 `ICorProfilerInfo2` arabiriminin yöntemleri, ücretsiz iş parçacıklı model kullanılarak CLR tarafından uygulanır. Her yöntem, başarılı veya başarısız olduğunu göstermek için bir HRESULT döndürür. Olası dönüş kodlarının listesi için CorError. h dosyasına bakın.  
  
 CLR, başlatma sırasında, profil oluşturucunun [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md)uygulamasını kullanarak her kod profil oluşturucuya bir `ICorProfilerInfo2` arabirimini geçirir. Kod Profilcisi daha sonra CLR denetimi altında yürütülen yönetilen kod hakkında bilgi almak için `ICorProfilerInfo2` arabiriminin yöntemlerini çağırabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
