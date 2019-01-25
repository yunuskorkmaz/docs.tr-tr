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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d7d5b4e7ed4fdf6ae20da654913cbf3e004eb09
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506751"
---
# <a name="icorprofilerinfo4requestrejit-method"></a>ICorProfilerInfo4::RequestReJIT Yöntemi
Belirtilen işlevler tüm örneklerinin bir JIT yeniden derlemesi ister.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cFunctions`  
 [in] Yeniden derlemek için işlev sayısı.  
  
 `moduleIds`  
 [in] Belirtir `moduleId` kısmı (`module`, `methodDef`) derlenmesi için işlevleri tanımlamak çiftleri.  
  
 `methodIds`  
 [in] Belirtir `methodId` kısmı (`module`, `methodDef`) derlenmesi için işlevleri tanımlamak çiftleri.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.  
  
|HRESULT|Açıklama|  
|-------------|-----------------|  
|S_OK|JIT yeniden derlemesi için tüm yöntemlerini işaretlemek için girişimde bulunuldu. Profil Oluşturucu uygulamalıdır [Icorprofilercallback4::rejıterror](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) hangi yöntemlerin JIT yeniden derlenmek üzere başarıyla işaretlenen belirlemek için yöntemi.|  
|CORPROF_E_CALLBACK4_REQUIRED|Profil Oluşturucu uygulamalıdır [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) desteklenmesi, bu çağrı için arabirim.|  
|CORPROF_E_REJIT_NOT_ENABLED|JIT yeniden derlemesi etkin değil. Başlatma sırasında JIT yeniden derlemesi kullanarak etkinleştirmelisiniz [Icorprofilerınfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) ayarlanacak yöntemi `COR_PRF_ENABLE_REJIT` bayrağı.|  
|E_INVALIDARG|`cFunctions` 0 ' dır veya `moduleIds` veya `methodIds` olduğu `NULL`.|  
|||  
|E_OUTOFMEMORY|CLR, belleği tükendiğinden, isteği tamamlayamadı.|  
  
## <a name="remarks"></a>Açıklamalar  
 Çağrı `RequestReJIT` belirtilen bir işlevler kümesi derlemeniz çalışma zamanı sağlamak için. Bir kod profil oluşturucu ardından kullanabilirsiniz [Icorprofilerfunctioncontrol](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) işlevleri derlenir, oluşturulan kodu ayarlamak için arabirim. Bu, şu anda yürütülen İşlevler, yalnızca gelecekteki işlev çağrılarını etkilemez. JIT yeniden derlenen belirtilen işlevlerden herhangi birinin daha önce, öyle isteme geri alma ve işlevi yeniden derlemeden eşdeğerdir. Reversibility, JIT Derleyici bir işlevi orijinal sürümünü derlediğinde korumak için yalnızca özgün sürümlerini kendi çağrılanlar inlining'i kararları için değerlendirir. JIT Derleyici bir işlevi yeniden derlenir, geçerli sürümleri (znovu veya özgün) için kendi çağrılanlar düşünür. satır içi kullanım.  
  
 Bir profil oluşturucu genellikle çağrıları `RequestReJIT` profil oluşturucu yöntemleri bir veya daha fazla izleme isteyen kullanıcı girişine yanıt. `RequestReJIT` genellikle bazı iş yapın ve büyük olasılıkla tetikleyici bir çöp toplama için için çalışma zamanı askıya alır. Bu nedenle, profil oluşturucu çağırmalıdır `RequestReJIT` bir iş parçacığından, daha önce oluşturduğunuz ve bir CLR tarafından oluşturulan iş parçacığından, şu anda bir profil oluşturucu geri çağırma yürütülmüyor.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerInfo4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
