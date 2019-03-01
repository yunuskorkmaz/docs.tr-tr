---
title: ICorDebugEval2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugEval2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2
helpviewer_keywords:
- ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: fce34531-2687-406d-9131-d6ad94f2ce0e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4315c9f5296e8c3ffc9d8241b929c71c2448db6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965871"
---
# <a name="icordebugeval2-interface"></a>ICorDebugEval2 Arabirimi

"ICorDebugEval" genişleten genel türler için destek sağlamak için.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CallParameterizedFunction Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|"Hangi tür parametreleri alır veya kendi tür parametreleri alabilir, Oluşturucusu türü içinde iç içe belirtilen ICorDebugFunction", bir çağrı ayarlar.|  
|[CreateValueForType Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|Bir işaretçi bir yeni "Icordebugvalue için" bir başlangıç değeri null ya da sıfır ile belirtilen türünü alır.|  
|[NewParameterizedArray Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|Belirtilen öğe türü ve boyut yeni bir dizi ayırır.|  
|[NewParameterizedObject Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|Yeni bir parametreli tür nesnesi oluşturur ve nesnenin oluşturucusu yöntemini çağırır.|  
|[NewParameterizedObjectNoConstructor Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|Belirtilen sınıfın yeni bir parametreli tür nesnesi bir oluşturucu yöntemini çağırma girişimi olmadan örneğini oluşturur.|  
|[NewStringWithLength Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|Belirtilen içerikle belirtilen uzunlukta yeni bir dize oluşturur.|  
|[RudeAbort Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|Hesaplama durdurur bu `ICorDebugEval2` şu anda gerçekleştiriyor.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
