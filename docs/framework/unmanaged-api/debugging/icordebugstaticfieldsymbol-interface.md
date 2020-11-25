---
title: ICorDebugStaticFieldSymbol Arabirimi
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
ms.openlocfilehash: fcf3bb61ccd903f2dd375e638814247a98aaf7b2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717571"
---
# <a name="icordebugstaticfieldsymbol-interface"></a>ICorDebugStaticFieldSymbol Arabirimi

Statik bir alan için hata ayıklama simgesi bilgisini temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetAddress Yöntemi](icordebugstaticfieldsymbol-getaddress-method.md)|Statik alanın adresini alır.|  
|[GetName Yöntemi](icordebugstaticfieldsymbol-getname-method.md)|Statik alanın adını alır.|  
|[GetSize Yöntemi](icordebugstaticfieldsymbol-getsize-method.md)|Statik alanın bayt cinsinden boyutunu alır.|  
  
## <a name="remarks"></a>Açıklamalar  

 `ICorDebugStaticFieldSymbol`Arabirim, bir statik alana yönelik hata ayıklama simgesi bilgilerini almak için kullanılır.  
  
> [!NOTE]
> Bu arabirim yalnızca .NET Native kullanılabilir. Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugInstanceFieldSymbol Arabirimi](icordebuginstancefieldsymbol-interface.md)
- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
