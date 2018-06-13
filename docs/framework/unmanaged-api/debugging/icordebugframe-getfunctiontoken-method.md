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
ms.openlocfilehash: 3bb4331b1c55cbda818866c5ff08f9bacd3ebae0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413991"
---
# <a name="icordebugframegetfunctiontoken-method"></a><span data-ttu-id="e4406-102">ICorDebugFrame::GetFunctionToken Metodu</span><span class="sxs-lookup"><span data-stu-id="e4406-102">ICorDebugFrame::GetFunctionToken Method</span></span>
<span data-ttu-id="e4406-103">Bu yığın çerçevesi ile ilişkili kodunu içerir işlevi için meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="e4406-103">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4406-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4406-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionToken (  
    [out] mdMethodDef        *pToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e4406-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e4406-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="e4406-106">[out] Bir işaretçi bir `mdMethodDef` işlevi için meta veriler başvuran belirteci.</span><span class="sxs-lookup"><span data-stu-id="e4406-106">[out] A pointer to an `mdMethodDef` token that references the metadata for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4406-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e4406-107">Requirements</span></span>  
 <span data-ttu-id="e4406-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4406-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4406-109">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4406-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4406-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4406-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4406-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4406-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
