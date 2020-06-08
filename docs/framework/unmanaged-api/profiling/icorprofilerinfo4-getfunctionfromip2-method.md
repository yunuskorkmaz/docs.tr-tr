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
ms.openlocfilehash: ea66474e809b3813faceef79a69dd8a639a72a3b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502801"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a>ICorProfilerInfo4::GetFunctionFromIP2 Yöntemi
Yönetilen bir kod yönerge işaretçisini bir işlevin JıT yeniden derlenmiş sürümüne eşler.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 `GetFunctionFromIP2`, öğesine benzerdir `GetFunctionFromIP` , ancak BELIRTILEN IP adresini içeren işlevin Işlev kimliği yerıne JIT-yeniden DERLENMESI kimliğini alır.  
  
> [!NOTE]
> `GetFunctionFromIP2`bir çöp toplama tetiklenebilir, ancak `GetFunctionFromIP` olmayacaktır.  Daha fazla bilgi için bkz. [HRESULT corprof_e_unsupported_call_sequence](corprof-e-unsupported-call-sequence-hresult.md).  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](icorprofilerinfo-interface.md)
