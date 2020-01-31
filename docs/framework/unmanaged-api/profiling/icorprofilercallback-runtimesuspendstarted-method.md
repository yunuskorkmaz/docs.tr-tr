---
title: ICorProfilerCallback::RuntimeSuspendStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted method [.NET Framework profiling]
- RuntimeSuspendStarted method [.NET Framework profiling]
ms.assetid: c8461cac-e31b-4efa-ad2c-26598173eb96
topic_type:
- apiref
ms.openlocfilehash: e88f6356c2e29a1d8a9e49527c5921e8155c3ce4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865889"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a>ICorProfilerCallback::RuntimeSuspendStarted Yöntemi
Profil oluşturucuya çalışma zamanının tüm çalışma zamanı iş parçacıklarını askıya almak için olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a>Parametreler  
 `suspendReason`  
 'ndaki Askıya alma nedenini gösteren [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) numaralandırması değeri.  
  
## <a name="remarks"></a>Açıklamalar  
 Yönetilmeyen koddaki tüm çalışma zamanı iş parçacıklarının, çalışma zamanını yeniden girmeye çalıştıklarında çalışmaya devam etmesine izin verilir. Bu noktada, çalışma zamanı sürdürülene kadar de askıya alınır. Bu, çalışma zamanını belirten yeni iş parçacıkları için de geçerlidir. Çalışma zamanındaki tüm iş parçacıkları, zaten kesilebilir kodunda olduklarında askıya alınır ya da kesilebilir koduna ulaştığında askıya alınması istenir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [RuntimeSuspendAborted Yöntemi](icorprofilercallback-runtimesuspendaborted-method.md)
- [RuntimeSuspendFinished Yöntemi](icorprofilercallback-runtimesuspendfinished-method.md)
