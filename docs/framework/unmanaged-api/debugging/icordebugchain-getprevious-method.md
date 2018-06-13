---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c0545440ed63ba914229249080ec9f6be8eb2b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402259"
---
# <a name="icordebugchaingetprevious-method"></a><span data-ttu-id="c69bb-102">ICorDebugChain::GetPrevious Metodu</span><span class="sxs-lookup"><span data-stu-id="c69bb-102">ICorDebugChain::GetPrevious Method</span></span>
<span data-ttu-id="c69bb-103">Çerçeve önceki zincirine iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="c69bb-103">Gets the previous chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c69bb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c69bb-104">Syntax</span></span>  
  
```  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c69bb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c69bb-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="c69bb-106">[out] Bu iş parçacığı için çerçeveleri önceki zincirine temsil eden Icordebugchain nesne adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c69bb-106">[out] A pointer to the address of an ICorDebugChain object that represents the previous chain of frames for this thread.</span></span> <span data-ttu-id="c69bb-107">Bu zincir ilk zinciri ise `ppChain` null.</span><span class="sxs-lookup"><span data-stu-id="c69bb-107">If this chain is the first chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c69bb-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c69bb-108">Requirements</span></span>  
 <span data-ttu-id="c69bb-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c69bb-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c69bb-110">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c69bb-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c69bb-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c69bb-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c69bb-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c69bb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
