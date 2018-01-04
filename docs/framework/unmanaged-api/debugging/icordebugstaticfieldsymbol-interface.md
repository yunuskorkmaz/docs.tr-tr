---
title: ICorDebugStaticFieldSymbol arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a25e19bf43d852670bc5f4f491fb25707395e04a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstaticfieldsymbol-interface"></a>ICorDebugStaticFieldSymbol arabirimi
Statik bir alana hata ayıklama sembol bilgilerini temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetAddress Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|Statik alan adresini alır.|  
|[GetName Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|Statik alanın adını alır.|  
|[GetSize Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|Statik alanının bayt cinsinden boyutu alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugStaticFieldSymbol` Arabirimi statik bir alan için hata ayıklama simgesi bilgi almak için kullanılır.  
  
> [!NOTE]
>  Bu arabirim yalnızca .NET yerel ile kullanılabilir. Bu arabirim .NET yerel dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirim göz ardı eder.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugInstanceFieldSymbol Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
