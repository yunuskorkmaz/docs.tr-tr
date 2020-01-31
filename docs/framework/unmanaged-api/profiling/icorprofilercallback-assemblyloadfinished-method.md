---
title: ICorProfilerCallback::AssemblyLoadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type:
- apiref
ms.openlocfilehash: 15ce195af0c0e8f8777f6e5d02043e17e32308da
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866656"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a>ICorProfilerCallback::AssemblyLoadFinished Yöntemi
Profiler 'ın bir derlemenin yüklemeyi bitirmiş olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a>Parametreler

- `assemblyId`

  \[in], yüklenen derlemeyi tanımlar.

- `hrStatus`

  \[içinde] derlemenin başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.

## <a name="remarks"></a>Açıklamalar  
 `assemblyId` değeri, `AssemblyLoadFinished` yöntemi çağrılana kadar bir bilgi isteği için geçerli değildir.  
  
 Derlemeyi yüklemenin bazı bölümleri `AssemblyLoadFinished` geri çağrısından sonra devam edebilir. `hrStatus` HRESULT hatası, bir hatayı gösterir. Ancak, `hrStatus` başarılı bir HRESULT, sadece derlemeyi yüklemenin ilk bölümünün başarılı olduğunu gösterir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
