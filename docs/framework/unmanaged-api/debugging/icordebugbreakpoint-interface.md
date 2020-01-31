---
title: ICorDebugBreakpoint Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint
helpviewer_keywords:
- ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type:
- apiref
ms.openlocfilehash: 53d8d219a13f2dade16a338efccf0837f8de0158
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784370"
---
# <a name="icordebugbreakpoint-interface"></a>ICorDebugBreakpoint Arabirimi

Bir işlevde bir kesme noktasını veya bir değer üzerinde bir izleme noktasını temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Activate Yöntemi](icordebugbreakpoint-activate-method.md)|Bu `ICorDebugBreakpoint`etkin durumunu ayarlar.|  
|[IsActive Yöntemi](icordebugbreakpoint-isactive-method.md)|Bu `ICorDebugBreakpoint` etkin olup olmadığını gösteren bir değer alır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Kesme noktaları, Koşullu ifadeleri doğrudan desteklemez. Bu işlevsellik isteniyorsa, bir hata ayıklayıcı onu `ICorDebugBreakpoint`en üstünde uygulamalıdır.  
  
 ICorDebugFunctionBreakpoint Arabirimi, işlevleri içindeki kesme noktalarını desteklemek için `ICorDebugBreakpoint` genişletir.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
