---
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
ms.openlocfilehash: 33a39cf2781f49ff0e31989831c4c9829889ec3d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732009"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a>ICorProfilerCallback::RuntimeThreadSuspended Yöntemi

Profil oluşturucuyu belirtilen iş parçacığının askıya alındığını veya askıya alınmayı bildirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
