---
description: ': Icordebugınstancefieldsymbol arabirimi hakkında daha fazla bilgi edinin'
title: ICorDebugInstanceFieldSymbol Arabirimi
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
ms.openlocfilehash: aa47c858ec5b4b0d04b851357fe81c0fc9b2e30a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791139"
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

 `ICorDebugInstanceFieldSymbol`Arabirim, bir örnek alanı için hata ayıklama sembol bilgisini almak için kullanılır.  
  
> [!NOTE]
> Bu arabirim yalnızca .NET Native kullanılabilir. Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugStaticFieldSymbol Arabirimi](icordebugstaticfieldsymbol-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
