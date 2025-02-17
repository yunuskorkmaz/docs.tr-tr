---
description: ': Icordebugstackyürüme arabirimi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 27dcdfc90829a3a28d81ad28dce0cd4d1d674948
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738097"
---
# <a name="icordebugstackwalk-interface"></a>ICorDebugStackWalk Arabirimi

İş parçacığının yığınındaki yönetilen yöntemleri veya çerçeveleri almak için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetContext Yöntemi](icordebugstackwalk-getcontext-method.md)|Nesnedeki geçerli karenin bağlamını döndürür `ICorDebugStackWalk` .|  
|[SetContext Yöntemi](icordebugstackwalk-setcontext-method.md)|`ICorDebugStackWalk`Nesnenin geçerli bağlamını iş parçacığı için geçerli bir bağlam olarak ayarlar.|  
|[Next Yöntemi](icordebugstackwalk-next-method.md)|`ICorDebugStackWalk`Nesneyi sonraki çerçeveye kaydırır.|  
|[GetFrame Yöntemi](icordebugstackwalk-getframe-method.md)|Nesnenin geçerli çerçevesini alır `ICorDebugStackWalk` .|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
