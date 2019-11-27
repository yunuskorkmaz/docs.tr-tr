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
ms.openlocfilehash: cbd7c0d8fff55766a98e727ce22c77dd5214611b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448009"
---
# <a name="icorprofilerinfo4-interface"></a>ICorProfilerInfo4 Arabirimi
Olay izlemeyi ve istek bilgilerini denetlemek için ortak dil çalışma zamanı (CLR) ile iletişim kurmak üzere kod profil oluşturucular kullanan yöntemler sağlar. . `ICorProfilerInfo4` arabirimi, diğer `ICorProfilerInfo` arabirimlerinin bir uzantısıdır. .NET Framework 4,5 ' ye eklenen tam zamanında (JıT) yeniden derlemeyi desteklemek için yeni yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumJITedFunctions2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|Daha önce JıT olarak derlenen ve JıT-yeniden derlenmiş olan tüm işlevler için bir Numaralandırıcı döndürür.|  
|[EnumThreads Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|Profili oluşturulan işlemdeki tüm yönetilen iş parçacıklarının koleksiyonunu sırayla yinelemek için yöntemler sağlayan bir Numaralandırıcı alır.|  
|[GetCodeInfo3 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|Belirtilen işlevin JıT yeniden derlenmesi sürümü ile ilişkili yerel kod kapsamlarını alır.|  
|[GetFunctionFromIP2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|Yönetilen bir kod yönerge işaretçisini belirtilen işlevin JıT yeniden derlenmiş sürümüne eşler.|  
|[GetILToNativeMapping2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|Belirtilen işlevin JıT yeniden derlenmiş sürümünde yer alan kodun yerel uzaklıklarından Microsoft ara dil (MSIL) uzaklıklarını bir harita alır.|  
|[GetObjectSize2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|Belirtilen nesnenin boyutunu döndürür.|  
|[GetReJITIDs Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|Hala ayrılan belirtilen işlevin tüm JıT yeniden derlenmiş sürümlerini tanımlayan bir kimlik dizisi döndürür.|  
|[InitializeCurrentThread Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|Geçerli iş parçacığını aynı iş parçacığında sonraki profil oluşturucu API çağrılarından önce başlatır, böylece kilitlenme kaçınılabilir.|  
|[RequestReJIT Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|Belirtilen işlevlerin tüm örneklerinin JıT yeniden derlemesini ister.|  
|[RequestRevert Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|Belirtilen işlevlerin tüm örneklerini orijinal sürümlerine geri döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, serbest iş parçacıklı modeli kullanarak `ICorProfilerInfo4` arabiriminin yöntemlerini uygular. Her yöntem, başarılı veya başarısız olduğunu göstermek için bir HRESULT döndürür. Olası dönüş kodlarının listesi için CorError. h dosyasına bakın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
