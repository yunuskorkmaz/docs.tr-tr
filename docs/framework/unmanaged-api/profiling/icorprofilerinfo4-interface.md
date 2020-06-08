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
ms.openlocfilehash: 58d11e9084f53c69f2656b4f0ee6bc7d2cc4ae21
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495872"
---
# <a name="icorprofilerinfo4-interface"></a>ICorProfilerInfo4 Arabirimi
Olay izlemeyi ve istek bilgilerini denetlemek için ortak dil çalışma zamanı (CLR) ile iletişim kurmak üzere kod profil oluşturucular kullanan yöntemler sağlar. . `ICorProfilerInfo4`Arabirim, diğer arabirimlerin bir uzantısıdır `ICorProfilerInfo` . .NET Framework 4,5 ' ye eklenen tam zamanında (JıT) yeniden derlemeyi desteklemek için yeni yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Description|  
|------------|-----------------|  
|[EnumJITedFunctions2 Yöntemi](icorprofilerinfo4-enumjitedfunctions2-method.md)|Daha önce JıT olarak derlenen ve JıT-yeniden derlenmiş olan tüm işlevler için bir Numaralandırıcı döndürür.|  
|[EnumThreads Yöntemi](icorprofilerinfo4-enumthreads-method.md)|Profili oluşturulan işlemdeki tüm yönetilen iş parçacıklarının koleksiyonunu sırayla yinelemek için yöntemler sağlayan bir Numaralandırıcı alır.|  
|[GetCodeInfo3 Yöntemi](icorprofilerinfo4-getcodeinfo3-method.md)|Belirtilen işlevin JıT yeniden derlenmesi sürümü ile ilişkili yerel kod kapsamlarını alır.|  
|[GetFunctionFromIP2 Yöntemi](icorprofilerinfo4-getfunctionfromip2-method.md)|Yönetilen bir kod yönerge işaretçisini belirtilen işlevin JıT yeniden derlenmiş sürümüne eşler.|  
|[GetILToNativeMapping2 Yöntemi](icorprofilerinfo4-getiltonativemapping2-method.md)|Belirtilen işlevin JıT yeniden derlenmiş sürümünde yer alan kodun yerel uzaklıklarından Microsoft ara dil (MSIL) uzaklıklarını bir harita alır.|  
|[GetObjectSize2 Yöntemi](icorprofilerinfo4-getobjectsize2-method.md)|Belirtilen nesnenin boyutunu döndürür.|  
|[GetReJITIDs Yöntemi](icorprofilerinfo4-getrejitids-method.md)|Hala ayrılan belirtilen işlevin tüm JıT yeniden derlenmiş sürümlerini tanımlayan bir kimlik dizisi döndürür.|  
|[InitializeCurrentThread Yöntemi](icorprofilerinfo4-initializecurrentthread-method.md)|Geçerli iş parçacığını aynı iş parçacığında sonraki profil oluşturucu API çağrılarından önce başlatır, böylece kilitlenme kaçınılabilir.|  
|[RequestReJIT Yöntemi](icorprofilerinfo4-requestrejit-method.md)|Belirtilen işlevlerin tüm örneklerinin JıT yeniden derlemesini ister.|  
|[RequestRevert Yöntemi](icorprofilerinfo4-requestrevert-method.md)|Belirtilen işlevlerin tüm örneklerini orijinal sürümlerine geri döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 CLR, `ICorProfilerInfo4` serbest iş parçacıklı modeli kullanarak arabirimin yöntemlerini uygular. Her yöntem, başarılı veya başarısız olduğunu göstermek için bir HRESULT döndürür. Olası dönüş kodlarının listesi için CorError. h dosyasına bakın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
