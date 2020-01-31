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
ms.openlocfilehash: a6283d699263dc9b79e457010f31923f77443129
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791887"
---
# <a name="icordebugstackwalk-interface"></a>ICorDebugStackWalk Arabirimi
İş parçacığının yığınındaki yönetilen yöntemleri veya çerçeveleri almak için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetContext Yöntemi](icordebugstackwalk-getcontext-method.md)|`ICorDebugStackWalk` nesnesindeki geçerli karenin bağlamını döndürür.|  
|[SetContext Yöntemi](icordebugstackwalk-setcontext-method.md)|`ICorDebugStackWalk` nesnenin geçerli bağlamını iş parçacığı için geçerli bir bağlam olarak ayarlar.|  
|[Next Yöntemi](icordebugstackwalk-next-method.md)|`ICorDebugStackWalk` nesnesini sonraki çerçeveye kaydırır.|  
|[GetFrame Yöntemi](icordebugstackwalk-getframe-method.md)|`ICorDebugStackWalk` nesnesindeki geçerli çerçeveyi alır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
