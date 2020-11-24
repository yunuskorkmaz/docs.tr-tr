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
ms.openlocfilehash: d605ac36c17a815bf546819e331830f51142cfcd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690427"
---
# <a name="icordebugframegetchain-method"></a><span data-ttu-id="baa4c-102">ICorDebugFrame::GetChain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="baa4c-102">ICorDebugFrame::GetChain Method</span></span>

<span data-ttu-id="baa4c-103">Bu çerçevenin parçası olduğu zincire yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="baa4c-103">Gets a pointer to the chain this frame is a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baa4c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="baa4c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetChain (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="baa4c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="baa4c-105">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="baa4c-106">dışı Bu çerçeveyi içeren zinciri temsil eden bir ıcordebugzincirleri nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="baa4c-106">[out] A pointer to the address of an ICorDebugChain object that represents the chain containing this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="baa4c-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="baa4c-107">Requirements</span></span>  

 <span data-ttu-id="baa4c-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="baa4c-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="baa4c-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="baa4c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="baa4c-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="baa4c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="baa4c-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="baa4c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
