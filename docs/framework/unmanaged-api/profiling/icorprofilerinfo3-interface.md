---
title: ICorProfilerInfo3 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3
helpviewer_keywords:
- ICorProfilerInfo3 interface [.NET Framework profiling]
ms.assetid: 044a262f-0fa7-485d-b0c1-64cdc359c654
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7b523c5819994e6da0332188311b4b631e3f9072
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178769"
---
# <a name="icorprofilerinfo3-interface"></a>ICorProfilerInfo3 Arabirimi
Kod profil oluşturucuları (CLR) olayı izlemeyi denetlemek ve bilgi istemek için ortak dil çalışma zamanıyla iletişim kurmak için yöntemler sağlar. `ICorProfilerInfo3` Arabirimi uzantısıdır [Icorprofilerınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) arabirimi. Destekleyen yeni yöntemler sağlar [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] ve sonraki sürümler.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumJITedFunctions Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)|Tüm daha önce JIT olarak derlenmiş işlevler için bir numaralandırıcı döndürür.|  
|[EnumModules Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)|Sıralı olarak uygulamasına yüklü yönetilen modülleri koleksiyonu üzerinden yineleme yapmak için yöntemler sağlayan bir numaralandırıcı döndürür.|  
|[GetAppDomainsContainingModule Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getappdomainscontainingmodule-method.md)|Belirtilen modül yüklenmiş olan uygulama etki alanları tanımlayıcılarını alır.|  
|[GetFunctionEnter3Info Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)|Profil Oluşturucu tarafından bildirilen işlev yığın çerçeve ve bağımsız değişken bilgilerini sağlar [Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) işlev; yalnızca sırasında çağrılabilir `FunctionEnter3WithInfo` geri çağırma.|  
|[GetFunctionLeave3Info Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)|Yığın çerçevesi ve Profil Oluşturucu tarafından bildirilen işlevin dönüş değeri sağlar [Functionleave3withınfo işlevi](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) işlev; yalnızca sırasında çağrılabilir `FunctionLeave3WithInfo` geri çağırma.|  
|[GetFunctionTailcall3Info Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md)|Profil Oluşturucu tarafından bildirilen işlev yığın çerçevesinde sağlar [Functiontailcall3withınfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) işlev; yalnızca sırasında çağrılabilir `FunctionTailcall3WithInfo` geri çağırma.|  
|[GetModuleInfo2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)|Derleme ve modül özelliklerini açıklayan bir bit maskesi, bir modül kimliği modül, modülün üst kimliği dosya adını döndürür.|  
|[GetRuntimeInformation Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getruntimeinformation-method.md)|Profili oluşturulan çalışma zamanı sürüm bilgilerini sağlar.|  
|[GetStringLayout2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md)|Bir dize nesnesinin düzeni hakkındaki bilgileri alır.|  
|[GetThreadStaticAddress2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getthreadstaticaddress2-method.md)|Belirtilen iş parçacığı ve uygulama etki alanı kapsamı içinde belirtilen statik iş parçacığı alanı adresini alır.|  
|[RequestProfilerDetach Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)|Profil oluşturucuyu ayırmak için çalışma zamanı bildirir.|  
|[SetEnterLeaveFunctionHooks3 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)|Üzerinde çağrılır profil oluşturucu uygulanan işlevleri belirtir [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), ve [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) işlevleri.|  
|[SetEnterLeaveFunctionHooks3WithInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)|Üzerinde çağrılır profil oluşturucu uygulanan işlevleri belirtir [Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [Functionleave3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), ve [Functiontailcall3withınfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) Yönetilen işlevlerin kancaları.|  
|[SetFunctionIDMapper2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)|Profil Oluşturucu uygulanan eşlemek için çağrılacak işlevi belirtir `FunctionID` değerleri oluşturucunun geçirilen alternatif, işlev girişi/çıkışı kancaları. Bu yöntemin genişlettiği [Icorprofilerınfo::setfunctionıdmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) bir parametresiyle profil Oluşturucular, çalışma zamanları arasındaki belirsizliğini ortadan kaldırmak için kullanabilirsiniz.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR yöntemlerini uygulayan `ICorProfilerInfo3` ücretsiz iş parçacıklı model kullanarak arabirimi. Her yöntem başarısı veya başarısızlığı göstermek için HRESULT döndürür. Olası dönüş kodları listesi için CorError.h dosyasına bakın.  
  
 CLR geçirmeden bir `ICorProfilerInfo3` profil oluşturucu uygulamasını kullanarak her kod profil oluşturucu başlatma sırasında arabirimine [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) veya [ICorProfilerCallback3::I nitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) yöntemi. Bir kod profil oluşturucu ardından çağırabilirsiniz `ICorProfilerInfo3` yöntemleri hakkında bilgi almak için yönetilen CLR denetimi altında yürütülen kod.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
