---
title: ICorProfilerInfo Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo
helpviewer_keywords:
- ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: eb4e4ce0-06e7-4469-bbc4-edc2eb5da4b1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b82d9ac610cb393696ef94fb797a48b737b0231
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965741"
---
# <a name="icorprofilerinfo-interface"></a>ICorProfilerInfo Arabirimi
Olay izlemeyi ve istek bilgilerini denetlemek için ortak dil çalışma zamanı (CLR) ile iletişim kurmak üzere kod profil oluşturucular tarafından kullanılacak yöntemler sağlar.  
  
> [!NOTE]
> Arabirimdeki her yöntem, `ICorProfilerInfo` başarılı veya başarısız olduğunu göstermek için bir hresult döndürür. Olası dönüş kodlarının bir listesi için bkz. CorError. h.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[BeginInprocDebugging Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md)|İşlem içi hata ayıklama desteğini başlatır. Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.|  
|[EndInprocDebugging Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-endinprocdebugging-method.md)|İşlem içi hata ayıklama oturumunu kapatır. Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.|  
|[ForceGC Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)|Çöp toplamayı çalışma zamanı içinde gerçekleşmeye zorlar.|  
|[GetAppDomainInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)|Belirtilen uygulama etki alanı hakkında bilgi alır.|  
|[GetAssemblyInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getassemblyinfo-method.md)|Belirtilen derleme hakkında bilgi alır.|  
|[GetClassFromObject Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromobject-method.md)|`ClassID` Bir<br /><br /> `ObjectID`nesnesi.|  
|[GetClassFromToken Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)|Meta veri belirteci verilen sınıfın KIMLIĞINI alır. Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor. Bunun yerine [ICorProfilerInfo2:: GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) metodunu kullanın.|  
|[GetClassIDInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)|Belirtilen sınıf için üst modülü ve meta veri belirtecini alır.|  
|[GetCodeInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)|Belirtilen işlev KIMLIĞIYLE ilişkili yerel kod kapsamını alır. Bu yöntem artık kullanılmıyor. Bunun yerine [ICorProfilerInfo2:: GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) yöntemini kullanın.|  
|[GetCurrentThreadID Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)|Yönetilen bir iş parçacığı ise, geçerli iş parçacığının KIMLIĞINI alır.|  
|[GetEventMask Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)|Profil oluşturucunun CLR 'den olay bildirimleri almak istediği geçerli olay kategorilerini alır.|  
|[GetFunctionFromIP Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)|Yönetilen bir kod yönerge işaretçisini bir `FunctionID`ile eşler.|  
|[GetFunctionFromToken Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromtoken-method.md)|Bir işlevin KIMLIĞINI alır. Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor. Bunun yerine [ICorProfilerInfo2:: GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) metodunu kullanın.|  
|[GetFunctionInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)|Belirtilen işlev için üst sınıfı ve meta veri belirtecini alır.|  
|[GetHandleFromThread Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gethandlefromthread-method.md)|Bir iş parçacığının KIMLIĞINI bir Win32 iş parçacığı tanıtıcısına eşler.|  
|[GetILFunctionBody Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md)|Üst bilgisinden başlayarak, Microsoft ara dili (MSIL) kodundaki bir yöntemin gövdesine yönelik bir işaretçi alır.|  
|[GetILFunctionBodyAllocator Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)|MSIL kodunda bir yöntemin gövdesini takas etmek için kullanılacak belleği ayırmak üzere bir yöntemi sağlayan bir arabirim alır.|  
|[GetILToNativeMapping Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)|Belirtilen işlevde bulunan kod için MSIL uzaklıklarından yerel uzaklıklara bir eşleme alır.|  
|[GetInprocInspectionInterface Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectioninterface-method.md)|ICorDebugProcess arabirimi için sorgulanabilen bir nesne alır. Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.|  
|[GetInprocInspectionIThisThread Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectionithisthread-method.md)|ICorDebugThread arabirimi için sorgulanabilen bir nesne alır. Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.|  
|[GetModuleInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)|Bir modül KIMLIĞI verildiğinde, modülün dosya adını ve modülün üst derleme KIMLIĞINI döndürür.|  
|[GetModuleMetaData Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)|Belirtilen modülle eşlenen meta veri arabirimi örneğini alır.|  
|[GetObjectSize Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md)|Belirtilen nesnenin boyutunu alır.|  
|[GetThreadContext Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)|Belirtilen iş parçacığıyla Şu anda ilişkili olan bağlam Kimliğini alır.|  
|[GetThreadInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadinfo-method.md)|Belirtilen iş parçacığı için geçerli Win32 iş parçacığı kimliğini alır.|  
|[GetTokenAndMetadataFromFunction Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gettokenandmetadatafromfunction-method.md)|Belirtilen işlev için belirtece karşı kullanılabilecek meta veri belirtecini ve bir meta veri arabirimi örneğini alır.|  
|[IsArrayClass Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)|Belirtilen sınıfın bir dizi sınıfı olup olmadığını belirler.|  
|[SetEnterLeaveFunctionHooks Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)|Yönetilen işlevlerin "Enter", "Leave" ve "cloncall" kancalarında çağrılacak Profil Oluşturucu uygulanmış işlevleri belirtir.|  
|[SetEventMask Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)|Profil oluşturucunun CLR 'den bildirim almak istediği olay türlerini belirten bir değer ayarlar.|  
|[SetFunctionIDMapper Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)|Profil oluşturucunun işlev girişine/çıkış kancalarına geçirilen değerleri alternatif değerlerle `FunctionID` eşlemek için çağrılacak Profil Oluşturucu uygulanmış işlevi belirtir.|  
|[SetFunctionReJIT Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionrejit-method.md)|Uygulanmadı. Kullanmayın.|  
|[SetILFunctionBody Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)|Belirtilen modüldeki belirtilen işlevin gövdesini değiştirir.|  
|[SetILInstrumentedCodeMap Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)|Belirtilen işlevin özgün MSIL 'in, işlevin profiler-modified MSIL 'in yeni uzaklıklardır nasıl eşlendiğini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Profil Oluşturucu, olay izleme ve istek `ICorProfilerInfo` bilgilerini denetlemek üzere clr ile iletişim kurmak için arabirimdeki bir yöntemi çağırır.  
  
 `ICorProfilerInfo` Arabirim yöntemleri, CLR tarafından ücretsiz iş parçacıklı model kullanılarak uygulanır. Her yöntem, başarılı veya başarısız olduğunu göstermek için bir HRESULT döndürür. Olası dönüş kodlarının bir listesi için bkz. CorError. h.  
  
 CLR, profil oluşturucunun [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)uygulaması aracılığıyla, başlatma sırasında her kod Profilcisi için bir `ICorProfilerInfo` arabirim aracılığıyla geçer. Kod Profilcisi daha sonra, clr denetimi altında `ICorProfilerInfo` yürütülen yönetilen kod hakkında bilgi almak için arabirimin yöntemlerini çağırabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorProf. IDL, CorProf. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
