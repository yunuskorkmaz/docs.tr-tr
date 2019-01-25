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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 63d03e83e1688979e4fffe5d31d1f3c393f60e44
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573589"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a>ICorProfilerCallback::RuntimeSuspendAborted Yöntemi
Profil Oluşturucu çalışma zamanı oluşan çalışma zamanı askıya alınması iptal edildiğini bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Çalışma zamanı askıya almak iki iş parçacığı aynı anda denerseniz çalışma zamanı askıya alınması iptal.  
  
 Her iki [Icorprofilercallback::runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) geri çağırma veya `RuntimeSuspendAborted` geri çağırma bir tek iş parçacığı şu oluşacak bir [Icorprofilercallback::runtimesuspendstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) geri çağırma.  
  
 `RuntimeSuspendAborted` Aynı iş parçacığı üzerinde gerçekleşmesi için geri çağırma garantisi `RuntimeSuspendStarted` geri çağırma.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
