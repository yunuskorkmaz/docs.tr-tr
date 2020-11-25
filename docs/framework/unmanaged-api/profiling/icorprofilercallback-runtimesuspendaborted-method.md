---
title: ICorProfilerCallback::RuntimeSuspendAborted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendAborted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted method [.NET Framework profiling]
- RuntimeSuspendAborted method [.NET Framework profiling]
ms.assetid: 5a8a4277-345b-448b-a028-fc8cff9998aa
topic_type:
- apiref
ms.openlocfilehash: 4b6eb59dd771e4013106e6a77fc7475b77b2b007
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732027"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a>ICorProfilerCallback::RuntimeSuspendAborted Yöntemi

Profil oluşturucuyu, çalışma zamanının oluşan çalışma zamanı askıya alma işlemi durdurdu olduğunu bildirir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a>Açıklamalar  

 Çalışma zamanı askıya alma, iki iş parçacığını eşzamanlı olarak askıya almaya çalışıyorsa durdurulmuş olabilir.  
  
 [ICorProfilerCallback:: RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) geri çağırması veya `RuntimeSuspendAborted` geri çağırma, [ICorProfilerCallback:: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) geri çağrısından sonraki tek bir iş parçacığında gerçekleşmelidir.  
  
 Geri aramanın, `RuntimeSuspendAborted` geri çağırma ile aynı iş parçacığında oluşması garanti edilir `RuntimeSuspendStarted` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
