---
title: ICorDebugRuntimeUnwindableFrame Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugUnwindableFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnwindableFrame
helpviewer_keywords:
- ICorDebugUnwindableFrame interface [.NET Framework debugging]
ms.assetid: cd6a3982-6ed3-4909-808d-a66055e813e0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f006085aba140264e2a2605adce39924dbe082e4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568120"
---
# <a name="icordebugruntimeunwindableframe-interface"></a>ICorDebugRuntimeUnwindableFrame Arabirimi
Çerçeveyi geriye doğru izlemek için ortak dil çalışma zamanı (CLR) gerektiren yönetilmeyen yöntemler için destek sağlar.  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugRuntimeUnwindableFrame` Icordebugframe arabirimi, özelleştirilmiş bir sürümüdür. Geçerli yığındaki bir çerçeveyi geriye doğru izlemek için çalışma zamanı gerektiren yönetilmeyen yöntemler tarafından kullanılır. JIT olarak derlenmiş kod kullanmadığından mevcut geriye doğru izleme kuralları çalışmaz. Hata ayıklayıcı izlenemeyen bir çerçeve gördüğünde kullanması gereken [Icordebugstackwalk::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) yöntemi, ancak geriye doğru izleme, inceleme kendisini gerçekleştirmesi gereken. Hata ayıklayıcı aldığında bir `ICorDebugRuntimeUnwindableFrame`, çağırabilirsiniz [Icordebugstackwalk::getcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) çerçevenin içeriği almak için yöntemi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
