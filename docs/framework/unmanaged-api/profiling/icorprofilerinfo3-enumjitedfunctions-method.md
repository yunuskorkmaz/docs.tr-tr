---
title: ICorProfilerInfo3::EnumJITedFunctions Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumJITedFunctions Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumJITedFunctions
helpviewer_keywords:
- ICorProfilerInfo3::EnumJITedFunctions method [.NET Framework profiling]
- EnumJITedFunctions method [.NET Framework profiling]
ms.assetid: e2847a36-f460-45e2-9b6c-b33b008f40d9
topic_type:
- apiref
ms.openlocfilehash: 3ebf4a7706b3d3495e4a617b4f86a50281115436
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496561"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a>ICorProfilerInfo3::EnumJITedFunctions Yöntemi
Daha önce JıT olarak derlenen tüm işlevler için bir Numaralandırıcı döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppEnum`  
 dışı [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) numaralandırıcısı için bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem `JITCompilation` [ICorProfilerCallback:: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) yöntemi gibi geri çağırmalar ile çakışabilir. Bu yöntemin döndürdüğü Numaralandırıcı, Ngen. exe ile oluşturulan yerel görüntülerden yüklenen işlevleri içermez.  
  
> [!NOTE]
> Döndürülen numaralandırma alanın değeri için yalnızca "0" içerir `COR_PRF_FUNCTION::reJitId` .  Geçerli değerlere ihtiyacınız varsa `COR_PRF_FUNCTION::reJitId` , [ICorProfilerInfo4:: EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) yöntemini kullanın.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo3 Arabirimi](icorprofilerinfo3-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
