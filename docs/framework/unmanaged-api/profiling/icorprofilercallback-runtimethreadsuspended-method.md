---
description: ': ICorProfilerCallback:: Runtimethreadaskıya alındı yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::RuntimeThreadSuspended Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadSuspended
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadSuspended
helpviewer_keywords:
- RuntimeThreadSuspended method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeThreadSuspended method [.NET Framework profiling]
ms.assetid: de830a8b-6ee1-4900-ace3-4237108f6b12
topic_type:
- apiref
ms.openlocfilehash: f7c2f5baf5a320375d9a2606ca05b13d522336be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657340"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a>ICorProfilerCallback::RuntimeThreadSuspended Yöntemi

Profil oluşturucuyu belirtilen iş parçacığının askıya alındığını veya askıya alınmayı bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a>Parametreler  

 `threadId`  
 'ndaki Askıya alınmış olan iş parçacığının KIMLIĞI.  
  
## <a name="remarks"></a>Açıklamalar  

 `RuntimeThreadSuspended`Bildirim, [ICorProfilerCallback:: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) ve Ilişkili [ICorProfilerCallback:: RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) geri çağırmaları arasında herhangi bir zaman oluşabilir. [ICorProfilerCallback:: RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) arasında oluşan bildirimler ve `RuntimeResumeStarted` yönetilmeyen kodda çalışan ve çalışma zamanına giriş yapıldığında askıya alınan iş parçacıkları içindir.  
  
 Genellikle, bu geri çağrı yalnızca bir iş parçacığı askıya alındıktan sonra oluşur. Ancak, şu anda yürütülmekte olan iş parçacığı (Bu geri çağırma işlemini çağıran iş parçacığı) askıya alınmışsa, bu geri arama iş parçacığı askıya alınmadan hemen önce gerçekleşir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [RuntimeThreadResumed Yöntemi](icorprofilercallback-runtimethreadresumed-method.md)
