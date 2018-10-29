---
title: ICorProfilerInfo4 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4
helpviewer_keywords:
- ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 27cce8a77d4236829124b45650d5d0ac32a5150c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198009"
---
# <a name="icorprofilerinfo4-interface"></a>ICorProfilerInfo4 Arabirimi
İstek bilgilerini ve ortak dil çalışma zamanı olayı izlemeyi denetlemek için (CLR) ile iletişim kurmak için kod profil oluşturucuları kullanmak için yöntemler sağlar. biçimindeki telefon numarasıdır. `ICorProfilerInfo4` Arabirimidir diğer uzantı `ICorProfilerInfo` arabirimleri. Just-in-time (JIT) yeniden derleme, eklenen desteklemek için yeni yöntemler sağlar [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumJITedFunctions2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|Daha önce JIT olarak derlenmiş ve JIT yeniden derlenen tüm işlevler için bir numaralandırıcı döndürür.|  
|[EnumThreads Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|Profili oluşturulan işlemdeki tüm yönetilen iş parçacıkları koleksiyonu sırayla yinelemek için yöntemler sağlayan bir numaralandırıcıyı alır.|  
|[GetCodeInfo3 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|Belirtilen işlev JIT yeniden derlenen sürümü ile ilişkili yerel kod kapsam alır.|  
|[GetFunctionFromIP2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|Yönetilen kod yönerge işaretçisini belirtilen işlevi yeniden JIT derlenen sürümüne eşler.|  
|[GetILToNativeMapping2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|Harita, Microsoft Ara dil (MSIL) için belirtilen işlev JIT yeniden derlenen sürümünde yer alan kodun yerel uzaklıklar uzaklıkları alır.|  
|[GetObjectSize2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|Belirtilen nesnenin boyutunu döndürür.|  
|[GetReJITIDs Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|Yine de atanan tüm JIT yeniden derlenen sürümlerini belirtilen işlev tanımlamak kimlikleri dizisi döndürür.|  
|[InitializeCurrentThread Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|Geçerli iş parçacığı sonraki profil oluşturucu bu kilitlenme önlenebilir şekilde aynı iş parçacığında API çağrılarının tarifelerindeki başlatır.|  
|[RequestReJIT Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|Belirtilen işlevler tüm örneklerinin bir JIT yeniden derlemesi ister.|  
|[RequestRevert Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|Tüm örneklerinin özgünlüğünü belirtilen işleve döner.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR yöntemlerini uygulayan `ICorProfilerInfo4` ücretsiz iş parçacıklı model kullanarak arabirimi. Her yöntem başarısı veya başarısızlığı göstermek için HRESULT döndürür. Olası dönüş kodları listesi için CorError.h dosyasına bakın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
