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
ms.openlocfilehash: 3a107176e48a88a0a04534f7044c1e416caf4091
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788887"
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
 Kullanılmıyor.  
  
## <a name="remarks"></a>Açıklamalar  
 `Stop`, işlemde yönetilen kod çalıştıran tüm iş parçacıklarında birlikte bir durdurma işlemi gerçekleştirir. Yalnızca yönetilen bir hata ayıklama oturumu sırasında, yönetilmeyen iş parçacıkları çalışmaya devam edebilir (ancak yönetilen kodu çağırmaya çalışırken engellenecektir). Birlikte çalışma hata ayıklama oturumu sırasında, yönetilmeyen iş parçacıkları da durdurulacak. `dwTimeoutIgnored` değeri şu anda yoksayıldı ve sonsuz (-1) olarak kabul edilir. Kilitlenme nedeniyle birlikte çalışmayan durdurma başarısız olursa, tüm iş parçacıkları askıya alınır ve E_TIMEOUT döndürülür.  
  
> [!NOTE]
> `Stop`, hata ayıklama API 'sindeki tek zaman uyumlu yöntemidir. `Stop` S_OK döndürdüğünde işlem durdurulur. Durun dinleyicilerini bilgilendirmek için hiçbir geri arama verilmez. Hata ayıklayıcı, işlemin devam etmesine izin vermek için [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) çağırmalıdır.  
  
 Hata ayıklayıcı bir durdurma sayacı tutar. Sayaç sıfıra gittiğinde, denetleyici sürdürülür. `Stop` veya dağıtılan her bir geri çağırma çağrısı sayacı arttırır. `ICorDebugController::Continue` yapılan her çağrı sayacı azaltır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
