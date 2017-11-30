---
title: ICorDebugChain::GetPrevious Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.GetPrevious
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::GetPrevious
helpviewer_keywords:
- ICorDebugChain::GetPrevious method [.NET Framework debugging]
- GetPrevious method [.NET Framework debugging]
ms.assetid: 58eed4c8-d80c-4c6a-a875-967a90dd926c
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1203aa4a6e35574c1d026ddc05cac810fed5b78b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchaingetprevious-method"></a><span data-ttu-id="fa98b-102">ICorDebugChain::GetPrevious Metodu</span><span class="sxs-lookup"><span data-stu-id="fa98b-102">ICorDebugChain::GetPrevious Method</span></span>
<span data-ttu-id="fa98b-103">Çerçeve önceki zincirine iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="fa98b-103">Gets the previous chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa98b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa98b-104">Syntax</span></span>  
  
```  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fa98b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fa98b-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="fa98b-106">[out] Bu iş parçacığı için çerçeveleri önceki zincirine temsil eden Icordebugchain nesne adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fa98b-106">[out] A pointer to the address of an ICorDebugChain object that represents the previous chain of frames for this thread.</span></span> <span data-ttu-id="fa98b-107">Bu zincir ilk zinciri ise `ppChain` null.</span><span class="sxs-lookup"><span data-stu-id="fa98b-107">If this chain is the first chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa98b-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fa98b-108">Requirements</span></span>  
 <span data-ttu-id="fa98b-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa98b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa98b-110">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa98b-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa98b-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa98b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa98b-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa98b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
