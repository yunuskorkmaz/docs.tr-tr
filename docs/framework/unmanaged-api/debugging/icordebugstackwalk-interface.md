---
title: ICorDebugStackWalk Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk
helpviewer_keywords:
- ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb58040394d99ae0c5a10672946fa5a6ead5e751
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54533422"
---
# <a name="icordebugstackwalk-interface"></a>ICorDebugStackWalk Arabirimi
İş parçacığının yığınındaki yönetilen yöntemleri veya çerçeveleri almak için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetContext Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|Geçerli kare bağlamını döndürür `ICorDebugStackWalk` nesne.|  
|[SetContext Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|Kümeleri `ICorDebugStackWalk` iş parçacığı için geçerli bir bağlamı için geçerli bağlam nesnesi.|  
|[Next Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|Taşır `ICorDebugStackWalk` sonraki kareye nesne.|  
|[GetFrame Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|Geçerli çerçevenin alır `ICorDebugStackWalk` nesne.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
