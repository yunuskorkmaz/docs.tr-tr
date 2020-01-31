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
ms.openlocfilehash: 32774aacecf3e56510bc6f0670538a44fde794c9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792983"
---
# <a name="icordebugmodule2-interface"></a>ICorDebugModule2 Arabirimi

ICorDebugModule arabirimine bir mantıksal uzantı görevi görür.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[ApplyChanges Yöntemi](icordebugmodule2-applychanges-method.md)|Meta verilerde yapılan değişiklikleri ve Microsoft ara dili (MSIL) kodundaki değişiklikleri çalışan işleme uygular.|  
|[GetJITCompilerFlags Yöntemi](icordebugmodule2-getjitcompilerflags-method.md)|Bu `ICorDebugModule2`için tam zamanında (JıT) derlemeyi denetleyen bayrakları alır.|  
|[ResolveAssembly Yöntemi](icordebugmodule2-resolveassembly-method.md)|Belirtilen meta veri belirtecinin başvurduğu derlemeyi çözer.|  
|[SetJITCompilerFlags Yöntemi](icordebugmodule2-setjitcompilerflags-method.md)|Bu `ICorDebugModule2`JıT derlemesini denetleyen bayrakları ayarlar.|  
|[SetJMCStatus Yöntemi](icordebugmodule2-setjmcstatus-method.md)|Bu `ICorDebugModule2` tüm sınıfların tüm yöntemlerinin Yalnızca kendi kodum (JMC) durumunu, `pTokens` dizisinde, zıt değere göre ayarlaanlar dışında, belirtilen değere ayarlar.|  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
