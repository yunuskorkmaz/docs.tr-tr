---
title: Icordebugvalue arabirimi1
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
ms.openlocfilehash: 41afc2e4305034340ad408e52ce08372bf8962dd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54507453"
---
# <a name="icordebugvalue-interface1"></a>Icordebugvalue arabirimi1
Hatası ayıklanmakta olan işlemindeki bir değeri temsil eder. Değer, bir okuma veya yazma değeri olabilir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CreateBreakpoint Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|Bu yöntem henüz uygulanmadı.|  
|[GetAddress Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|Bu adresini alır `ICorDebugValue` ayıklanan sürecinde olan nesne.|  
|[GetSize Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|Bu bayt cinsinden boyutunu alır `ICorDebugValue` nesne.|  
|[GetType Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|Bu temel türünü alır `ICorDebugValue` nesne.|  
  
## <a name="remarks"></a>Açıklamalar  
 Genel olarak, bu iade edildiğinde bir değer nesnesini sahipliğini geçirilir. Alıcı, nesneyle tamamlandığında, bir başvuru nesneden kaldırmak için sorumludur.  
  
 İşlem çıktıktan sonra nerede değeri öğesinden alınan bağlı olarak, değeri geçerli sürdürülemeyebilir. Bu nedenle, genel olarak, değerin bir çağrıyla tutulması olmamalıdır [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) yöntemi.  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.




- [ICorDebugValue3 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
