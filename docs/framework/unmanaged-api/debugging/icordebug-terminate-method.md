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
ms.openlocfilehash: 2d3f8360a1fb1164fd4e26f85246251409bee376
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788957"
---
# <a name="icordebugterminate-method"></a>ICorDebug::Terminate Yöntemi
`ICorDebug` nesnesini sonlandırır.  
  
> [!NOTE]
> hata ayıklamakta olan tüm işlemler için [ICorDebugManagedCallback:: ExitProcess](icordebugmanagedcallback-exitprocess-method.md) geri çağırması alınana kadar `Terminate` çağrılmamalıdır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `Terminate`, `ICorDebug` nesnesine artık gerek kalmadığında çağrılmalıdır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebug Arabirimi](icordebug-interface.md)
