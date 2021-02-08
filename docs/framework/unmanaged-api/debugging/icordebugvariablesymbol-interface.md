---
description: ': ICorDebugVariableSymbol arabirimi hakkında daha fazla bilgi edinin'
title: ICorDebugVariableSymbol Arabirimi
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
ms.openlocfilehash: fa3fc1f318627e9175a3066c3bd3eac00929ea60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790548"
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

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
