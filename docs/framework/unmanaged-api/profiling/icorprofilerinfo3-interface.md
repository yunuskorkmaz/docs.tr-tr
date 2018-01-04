---
title: ICorProfilerInfo3 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3
helpviewer_keywords: ICorProfilerInfo3 interface [.NET Framework profiling]
ms.assetid: 044a262f-0fa7-485d-b0c1-64cdc359c654
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3c0251e4e4934ac632eb977f2f1505fe6610b31b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3-interface"></a>ICorProfilerInfo3 Arabirimi
Ortak dil çalışma zamanı ile (CLR) olayı izlemeyi denetlemek ve bilgi istemek için iletişim kurmak için kod profil oluşturucuları kullanma yöntemleri sağlar. `ICorProfilerInfo3` Arabirimi uzantısıdır [Icorprofilerınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) arabirimi. ' De desteklenen yeni yöntemleri sağlar [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] ve sonraki sürümler.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumJITedFunctions Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)|Tüm daha önce JIT derlenmiş işlevleri için bir numaralandırıcı döndürür.|  
|[EnumModules Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)|Uygulamaya yüklenen yönetilen modüller koleksiyonu sırayla yinelemek için yöntemler sağlayan bir numaralandırıcı döndürür.|  
|[GetAppDomainsContainingModule Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getappdomainscontainingmodule-method.md)|Belirtilen modül yüklendi uygulama etki alanları tanımlayıcısını alır.|  
|[GetFunctionEnter3Info Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)|Profil Oluşturucu tarafından için bildirilen işlevi yığın çerçevesi ve bağımsız değişkeni bilgi verilmektedir [Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) işlev; yalnızca sırasında çağrılabilir `FunctionEnter3WithInfo` geri çağırma.|  
|[GetFunctionLeave3Info Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)|Yığın çerçevesi ve için Profil Oluşturucu tarafından bildirilen işlevin dönüş değeri sağlar [Functionleave3withınfo işlevi](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) işlev; yalnızca sırasında çağrılabilir `FunctionLeave3WithInfo` geri çağırma.|  
|[GetFunctionTailcall3Info Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md)|Yığın çerçevesi için Profil Oluşturucu tarafından bildirilen işlevinin sağlar [Functiontailcall3withınfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) işlev; yalnızca sırasında çağrılabilir `FunctionTailcall3WithInfo` geri çağırma.|  
|[GetModuleInfo2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)|Modül kimliği derleme ve modül özelliklerini açıklayan bir bit maskesi modül, modülün üst Kimliğini dosya adını döndürür.|  
|[GetRuntimeInformation Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getruntimeinformation-method.md)|Profili oluşturuluyor çalışma zamanı sürüm bilgilerini sağlar.|  
|[GetStringLayout2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md)|Bir dize nesnesi düzeni hakkındaki bilgileri alır.|  
|[GetThreadStaticAddress2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getthreadstaticaddress2-method.md)|Belirtilen iş parçacığı ve uygulama etki alanı kapsamında belirtilen statik iş parçacığı alan adresini alır.|  
|[RequestProfilerDetach Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)|Profil Oluşturucu ayırmak için çalışma zamanı bildirir.|  
|[SetEnterLeaveFunctionHooks3 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)|Üzerinde adlı profil oluşturucu uygulanan işlevler belirtir [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), ve [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) işlevleri.|  
|[SetEnterLeaveFunctionHooks3WithInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)|Üzerinde adlı profil oluşturucu uygulanan işlevler belirtir [Functionenter3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [Functionleave3withınfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), ve [Functiontailcall3withınfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) Yönetilen işlevler kancaları.|  
|[SetFunctionIDMapper2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)|Eşlenecek adlı profil oluşturucu uygulanan işlevini belirten `FunctionID` değerleri profil oluşturucu için 's geçirilen alternatif değerler için giriş/çıkış kancaları işlev. Bu yöntemin genişlettiği [Icorprofilerınfo::setfunctionıdmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) bir parametresiyle profil oluşturucular çalışma zamanları arasında belirsizliğini ortadan kaldırmak için kullanabilirsiniz.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR yöntemlerini uygular `ICorProfilerInfo3` ücretsiz iş parçacıklı modeli kullanarak arabirimi. Her yöntem, başarı veya hata durumunu göstermek için bir HRESULT döndürür. Olası dönüş kodları listesi için CorError.h dosyasına bakın.  
  
 CLR geçirmeden bir `ICorProfilerInfo3` Profil Oluşturucu'nın uygulaması kullanarak her kod profil oluşturucu başlatma sırasında arabirimine [Icorprofilercallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) veya [ICorProfilerCallback3::I nitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) yöntemi. Kod profil oluşturucu sonra çağırabilirsiniz `ICorProfilerInfo3` yöntemleri hakkında bilgi almak için yönetilen CLR denetiminde yürütülen kod.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
