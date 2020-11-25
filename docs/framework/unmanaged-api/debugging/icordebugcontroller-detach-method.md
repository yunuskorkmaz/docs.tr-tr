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
ms.openlocfilehash: 55acb6e3ec60925cba3d8aa5328547c54f270356
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732677"
---
# <a name="icordebugcontrollerdetach-method"></a>ICorDebugController::Detach Yöntemi

Hata ayıklayıcıyı işlem veya uygulama etki alanından ayırır.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a>Açıklamalar  

 İşlem veya uygulama etki alanı normal şekilde yürütmeye devam eder, ancak "ICorDebugProcess" veya "ICorDebugAppDomain" nesnesi artık geçerli değildir ve başka hiçbir geri çağırma gerçekleşmeyecektir.  
  
 .NET Framework sürüm 2,0 ' de, yönetilmeyen hata ayıklama etkinse, bu yöntem işletim sistemi sınırlamaları nedeniyle başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
