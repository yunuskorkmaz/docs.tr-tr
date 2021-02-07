---
description: ': ICorDebugFrame:: GetFunction metodu hakkında daha fazla bilgi edinin'
title: ICorDebugFrame::GetFunction Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetFunction method [.NET Framework debugging]
ms.assetid: 879d2311-0ff1-4616-a8b3-959ea5868b2e
topic_type:
- apiref
ms.openlocfilehash: 0309a066f686e55d086de1cbb040eea58e031df3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692998"
---
# <a name="icordebugframegetfunction-method"></a><span data-ttu-id="07e14-103">ICorDebugFrame::GetFunction Metodu</span><span class="sxs-lookup"><span data-stu-id="07e14-103">ICorDebugFrame::GetFunction Method</span></span>

<span data-ttu-id="07e14-104">Bu yığın çerçevesiyle ilişkili kodu içeren işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="07e14-104">Gets the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07e14-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07e14-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07e14-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="07e14-106">Parameters</span></span>  

 `ppFunction`  
 <span data-ttu-id="07e14-107">dışı Bu yığın çerçevesiyle ilişkili kodu içeren işlevi temsil eden bir ICorDebugFunction nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="07e14-107">[out] A pointer to the address of an ICorDebugFunction object that represents the function containing the code associated with this stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07e14-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07e14-108">Remarks</span></span>  

 <span data-ttu-id="07e14-109">`GetFunction`Çerçeve belirli bir işlevle ilişkilendirilmediği takdirde yöntem başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="07e14-109">The `GetFunction` method may fail if the frame is not associated with any particular function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07e14-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07e14-110">Requirements</span></span>  

 <span data-ttu-id="07e14-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07e14-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07e14-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="07e14-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07e14-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="07e14-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07e14-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07e14-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
