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
ms.openlocfilehash: cab25738c9f4727fe3970cc1db15c38e68b08de6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212925"
---
# <a name="icordebugframegetchain-method"></a><span data-ttu-id="ba2ee-102">ICorDebugFrame::GetChain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba2ee-102">ICorDebugFrame::GetChain Method</span></span>
<span data-ttu-id="ba2ee-103">Bu çerçevenin parçası olduğu zincire yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="ba2ee-103">Gets a pointer to the chain this frame is a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba2ee-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba2ee-104">Syntax</span></span>  
  
```cpp  
HRESULT GetChain (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba2ee-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba2ee-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="ba2ee-106">dışı Bu çerçeveyi içeren zinciri temsil eden bir ıcordebugzincirleri nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ba2ee-106">[out] A pointer to the address of an ICorDebugChain object that represents the chain containing this frame.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba2ee-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba2ee-107">Requirements</span></span>  
 <span data-ttu-id="ba2ee-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba2ee-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba2ee-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ba2ee-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba2ee-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ba2ee-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba2ee-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba2ee-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
