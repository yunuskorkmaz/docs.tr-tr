---
title: ICorProfilerInfo4::GetFunctionFromIP2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetFunctionFromIP2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 18099e6e658391d6dae7a666cd0cebefa5859b1a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110540"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a>ICorProfilerInfo4::GetFunctionFromIP2 Yöntemi
Yönetilen kod yönerge işaretçisi bir işlevin JIT yeniden derlenen sürümüne eşler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ip`  
 [in] Yönetilen kodda yönerge işaretçisi.  
  
 `pFunctionId`  
 [out] İşlev kimliği.  
  
 `pReJitId`  
 [out] İşlev JIT yeniden derlenen sürümü kimliği.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetFunctionFromIP2` benzer `GetFunctionFromIP`dışında belirtilen IP adresi içeren işlev işlevi kimliği yerine JIT yeniden derlenen Kimliğini alır.  
  
> [!NOTE]
>  `GetFunctionFromIP2` bir çöp toplama ise tetikleyebilirsiniz `GetFunctionFromIP` erişemez.  Daha fazla bilgi için [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
