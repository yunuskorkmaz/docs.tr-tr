---
description: ': ICorDebugBreakpoint arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 63917512cceeccedea37acdf2ba7ab3b849d9fad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711810"
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
