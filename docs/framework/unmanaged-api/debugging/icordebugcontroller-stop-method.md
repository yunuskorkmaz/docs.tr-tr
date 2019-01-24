---
title: ICorDebugController::Stop Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugController.Stop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4cb5b091aadbdd503dd7988f713f40a00876a2dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608332"
---
# <a name="icordebugcontrollerstop-method"></a>ICorDebugController::Stop Yöntemi
Yönetilen kod işlemde çalışan tüm iş parçacıkları üzerinde işbirliği yapan Durma gerçekleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwTimeoutIgnored`  
 Kullanılmadı.  
  
## <a name="remarks"></a>Açıklamalar  
 `Stop` işlemdeki tüm iş parçacıkları üzerinde işbirliği yapan durdurma yönetilen kodu gerçekleştirir. Yalnızca yönetilen hata ayıklama oturumu sırasında yönetilmeyen iş parçacığı çalışmaya devam edebilir (ancak yönetilen kod çağrılmaya çalışılırken engellenecek). Hata ayıklama oturumu bir birlikte çalışma sırasında yönetilmeyen iş parçacığı da durdurulur. `dwTimeoutIgnored` Değeri şu anda yok sayıldı ve SONSUZ (-1) kabul edilir. İşbirlikçi Durdur kilitlenme nedeniyle başarısız olursa, tüm iş parçacıkları askıya alınır ve E_TIMEOUT döndürülür.  
  
> [!NOTE]
>  `Stop` hata ayıklama API'sindeki yalnızca zaman uyumlu yöntemdir. Zaman `Stop` döndürür: S_OK, işlem durduruldu. Hiçbir geri çağırma duraklarının dinleyicileri bildirmek için verilir. Hata ayıklayıcı çağırmalıdır [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) işleminin devam etmesini sağlayacak.  
  
 Hata ayıklayıcıyı Durdur sayaç tutar. Sayaç sıfıra gittiğinde, denetleyici sürdürülür. Her çağrı `Stop` veya her gönderilen geri çağırma sayacı artırır. Her çağrı `ICorDebugController::Continue` azaltır sayacı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

