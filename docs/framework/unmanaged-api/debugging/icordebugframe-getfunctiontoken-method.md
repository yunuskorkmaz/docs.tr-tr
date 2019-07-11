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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f50e5fcee3705e05aeed820cf736613c12b00e50
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754865"
---
# <a name="icordebugframegetfunctiontoken-method"></a><span data-ttu-id="45bcf-102">ICorDebugFrame::GetFunctionToken Metodu</span><span class="sxs-lookup"><span data-stu-id="45bcf-102">ICorDebugFrame::GetFunctionToken Method</span></span>
<span data-ttu-id="45bcf-103">Bu yığın çerçevesiyle ilgili kodu içeren işlevi için meta veri belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="45bcf-103">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45bcf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="45bcf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionToken (  
    [out] mdMethodDef        *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45bcf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="45bcf-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="45bcf-106">[out] Bir işaretçi bir `mdMethodDef` işlevi için meta veriler başvuran belirteci.</span><span class="sxs-lookup"><span data-stu-id="45bcf-106">[out] A pointer to an `mdMethodDef` token that references the metadata for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45bcf-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="45bcf-107">Requirements</span></span>  
 <span data-ttu-id="45bcf-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45bcf-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45bcf-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45bcf-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45bcf-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45bcf-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45bcf-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45bcf-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
