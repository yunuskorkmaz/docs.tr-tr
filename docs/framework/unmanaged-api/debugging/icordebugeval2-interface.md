---
title: Icordebugeval2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2
helpviewer_keywords: ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: fce34531-2687-406d-9131-d6ad94f2ce0e
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fbcf36ff7aca84299c55083b4ae135ce0a9ec4f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugeval2-interface1"></a>Icordebugeval2 Interface1
"ICorDebugEval" genişletir genel türleri için destek sağlamak için.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[CallParameterizedFunction yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|"Hangi Oluşturucusu tür parametreleri alır veya kendisi tür parametreleri sürebilir türü içinde yuvalanmış belirtilen ICorDebugFunction", çağrı ayarlar.|  
|[CreateValueForType yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|Bir işaretçi bir yeni "Icordebugvalue için" ilk bir null ya da sıfır değeriyle belirtilen türünü alır.|  
|[NewParameterizedArray yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|Belirtilen öğe türü ve boyutları yeni bir dizi ayırır.|  
|[NewParameterizedObject yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|Yeni bir parametreli türü nesnesi oluşturur ve nesnenin oluşturucusu yöntemini çağırır.|  
|[NewParameterizedObjectNoConstructor yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|Belirtilen sınıfının yeni bir parametreli türü nesnesi Oluşturucusu yöntemini çağırmak çalışırken olmadan başlatır|  
|[NewStringWithLength yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|Belirtilen uzunlukta yeni bir dize belirtilen içerikle oluşturur.|  
|[RudeAbort yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|Hesaplama durdurur bu `ICorDebugEval2` şu anda gerçekleştiriyor.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
>  Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
