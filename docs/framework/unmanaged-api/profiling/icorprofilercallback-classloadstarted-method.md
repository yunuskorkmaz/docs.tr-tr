---
title: ICorProfilerCallback::ClassLoadStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::ClassLoadStarted method [.NET Framework profiling]
- ClassLoadStarted method [.NET Framework profiling]
ms.assetid: 9f728de8-45c2-45a5-ac4a-45660bd36ecf
topic_type:
- apiref
ms.openlocfilehash: 9a9fdc80c8f63dd5b004953266a5d7399655bc71
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500372"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a>ICorProfilerCallback::ClassLoadStarted Yöntemi
Profil oluşturucuyu bir sınıfın yüklenmekte olduğunu bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a>Parametreler

- `classId`

  \[içinde] yüklenmekte olan sınıfı tanımlar.

## <a name="remarks"></a>Açıklamalar  
 Değeri, `classId` [ICorProfilerCallback:: ClassLoadFinished](icorprofilercallback-classloadfinished-method.md) yöntemi çağrılana kadar bir bilgi isteği için geçerli değildir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
