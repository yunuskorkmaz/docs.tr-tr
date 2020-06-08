---
title: ICorProfilerInfo4::GetReJITIDs Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetReJITIDs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetReJITIDs
helpviewer_keywords:
- GetReJITIDs method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetReJITIDs method [.NET Framework profiling]
ms.assetid: 634ac28c-a5b7-4fc3-af84-256c24ca8177
topic_type:
- apiref
ms.openlocfilehash: ba15440df79dded95a8afa9438657d064e167f36
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495976"
---
# <a name="icorprofilerinfo4getrejitids-method"></a>ICorProfilerInfo4::GetReJITIDs Yöntemi
Hala ayrılan belirtilen işlevin tüm JıT yeniden derlenmiş sürümlerini tanımlayan bir kimlik dizisi döndürür. Bu, daha sonra geri alınmış ancak henüz serbest bırakılmayan işlevlerin JıT yeniden derlenmiş sürümlerini içerir (örneğin, geri döndürülmüş işlevi içeren uygulama etki alanı hala kullanımda olduğunda).  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a>Parametreler  
 `functionId`  
 'ndaki `FunctionID`Sürümlerinin numaralandırılacağı işlev örneği.  
  
 `cReJitIds`  
 'ndaki Dizide ayrılan JıT yeniden derleme kimliği sayısı `reJitIds` .  
  
 `pcReJitIds`  
 dışı JıT yeniden derlenen kimliklerinin gerçek sayısı.  
  
 `reJitIds`  
 dışı Belirtilen işlev için JıT-yeniden derleme kimliklerini içeren, arayan tarafından ayrılmış bir dizi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetReJITIDs`belirli bir işlev örneği için etkin JıT-yeniden derlenmesi kimliklerini numaralandırır. Bu, `ICorProfilerInfo` çağıran ayrılmış arabellekleri kabul eden diğer işlevlerle aynı kullanım modelini izler.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo4 Arabirimi](icorprofilerinfo4-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
