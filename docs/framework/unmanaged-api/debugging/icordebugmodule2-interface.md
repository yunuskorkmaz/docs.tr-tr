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
ms.openlocfilehash: a3a1b658f4ab05c7029de907882fe5ab2513ccd8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127880"
---
# <a name="icordebugmodule2-interface"></a>ICorDebugModule2 Arabirimi

ICorDebugModule arabirimine bir mantıksal uzantı görevi görür.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ApplyChanges Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|Meta verilerde yapılan değişiklikleri ve Microsoft ara dili (MSIL) kodundaki değişiklikleri çalışan işleme uygular.|  
|[GetJITCompilerFlags Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|Bu `ICorDebugModule2`için tam zamanında (JıT) derlemeyi denetleyen bayrakları alır.|  
|[ResolveAssembly Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|Belirtilen meta veri belirtecinin başvurduğu derlemeyi çözer.|  
|[SetJITCompilerFlags Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|Bu `ICorDebugModule2`JıT derlemesini denetleyen bayrakları ayarlar.|  
|[SetJMCStatus Yöntemi](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|Bu `ICorDebugModule2` tüm sınıfların tüm yöntemlerinin Yalnızca kendi kodum (JMC) durumunu, `pTokens` dizisinde, zıt değere göre ayarlaanlar dışında, belirtilen değere ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
