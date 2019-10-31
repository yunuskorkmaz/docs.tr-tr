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
ms.openlocfilehash: 2902744b6af3c7b2bd4def73b04807ce3333a8a1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131883"
---
# <a name="icordebugruntimeunwindableframe-interface"></a>ICorDebugRuntimeUnwindableFrame Arabirimi
Çerçeveyi geriye doğru izlemek için ortak dil çalışma zamanı (CLR) gerektiren yönetilmeyen yöntemler için destek sağlar.  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugRuntimeUnwindableFrame`, ICorDebugFrame arabiriminin özelleşmiş bir sürümüdür. Çalışma zamanının geçerli yığında bir çerçeveyi geriye doğru bir şekilde aşağı doğru bir şekilde geri kopyasını gerektiren yönetilmeyen yöntemler tarafından kullanılır. Mevcut geri sarma kuralları, JıT derlenmiş kod kullanmadığından çalışmaz. Hata ayıklayıcı beklenmeyen bir çerçeve gördüğünde, geri dönmek için [ıcordebugstackizlenecek:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) metodunu kullanmalıdır, ancak İnceleme kendisini gerçekleştirmelidir. Hata ayıklayıcı bir `ICorDebugRuntimeUnwindableFrame`aldığında, çerçeve bağlamını almak için [ıcordebugstackyürüme:: GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) metodunu çağırabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
