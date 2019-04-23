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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b17c7630160af78fe3163e6962b8fe085af1edc1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206622"
---
# <a name="icordebugilframe4-interface"></a>ICorDebugILFrame4 Arabirimi
[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]  
  
 Yerel değişkenleri ve Ara dil (IL) kodu bir yığın çerçevesi kodu erişim olanak tanıyan yöntemler sağlar. Bir parametre, hata ayıklayıcı değişkenleri ve ReJIT izleme profil oluşturucu, eklenen kod erişimi olup olmadığını belirtir.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[EnumerateLocalVariablesEx Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)|Geçerli kare yerel değişkenler listesini döndürür.|  
|[GetCodeEx Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)|Bu yığın çerçevesi çalışan kodu döndürür.|  
|[GetLocalVariableEx Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)|IL çerçevesinde yerel değişkenin değerini döndürür.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntemlere ek olarak, tarafından sağlanan işlevsellik sunabilir [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), ve [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) yöntemleri. Her yöntem içeren bir `flags` parametresi ek yerel değişkenler veya bir profil oluşturucunun ReJIT istek tarafından tanımlanan kod görünür olup olmadığını belirtir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug.idl, CorDebug.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Hata Ayıklama](../../../../docs/framework/unmanaged-api/debugging/index.md)
