---
description: ': Icordebugzincirine:: GetPrevious yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugChain::GetPrevious Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetPrevious
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetPrevious
helpviewer_keywords:
- ICorDebugChain::GetPrevious method [.NET Framework debugging]
- GetPrevious method [.NET Framework debugging]
ms.assetid: 58eed4c8-d80c-4c6a-a875-967a90dd926c
topic_type:
- apiref
ms.openlocfilehash: 169c46afd545835e6da87686a8e74ecd12173904
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661291"
---
# <a name="icordebugchaingetprevious-method"></a><span data-ttu-id="69b68-103">ICorDebugChain::GetPrevious Metodu</span><span class="sxs-lookup"><span data-stu-id="69b68-103">ICorDebugChain::GetPrevious Method</span></span>

<span data-ttu-id="69b68-104">İş parçacığı için önceki çerçeve zincirini alır.</span><span class="sxs-lookup"><span data-stu-id="69b68-104">Gets the previous chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69b68-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69b68-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69b68-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="69b68-106">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="69b68-107">dışı Bu iş parçacığı için önceki çerçeve zincirini temsil eden bir ıcordebugzincirleri nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="69b68-107">[out] A pointer to the address of an ICorDebugChain object that represents the previous chain of frames for this thread.</span></span> <span data-ttu-id="69b68-108">Bu zincir ilk zincirdir, `ppChain` null olur.</span><span class="sxs-lookup"><span data-stu-id="69b68-108">If this chain is the first chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69b68-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="69b68-109">Requirements</span></span>  

 <span data-ttu-id="69b68-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69b68-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69b68-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="69b68-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69b68-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="69b68-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69b68-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69b68-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
