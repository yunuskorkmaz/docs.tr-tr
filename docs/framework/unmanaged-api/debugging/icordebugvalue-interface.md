---
title: Icordebugvalue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue
helpviewer_keywords: ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 01c94df1d8e6ddef0110268461a2b28f594201b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvalue-interface1"></a>Icordebugvalue Interface1
Ayıklanacak işlemindeki bir değeri temsil eder. Değer bir okuma veya yazma değeri olabilir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateBreakpoint yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|Bu metot şu anda uygulanmadı.|  
|[GetAddress yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|Bu adresini alır `ICorDebugValue` hata ayıklaması sürecinde nesne.|  
|[GetSize yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|Bu bayt cinsinden boyutu alır `ICorDebugValue` nesnesi.|  
|[GetType yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|Bu temel türünü alır `ICorDebugValue` nesnesi.|  
  
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
    
    
    
    
 [Icordebugvalue3 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
