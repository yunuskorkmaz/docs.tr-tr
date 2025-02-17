---
description: ': ICorProfilerCallback:: Runtimethreadsürdürülme yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerCallback::RuntimeThreadResumed Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadResumed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadResumed
helpviewer_keywords:
- ICorProfilerCallback::RuntimeThreadResumed method [.NET Framework profiling]
- RuntimeThreadResumed method [.NET Framework profiling]
ms.assetid: da984f89-4f53-4ab0-ae6f-3e2ee6085994
topic_type:
- apiref
ms.openlocfilehash: a01be057bb442c69890d3b1cb4ebe1f861d2518c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657352"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a>ICorProfilerCallback::RuntimeThreadResumed Yöntemi

Profil oluşturucuyu, belirtilen iş parçacığının askıya alındıktan sonra devam ettirmekte olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a>Parametreler  

 `threadId`  
 'ndaki Devam eden iş parçacığının KIMLIĞI.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [RuntimeThreadSuspended Yöntemi](icorprofilercallback-runtimethreadsuspended-method.md)
