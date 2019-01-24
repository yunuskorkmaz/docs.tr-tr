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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bb93dbf35501d44bb21d3d689aebeba3acd19f79
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616816"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a>ICorProfilerCallback::RuntimeThreadSuspended Yöntemi
Belirtilen iş parçacığını askıya alındı veya askıya alınması için profil oluşturucu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `threadId`  
 [in] Askıya alındı iş parçacığının kimliği.  
  
## <a name="remarks"></a>Açıklamalar  
 `RuntimeThreadSuspended` Bildirim arasında istediğiniz zaman meydana gelebilir [Icorprofilercallback::runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) ve ilişkili [Icorprofilercallback::runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) geri çağırmalar. Bildirimler arasında gerçekleşen [Icorprofilercallback::runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) ve `RuntimeResumeStarted` çalışmakta olan, iş parçacıklarını yönetilmeyen kod ve çalışma zamanı girişte askıya alındığından.  
  
 Genellikle, yalnızca bir iş parçacığı askıda sonra bu geri çağırma gerçekleşir. Ancak, yürütülmekte olan iş parçacığını (Bu geri çağırma çağıran iş parçacığının) askıya alınmış bir ise, bu geri arama yalnızca iş parçacığını askıya alınmadan önce ortaya çıkar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [RuntimeThreadResumed Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
