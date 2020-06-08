---
title: ICorProfilerCallback::AssemblyUnloadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
ms.openlocfilehash: d00e67d29921edc6b7487ceeb12aaa9e9f9bd0ac
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500422"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a>ICorProfilerCallback::AssemblyUnloadFinished Yöntemi
Profiler öğesine bir derlemenin kaldırılmış olduğunu bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a>Parametreler

- `assemblyId`

  \[' de], kaldırılmakta olan derlemeyi tanımlar.

- `hrStatus`

  \[içinde] derlemenin başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.

## <a name="remarks"></a>Açıklamalar  
 Değeri, `assemblyId` [ICorProfilerCallback:: AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md) yönteminin döndürdüğü bir bilgi isteği için geçerli değildir.  
  
 Derlemeyi kaldırma işleminin bazı bölümleri geri aramadan sonra devam edebilir `AssemblyUnloadFinished` . ' De HRESULT hatası, `hrStatus` bir hatayı gösterir. Ancak, içinde başarılı bir HRESULT, `hrStatus` sadece derlemeyi kaldırma ilk bölümünün başarılı olduğunu gösterir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
