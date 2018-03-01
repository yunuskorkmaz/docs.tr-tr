---
title: Icordebugvalue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue
helpviewer_keywords:
- ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c3464b4ad963b2fe764cefc5868440b7748f8c4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvalue-interface1"></a>Icordebugvalue Interface1
Ayıklanacak işlemindeki bir değeri temsil eder. Değer bir okuma veya yazma değeri olabilir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateBreakpoint Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|Bu metot şu anda uygulanmadı.|  
|[GetAddress Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|Bu adresini alır `ICorDebugValue` hata ayıklaması sürecinde nesne.|  
|[GetSize Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|Bu bayt cinsinden boyutu alır `ICorDebugValue` nesnesi.|  
|[GetType Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|Bu temel türünü alır `ICorDebugValue` nesnesi.|  
  
## <a name="remarks"></a>Açıklamalar  
 Genel olarak, bu döndürüldüğünde bir değer nesnesi sahipliğini geçirilir. Alıcı nesnesiyle tamamlandığında, bir başvuru nesneden kaldırmak için sorumludur.  
  
 İşlem çıktıktan sonra değeri gelen alındığı bağlı olarak, değeri geçerli sürdürülemeyebilir. Bu nedenle, genel olarak, değerin bir çağrıyla tutulması döndürmemelidir [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) yöntemi.  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
    
    
    
    
 [ICorDebugValue3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
