---
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
ms.openlocfilehash: eb4d5e1c4efd67914df95868b67ec5cc3fe6139a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444825"
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
 'ndaki Yeniden derlenecek işlevleri tanımlayan (`module`, `methodDef`) çiftlerinin `moduleId` bölümünü belirtir.  
  
 `methodIds`  
 'ndaki Yeniden derlenecek işlevleri tanımlayan (`module`, `methodDef`) çiftlerinin `methodId` bölümünü belirtir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|JıT yeniden derleme için tüm yöntemleri işaretlemek için bir girişimde bulunuldu. Profil Oluşturucu, JıT yeniden derleme için hangi yöntemlerin başarıyla işaretlendiğini belirleyen [ICorProfilerCallback4:: ReJITError](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) metodunu uygulamalıdır.|  
|CORPROF_E_CALLBACK4_REQUIRED|Bu çağrının desteklenmesi için profil oluşturucunun [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) arabirimini uygulaması gerekir.|  
|CORPROF_E_REJIT_NOT_ENABLED|JıT yeniden derleme etkinleştirilmemiş. `COR_PRF_ENABLE_REJIT` bayrağını ayarlamak için [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) yöntemini kullanarak başlatma sırasında JIT yeniden derlemeyi etkinleştirmeniz gerekir.|  
|E_INVALIDARG|`cFunctions` 0 ' dır veya `moduleIds` veya `methodIds` `NULL`.|  
|||  
|E_OUTOFMEMORY|CLR belleği tükendiğinden isteği tamamlayamadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çalışma zamanının belirtilen bir işlev kümesini yeniden derlemek için `RequestReJIT` çağırın. Kod Profilcisi daha sonra [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) arabirimini kullanarak işlevler yeniden derlenmeye başlatıldığında oluşturulan kodu ayarlayabilir. Bu, şu anda yürütülmekte olan işlevleri etkilemez, yalnızca gelecekteki işlev etkinleştirmeleri. Belirtilen işlevlerden herhangi biri daha önce JıT olarak yeniden derlendikten sonra yeniden derleme isteğinde bulunulmaya, işlevin geri döndürülmesi ve yeniden derlenmesi ile eşdeğerdir. Geri almayı korumak için, JıT derleyicisi bir işlevin orijinal sürümünü derlediğinde, iç kararları almak için yalnızca özgün sürümlerini dikkate alır. JıT derleyicisi bir işlevi yeniden derlediğinde, iç içe için kendi caltaları 'nın geçerli sürümlerini (yeniden derlenir veya özgün) dikkate alır.  
  
 Profil Oluşturucu tipik olarak, profil oluşturucunun bir veya daha fazla yöntemi işaretlemesini isteyen kullanıcı girdisine yanıt olarak `RequestReJIT` çağırır. `RequestReJIT` genellikle çalışma zamanını bir kısmını yapmak için askıya alır ve bir çöp toplamayı tetikleyebilirler. Bu nedenle, profil oluşturucu, şu anda profil oluşturucu geri çağrısını yürüten CLR tarafından oluşturulan bir iş parçacığından değil, önceden oluşturduğu bir iş parçacığından `RequestReJIT` çağırmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
