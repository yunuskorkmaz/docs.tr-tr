---
title: ICorDebugThread::SetDebugState Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread.SetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::SetDebugState
helpviewer_keywords:
- ICorDebugThread::SetDebugState method [.NET Framework debugging]
- SetDebugState method [.NET Framework debugging]
ms.assetid: 6382bdf6-d488-4952-b653-cb09b6e1c6c2
topic_type:
- apiref
ms.openlocfilehash: e28d37e4477862ff2ebeeb05ea5f5386e157cd83
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678749"
---
# <a name="icordebugthreadsetdebugstate-method"></a>ICorDebugThread::SetDebugState Yöntemi

Bu ICorDebugThread 'in hata ayıklama durumunu tanımlayan bayrakları ayarlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `state`  
 'ndaki Bu iş parçacığının hata ayıklama durumunu belirten, CorDebugThreadState numaralandırma değerlerinin bit düzeyinde birleşimi.  
  
## <a name="remarks"></a>Açıklamalar  

 `SetDebugState` iş parçacığının geçerli hata ayıklama durumunu ayarlar. ("Geçerli hata ayıklama durumu" işlemi devam etseydi, gerçek geçerli durum değil, hata ayıklama durumunu temsil eder.) Bunun için normal değer THREAD_RUN. Yalnızca hata ayıklayıcı bir iş parçacığının hata ayıklama durumunu etkileyebilir. Hata ayıklama durumları son boyunca devam eder, bu nedenle bir iş parçacığı THREAD_SUSPENDed birden çok kez devam etmek istiyorsanız, onu bir kez ayarlayabilir ve bundan sonra endişelenmenize gerek kalmaz. İş parçacıklarını askıya almak ve işlemi sürdürmek kilitlenmeye neden olabilir, ancak bu genellikle düşüktür. Bu, iş parçacıklarının ve işlemlerin gerçek bir kalitesidir ve tasarıma göre yapılır. Hata ayıklayıcı kilitlenme kesmek için zaman uyumsuz olarak kesintiye uğratır ve iş parçacıklarını sürdürür. İş parçacığının kullanıcı durumu USER_UNSAFE_POINT içeriyorsa, iş parçacığı çöp toplamayı (GC) engelleyebilir. Bu, askıya alınan iş parçacığının kilitlenmeye neden olma olasılığını çok daha yüksek olduğu anlamına gelir. Bu, zaten kuyruğa alınmış olan hata ayıklama olaylarını etkilemeyebilir. Bu nedenle, iş parçacıklarını askıya almadan veya devam ettirmeden önce hata ayıklayıcı tüm olay kuyruğunu ( [ICorDebugController:: HasQueuedCallbacks](icordebugcontroller-hasqueuedcallbacks-method.md)çağırarak) boşaltmalıdır. Diğer bir deyişle, zaten askıya alınmış olduğunu düşündüğü bir iş parçacığında olayları alabilir.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
