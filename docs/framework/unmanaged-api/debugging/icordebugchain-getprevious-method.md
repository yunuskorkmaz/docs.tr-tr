---
title: ICorDebugChain::GetPrevious Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c5f98395ff8e77aa52a470f893ea5db02d73fdf3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchaingetprevious-method"></a><span data-ttu-id="4ae4a-102">ICorDebugChain::GetPrevious Metodu</span><span class="sxs-lookup"><span data-stu-id="4ae4a-102">ICorDebugChain::GetPrevious Method</span></span>
<span data-ttu-id="4ae4a-103">Çerçeve önceki zincirine iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="4ae4a-103">Gets the previous chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ae4a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ae4a-104">Syntax</span></span>  
  
```  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4ae4a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4ae4a-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="4ae4a-106">[out] Bu iş parçacığı için çerçeveleri önceki zincirine temsil eden Icordebugchain nesne adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4ae4a-106">[out] A pointer to the address of an ICorDebugChain object that represents the previous chain of frames for this thread.</span></span> <span data-ttu-id="4ae4a-107">Bu zincir ilk zinciri ise `ppChain` null.</span><span class="sxs-lookup"><span data-stu-id="4ae4a-107">If this chain is the first chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ae4a-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4ae4a-108">Requirements</span></span>  
 <span data-ttu-id="4ae4a-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ae4a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ae4a-110">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4ae4a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4ae4a-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ae4a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ae4a-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ae4a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
