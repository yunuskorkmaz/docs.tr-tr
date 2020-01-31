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
ms.openlocfilehash: 7f1c5d7a6fdae3e4c5a66c9aa4a82911105f4597
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788501"
---
# <a name="icordebugilframe4-interface"></a>ICorDebugILFrame4 Arabirimi
[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]  
  
 Ara dil (IL) kodunun yığın çerçevesindeki yerel değişkenlere ve koda erişmenize imkan tanıyan yöntemler sağlar. Bir parametre, hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen değişkenlere ve koda erişip erişemeyeceğini belirtir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumerateLocalVariablesEx Yöntemi](icordebugilframe4-enumeratelocalvariablesex-method.md)|Geçerli çerçevede kullanılabilir olan yerel değişkenlerin listesini döndürür.|  
|[GetCodeEx Yöntemi](icordebugilframe4-getcodeex-method.md)|Bu yığın çerçevesinin çalıştığı kodu döndürür.|  
|[GetLocalVariableEx Yöntemi](icordebugilframe4-getlocalvariableex-method.md)|Il çerçevesindeki yerel bir değişkenin değerini döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntemler, [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md), [GetCode](icordebugframe-getcode-method.md)ve [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) yöntemleri tarafından sağlana ek olarak işlevsellik sunar. Her yöntem, profil oluşturucunun ReJIT isteği tarafından tanımlanan ek yerel değişkenlerin veya kodun görünür olup olmadığını belirten bir `flags` parametresi içerir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
- [Hata Ayıklama](index.md)
