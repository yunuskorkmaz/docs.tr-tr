---
title: ICorProfilerCallback::AssemblyUnloadStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyUnloadStarted method [.NET Framework profiling]
- AssemblyUnloadStarted method [.NET Framework profiling]
ms.assetid: 6e47b7e5-0335-4dd3-8c42-d3c07d62b102
topic_type:
- apiref
ms.openlocfilehash: 80054a8292c69b957664cb3573b0a8694c7f9fd2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500409"
---
# <a name="icorprofilercallbackassemblyunloadstarted-method"></a>ICorProfilerCallback::AssemblyUnloadStarted Yöntemi
Profiler öğesine bir derlemenin kaldırılmakta olduğunu bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT AssemblyUnloadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a>Parametreler

- `assemblyId`

  \[' de], kaldırılmakta olan derlemeyi tanımlar.

## <a name="remarks"></a>Açıklamalar  
 Değeri, `assemblyId` yöntemin döndürdüğü bir bilgi isteği için geçerli değil — bu `AssemblyUnloadStarted` derleme hakkında bilgi almak için profil oluşturucunun son şansı budur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [AssemblyUnloadFinished Yöntemi](icorprofilercallback-assemblyunloadfinished-method.md)
