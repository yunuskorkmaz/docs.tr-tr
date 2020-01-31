---
title: ICorProfilerCallback::ModuleLoadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadFinished
helpviewer_keywords:
- ModuleLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadFinished method [.NET Framework profiling]
ms.assetid: 050649e5-ffc0-4458-a0a4-d9ee128a219e
topic_type:
- apiref
ms.openlocfilehash: 661229e5fbd5d106662f0e823a1753bd76c33311
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866175"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a>ICorProfilerCallback::ModuleLoadFinished Yöntemi
Profiler 'ın bir modülün yüklemeyi bitirdiğinden emin olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a>Parametreler  
 `moduleId`  
 'ndaki Yüklemeyi tamamlamış modülün KIMLIĞI.  
  
 `hrStatus`  
 'ndaki Modülün başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.  
  
## <a name="remarks"></a>Açıklamalar  
 `moduleId` değeri, `ModuleLoadFinished` yöntemi çağrılana kadar bir bilgi isteği için geçerli değildir.  
  
 Modülün yüklenmesinin bazı bölümleri `ModuleLoadFinished` geri çağrısından sonra devam edebilir. `hrStatus` HRESULT hatası, bir hatayı gösterir. Ancak `hrStatus` başarılı bir HRESULT, yalnızca modülün yüklenmesinin ilk bölümünün başarılı olduğunu gösterir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ModuleLoadStarted Yöntemi](icorprofilercallback-moduleloadstarted-method.md)
