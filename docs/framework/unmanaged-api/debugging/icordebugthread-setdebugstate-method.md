---
title: "ICorDebugThread::SetDebugState Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f2754caf11f89358b3e81e6324835d5b2e12f17e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadsetdebugstate-method"></a>ICorDebugThread::SetDebugState Yöntemi
Bu Icordebugthread hata ayıklama durumunu açıklayan bayrakları ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `state`  
 [in] Bu iş parçacığı hata ayıklama durumunu belirtin CorDebugThreadState numaralandırma değerlerinin Bitsel bir birleşimi.  
  
## <a name="remarks"></a>Açıklamalar  
 `SetDebugState`iş parçacığı geçerli hata ayıklama durumunu ayarlar. (İşlemi devam için gerçek geçerli durumunda olsaydı "Geçerli hata ayıklama durumu" hata ayıklama durumu gösterir.) Normal bu THREAD_RUNNING değerdir. Hata ayıklayıcı yalnızca bir iş parçacığı hata ayıklama durumunu etkileyebilir. Durumları hata ayıklama son çapraz devam eder, böylece THREAD_SUSPENDed birden çok üzerinden devam bir iş parçacığı tutmak istiyorsanız, bir kez ayarlamak ve bundan sonra hakkında endişelenmenize gerek kalmaz. İş parçacıklarını askıya alma ve sürdürme işlemi kilitlenmeler, genellikle olsa da neden olabilir. Bu bir iç iş parçacıklarında ve işlemlerde kalitesi ve tasarım gereği. Zaman uyumsuz olarak bir hata ayıklayıcısı bölün ve kilitlenme ayırmak için iş parçacığı sürdürün. İş parçacığının kullanıcı durumunu USER_UNSAFE_POINT içeriyorsa, iş parçacığı çöp toplama (GC) engelleyebilir. Başka bir deyişle, askıya alınmış iş parçacığı bir kilitlenmeye neden bir çok daha yüksek olasılığı vardır. Bu olaylar zaten kuyruğa alınmış hata ayıklama etkileyebilir değil. Bir hata ayıklayıcısı tüm olay sırası böylece boşaltma (çağırarak [Icordebugcontroller::hasqueuedcallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) askıya alma veya iş parçacıklarını sürdürme önce. Else olayları askıya aldı bulunduğu bir iş parçacığında alabilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
