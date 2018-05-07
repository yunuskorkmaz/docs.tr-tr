---
title: ICorProfilerInfo4::GetReJITIDs Metodu
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1055366576f45a7ca137b6d8170d1786c2ba4492
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo4getrejitids-method"></a>ICorProfilerInfo4::GetReJITIDs Metodu
Hala ayrılan tüm JIT yeniden derlenmesi sürümlerini belirtilen işlev tanımlamak kimlikleri bir dizi döndürür. Bu, daha sonra geri döndürüldü, ancak (örneğin, geri döndürülen işlevi içeren uygulama etki alanı hala kullanımda olduğunda) henüz serbest işlevleri JIT yeniden derlenmesi sürümlerini içerir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `functionId`  
 [in] `FunctionID` Olan sürümler Numaralandırılacak işlevi örneğinin.  
  
 `cReJitIds`  
 [in] JIT yeniden derlenmesi kimlikleri ayrılan sayısı `reJitIds` dizi.  
  
 `pcReJitIds`  
 [out] JIT yeniden derlenmesi kimlikleri gerçek sayısı.  
  
 `reJitIds`  
 [out] Belirtilen işlev için JIT yeniden derlenmesi kimlikleri içerecek bir çağıran tarafından ayrılmış bir dizi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetReJITIDs` verilen işlevin örneği için etkin JIT yeniden derlenmesi kimlikleri numaralandırır. Diğer aynı kullanım deseni takip `ICorProfilerInfo` arayana ayrılan arabellekleri kabul işlevleri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
