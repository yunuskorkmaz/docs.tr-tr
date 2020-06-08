---
title: ICorProfilerCallback::ClassUnloadStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadStarted
helpviewer_keywords:
- ClassUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ClassUnloadStarted method [.NET Framework profiling]
ms.assetid: bc93bead-f3a9-415c-b919-ddd3ca80facc
topic_type:
- apiref
ms.openlocfilehash: 86402abca5386f34256f1f44f674f1e1898ad5fd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500357"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a>ICorProfilerCallback::ClassUnloadStarted Yöntemi
Profil oluşturucuyu bir sınıfın kaldırılmakta olduğunu bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a>Parametreler

- `classId`

  \[' de], kaldırılmakta olan sınıfı tanımlar.

## <a name="remarks"></a>Açıklamalar  
 Değeri, `classId` yöntemin döndürdüğü bir bilgi isteği için geçerli değil `ClassUnloadStarted` — Bu sınıf hakkında bilgi edinmek için profil oluşturucunun son şansı budur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ClassUnloadFinished Yöntemi](icorprofilercallback-classunloadfinished-method.md)
