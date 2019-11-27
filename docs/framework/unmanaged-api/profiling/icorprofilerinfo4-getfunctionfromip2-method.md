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
ms.openlocfilehash: 5153a25ef87d9c06bb46b74945c8eb68eb041682
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443150"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a>ICorProfilerInfo4::GetFunctionFromIP2 Yöntemi
Yönetilen bir kod yönerge işaretçisini bir işlevin JıT yeniden derlenmiş sürümüne eşler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ip`  
 'ndaki Yönetilen koddaki yönerge işaretçisi.  
  
 `pFunctionId`  
 dışı İşlev KIMLIĞI.  
  
 `pReJitId`  
 dışı İşlevin JıT yeniden derlenmesi sürümünün kimliği.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetFunctionFromIP2`, belirtilen IP adresini içeren işlevin işlev KIMLIĞI yerine JıT-yeniden derlenmesi KIMLIĞINI aldığından, `GetFunctionFromIP`benzer.  
  
> [!NOTE]
> `GetFunctionFromIP2` bir çöp toplamayı tetikleyebilir, ancak `GetFunctionFromIP` olmayacaktır.  Daha fazla bilgi için bkz. [HRESULT corprof_e_unsupported_call_sequence](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
