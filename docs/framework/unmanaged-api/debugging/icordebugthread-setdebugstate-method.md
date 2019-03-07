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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d29f5cefd22592fa8949ff5361109c09c0972b24
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499699"
---
# <a name="icordebugthreadsetdebugstate-method"></a>ICorDebugThread::SetDebugState Yöntemi
Bu Icordebugthread hata ayıklama durumunu açıklayan bir bayrak ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `state`  
 [in] Bu iş parçacığı hata ayıklama durumunu belirten CorDebugThreadState sabit listesi değerlerinin Bitsel bir birleşimi.  
  
## <a name="remarks"></a>Açıklamalar  
 `SetDebugState` Geçerli iş parçacığı hata ayıklama durumunu ayarlar. (İşlemi devam için gerçek geçerli durumunda olsaydı "Geçerli hata ayıklama durumunu" hata ayıklama durumunu gösterir.) Normal bu THREAD_RUNNING değerdir. Yalnızca hata ayıklayıcı, bir iş parçacığı hata ayıklama durumunu etkileyebilir. Hata ayıklama durumlarını son boyunca devam eder, bir iş parçacığı üzerinde birden çok THREAD_SUSPENDed devam tutmak istiyorsanız, bunu ayarlamalı ve bundan sonra endişelenmenize gerek yok. İş parçacıklarını askıya alma ve sürdürme işlemi kilitlenmeler, genellikle olsa da neden olabilir. Bu bir iç kalitesi iş parçacıklarında ve işlemlerde ve tasarım. Zaman uyumsuz olarak bir hata ayıklayıcı kesme ve kilitlenme ayırmak için iş parçacığı sürdürme. Kullanıcı durumu iş parçacığının USER_UNSAFE_POINT içeriyorsa, iş parçacığı bir çöp toplama (GC) engelliyor olabilir. Bu, askıya alınan iş parçacığı bir kilitlenmeye neden olan bir çok daha yüksek şansı anlamına gelir. Bu, hata ayıklama olaylarını zaten kuyruğa alınmış etkilemeyebilir. Bu nedenle bir hata ayıklayıcı tüm olay sırasındaki boşaltma (çağırarak [Icordebugcontroller::hasqueuedcallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) askıya alma ya da iş parçacıklarını önce. Aksi takdirde, zaten askıya aldı düşündüğü bir iş parçacığı üzerinde olayları alabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
