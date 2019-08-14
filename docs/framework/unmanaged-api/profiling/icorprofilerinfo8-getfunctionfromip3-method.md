---
title: ICorProfilerInfo8::GetFunctionFromIP3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetFunctionFromIP3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: f3c0a3525c87fbf39199c15a6619ff4a0d2acc42
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973704"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a>ICorProfilerInfo8:: GetFunctionFromIP3 yöntemi
  
  Yönetilen bir kod yönerge işaretçisini FunctionID 'ye eşler. Bu yöntem hem dinamik hem de dinamik olmayan yöntemler için geçerlidir.    
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```  
  
#### <a name="parameters"></a>Parametreler  
 `ip`  
 'ndaki Yönetilen koddaki yönerge işaretçisi.  

 `pFunctionId`  
 dışı İşlev KIMLIĞI.  
  
 `pReJitId`  
 dışı İşlevin JıT yeniden derlenmesi sürümünün kimliği.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem hem dinamik hem de dinamik olmayan yöntemler için geçerlidir. Yalnızca meta verileri olan işlevler için çalışır olan [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md)öğesinin bir üst kümesidir.
  

## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorProf. IDL, CorProf. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [! [NET_CURRENT_V472PLUS](../../../../includes/net-current-v472plus.md) Ekle  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerInfo8 arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)

