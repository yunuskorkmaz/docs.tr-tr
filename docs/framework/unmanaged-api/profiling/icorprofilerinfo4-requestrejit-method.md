---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo4:: RequestReJIT yöntemi'
title: ICorProfilerInfo4::RequestReJIT Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestReJIT
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestReJIT
helpviewer_keywords:
- RequestReJIT method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestReJIT method [.NET Framework profiling]
ms.assetid: 781ed736-f30c-4816-920e-3552e36542c6
topic_type:
- apiref
ms.openlocfilehash: 2da65c2db5722f689f1a8588169ea099aff71be6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799024"
---
# <a name="icorprofilerinfo4requestrejit-method"></a>ICorProfilerInfo4::RequestReJIT Yöntemi

Belirtilen işlevlerin tüm örneklerinin JıT yeniden derlemesini ister.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
## <a name="parameters"></a>Parametreler  

 `cFunctions`  
 'ndaki Yeniden derlemek için işlev sayısı.  
  
 `moduleIds`  
 'ndaki `moduleId` `module` Yeniden `methodDef` derlenecek işlevleri tanımlayan (,) çiftlerinin bölümünü belirtir.  
  
 `methodIds`  
 'ndaki `methodId` `module` Yeniden `methodDef` derlenecek işlevleri tanımlayan (,) çiftlerinin bölümünü belirtir.  
  
## <a name="return-value"></a>Dönüş Değeri  

 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|JıT yeniden derleme için tüm yöntemleri işaretlemek için bir girişimde bulunuldu. Profil Oluşturucu, JıT yeniden derleme için hangi yöntemlerin başarıyla işaretlendiğini belirleyen [ICorProfilerCallback4:: ReJITError](icorprofilercallback4-rejiterror-method.md) metodunu uygulamalıdır.|  
|CORPROF_E_CALLBACK4_REQUIRED|Bu çağrının desteklenmesi için profil oluşturucunun [ICorProfilerCallback4](icorprofilercallback4-interface.md) arabirimini uygulaması gerekir.|  
|CORPROF_E_REJIT_NOT_ENABLED|JıT yeniden derleme etkinleştirilmemiş. Bayrağı ayarlamak için [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) yöntemini kullanarak başlatma sırasında JIT yeniden derlemeyi etkinleştirmelisiniz `COR_PRF_ENABLE_REJIT` .|  
|E_INVALIDARG|`cFunctions` 0 veya veya ' `moduleIds` dir `methodIds` `NULL` .|  
|||  
|E_OUTOFMEMORY|CLR belleği tükendiğinden isteği tamamlayamadı.|  
  
## <a name="remarks"></a>Açıklamalar  

 `RequestReJIT`Çalışma zamanının belirtilen işlev kümesini yeniden derleyeme çağrısı. Kod Profilcisi daha sonra [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) arabirimini kullanarak işlevler yeniden derlenmeye başlatıldığında oluşturulan kodu ayarlayabilir. Bu, şu anda yürütülmekte olan işlevleri etkilemez, yalnızca gelecekteki işlev etkinleştirmeleri. Belirtilen işlevlerden herhangi biri daha önce JıT olarak yeniden derlendikten sonra yeniden derleme isteğinde bulunulmaya, işlevin geri döndürülmesi ve yeniden derlenmesi ile eşdeğerdir. Geri almayı korumak için, JıT derleyicisi bir işlevin orijinal sürümünü derlediğinde, iç kararları almak için yalnızca özgün sürümlerini dikkate alır. JıT derleyicisi bir işlevi yeniden derlediğinde, iç içe için kendi caltaları 'nın geçerli sürümlerini (yeniden derlenir veya özgün) dikkate alır.  
  
 Profil Oluşturucu tipik olarak `RequestReJIT` , profil oluşturucunun bir veya daha fazla yöntemi işaretlemesini isteyen kullanıcı girdisine yanıt olarak çağrı yapılır. `RequestReJIT` genellikle çalışma zamanını, işini bir kısmını yapmak için askıya alır ve bir çöp toplama tetikleyebilecek. Bu nedenle, profil oluşturucu, `RequestReJIT` Şu anda profil oluşturucu geri çağrısını yürüten CLR tarafından oluşturulan bir iş parçacığından değil, daha önce oluşturduğu bir iş parçacığından çağırmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo4 Arabirimi](icorprofilerinfo4-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
