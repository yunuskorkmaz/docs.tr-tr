---
title: ICorProfilerCallback::ThreadDestroyed Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadDestroyed
helpviewer_keywords:
- ThreadDestroyed method [.NET Framework profiling]
- ICorProfilerCallback::ThreadDestroyed method [.NET Framework profiling]
ms.assetid: 4c2b66fd-0595-40a3-8931-f9c4fff97ac8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 40bbde940538d7b06aa74ab55986da2dca3ec225
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599510"
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a>ICorProfilerCallback::ThreadDestroyed Yöntemi
Profil Oluşturucu, bir iş parçacığı yok edildi bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `threadId`  
 [in] Yok edilmiş iş parçacığı kimliği.  
  
## <a name="remarks"></a>Açıklamalar  
 `threadId` Değeri artık geçerli değil Bu çağrı anda.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ThreadCreated Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)
