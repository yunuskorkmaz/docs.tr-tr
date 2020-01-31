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
ms.openlocfilehash: b8cba2b1a1f206392a59f8bc9b968e725e0ce6ee
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869318"
---
# <a name="icorprofilerinfo-interface"></a>ICorProfilerInfo Arabirimi
Olay izlemeyi ve istek bilgilerini denetlemek için ortak dil çalışma zamanı (CLR) ile iletişim kurmak üzere kod profil oluşturucular tarafından kullanılacak yöntemler sağlar.  
  
> [!NOTE]
> `ICorProfilerInfo` arabirimindeki her yöntem, başarılı veya başarısız olduğunu göstermek için bir HRESULT döndürür. Olası dönüş kodlarının bir listesi için bkz. CorError. h.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[BeginInprocDebugging Yöntemi](icorprofilerinfo-begininprocdebugging-method.md)|İşlem içi hata ayıklama desteğini başlatır. Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.|  
|[EndInprocDebugging Yöntemi](icorprofilerinfo-endinprocdebugging-method.md)|İşlem içi hata ayıklama oturumunu kapatır. Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.|  
|[ForceGC Yöntemi](icorprofilerinfo-forcegc-method.md)|Çöp toplamayı çalışma zamanı içinde gerçekleşmeye zorlar.|  
|[GetAppDomainInfo Yöntemi](icorprofilerinfo-getappdomaininfo-method.md)|Belirtilen uygulama etki alanı hakkında bilgi alır.|  
|[GetAssemblyInfo Yöntemi](icorprofilerinfo-getassemblyinfo-method.md)|Belirtilen derleme hakkında bilgi alır.|  
|[GetClassFromObject Yöntemi](icorprofilerinfo-getclassfromobject-method.md)|`ClassID` alır<br /><br /> nesnesini `ObjectID`verildiğinde.|  
|[GetClassFromToken Yöntemi](icorprofilerinfo-getclassfromtoken-method.md)|Meta veri belirteci verilen sınıfın KIMLIĞINI alır. Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor. Bunun yerine [ICorProfilerInfo2:: GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) metodunu kullanın.|  
|[GetClassIDInfo Yöntemi](icorprofilerinfo-getclassidinfo-method.md)|Belirtilen sınıf için üst modülü ve meta veri belirtecini alır.|  
|[GetCodeInfo Yöntemi](icorprofilerinfo-getcodeinfo-method.md)|Belirtilen işlev KIMLIĞIYLE ilişkili yerel kod kapsamını alır. Bu yöntem artık kullanılmıyor. Bunun yerine [ICorProfilerInfo2:: GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) yöntemini kullanın.|  
|[GetCurrentThreadID Yöntemi](icorprofilerinfo-getcurrentthreadid-method.md)|Yönetilen bir iş parçacığı ise, geçerli iş parçacığının KIMLIĞINI alır.|  
|[GetEventMask Yöntemi](icorprofilerinfo-geteventmask-method.md)|Profil oluşturucunun CLR 'den olay bildirimleri almak istediği geçerli olay kategorilerini alır.|  
|[GetFunctionFromIP Yöntemi](icorprofilerinfo-getfunctionfromip-method.md)|Yönetilen bir kod yönerge işaretçisini `FunctionID`eşler.|  
|[GetFunctionFromToken Yöntemi](icorprofilerinfo-getfunctionfromtoken-method.md)|Bir işlevin KIMLIĞINI alır. Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor. Bunun yerine [ICorProfilerInfo2:: GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) metodunu kullanın.|  
|[GetFunctionInfo Yöntemi](icorprofilerinfo-getfunctioninfo-method.md)|Belirtilen işlev için üst sınıfı ve meta veri belirtecini alır.|  
|[GetHandleFromThread Yöntemi](icorprofilerinfo-gethandlefromthread-method.md)|Bir iş parçacığının KIMLIĞINI bir Win32 iş parçacığı tanıtıcısına eşler.|  
|[GetILFunctionBody Yöntemi](icorprofilerinfo-getilfunctionbody-method.md)|Üst bilgisinden başlayarak, Microsoft ara dili (MSIL) kodundaki bir yöntemin gövdesine yönelik bir işaretçi alır.|  
|[GetILFunctionBodyAllocator Yöntemi](icorprofilerinfo-getilfunctionbodyallocator-method.md)|MSIL kodunda bir yöntemin gövdesini takas etmek için kullanılacak belleği ayırmak üzere bir yöntemi sağlayan bir arabirim alır.|  
|[GetILToNativeMapping Yöntemi](icorprofilerinfo-getiltonativemapping-method.md)|Belirtilen işlevde bulunan kod için MSIL uzaklıklarından yerel uzaklıklara bir eşleme alır.|  
|[GetInprocInspectionInterface Yöntemi](icorprofilerinfo-getinprocinspectioninterface-method.md)|ICorDebugProcess arabirimi için sorgulanabilen bir nesne alır. Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.|  
|[GetInprocInspectionIThisThread Yöntemi](icorprofilerinfo-getinprocinspectionithisthread-method.md)|ICorDebugThread arabirimi için sorgulanabilen bir nesne alır. Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.|  
|[GetModuleInfo Yöntemi](icorprofilerinfo-getmoduleinfo-method.md)|Bir modül KIMLIĞI verildiğinde, modülün dosya adını ve modülün üst derleme KIMLIĞINI döndürür.|  
|[GetModuleMetaData Yöntemi](icorprofilerinfo-getmodulemetadata-method.md)|Belirtilen modülle eşlenen meta veri arabirimi örneğini alır.|  
|[GetObjectSize Yöntemi](icorprofilerinfo-getobjectsize-method.md)|Belirtilen nesnenin boyutunu alır.|  
|[GetThreadContext Yöntemi](icorprofilerinfo-getthreadcontext-method.md)|Belirtilen iş parçacığıyla Şu anda ilişkili olan bağlam Kimliğini alır.|  
|[GetThreadInfo Yöntemi](icorprofilerinfo-getthreadinfo-method.md)|Belirtilen iş parçacığı için geçerli Win32 iş parçacığı kimliğini alır.|  
|[GetTokenAndMetadataFromFunction Yöntemi](icorprofilerinfo-gettokenandmetadatafromfunction-method.md)|Belirtilen işlev için belirtece karşı kullanılabilecek meta veri belirtecini ve bir meta veri arabirimi örneğini alır.|  
|[IsArrayClass Yöntemi](icorprofilerinfo-isarrayclass-method.md)|Belirtilen sınıfın bir dizi sınıfı olup olmadığını belirler.|  
|[SetEnterLeaveFunctionHooks Yöntemi](icorprofilerinfo-setenterleavefunctionhooks-method.md)|Yönetilen işlevlerin "Enter", "Leave" ve "cloncall" kancalarında çağrılacak Profil Oluşturucu uygulanmış işlevleri belirtir.|  
|[SetEventMask Yöntemi](icorprofilerinfo-seteventmask-method.md)|Profil oluşturucunun CLR 'den bildirim almak istediği olay türlerini belirten bir değer ayarlar.|  
|[SetFunctionIDMapper Yöntemi](icorprofilerinfo-setfunctionidmapper-method.md)|Profil oluşturucunun işlev girişine/çıkış kancalarına geçirilen `FunctionID` değerlerini alternatif değerlerle eşlemek için çağrılacak Profil Oluşturucu uygulanmış işlevi belirtir.|  
|[SetFunctionReJIT Yöntemi](icorprofilerinfo-setfunctionrejit-method.md)|Uygulanmadı. Kullanmayın.|  
|[SetILFunctionBody Yöntemi](icorprofilerinfo-setilfunctionbody-method.md)|Belirtilen modüldeki belirtilen işlevin gövdesini değiştirir.|  
|[SetILInstrumentedCodeMap Yöntemi](icorprofilerinfo-setilinstrumentedcodemap-method.md)|Belirtilen işlevin özgün MSIL 'in, işlevin profiler-modified MSIL 'in yeni uzaklıklardır nasıl eşlendiğini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Profil Oluşturucu, olay izleme ve istek bilgilerini denetlemek üzere CLR ile iletişim kurmak için `ICorProfilerInfo` arabirimindeki bir yöntemi çağırır.  
  
 `ICorProfilerInfo` arabiriminin yöntemleri, ücretsiz iş parçacıklı model kullanılarak CLR tarafından uygulanır. Her yöntem, başarılı veya başarısız olduğunu göstermek için bir HRESULT döndürür. Olası dönüş kodlarının bir listesi için bkz. CorError. h.  
  
 CLR, başlatma sırasında her kod profil Oluşturucu için bir `ICorProfilerInfo` arabirimi olan [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md)uygulaması aracılığıyla başarılı oldu. Kod Profilcisi daha sonra CLR denetimi altında yürütülen yönetilen kod hakkında bilgi almak için `ICorProfilerInfo` arabiriminin yöntemlerini çağırabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerInfo2 Arabirimi](icorprofilerinfo2-interface.md)
