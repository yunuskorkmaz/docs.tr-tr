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
ms.openlocfilehash: 26b0c78d5b34b920decc8c549d90ba8147e3f323
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791915"
---
# <a name="icordebugruntimeunwindableframe-interface"></a>ICorDebugRuntimeUnwindableFrame Arabirimi
Çerçeveyi geriye doğru izlemek için ortak dil çalışma zamanı (CLR) gerektiren yönetilmeyen yöntemler için destek sağlar.  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugRuntimeUnwindableFrame`, ICorDebugFrame arabiriminin özelleşmiş bir sürümüdür. Çalışma zamanının geçerli yığında bir çerçeveyi geriye doğru bir şekilde aşağı doğru bir şekilde geri kopyasını gerektiren yönetilmeyen yöntemler tarafından kullanılır. Mevcut geri sarma kuralları, JıT derlenmiş kod kullanmadığından çalışmaz. Hata ayıklayıcı beklenmeyen bir çerçeve gördüğünde, geri dönmek için [ıcordebugstackizlenecek:: Next](icordebugstackwalk-next-method.md) metodunu kullanmalıdır, ancak İnceleme kendisini gerçekleştirmelidir. Hata ayıklayıcı bir `ICorDebugRuntimeUnwindableFrame`aldığında, çerçeve bağlamını almak için [ıcordebugstackyürüme:: GetContext](icordebugstackwalk-getcontext-method.md) metodunu çağırabilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
