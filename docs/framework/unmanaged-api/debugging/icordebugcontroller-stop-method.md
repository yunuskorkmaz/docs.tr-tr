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
ms.openlocfilehash: c8c6b40f7a9c63a577140209eed65436040addcb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125381"
---
# <a name="icordebugcontrollerstop-method"></a>ICorDebugController::Stop Yöntemi
İşlemde yönetilen kod çalıştıran tüm iş parçacıkları üzerinde birlikte bir durdurma işlemi gerçekleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `dwTimeoutIgnored`  
 Kullanılmadı.  
  
## <a name="remarks"></a>Açıklamalar  
 `Stop`, işlemde yönetilen kod çalıştıran tüm iş parçacıklarında birlikte bir durdurma işlemi gerçekleştirir. Yalnızca yönetilen bir hata ayıklama oturumu sırasında, yönetilmeyen iş parçacıkları çalışmaya devam edebilir (ancak yönetilen kodu çağırmaya çalışırken engellenecektir). Birlikte çalışma hata ayıklama oturumu sırasında, yönetilmeyen iş parçacıkları da durdurulacak. `dwTimeoutIgnored` değeri şu anda yoksayıldı ve sonsuz (-1) olarak kabul edilir. Kilitlenme nedeniyle birlikte çalışmayan durdurma başarısız olursa, tüm iş parçacıkları askıya alınır ve E_TIMEOUT döndürülür.  
  
> [!NOTE]
> `Stop`, hata ayıklama API 'sindeki tek zaman uyumlu yöntemidir. `Stop` S_OK döndürdüğünde, işlem durdurulur. Durun dinleyicilerini bilgilendirmek için hiçbir geri arama verilmez. Hata ayıklayıcı, işlemin devam etmesine izin vermek için [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) çağırmalıdır.  
  
 Hata ayıklayıcı bir durdurma sayacı tutar. Sayaç sıfıra gittiğinde, denetleyici sürdürülür. `Stop` veya dağıtılan her bir geri çağırma çağrısı sayacı arttırır. `ICorDebugController::Continue` yapılan her çağrı sayacı azaltır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
