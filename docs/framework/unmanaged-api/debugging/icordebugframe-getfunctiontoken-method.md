---
description: ': ICorDebugFrame:: GetFunctionToken metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: c64bb8d59c8de03c3d8c667384ffe4118c996d8e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692946"
---
# <a name="icordebugframegetfunctiontoken-method"></a><span data-ttu-id="a7d21-103">ICorDebugFrame::GetFunctionToken Metodu</span><span class="sxs-lookup"><span data-stu-id="a7d21-103">ICorDebugFrame::GetFunctionToken Method</span></span>

<span data-ttu-id="a7d21-104">Bu yığın çerçevesiyle ilişkili kodu içeren işleve ait meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="a7d21-104">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7d21-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a7d21-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionToken (  
    [out] mdMethodDef        *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7d21-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7d21-106">Parameters</span></span>  

 `pToken`  
 <span data-ttu-id="a7d21-107">dışı `mdMethodDef` İşlevin meta verilerine başvuran bir belirteç işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="a7d21-107">[out] A pointer to an `mdMethodDef` token that references the metadata for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7d21-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7d21-108">Requirements</span></span>  

 <span data-ttu-id="a7d21-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7d21-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7d21-110">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a7d21-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7d21-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a7d21-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7d21-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7d21-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
