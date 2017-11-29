---
title: "ICorProfilerCallback::ThreadAssignedToOSThread Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ThreadAssignedToOSThread
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ThreadAssignedToOSThread
helpviewer_keywords:
- ThreadAssignedToOSThread method [.NET Framework profiling]
- ICorProfilerCallback::ThreadAssignedToOSThread method [.NET Framework profiling]
ms.assetid: f9671e5a-7b14-4f5b-8404-58136422c8b2
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c70de2b53fd428361d5404aa406d2b2be67d0914
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a>ICorProfilerCallback::ThreadAssignedToOSThread Yöntemi
Profil Oluşturucu, belirli bir işletim sistemi iş parçacığı kullanan bir yönetilen iş parçacığı uygulanan olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `managedThreadId`  
 [in] Yönetilen iş parçacığı tanımlayıcısı.  
  
 `osThreadId`  
 [in] İşletim sistemi iş parçacığı tanımlayıcısı.  
  
## <a name="remarks"></a>Açıklamalar  
 `ThreadAssignedToOSThread` Geri çağırma var. böylece profil oluşturucu lifleri yönetilen iş parçacığı için işletim sistemi iş parçacıkları arasında doğru bir eşleme koruyabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icorprofilercallback arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
