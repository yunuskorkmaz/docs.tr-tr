---
title: ICorDebug::Terminate Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebug.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Terminate
helpviewer_keywords:
- Terminate method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Terminate method [.NET Framework debugging]
ms.assetid: fffe5616-0896-4426-ab5e-21869b514883
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 321298ce942b35d11a861c87cdf6b8714179ea97
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786314"
---
# <a name="icordebugterminate-method"></a>ICorDebug::Terminate Yöntemi
Sonlandırır `ICorDebug` nesne.  
  
> [!NOTE]
>  `Terminate` kadar çağrılmamalıdır bir [Icordebugmanagedcallback::exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) hata ayıklama gerçekleştirilen tüm işlemler için geri çağırma alınmış.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `Terminate` ne zaman çağrılmalıdır `ICorDebug` nesne artık gerekli.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebug Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
