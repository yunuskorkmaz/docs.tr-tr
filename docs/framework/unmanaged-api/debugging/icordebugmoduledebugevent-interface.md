---
title: ICorDebugModuleDebugEvent Arabirimi
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7bf1fa21872c710ebc69c45e9980aeaa577a45fc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160920"
---
# <a name="icordebugmoduledebugevent-interface"></a>ICorDebugModuleDebugEvent Arabirimi
Genişletir [Icordebugdebugevent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) Modül düzeyinde olaylar desteklemek için arabirim.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[GetModule Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|Yalnızca yüklü veya kaldırılmış birleştirilmiş modül alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) ve [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) olay türleri bu arabirimi uygulayın.  
  
> [!NOTE]
>  Arabirimi yalnızca .NET Native ile kullanılabilir. Arama girişimi `QueryInterface` bir arabirim işaretçisini almak için döndürür `E_NOINTERFACE` .NET Native dışında Icordebug senaryolar için.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
