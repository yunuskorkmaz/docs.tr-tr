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
ms.workload: dotnet
ms.openlocfilehash: 018ed69e52efd21ca25029284c70f1c8493d877f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstackwalk-interface"></a>ICorDebugStackWalk Arabirimi
İş parçacığının yığınındaki yönetilen yöntemleri veya çerçeveleri almak için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetContext Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|Geçerli kare bağlamının döndürür `ICorDebugStackWalk` nesnesi.|  
|[SetContext Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|Ayarlar `ICorDebugStackWalk` nesnenin iş parçacığı için geçerli bir bağlam için geçerli bağlam.|  
|[Next Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|Taşır `ICorDebugStackWalk` sonraki çerçeveye nesne.|  
|[GetFrame Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|Geçerli çerçeve alır `ICorDebugStackWalk` nesnesi.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
