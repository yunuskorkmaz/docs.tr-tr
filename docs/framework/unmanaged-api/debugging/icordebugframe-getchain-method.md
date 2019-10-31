---
title: ICorDebugFrame::GetChain Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetChain
helpviewer_keywords:
- ICorDebugFrame::GetChain method [.NET Framework debugging]
- GetChain method [.NET Framework debugging]
ms.assetid: e28e51d3-8f73-494f-bcd4-48bac239fbe1
topic_type:
- apiref
ms.openlocfilehash: 9677fd14f50cf93eac7eeaef784082d45e8884c7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137683"
---
# <a name="icordebugframegetchain-method"></a><span data-ttu-id="bb2f3-102">ICorDebugFrame::GetChain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb2f3-102">ICorDebugFrame::GetChain Method</span></span>
<span data-ttu-id="bb2f3-103">Bu çerçevenin parçası olduğu zincire yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="bb2f3-103">Gets a pointer to the chain this frame is a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb2f3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb2f3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetChain (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb2f3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bb2f3-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="bb2f3-106">dışı Bu çerçeveyi içeren zinciri temsil eden bir ıcordebugzincirleri nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bb2f3-106">[out] A pointer to the address of an ICorDebugChain object that represents the chain containing this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb2f3-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bb2f3-107">Requirements</span></span>  
 <span data-ttu-id="bb2f3-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb2f3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb2f3-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bb2f3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb2f3-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bb2f3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb2f3-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb2f3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
