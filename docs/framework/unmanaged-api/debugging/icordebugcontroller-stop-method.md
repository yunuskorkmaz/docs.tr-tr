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
ms.openlocfilehash: 11cc6e4108a2064a8a9fcefa760bf3c3411d63fb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679864"
---
# <a name="icordebugcontrollerstop-method"></a>ICorDebugController::Stop Yöntemi

İşlemde yönetilen kod çalıştıran tüm iş parçacıkları üzerinde birlikte bir durdurma işlemi gerçekleştirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `dwTimeoutIgnored`  
 Kullanılmadı.  
  
## <a name="remarks"></a>Açıklamalar  

 `Stop` işlemde yönetilen kod çalıştıran tüm iş parçacıklarında birlikte bir durdurma gerçekleştirir. Yalnızca yönetilen bir hata ayıklama oturumu sırasında, yönetilmeyen iş parçacıkları çalışmaya devam edebilir (ancak yönetilen kodu çağırmaya çalışırken engellenecektir). Birlikte çalışma hata ayıklama oturumu sırasında, yönetilmeyen iş parçacıkları da durdurulacak. `dwTimeoutIgnored`Değer şu anda yoksayıldı ve sonsuz (-1) olarak kabul edilir. Kilitlenme nedeniyle birlikte çalışmayan durdurma başarısız olursa, tüm iş parçacıkları askıya alınır ve E_TIMEOUT döndürülür.  
  
> [!NOTE]
> `Stop` , hata ayıklama API 'sindeki tek zaman uyumlu yöntemidir. `Stop`S_OK döndüğünde işlem durdurulur. Durun dinleyicilerini bilgilendirmek için hiçbir geri arama verilmez. Hata ayıklayıcı, işlemin devam etmesine izin vermek için [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) çağırmalıdır.  
  
 Hata ayıklayıcı bir durdurma sayacı tutar. Sayaç sıfıra gittiğinde, denetleyici sürdürülür. Dağıtılan her bir `Stop` geri çağırma veya her bir çağrı sayacı arttırır. Her bir çağrı `ICorDebugController::Continue` sayacı azaltır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
