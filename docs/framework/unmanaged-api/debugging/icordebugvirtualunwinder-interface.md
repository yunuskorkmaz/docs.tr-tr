---
title: ICorDebugVirtualUnwinder Arabirimi
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
ms.openlocfilehash: 065f71e45c2a56dbaa16a45f70958ca3dea80c48
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790831"
---
# <a name="icordebugvirtualunwinder-interface"></a>ICorDebugVirtualUnwinder Arabirimi
Yığın geri sarma konusunda yardımcı olmak için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Name|  
|------------|----------|  
|[GetContext Yöntemi](icordebugvirtualunwinder-getcontext-method.md)|Bu unwinder 'in geçerli bağlamını alır.|  
|[Next Yöntemi](icordebugvirtualunwinder-next-method.md)|Çağıranın bağlamına ilerletir.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugVirtualUnwinder` arabiriminin üyeleri, yığın geri sarma konusunda yardımcı olmak için hata ayıklayıcı tarafından uygulanır.  
  
> [!NOTE]
> Bu arabirim yalnızca .NET Native kullanılabilir. Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
