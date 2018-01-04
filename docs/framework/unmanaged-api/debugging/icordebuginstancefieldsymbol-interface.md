---
title: ICorDebugInstanceFieldSymbol arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b13df0d70a36e475e87bae3152912e58a9f8443
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginstancefieldsymbol-interface"></a>ICorDebugInstanceFieldSymbol arabirimi
Bir örnek alanındaki hata ayıklama sembol bilgilerini temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetName Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|Örnek alanın adını alır.|  
|[GetOffset Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|Bu örnek alanı kendi üst sınıfı'bayt uzaklığını alır.|  
|[GetSize Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|Örnek alanı bayt cinsinden boyutu alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 `ICorDebugInstanceFieldSymbol` Arabirimi bir örnek alanındaki hata ayıklama sembol bilgilerini almak için kullanılır.  
  
> [!NOTE]
>  Bu arabirim yalnızca .NET yerel ile kullanılabilir. Bu arabirim .NET yerel dışında Icordebug senaryoları için uygularsanız, ortak dil çalışma zamanı bu arabirim göz ardı eder.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugStaticFieldSymbol Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
