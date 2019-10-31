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
ms.openlocfilehash: 51ee8b3631bffe9fd7fef4351e0aa67d1cbbe2c9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125393"
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
 dışı Belirtilen iş parçacığı için şu anda herhangi bir yönetilen geri çağırma sıraya alınmışsa `true` bir değere yönelik işaretçi. Aksi takdirde, `false`.  
  
 `pThread` parametresi için null belirtilirse `HasQueuedCallbacks`, şu anda herhangi bir iş parçacığı için sıraya alınmış yönetilen geri çağrılar varsa `true` döndürülür.  
  
## <a name="remarks"></a>Açıklamalar  
 Geri çağrılar her seferinde bir kez gönderilir, her zaman [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) çağrılır. Hata ayıklayıcı, aynı anda oluşan birden çok hata ayıklama olayını raporlamak isterse bu bayrağı denetleyebilir.  
  
 Hata ayıklama olaylarının sırası sıralandığında, zaten gerçekleştiyse, bu nedenle hata ayıklayıcının, hata ayıklamanın durumuyla emin olmak için tüm kuyruğu boşaltmalıdır. (Kuyruğu boşaltmak için `ICorDebugController::Continue` çağırın.) Örneğin, kuyruk *x*iş parçacığı üzerinde iki hata ayıklama olayı içeriyorsa ve hata ayıklayıcı ilk hata ayıklama olayından sonra Iş parçacığı *x* 'i askıya alıyorsa ve `ICorDebugController::Continue`çağırırsa, *x* iş parçacığı için ikinci hata ayıklama olayı şu şekilde gönderilir iş parçacığı askıya alındı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
