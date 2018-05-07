---
title: ICorDebugController::HasQueuedCallbacks Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugController.HasQueuedCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::HasQueuedCallbacks
helpviewer_keywords:
- HasQueuedCallbacks method [.NET Framework debugging]
- ICorDebugController::HasQueuedCallbacks method [.NET Framework debugging]
ms.assetid: 0d6a1cd9-370b-4462-adbf-e3980e897ea7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eba265b727d00690ab77c6ae831e954d59df7c50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a>ICorDebugController::HasQueuedCallbacks Yöntemi
Tüm yönetilen geri aramalar için belirtilen iş parçacığı sıraya alınmış olup olmadığını belirten bir değer alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pThread`  
 [in] İş parçacığı temsil eden bir "ICorDebugThread" nesnesi için bir işaretçi.  
  
 `pbQueued`  
 [out] Bir değer için bir işaretçi `true` tüm yönetilen geri aramalar şu anda, belirtilen iş parçacığı için sıraya alınan Aksi takdirde `false`.  
  
 İçin NULL belirtilirse `pThread` parametresi `HasQueuedCallbacks` döndürülecek `true` şu anda yönetilen geri aramalar için herhangi bir iş parçacığı sıraya alındı.  
  
## <a name="remarks"></a>Açıklamalar  
 Geri aramalar gönderilen birer birer, her zaman olacaktır [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) olarak adlandırılır. Hata ayıklayıcı, aynı anda gerçekleşen birden çok hata ayıklama olaylara rapor isterse Bu bayrak kontrol edebilirsiniz.  
  
 Hata ayıklama olayları sıralandığında hata ayıklayıcı ayıklayıcı durumunu emin olmak için tüm kuyruk boşaltma gerekir böylece bunlar zaten, oluştu. (Çağrı `ICorDebugController::Continue` sıranın boşaltmak için.) Örneğin, sıranın iş parçacığı üzerinde iki hata ayıklama olayları içeriyorsa *X*, ve iş parçacığı hata ayıklayıcı bekletir *X* ilk hata ayıklama olayı ve ardından çağrıları sonra `ICorDebugController::Continue`, ikinci hata ayıklama olayı için iş parçacığı *X* iş parçacığı askıya alındı ancak gönderilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 
