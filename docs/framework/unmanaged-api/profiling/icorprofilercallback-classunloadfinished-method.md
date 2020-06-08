---
title: ICorProfilerCallback::ClassUnloadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type:
- apiref
ms.openlocfilehash: 14eb90c707618796d6d62ed2ec5710ceba31ba6c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500383"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a>ICorProfilerCallback::ClassUnloadFinished Yöntemi
Profil oluşturucuyu bir sınıfın kaldırmayı tamamladığını bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a>Parametreler

- `classId`

  \[' de], kaldırılan sınıfı tanımlar.

- `hrStatus`

  \[içinde] sınıfın başarıyla yüklenip yüklenmediğini gösteren bir HRESULT.
  
## <a name="remarks"></a>Açıklamalar  
 Sınıfı kaldırma işleminin bazı bölümleri geri aramadan sonra devam edebilir `ClassUnloadFinished` . ' De HRESULT hatası, `hrStatus` bir hatayı gösterir. Ancak, içinde başarılı bir HRESULT, `hrStatus` yalnızca sınıfın kaldırılmasının ilk bölümünün başarılı olduğunu gösterir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ClassUnloadStarted Yöntemi](icorprofilercallback-classunloadstarted-method.md)
