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
ms.openlocfilehash: b979b5f4ee849b96cd29b6c8e2e6a8932e88c182
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201721"
---
# <a name="icorprofilerinfo-interface"></a>ICorProfilerInfo Arabirimi
Ortak dil çalışma olayı izleme denetim ve bilgi istemek için (CLR) ile iletişim kurmak için kod profil Oluşturucuları tarafından kullanım için yöntemler sağlar.  
  
> [!NOTE]
>  Her bir yöntemin `ICorProfilerInfo` arabirimi başarısı veya başarısızlığı göstermek için HRESULT döndürür. CorError.h olası dönüş kodlarının bir listesi için bkz.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[BeginInprocDebugging Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md)|Başlatır-hata ayıklama desteği işlem. Bu yöntem .NET Framework 2.0 sürümünde artık kullanılmıyor.|  
|[EndInprocDebugging Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-endinprocdebugging-method.md)|Bir işlemde hata ayıklama oturumunu kapatır. Bu yöntem .NET Framework 2.0 sürümünde artık kullanılmıyor.|  
|[ForceGC Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)|Çalışma zamanı içinde gerçekleşmesi için çöp toplama zorlar.|  
|[GetAppDomainInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)|Belirtilen uygulama etki alanı hakkındaki bilgileri alır.|  
|[GetAssemblyInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getassemblyinfo-method.md)|Belirtilen derleme hakkındaki bilgileri alır.|  
|[GetClassFromObject Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromobject-method.md)|Alır `ClassID` , bir<br /><br /> verilen nesne, kendi `ObjectID`.|  
|[GetClassFromToken Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)|Meta veri belirteci verilen sınıfı Kimliğini alır. Bu yöntem .NET Framework 2.0 sürümünde artık kullanılmıyor. Kullanım [Icorprofilerınfo2::getclassfromtokenandtypeargs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) yöntemi yerine.|  
|[GetClassIDInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)|Üst için belirtilen sınıf modülü ve meta veri belirteci alır.|  
|[GetCodeInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)|Belirtilen işlev kimlikle ilişkili yerel kod kapsamını alır Bu yöntem artık kullanılmıyor. Kullanım [Icorprofilerınfo2::getcodeınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) yöntemi yerine.|  
|[GetCurrentThreadID Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)|Yönetilen iş parçacığı ise, geçerli iş parçacığı Kimliğini alır.|  
|[GetEventMask Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)|Profil Oluşturucu CLR'den olay bildirimlerini almak istediği geçerli olay kategorileri alır.|  
|[GetFunctionFromIP Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)|Yönetilen kod yönerge işaretçisi eşleyen bir `FunctionID`.|  
|[GetFunctionFromToken Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromtoken-method.md)|Bir işlev Kimliğini alır. Bu yöntem .NET Framework 2.0 sürümünde artık kullanılmıyor. Kullanım [Icorprofilerınfo2::getfunctionfromtokenandtypeargs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) yöntemi yerine.|  
|[GetFunctionInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)|Belirtilen işlev için üst sınıf ve meta veri belirtecini alır.|  
|[GetHandleFromThread Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gethandlefromthread-method.md)|Bir iş parçacığının kimliği bir Win32 iş parçacığı tutamacı eşler.|  
|[GetILFunctionBody Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md)|Bir işaretçi bir yöntem gövdesi ile başlayarak, üst bilgisi, Microsoft Ara dili (MSIL) kodu alır.|  
|[GetILFunctionBodyAllocator Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)|MSIL kodunun bir yöntem gövdesi değiştirme için kullanılacak bellek ayırmak için bir yöntem sağlayan bir arabirimi alır.|  
|[GetILToNativeMapping Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)|Harita belirtilen işlevinde kodun yerel uzaklıklar için MSIL uzaklıkları alır.|  
|[GetInprocInspectionInterface Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectioninterface-method.md)|Icordebugprocess arabirimi sorgulanabilir bir nesne alır. Bu yöntem .NET Framework 2.0 sürümünde artık kullanılmıyor.|  
|[GetInprocInspectionIThisThread Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectionithisthread-method.md)|Icordebugthread arabirimi sorgulanabilir bir nesne alır. Bu yöntem .NET Framework 2.0 sürümünde artık kullanılmıyor.|  
|[GetModuleInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)|Bir modül kimliği söz konusu modülün dosya adı ve modülün üst derleme Kimliğini döndürür.|  
|[GetModuleMetaData Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)|Belirtilen modül için eşleşen bir meta veri arabirimi örneği alır.|  
|[GetObjectSize Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md)|Belirtilen nesnenin boyutunu alır.|  
|[GetThreadContext Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)|Şu anda belirtilen iş parçacığıyla ilişkilendirilmiş bağlam kimliğini alır.|  
|[GetThreadInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadinfo-method.md)|Belirtilen iş parçacığı için geçerli bir Win32 iş parçacığı kimliğini alır.|  
|[GetTokenAndMetadataFromFunction Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gettokenandmetadatafromfunction-method.md)|Meta veri belirteci ve belirteci karşı belirtilen işlev için kullanılabilir meta veri arabirimi örneğini alır.|  
|[IsArrayClass Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)|Array sınıfı belirtilen sınıf olup olmadığını belirler.|  
|[SetEnterLeaveFunctionHooks Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)|Profil Oluşturucu uygulanan işlevleri "enter", "Ayrıl" ve "tailcall" hooks yönetilen işlevlerin çağrılmasına belirtir.|  
|[SetEventMask Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)|Profil Oluşturucu CLR'den bildirim almak istediği olaylara türlerini belirten bir değeri ayarlar.|  
|[SetFunctionIDMapper Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)|Profil Oluşturucu uygulanan eşlemek için çağrılacak işlevi belirtir `FunctionID` değerleri oluşturucunun geçirilen alternatif, işlev girişi/çıkışı kancaları.|  
|[SetFunctionReJIT Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionrejit-method.md)|Henüz uygulanmadı. Kullanmayın.|  
|[SetILFunctionBody Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)|Belirtilen modüldeki belirtilen işlev gövdesinin yerini alır.|  
|[SetILInstrumentedCodeMap Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)|Belirtilen işlevin özgün MSIL uzaklıklarını işlevin MSIL profil oluşturucu değiştiren yeni uzaklıklarını için nasıl eşleştiği belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir profil oluşturucu bir yöntem çağrıları `ICorProfilerInfo` olayı izlemeyi denetlemek ve bilgi istemek için CLR ile iletişim kurmak için arabirim.  
  
 Yöntemlerinin `ICorProfilerInfo` arabirimi serbest iş parçacıklı modelini kullanarak CLR tarafından uygulanır. Her yöntem başarısı veya başarısızlığı göstermek için HRESULT döndürür. CorError.h olası dönüş kodlarının bir listesi için bkz.  
  
 CLR geçirir, profil oluşturucunun uygulaması [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)e `ICorProfilerInfo` her kod profil oluşturucu başlatma sırasında arabirim. Bir kod profil oluşturucu ardından yöntemlerini çağırabilirsiniz `ICorProfilerInfo` CLR denetimi altında yürütülmekte olan yönetilen kodu hakkında bilgi almak için arabirim.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
