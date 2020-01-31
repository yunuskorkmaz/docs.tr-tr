---
title: ICorDebugInstanceFieldSymbol Arabirimi
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
ms.openlocfilehash: 41258b0eeed5fbf8ab86546f74073f8eeaa3085c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777520"
---
# <a name="icordebuginstancefieldsymbol-interface"></a>ICorDebugInstanceFieldSymbol Arabirimi
Bir örnek alanı için hata ayıklama simgesi bilgisini temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetName Yöntemi](icordebuginstancefieldsymbol-getname-method.md)|Örnek alanının adını alır.|  
|[GetOffset Yöntemi](icordebuginstancefieldsymbol-getoffset-method.md)|Üst sınıfındaki bu örnek alanının bayt cinsinden konumunu alır.|  
|[GetSize Yöntemi](icordebuginstancefieldsymbol-getsize-method.md)|Örnek alanının bayt cinsinden boyutunu alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugInstanceFieldSymbol` arabirimi bir örnek alanı için hata ayıklama sembol bilgisini almak için kullanılır.  
  
> [!NOTE]
> Bu arabirim yalnızca .NET Native kullanılabilir. Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugStaticFieldSymbol Arabirimi](icordebugstaticfieldsymbol-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
