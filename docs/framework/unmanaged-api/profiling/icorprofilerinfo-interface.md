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
ms.openlocfilehash: da5a041e8a18420b4cf9962e4315683be8857711
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33462276"
---
# <a name="icorprofilerinfo-interface"></a>ICorProfilerInfo Arabirimi
Ortak dil çalışma olayı izleme denetlemek ve bilgi istemek için (CLR) ile iletişim kurmak için kod profil Oluşturucuları tarafından kullanım için yöntemleri sağlar.  
  
> [!NOTE]
>  Her bir yöntemin `ICorProfilerInfo` arabirimi başarı veya hata durumunu göstermek için bir HRESULT döndürür. CorError.h olası dönüş kodları listesi için bkz.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[BeginInprocDebugging Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md)|Başlatır hata ayıklama desteği işlemdeki. Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır.|  
|[EndInprocDebugging Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-endinprocdebugging-method.md)|İşlem içi hata ayıklama oturumu kapatır. Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır.|  
|[ForceGC Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)|Çalışma zamanı içinde gerçekleşmesi için atık toplama zorlar.|  
|[GetAppDomainInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)|Belirtilen uygulama etki alanı bilgilerini alır.|  
|[GetAssemblyInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getassemblyinfo-method.md)|Belirtilen derleme hakkındaki bilgileri alır.|  
|[GetClassFromObject Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromobject-method.md)|Alır `ClassID` , bir<br /><br /> verilen nesne, kendi `ObjectID`.|  
|[GetClassFromToken Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)|Meta veri simgesi verilen sınıf Kimliğini alır. Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır. Kullanım [Icorprofilerınfo2::getclassfromtokenandtypeargs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md) yöntemi yerine.|  
|[GetClassIDInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)|Üst modülü ve meta veri simgesi için belirtilen sınıf alır.|  
|[GetCodeInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)|Belirtilen işlev kimlikle ilişkili yerel kod kapsamını alır Bu yöntem artık kullanılmıyor. Kullanım [Icorprofilerınfo2::getcodeınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) yöntemi yerine.|  
|[GetCurrentThreadID Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)|Yönetilen iş parçacığı ise, geçerli iş parçacığının Kimliğini alır.|  
|[GetEventMask Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)|Profil Oluşturucu CLR olay bildirimlerini almak istediği geçerli olay kategorileri alır.|  
|[GetFunctionFromIP Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)|Yönetilen kod yönerge işaretçisi eşleyen bir `FunctionID`.|  
|[GetFunctionFromToken Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromtoken-method.md)|Bir işlev Kimliğini alır. Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır. Kullanım [Icorprofilerınfo2::getfunctionfromtokenandtypeargs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md) yöntemi yerine.|  
|[GetFunctionInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)|Üst sınıf ve meta verileri belirtilen işlevi için belirteç alır.|  
|[GetHandleFromThread Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gethandlefromthread-method.md)|Bir iş parçacığı kimliği için Win32 iş parçacığı tanıtıcı eşler.|  
|[GetILFunctionBody Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md)|Bir işaretçi bir yöntemin gövdesi Microsoft Ara dili (MSIL) kodda, kendi üst bilgisi başlangıç alır.|  
|[GetILFunctionBodyAllocator Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)|MSIL kodda bir yöntemin gövdesi değiştirme için kullanılacak bellek ayırmak için bir yöntem sağlayan bir arabirimi alır.|  
|[GetILToNativeMapping Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)|Bir harita MSIL uzaklıkları belirtilen işlevinde kod için yerel uzaklık için alır.|  
|[GetInprocInspectionInterface Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectioninterface-method.md)|Icordebugprocess arabirimi için sorgulanabilir bir nesneyi alır. Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır.|  
|[GetInprocInspectionIThisThread Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectionithisthread-method.md)|Icordebugthread arabirimi için sorgulanabilir bir nesneyi alır. Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır.|  
|[GetModuleInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)|Modül kimliği modülün dosya adı ve modülün üst derleme Kimliğini döndürür.|  
|[GetModuleMetaData Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)|Belirtilen modül eşleyen bir meta veri arabirimi örneğini alır.|  
|[GetObjectSize Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md)|Belirtilen nesnenin boyutu alır.|  
|[GetThreadContext Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)|Şu anda belirtilen iş parçacığı ile ilişkili bağlam kimliğini alır.|  
|[GetThreadInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadinfo-method.md)|Geçerli Win32 iş parçacığı kimliği için belirtilen iş parçacığı alır.|  
|[GetTokenAndMetadataFromFunction Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gettokenandmetadatafromfunction-method.md)|Meta veri simgesi ve belirteci karşı belirtilen işlevi için kullanılabilir meta veri arabirimi örneğini alır.|  
|[IsArrayClass Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)|Belirtilen sınıf bir dizi sınıf olup olmadığını belirler.|  
|[SetEnterLeaveFunctionHooks Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)|Profil Oluşturucu uygulanan işlevler "girin", "bırakın" ve "tailcall" kancaları yönetilen işlevlerin çağrılacak belirtir.|  
|[SetEventMask Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)|Profil Oluşturucu CLR bildirim almak istediği olay türlerini belirten bir değer ayarlar.|  
|[SetFunctionIDMapper Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)|Eşlenecek adlı profil oluşturucu uygulanan işlevini belirten `FunctionID` değerleri profil oluşturucu için 's geçirilen alternatif değerler için giriş/çıkış kancaları işlev.|  
|[SetFunctionReJIT Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionrejit-method.md)|Henüz uygulanmadı. Kullanmayın.|  
|[SetILFunctionBody Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)|Belirtilen modül belirtilen işlev gövdesi yerini alır.|  
|[SetILInstrumentedCodeMap Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)|Belirtilen işlevin özgün MSIL uzaklıklarını işlevin profil oluşturucu değiştiren MSIL yeni uzaklıklarını nasıl eşleme belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir profil oluşturucu bir yöntem çağrıları `ICorProfilerInfo` olayı izlemeyi denetlemek ve bilgi istemek için CLR ile iletişim kurmak için arabirim.  
  
 Yöntemlerinin `ICorProfilerInfo` arabirimi kullanarak ücretsiz iş parçacıklı model CLR tarafından uygulanır. Her yöntem, başarı veya hata durumunu göstermek için bir HRESULT döndürür. CorError.h olası dönüş kodları listesi için bkz.  
  
 CLR geçirir, Profil Oluşturucu'nın uygulaması [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md), bir `ICorProfilerInfo` her kod profil oluşturucu başlatma sırasında arabirimi. Kod profil oluşturucu sonra yöntemlerini çağırın `ICorProfilerInfo` CLR denetiminde yürütülmekte olan yönetilen kodu hakkında bilgi almak için arabirim.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
