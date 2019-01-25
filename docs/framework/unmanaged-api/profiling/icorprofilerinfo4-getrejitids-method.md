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
ms.openlocfilehash: 6cb3a2235325533d5bd943a530a0a8e5b77100e3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519950"
---
# <a name="icorprofilerinfo4getrejitids-method"></a>ICorProfilerInfo4::GetReJITIDs Metodu
Yine de atanan tüm JIT yeniden derlenen sürümlerini belirtilen işlev tanımlamak kimlikleri dizisi döndürür. Bu, daha sonra geri döndürüldü, ancak (örneğin, geri döndürülen işlevi içeren uygulama etki alanı hala kullanımda olduğunda) henüz serbest işlevlerin JIT yeniden derlenen sürümleri içerir.  
  
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
 [in] `FunctionID` Hangi sürümleri Numaralandırılacak işlevi örneği.  
  
 `cReJitIds`  
 [in] JIT yeniden derlenen kimlikleri ayrıldığı sayısı `reJitIds` dizisi.  
  
 `pcReJitIds`  
 [out] JIT yeniden derlenen kimlikleri gerçek sayısı.  
  
 `reJitIds`  
 [out] Belirtilen işlev için JIT yeniden derlenen kimlikleri içeren bir arayan tarafından ayrılmış dizi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetReJITIDs` verilen işlevin örneği için etkin JIT yeniden derlenen kimlikleri numaralandırır. Diğer olarak aynı kullanım deseni izler `ICorProfilerInfo` arayana ayrılan arabellekler kabul işlevleri.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerInfo4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
