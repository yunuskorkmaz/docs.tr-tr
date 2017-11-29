---
title: ICorDebugChain::GetCallee Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.GetCallee
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ed2bf8d8e91799fd0b01012d5d6e212d26a526be
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchaingetcallee-method"></a><span data-ttu-id="17d94-102">ICorDebugChain::GetCallee Metodu</span><span class="sxs-lookup"><span data-stu-id="17d94-102">ICorDebugChain::GetCallee Method</span></span>
<span data-ttu-id="17d94-103">Bu zincir tarafından çağrıldı zinciri alır.</span><span class="sxs-lookup"><span data-stu-id="17d94-103">Gets the chain that was called by this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17d94-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="17d94-104">Syntax</span></span>  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="17d94-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="17d94-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="17d94-106">[out] Bir işaretçi adresine Icordebugchain nesnenin çağrılan zinciri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="17d94-106">[out] A pointer to the address of an ICorDebugChain object that represents the called chain.</span></span> <span data-ttu-id="17d94-107">(Diğer bir deyişle, bu zincirini geri dönmek çağrılan bir zincir için bekliyor değil ise) bu zincirini şu anda yürütülmekte, `ppChain` null olur.</span><span class="sxs-lookup"><span data-stu-id="17d94-107">If this chain is currently executing (that is, if this chain is not waiting for a called chain to return), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17d94-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="17d94-108">Remarks</span></span>  
 <span data-ttu-id="17d94-109">Bu zincir çağrılan zinciri yürütme sürdürür önce dönmek bekler.</span><span class="sxs-lookup"><span data-stu-id="17d94-109">This chain will wait for the called chain to return before it resumes execution.</span></span> <span data-ttu-id="17d94-110">Çağrılan zinciri, başka bir iş parçacığında iş parçacıkları arası sıralanmış çağrıları durumunda olabilir.</span><span class="sxs-lookup"><span data-stu-id="17d94-110">The called chain may be on another thread in the case of cross-thread marshaled calls.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17d94-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="17d94-111">Requirements</span></span>  
 <span data-ttu-id="17d94-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17d94-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17d94-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17d94-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17d94-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17d94-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17d94-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17d94-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
