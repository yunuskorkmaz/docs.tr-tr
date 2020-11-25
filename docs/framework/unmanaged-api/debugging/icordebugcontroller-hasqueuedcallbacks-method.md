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
ms.openlocfilehash: bd623f8bee2feafebe80c0c7513bcfb33d6ad367
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707925"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a>ICorDebugController::HasQueuedCallbacks Yöntemi

Belirtilen iş parçacığı için herhangi bir yönetilen geri çağırmaların sıraya alınıp alınmayacağını gösteren bir değer alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 dışı `true` Belirtilen iş parçacığı için şu anda herhangi bir yönetilen geri çağırma sıraya alınmışsa bir değer işaretçisi; Aksi takdirde, `false` .  
  
 Parametresi için null belirtilirse `pThread` , `HasQueuedCallbacks` `true` Şu anda herhangi bir iş parçacığı için sıraya alınmış yönetilen geri çağrılar varsa döndürülür.  
  
## <a name="remarks"></a>Açıklamalar  

 Geri çağrılar her seferinde bir kez gönderilir, her zaman [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) çağrılır. Hata ayıklayıcı, aynı anda oluşan birden çok hata ayıklama olayını raporlamak isterse bu bayrağı denetleyebilir.  
  
 Hata ayıklama olaylarının sırası sıralandığında, zaten gerçekleştiyse, bu nedenle hata ayıklayıcının, hata ayıklamanın durumuyla emin olmak için tüm kuyruğu boşaltmalıdır. ( `ICorDebugController::Continue` Kuyruğu boşaltmak için çağırın.) Örneğin, kuyruk *x* iş parçacığı üzerinde iki hata ayıklama olayı içeriyorsa ve hata ayıklayıcı ilk hata ayıklama olayından sonra Iş parçacığı *x* 'i askıya alıyorsa ve sonra `ICorDebugController::Continue` , iş parçacığı askıya alınmış olsa da, iş parçacığı *x* için ikinci hata ayıklama olayı gönderilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
