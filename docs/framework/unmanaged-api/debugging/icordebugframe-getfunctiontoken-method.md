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
ms.openlocfilehash: e7821022e6966dbdea90d57b6899f09b2ed1964e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090523"
---
# <a name="icordebugframegetfunctiontoken-method"></a><span data-ttu-id="08e65-102">ICorDebugFrame::GetFunctionToken Metodu</span><span class="sxs-lookup"><span data-stu-id="08e65-102">ICorDebugFrame::GetFunctionToken Method</span></span>
<span data-ttu-id="08e65-103">Bu yığın çerçevesiyle ilişkili kodu içeren işleve ait meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="08e65-103">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08e65-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08e65-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionToken (  
    [out] mdMethodDef        *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08e65-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="08e65-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="08e65-106">dışı İşlevin meta verilerine başvuran `mdMethodDef` belirtece yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="08e65-106">[out] A pointer to an `mdMethodDef` token that references the metadata for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08e65-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08e65-107">Requirements</span></span>  
 <span data-ttu-id="08e65-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08e65-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08e65-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="08e65-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08e65-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="08e65-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08e65-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08e65-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
