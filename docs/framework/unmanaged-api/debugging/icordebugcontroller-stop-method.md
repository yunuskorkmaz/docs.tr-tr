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
ms.openlocfilehash: 2cd0fc9f86515d63533275002301eb47f11feebb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411272"
---
# <a name="icordebugcontrollerstop-method"></a>ICorDebugController::Stop Yöntemi
Yönetilen kod işlemde çalışan tüm iş parçacıklarının işbirlikçi Dur gerçekleştirir.  
  
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
 `Stop` üzerinde çalışan tüm iş parçacıklarının işbirlikçi durdurma yönetilen kodu işleminde gerçekleştirir. Bir yalnızca yönetilen hata ayıklama oturumu sırasında yönetilmeyen iş parçacığı çalışmaya devam edebilir (ancak yönetilen koda çağrı çalışılırken engellenir). Hata ayıklama oturumunun bir birlikte çalışma sırasında yönetilmeyen iş parçacığı de durdurulur. `dwTimeoutIgnored` Değeri şu anda yoksayıldı ve SONSUZ (-1) kabul edilir. İşbirlikçi Durdur bir kilitlenme nedeniyle başarısız olursa, tüm iş parçacıklarını askıya alınır ve E_TIMEOUT döndürülür.  
  
> [!NOTE]
>  `Stop` yalnızca zaman uyumlu hata ayıklama API'si yöntemidir. Zaman `Stop` döndürür S_OK, işlem durduruldu. Geri arama yok Durdur dinleyicileri bildirmek için verilir. Hata ayıklayıcı çağırmalısınız [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) işleminin devam etmesini izin vermek için.  
  
 Hata ayıklayıcı Dur sayaç tutar. Sayaç sıfıra gittiğinde, denetleyici devam ettirilir. Her çağrı `Stop` veya gönderilen her geri çağırma sayaç artırılır. Her çağrı `ICorDebugController::Continue` azaltır sayacı.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 
