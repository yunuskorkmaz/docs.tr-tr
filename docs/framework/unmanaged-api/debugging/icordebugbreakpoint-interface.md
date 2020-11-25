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
ms.openlocfilehash: 0c84a91c7da553d0c84a4995b4744576d861dcb9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730207"
---
# <a name="icordebugbreakpoint-interface"></a>ICorDebugBreakpoint Arabirimi

Bir işlevde bir kesme noktasını veya bir değer üzerinde bir izleme noktasını temsil eder.  
  
## <a name="methods"></a>Yöntemler  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Activate Yöntemi](icordebugbreakpoint-activate-method.md)|Bunun etkin durumunu ayarlar `ICorDebugBreakpoint` .|  
|[IsActive Yöntemi](icordebugbreakpoint-isactive-method.md)|Bu, etkin olup olmadığını gösteren bir değer alır `ICorDebugBreakpoint` .|  
  
## <a name="remarks"></a>Açıklamalar  

 Kesme noktaları, Koşullu ifadeleri doğrudan desteklemez. Bu tür işlevler isteniyorsa, bir hata ayıklayıcının üzerinde uygulaması gerekir `ICorDebugBreakpoint` .  
  
 ICorDebugFunctionBreakpoint Arabirimi `ICorDebugBreakpoint` işlevleri içindeki kesme noktalarını destekleyecek şekilde genişletilir.  
  
> [!NOTE]
> Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklama Arabirimleri](debugging-interfaces.md)
