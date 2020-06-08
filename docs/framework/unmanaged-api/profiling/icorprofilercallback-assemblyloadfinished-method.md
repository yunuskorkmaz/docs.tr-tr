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
ms.openlocfilehash: ce4a842bc71ff144e46efb0d6f7068dfca9d207d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500448"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a>ICorProfilerCallback::AssemblyLoadFinished Yöntemi
Profiler 'ın bir derlemenin yüklemeyi bitirmiş olduğunu bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a>Parametreler

- `assemblyId`

  \[' de], yüklenmiş derlemeyi tanımlar.

- `hrStatus`

  \[içinde] derlemenin başarıyla yüklenip yüklenmediğini belirten bir HRESULT.

## <a name="remarks"></a>Açıklamalar  
 Değeri `assemblyId` , `AssemblyLoadFinished` yöntemi çağrılana kadar bir bilgi isteği için geçerli değildir.  
  
 Derlemeyi yüklemenin bazı bölümleri geri aramadan sonra devam edebilir `AssemblyLoadFinished` . ' De HRESULT hatası, `hrStatus` bir hatayı gösterir. Ancak, içinde başarılı bir HRESULT, `hrStatus` sadece derlemeyi yüklemenin ilk bölümünün başarılı olduğunu gösterir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
