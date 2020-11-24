---
title: ICorDebugFrame::GetFunctionToken Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetFunctionToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunctionToken
helpviewer_keywords:
- ICorDebugFrame::GetFunctionToken method [.NET Framework debugging]
- GetFunctionToken method [.NET Framework debugging]
ms.assetid: a46925b3-3bf8-404f-9f30-a86ae41032c1
topic_type:
- apiref
ms.openlocfilehash: 3430c5062bd5633e1178226974b7358783192e51
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675990"
---
# <a name="icordebugframegetfunctiontoken-method"></a>ICorDebugFrame::GetFunctionToken Metodu

Bu yığın çerçevesiyle ilişkili kodu içeren işleve ait meta veri belirtecini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetFunctionToken (  
    [out] mdMethodDef        *pToken  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 `pToken`  
 dışı `mdMethodDef` İşlevin meta verilerine başvuran bir belirteç işaretçisi.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorDebug. IDL, CorDebug. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
