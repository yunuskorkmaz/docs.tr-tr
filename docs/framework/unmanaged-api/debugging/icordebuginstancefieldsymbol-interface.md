---
title: Icordebugınstancefieldsymbol arabirimi
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 082d8e8c8b57b7d0938f59aebbe08e35a7e3f7df
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560754"
---
# <a name="icordebuginstancefieldsymbol-interface"></a>Icordebugınstancefieldsymbol arabirimi
Bir örnek alanıyla hata ayıklama sembolü bilgilerini temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetName Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|Örnek alanı adını alır.|  
|[GetOffset Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|Bu örnek alanı kendi üst sınıfı'bayt uzaklığını alır.|  
|[GetSize Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|Örnek alanı bayt cinsinden boyutunu alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugInstanceFieldSymbol` Arabirimi, bir örnek alanıyla hata ayıklama sembolü bilgilerini almak için kullanılır.  
  
> [!NOTE]
>  Bu arabirim yalnızca .NET Native ile kullanılabilir. Bu arabirim .NET Native dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirimi yoksayar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorDebugStaticFieldSymbol Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
