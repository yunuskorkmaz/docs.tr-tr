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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85a9bde77f7c393756ec1d3e7d30b96392aa6a94
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151807"
---
# <a name="icordebugcontrollerdetach-method"></a>ICorDebugController::Detach Yöntemi
Hata ayıklayıcı işlem veya uygulama etki alanından ayırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 İşlem veya uygulama etki alanı normalde, yürütme devam eder, ancak "ICorDebugProcess" veya "ICorDebugAppDomain" nesne artık geçerli değil ve başka hiçbir geri çağırmaları meydana gelir.  
  
 .NET Framework sürüm 2. 0'da, bu yöntem, yönetilmeyen hata ayıklama etkinleştirilirse, işletim sistemi sınırlamaları nedeniyle başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
