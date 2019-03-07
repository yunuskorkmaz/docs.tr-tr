---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a48396f8ef668cfe7755b2718180317b465793b6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475296"
---
# <a name="icordebugframegetfunction-method"></a><span data-ttu-id="3d208-102">ICorDebugFrame::GetFunction Metodu</span><span class="sxs-lookup"><span data-stu-id="3d208-102">ICorDebugFrame::GetFunction Method</span></span>
<span data-ttu-id="3d208-103">Bu yığın çerçevesiyle ilgili kodu içeren bir işlevi alır.</span><span class="sxs-lookup"><span data-stu-id="3d208-103">Gets the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d208-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d208-104">Syntax</span></span>  
  
```  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d208-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3d208-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="3d208-106">[out] Bu yığın çerçevesiyle ilgili kodu içeren bir işlevi temsil eden bir ICorDebugFunction nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3d208-106">[out] A pointer to the address of an ICorDebugFunction object that represents the function containing the code associated with this stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d208-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d208-107">Remarks</span></span>  
 <span data-ttu-id="3d208-108">`GetFunction` Yöntemi çerçeve herhangi belirli bir işlev ile ilişkili değilse başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="3d208-108">The `GetFunction` method may fail if the frame is not associated with any particular function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d208-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d208-109">Requirements</span></span>  
 <span data-ttu-id="3d208-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d208-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d208-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d208-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d208-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d208-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d208-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d208-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
