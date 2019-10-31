---
title: ICorDebugILFrame4 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame4
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1e739183-3e05-49e5-846f-4075256e41de
topic_type:
- apiref
ms.openlocfilehash: 010d73309ae21f9a593f72533691bdd95fbd4132
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130845"
---
# <a name="icordebugilframe4-interface"></a>ICorDebugILFrame4 Arabirimi
[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Ara dil (IL) kodunun yığın çerçevesindeki yerel değişkenlere ve koda erişmenize imkan tanıyan yöntemler sağlar. Bir parametre, hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen değişkenlere ve koda erişip erişemeyeceğini belirtir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumerateLocalVariablesEx Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)|Geçerli çerçevede kullanılabilir olan yerel değişkenlerin listesini döndürür.|  
|[GetCodeEx Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)|Bu yığın çerçevesinin çalıştığı kodu döndürür.|  
|[GetLocalVariableEx Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)|Il çerçevesindeki yerel bir değişkenin değerini döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntemler, [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)ve [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) yöntemleri tarafından sağlana ek olarak işlevsellik sunar. Her yöntem, profil oluşturucunun ReJIT isteği tarafından tanımlanan ek yerel değişkenlerin veya kodun görünür olup olmadığını belirten bir `flags` parametresi içerir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
