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
ms.openlocfilehash: f452a3324365fb23e1affc11dbdb2ede15346010
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33462448"
---
# <a name="icorprofilerinfo4-interface"></a>ICorProfilerInfo4 Arabirimi
Kod profil oluşturucuları ortak dil çalışma zamanı (CLR) olayı izlemeyi denetlemek için ve istek bilgileri ile iletişim kurmak için kullandığı yöntemlerini sağlar. biçimindeki telefon numarasıdır. `ICorProfilerInfo4` Arabirimi uzantısıdır diğer `ICorProfilerInfo` arabirimleri. Tam zamanında (JIT) yeniden derlenmek, eklenen desteklemek için yeni yöntemler sağlar [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumJITedFunctions2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|JIT derlenmiş ve JIT yeniden derlenmesi daha önce tüm işlevleri için bir numaralandırıcı döndürür.|  
|[EnumThreads Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|Bir numaralandırıcı sırayla tüm yönetilen iş parçacıklarında profili işlem koleksiyonunu yinelemek için yöntemler sağlayan alır.|  
|[GetCodeInfo3 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|Belirtilen işlev JIT yeniden derlenmesi sürümü ile ilişkili yerel kod kapsam alır.|  
|[GetFunctionFromIP2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|Yönetilen kod yönerge işaretçisi belirtilen işlev JIT yeniden derlenmesi sürümüne eşler.|  
|[GetILToNativeMapping2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|Belirtilen işlev JIT yeniden derlenmesi sürümünde yer alan kodu için yerel uzaklık için Ara dili (MSIL) kaydırır Microsoft'tan bir harita alır.|  
|[GetObjectSize2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|Belirtilen nesnenin boyutu döndürür.|  
|[GetReJITIDs Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|Hala ayrılan tüm JIT yeniden derlenmesi sürümlerini belirtilen işlev tanımlamak kimlikleri bir dizi döndürür.|  
|[InitializeCurrentThread Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|Bu kilitlenme önlenebilir şekilde aynı iş parçacığı üzerinde API çağrılarının sonraki profil oluşturucu çalıştırılmasının geçerli iş parçacığının başlatır.|  
|[RequestReJIT Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|JIT derleme belirtilen işlevler tüm örneklerinin ister.|  
|[RequestRevert Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|Özgün sürümlerine belirtilen işleve tüm örneklerini döner.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR yöntemlerini uygular `ICorProfilerInfo4` ücretsiz iş parçacıklı modeli kullanarak arabirimi. Her yöntem, başarı veya hata durumunu göstermek için bir HRESULT döndürür. Olası dönüş kodları listesi için CorError.h dosyasına bakın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
