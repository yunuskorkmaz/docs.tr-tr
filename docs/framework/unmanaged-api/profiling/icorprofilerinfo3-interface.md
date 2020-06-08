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
ms.openlocfilehash: 0a474719935ba763cbd15dc6e18fe5ba99c14ebc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496314"
---
# <a name="icorprofilerinfo3-interface"></a>ICorProfilerInfo3 Arabirimi
Olay izlemeyi denetlemek ve bilgi istemek için ortak dil çalışma zamanı (CLR) ile iletişim kurmak üzere kod profil oluşturucular kullanan yöntemler sağlar. `ICorProfilerInfo3`Arabirim, [ICorProfilerInfo2](icorprofilerinfo2-interface.md) arabiriminin bir uzantısıdır. .NET Framework 4 ve sonraki sürümlerde desteklenen yeni yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Description|  
|------------|-----------------|  
|[EnumJITedFunctions Yöntemi](icorprofilerinfo3-enumjitedfunctions-method.md)|Daha önce JıT olarak derlenen tüm işlevler için bir Numaralandırıcı döndürür.|  
|[EnumModules Yöntemi](icorprofilerinfo3-enummodules-method.md)|Uygulamaya yüklenen bir yönetilen modüller koleksiyonu aracılığıyla sırayla yinelemek için yöntemler sağlayan bir Numaralandırıcı döndürür.|  
|[GetAppDomainsContainingModule Yöntemi](icorprofilerinfo3-getappdomainscontainingmodule-method.md)|Verilen modülün yüklendiği uygulama etki alanlarının tanımlayıcılarını alır.|  
|[GetFunctionEnter3Info Yöntemi](icorprofilerinfo3-getfunctionenter3info-method.md)|[FunctionEnter3WithInfo](functionenter3withinfo-function.md) işlevi tarafından Profiler 'a bildirilen işlevin yığın çerçevesini ve bağımsız değişken bilgilerini sağlar; yalnızca `FunctionEnter3WithInfo` geri çağırma sırasında çağrılabilir.|  
|[GetFunctionLeave3Info Yöntemi](icorprofilerinfo3-getfunctionleave3info-method.md)|[FunctionLeave3WithInfo Function](functionleave3withinfo-function.md) işlevi tarafından Profiler 'a bildirilen işlevin yığın çerçevesini ve dönüş değerini sağlar; yalnızca `FunctionLeave3WithInfo` geri çağırma sırasında çağrılabilir.|  
|[GetFunctionTailcall3Info Yöntemi](icorprofilerinfo3-getfunctiontailcall3info-method.md)|[FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) işlevi tarafından Profiler 'a bildirilen işlevin yığın çerçevesini sağlar; yalnızca `FunctionTailcall3WithInfo` geri çağırma sırasında çağrılabilir.|  
|[GetModuleInfo2 Yöntemi](icorprofilerinfo3-getmoduleinfo2-method.md)|Modül KIMLIĞI verildiğinde, modülün dosya adını, modülün üst derleme KIMLIĞINI ve modülün özelliklerini açıklayan bir bit maskesini döndürür.|  
|[GetRuntimeInformation Yöntemi](icorprofilerinfo3-getruntimeinformation-method.md)|Profili oluşturulan çalışma zamanı hakkında sürüm bilgileri sağlar.|  
|[GetStringLayout2 Yöntemi](icorprofilerinfo3-getstringlayout2-method.md)|Bir dize nesnesinin yerleşimi hakkında bilgi alır.|  
|[GetThreadStaticAddress2 Yöntemi](icorprofilerinfo3-getthreadstaticaddress2-method.md)|Belirtilen iş parçacığının ve uygulama etki alanının kapsamındaki belirtilen thread-static alanının adresini alır.|  
|[RequestProfilerDetach Yöntemi](icorprofilerinfo3-requestprofilerdetach-method.md)|Çalışma zamanına profil oluşturucuyu ayırmasını söyler.|  
|[SetEnterLeaveFunctionHooks3 Yöntemi](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)|[FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)ve [FunctionTailcall3](functiontailcall3-function.md) işlevlerinde çağrılacak Profil Oluşturucu uygulanmış işlevleri belirtir.|  
|[SetEnterLeaveFunctionHooks3WithInfo Yöntemi](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)|Yönetilen işlevlerin [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)ve [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) kancaları üzerinde çağrılacak Profil Oluşturucu uygulanmış işlevleri belirtir.|  
|[SetFunctionIDMapper2 Yöntemi](icorprofilerinfo3-setfunctionidmapper2-method.md)|`FunctionID`Profil oluşturucunun işlev girişine/çıkış kancalarına geçirilen değerleri alternatif değerlerle eşlemek için çağrılacak Profil Oluşturucu uygulanmış işlevi belirtir. Bu yöntem [ICorProfilerInfo:: SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) öğesini, çalışma zamanları arasında belirsizliği ortadan kaldırmak için profil oluşturucular tarafından kullanılan bir parametre ile genişletir.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, `ICorProfilerInfo3` serbest iş parçacıklı modeli kullanarak arabirimin yöntemlerini uygular. Her yöntem, başarılı veya başarısız olduğunu göstermek için bir HRESULT döndürür. Olası dönüş kodlarının listesi için CorError. h dosyasına bakın.  
  
 CLR, `ICorProfilerInfo3` başlatma sırasında, profil oluşturucunun [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) veya [ICorProfilerCallback3:: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) yöntemi uygulamasını kullanarak her kod profil oluşturucuya bir arabirim geçirir. Daha sonra bir kod profil oluşturucu, `ICorProfilerInfo3` clr denetimi altında yürütülen yönetilen kod hakkında bilgi almak için yöntemleri çağırabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
