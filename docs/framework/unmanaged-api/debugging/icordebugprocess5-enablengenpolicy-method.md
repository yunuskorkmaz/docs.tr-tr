---
title: ICorDebugProcess5::EnableNGENPolicy Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 154243e45a41ec2ba8b02937794b372a0705d458
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219128"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a>ICorDebugProcess5::EnableNGENPolicy Yöntemi
Nasıl bir uygulama yönetilen bir hata ayıklayıcı altında çalışırken yerel görüntüleri yükler belirleyen değeri ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 `ePolicy`  
 [in] A [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md) nasıl bir uygulama yönetilen bir hata ayıklayıcı altında çalışırken yerel görüntüleri yükler belirleyen sabiti.  
  
## <a name="remarks"></a>Açıklamalar  
 İlke başarıyla olarak ayarlanırsa, yöntem döndürür `S_OK`. Varsa `ePolicy` tarafından tanımlanan Enum değerleri aralığı dışında [CorDebugNGenPolicy](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md), yöntemi döndürür `E_INVALIDARG` ve yöntem çağrısının hiçbir etkisi olmaz. Native Image Generator (Ngen.exe) ilkesi güncelleştirilemiyor ise, yöntem döndürür `E_FAIL`.  
  
 `ICorDebugProcess5::EnableNGenPolicy` İşlem ömrü boyunca herhangi bir zamanda yöntemi çağrılabilir. İlke, ilkeyi ayarlandıktan sonra yüklenen tüm modüller için geçerli olur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorDebugProcess5 Arabirimi](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
