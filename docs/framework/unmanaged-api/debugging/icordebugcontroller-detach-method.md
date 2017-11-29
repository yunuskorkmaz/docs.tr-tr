---
title: "ICorDebugController::Detach Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.Detach
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::Detach
helpviewer_keywords:
- Detach method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Detach method [.NET Framework debugging]
ms.assetid: 06fae364-f2c6-4a50-aa7e-3da9f2684dc3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2d8c1df2fd2aa52f9f5e90a27d42f6568686e908
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollerdetach-method"></a>ICorDebugController::Detach Yöntemi
Hata ayıklayıcı işlem veya uygulama etki alanından ayırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 İşlem veya uygulama etki alanı yürütme normal şekilde devam eder, ancak "ICorDebugProcess" veya "ICorDebugAppDomain" nesne artık geçerli değil ve başka hiçbir geri aramalar meydana gelir.  
  
 Yönetilmeyen hata ayıklama etkinleştirilirse, .NET Framework sürüm 2. 0'da, işletim sistemi kısıtlamaları nedeniyle bu yöntem başarısız olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 
