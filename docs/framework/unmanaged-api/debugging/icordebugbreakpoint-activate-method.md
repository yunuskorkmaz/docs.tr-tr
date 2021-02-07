---
description: ': ICorDebugBreakpoint:: Activate yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugBreakpoint::Activate Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint.Activate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint::Activate
helpviewer_keywords:
- ICorDebugBreakpoint::Activate method [.NET Framework debugging]
- Activate method [.NET Framework debugging]
ms.assetid: e30c29f7-3f19-4081-b572-a731aa14cd44
topic_type:
- apiref
ms.openlocfilehash: 1a3613ae071b3fc6c4f1005eafd515946d6b2685
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711875"
---
# <a name="icordebugbreakpointactivate-method"></a>ICorDebugBreakpoint::Activate Yöntemi

Bunun etkin durumunu ayarlar `ICorDebugBreakpoint` .  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Activate (  
    [in] BOOL bActive  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `bActive`  
 'ndaki `true` Durumu etkin olarak belirtmek için bu değeri olarak ayarlayın; Aksi takdirde, bu değeri olarak ayarlayın `false` .  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
