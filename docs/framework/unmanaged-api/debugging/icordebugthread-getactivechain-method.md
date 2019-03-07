---
title: ICorDebugThread::GetActiveChain Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveChain
helpviewer_keywords:
- ICorDebugThread::GetActiveChain method [.NET Framework debugging]
- GetActiveChain method [.NET Framework debugging]
ms.assetid: f50de1f7-40ef-4949-b542-1d9a61f7bfef
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b05f5a3f29c7b72ed83c1456175f68ef9b986e3e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57483322"
---
# <a name="icordebugthreadgetactivechain-method"></a><span data-ttu-id="34daa-102">ICorDebugThread::GetActiveChain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34daa-102">ICorDebugThread::GetActiveChain Method</span></span>
<span data-ttu-id="34daa-103">Bir arabirim işaretçisini bu Icordebugthread nesne üzerinde etkin (en son) yığın zincirinin alır.</span><span class="sxs-lookup"><span data-stu-id="34daa-103">Gets an interface pointer to the active (most recent) stack chain on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34daa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34daa-104">Syntax</span></span>  
  
```  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34daa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="34daa-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="34daa-106">[out] Yığın zincirinin temsil eden bir Icordebugchain nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="34daa-106">[out] A pointer to the address of an ICorDebugChain object that represents the stack chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34daa-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34daa-107">Remarks</span></span>  
 <span data-ttu-id="34daa-108">`ppChain` Parametredir hiçbir yığın zincirinin şu anda etkin değilse null.</span><span class="sxs-lookup"><span data-stu-id="34daa-108">The `ppChain` parameter is null if no stack chain is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34daa-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="34daa-109">Requirements</span></span>  
 <span data-ttu-id="34daa-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34daa-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34daa-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="34daa-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34daa-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34daa-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34daa-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34daa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
