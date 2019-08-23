---
title: ICorDebugModule2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugModule2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2
helpviewer_keywords:
- ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8fe1a25c4bc1f5e19f49f0d660d0aad5a180ea2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911896"
---
# <a name="icordebugmodule2-interface"></a>ICorDebugModule2 Arabirimi

ICorDebugModule arabirimine bir mantıksal uzantı görevi görür.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ApplyChanges Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|Meta verilerde yapılan değişiklikleri ve Microsoft ara dili (MSIL) kodundaki değişiklikleri çalışan işleme uygular.|  
|[GetJITCompilerFlags Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|Bunun `ICorDebugModule2`için tam zamanında (JIT) derlemeyi denetleyen bayrakları alır.|  
|[ResolveAssembly Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|Belirtilen meta veri belirtecinin başvurduğu derlemeyi çözer.|  
|[SetJITCompilerFlags Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|Bu `ICorDebugModule2`için JIT derlemesini denetleyen bayrakları ayarlar.|  
|[SetJMCStatus Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|Bu, `pTokens` dizideki tüm yöntemlerin tüm yöntemlerinin yalnızca kendi kodum (JMC) durumunu, dizideki değerler hariç `ICorDebugModule2` , bu değerin ters değere göre ayarlanır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi** CorDebug. IDL, CorDebug. h  
  
 **Kitaplığı** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
