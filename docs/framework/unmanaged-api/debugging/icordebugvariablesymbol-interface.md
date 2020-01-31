---
title: ICorDebugVariableSymbol Arabirimi
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
ms.openlocfilehash: 9d17bc92dcae9e906dfe18d7665fbf489d278234
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790865"
---
# <a name="icordebugvariablesymbol-interface"></a>ICorDebugVariableSymbol Arabirimi
Bir değişken için hata ayıklama sembol bilgisini alır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetName Yöntemi](icordebugvariablesymbol-getname-method.md)|Bir değişkenin adını alır.|  
|[GetSize Yöntemi](icordebugvariablesymbol-getsize-method.md)|Bir değişkenin boyutunu bayt cinsinden alır.|  
|[GetSlotIndex Yöntemi](icordebugvariablesymbol-getslotindex-method.md)|Yerel bir değişkenin yönetilen yuva dizinini alır.|  
|[GetValue Yöntemi](icordebugvariablesymbol-getvalue-method.md)|Bir değişkenin değerini bir bayt dizisi olarak alır.|  
|[SetValue Yöntemi](icordebugvariablesymbol-setvalue-method.md)|Bir bayt dizisinin değerini bir değişkene atar.|  
  
## <a name="remarks"></a>Açıklamalar  
  
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
