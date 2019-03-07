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
ms.openlocfilehash: 51f8768fc3cd73f0fd5bdb84842af03b900fafdf
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57495357"
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
