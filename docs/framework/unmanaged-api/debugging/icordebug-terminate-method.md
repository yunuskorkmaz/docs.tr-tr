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
ms.openlocfilehash: cf9c9d11c4725908fcf7ff4a0c91882b70a80190
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723382"
---
# <a name="icordebugterminate-method"></a>ICorDebug::Terminate Yöntemi

Nesneyi sonlandırır `ICorDebug` .  
  
> [!NOTE]
> `Terminate` hata ayıklamakta olan tüm işlemler için [ICorDebugManagedCallback:: ExitProcess](icordebugmanagedcallback-exitprocess-method.md) geri çağırması alınana kadar çağrılmamalıdır.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a>Açıklamalar  

 `Terminate``ICorDebug`nesne artık gerekli olmadığında çağrılmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebug Arabirimi](icordebug-interface.md)
