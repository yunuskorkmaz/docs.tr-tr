---
title: Icordebugvalue Interface1
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0fe53490014a2a7d9acc0a426613af54867599e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422129"
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
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
    
    
    
    
 [ICorDebugValue3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
