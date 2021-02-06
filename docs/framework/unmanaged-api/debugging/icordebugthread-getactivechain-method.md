---
description: ': ICorDebugThread:: Getactivezincirde yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: d9aff80801fa72a227a84b3b5216e3ffa72b0e24
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659289"
---
# <a name="icordebugthreadgetactivechain-method"></a><span data-ttu-id="79963-103">ICorDebugThread::GetActiveChain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="79963-103">ICorDebugThread::GetActiveChain Method</span></span>

<span data-ttu-id="79963-104">Bu ICorDebugThread nesnesindeki etkin (en son) yığın zincirine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="79963-104">Gets an interface pointer to the active (most recent) stack chain on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79963-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79963-105">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79963-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="79963-106">Parameters</span></span>  

 `ppChain`  
 <span data-ttu-id="79963-107">dışı Yığın zincirini temsil eden bir ıcordebugzincirleri nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="79963-107">[out] A pointer to the address of an ICorDebugChain object that represents the stack chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79963-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="79963-108">Remarks</span></span>  

 <span data-ttu-id="79963-109">`ppChain`Şu anda etkin bir yığın zinciri yoksa parametre null.</span><span class="sxs-lookup"><span data-stu-id="79963-109">The `ppChain` parameter is null if no stack chain is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79963-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79963-110">Requirements</span></span>  

 <span data-ttu-id="79963-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79963-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79963-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="79963-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79963-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="79963-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79963-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79963-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
