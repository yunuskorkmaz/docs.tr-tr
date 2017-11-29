---
title: ICorDebugStackWalk Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStackWalk
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStackWalk
helpviewer_keywords: ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0c8a4421b716614081368755388bd2ab8d8fe22e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstackwalk-interface"></a>ICorDebugStackWalk Arabirimi
İş parçacığının yığınındaki yönetilen yöntemleri veya çerçeveleri almak için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetContext yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|Geçerli kare bağlamının döndürür `ICorDebugStackWalk` nesnesi.|  
|[SetContext yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|Ayarlar `ICorDebugStackWalk` nesnenin iş parçacığı için geçerli bir bağlam için geçerli bağlam.|  
|[Next yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|Taşır `ICorDebugStackWalk` sonraki çerçeveye nesne.|  
|[GetFrame yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|Geçerli çerçeve alır `ICorDebugStackWalk` nesnesi.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
