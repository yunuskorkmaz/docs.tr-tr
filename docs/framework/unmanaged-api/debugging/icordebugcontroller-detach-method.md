---
title: ICorDebugController::Detach Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugController.Detach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Detach
helpviewer_keywords:
- Detach method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Detach method [.NET Framework debugging]
ms.assetid: 06fae364-f2c6-4a50-aa7e-3da9f2684dc3
topic_type:
- apiref
ms.openlocfilehash: b98077914d680c908587649fdd517aca9c8dcd40
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125439"
---
# <a name="icordebugcontrollerdetach-method"></a>ICorDebugController::Detach Yöntemi
Hata ayıklayıcıyı işlem veya uygulama etki alanından ayırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 İşlem veya uygulama etki alanı normal şekilde yürütmeye devam eder, ancak "ICorDebugProcess" veya "ICorDebugAppDomain" nesnesi artık geçerli değildir ve başka hiçbir geri çağırma gerçekleşmeyecektir.  
  
 .NET Framework sürüm 2,0 ' de, yönetilmeyen hata ayıklama etkinse, bu yöntem işletim sistemi sınırlamaları nedeniyle başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
