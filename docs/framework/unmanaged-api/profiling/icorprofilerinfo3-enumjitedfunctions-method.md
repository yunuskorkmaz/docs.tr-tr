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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c1b088d138948ed7e9ae5514fb62e37c324427dd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782185"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a>ICorProfilerInfo3::EnumJITedFunctions Yöntemi
Daha önce JIT olarak derlenmiş tüm işlevler için bir numaralandırıcı döndürür.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ppEnum`  
 [out] Bir işaretçi [Icorprofilerfunctionenum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) Numaralandırıcı.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem ile çakışabilen `JITCompilation` gibi geri çağırmaları [Icorprofilercallback::jıtcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) yöntemi. Bu yöntem tarafından döndürülen Numaralandırıcı, Ngen.exe ile oluşturulan yerel görüntülerden yüklenen işlevleri içermez.  
  
> [!NOTE]
>  Döndürülen sabit listesi yalnızca "0" değerini içeren `COR_PRF_FUNCTION::reJitId` alan.  Geçerli gerekiyorsa `COR_PRF_FUNCTION::reJitId` değerlerini kullanın [Icorprofilerınfo4::enumjıtedfunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo3 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
