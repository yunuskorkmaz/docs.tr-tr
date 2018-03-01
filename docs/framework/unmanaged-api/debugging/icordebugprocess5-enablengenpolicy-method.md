---
title: "ICorDebugProcess5::EnableNGENPolicy Yöntemi"
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
- ICorDebugProcess5::EnableNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dca0df7b0be643d53bb5b9a03bd3abbb186d69dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5enablengenpolicy-method"></a>ICorDebugProcess5::EnableNGENPolicy Yöntemi
Yönetilen hata ayıklayıcı altında çalışırken yerel görüntüler nasıl bir uygulamanın yüklediği belirleyen bir değer ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ePolicy`  
 [in] A [cordebugngenpolicy sabit](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) nasıl yönetilen bir hata ayıklayıcı altında çalışırken yerel görüntüler bir uygulamanın yüklediği belirler sabiti.  
  
## <a name="remarks"></a>Açıklamalar  
 İlke başarılı bir şekilde ayarlanmışsa, yöntem `S_OK`. Varsa `ePolicy` tarafından tanımlanan Enum değerleri aralığı dışında [cordebugngenpolicy sabit](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), yöntem döndürür `E_INVALIDARG` ve yöntem çağrısının etkisi yoktur. Yerel Görüntü Oluşturucu (Ngen.exe) ilkesi güncelleştirilemiyor ise, yöntem `E_FAIL`.  
  
 `ICorDebugProcess5::EnableNGenPolicy` Yöntemi, işlem kullanım ömrü süresince herhangi bir zamanda çağrılabilir. İlke İlkesi ayarlandıktan sonra yüklü olan tüm modülleri için etkindir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorDebugProcess5 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
