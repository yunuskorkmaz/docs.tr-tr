---
description: 'Daha fazla bilgi edinin: ICorDebugVirtualUnwinder Interface'
title: ICorDebugVirtualUnwinder Arabirimi
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
ms.openlocfilehash: e941ace2e7f72c9f7956c03bae19f9b92094b338
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738084"
---
# <a name="icordebugvirtualunwinder-interface"></a>ICorDebugVirtualUnwinder Arabirimi

Yığın geri sarma konusunda yardımcı olmak için yöntemler sağlar.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Name|  
|------------|----------|  
|[GetContext Yöntemi](icordebugvirtualunwinder-getcontext-method.md)|Bu unwinder 'in geçerli bağlamını alır.|  
|[Next Yöntemi](icordebugvirtualunwinder-next-method.md)|Çağıranın bağlamına ilerletir.|  
  
## <a name="remarks"></a>Açıklamalar  

 Arabirim üyeleri, `ICorDebugVirtualUnwinder` yığın geri sarma konusunda yardımcı olmak için hata ayıklayıcı tarafından uygulanır.  
  
> [!NOTE]
> Bu arabirim yalnızca .NET Native kullanılabilir. Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
