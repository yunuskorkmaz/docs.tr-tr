---
title: ICorDebugVariableSymbol Arabirimi
ms.date: 03/30/2017
ms.assetid: 0e58b85e-69bd-41ff-bedb-8cdc8be6a7a2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3fb2538894184c19bc107ce52cbef3ac86a97345
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967976"
---
# <a name="icordebugvariablesymbol-interface"></a>ICorDebugVariableSymbol Arabirimi
Bir değişken için hata ayıklama sembol bilgisini alır.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetName Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getname-method.md)|Bir değişkenin adını alır.|  
|[GetSize Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getsize-method.md)|Bir değişkenin boyutunu bayt cinsinden alır.|  
|[GetSlotIndex Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getslotindex-method.md)|Yerel bir değişkenin yönetilen yuva dizinini alır.|  
|[GetValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-getvalue-method.md)|Bir değişkenin değerini bir bayt dizisi olarak alır.|  
|[SetValue Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-setvalue-method.md)|Bir bayt dizisinin değerini bir değişkene atar.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim yalnızca .NET Native kullanılabilir. Bu arabirimi .NET Native dışında ICorDebug senaryolarında uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
