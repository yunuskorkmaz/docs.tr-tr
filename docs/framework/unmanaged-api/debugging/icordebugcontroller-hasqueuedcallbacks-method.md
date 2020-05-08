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
ms.openlocfilehash: bd656445c2451d0583ddbc45e71c9e090bb80305
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892787"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a>ICorDebugController::HasQueuedCallbacks Yöntemi
Belirtilen iş parçacığı için herhangi bir yönetilen geri çağırmaların sıraya alınıp alınmayacağını gösteren bir değer alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pThread`  
 'ndaki İş parçacığını temsil eden "ICorDebugThread" nesnesine yönelik bir işaretçi.  
  
 `pbQueued`  
 dışı Belirtilen iş parçacığı için şu anda herhangi `true` bir yönetilen geri çağırmalar sıraya alınmışsa bir değer işaretçisi; Aksi takdirde `false`,.  
  
 `pThread` Parametresi için null belirtilirse, `HasQueuedCallbacks` Şu anda herhangi bir iş parçacığı için sıraya alınmış yönetilen geri çağrılar varsa döndürülür `true` .  
  
## <a name="remarks"></a>Açıklamalar  
 Geri çağrılar her seferinde bir kez gönderilir, her zaman [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) çağrılır. Hata ayıklayıcı, aynı anda oluşan birden çok hata ayıklama olayını raporlamak isterse bu bayrağı denetleyebilir.  
  
 Hata ayıklama olaylarının sırası sıralandığında, zaten gerçekleştiyse, bu nedenle hata ayıklayıcının, hata ayıklamanın durumuyla emin olmak için tüm kuyruğu boşaltmalıdır. (Kuyruğu `ICorDebugController::Continue` boşaltmak için çağırın.) Örneğin, kuyruk *x*iş parçacığı üzerinde iki hata ayıklama olayı içeriyorsa ve hata ayıklayıcı ilk hata ayıklama olayından sonra Iş parçacığı *x* 'i askıya alıyorsa ve sonra `ICorDebugController::Continue`, iş parçacığı askıya alınmış olsa da, iş parçacığı *x* için ikinci hata ayıklama olayı gönderilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
