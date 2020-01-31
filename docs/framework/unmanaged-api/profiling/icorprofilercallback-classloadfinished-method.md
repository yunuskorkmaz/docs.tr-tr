---
title: ICorProfilerCallback::ClassLoadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadFinished
helpviewer_keywords:
- ClassLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ClassLoadFinished method [.NET Framework profiling]
ms.assetid: 3dd80fbe-d62d-4d4d-acf8-5b7d0efe607e
topic_type:
- apiref
ms.openlocfilehash: e0ff90f99c1127b5a4626f47514ba7099b5d48af
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866604"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a>ICorProfilerCallback::ClassLoadFinished Yöntemi
Profil oluşturucuyu bir sınıfın yükleme tamamlandığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a>Parametreler

- `classId`

  \[in], yüklenen sınıfı tanımlar.

- `hrStatus`

  \[, sınıfın başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.

## <a name="remarks"></a>Açıklamalar  
 `classId` değeri, `ClassLoadFinished` yöntemi çağrılana kadar bir bilgi isteği için geçerli değildir.  
  
 Sınıfı yüklemenin bazı bölümleri `ClassLoadFinished` geri çağrısından sonra devam edebilir. `hrStatus` HRESULT hatası, bir hatayı gösterir. Ancak, `hrStatus` başarılı bir HRESULT, yalnızca sınıfın yüklemesinin ilk bölümünün başarılı olduğunu gösterir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ClassLoadStarted Yöntemi](icorprofilercallback-classloadstarted-method.md)
