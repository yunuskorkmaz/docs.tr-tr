---
title: "ICorDebugProcess5::EnableNGENPolicy Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5::EnableNGenPolicy
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cd259308494e1a86f0a6cdec8866bb66a1614b76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Icordebugprocess5 arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [Hata ayıklama arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Hata ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
