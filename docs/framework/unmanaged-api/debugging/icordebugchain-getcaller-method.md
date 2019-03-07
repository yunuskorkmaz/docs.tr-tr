---
title: ICorDebugChain::GetCaller Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCaller
helpviewer_keywords:
- ICorDebugChain::GetCaller method [.NET Framework debugging]
- GetCaller method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: d0b8ab4b-d7d2-4fa0-945f-3d2b87e7e991
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd65de77209f5a981c0a4c291f8573a61cf6335b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489559"
---
# <a name="icordebugchaingetcaller-method"></a><span data-ttu-id="24a98-102">ICorDebugChain::GetCaller Metodu</span><span class="sxs-lookup"><span data-stu-id="24a98-102">ICorDebugChain::GetCaller Method</span></span>
<span data-ttu-id="24a98-103">Bu zincir denir zinciri alır.</span><span class="sxs-lookup"><span data-stu-id="24a98-103">Gets the chain that called this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24a98-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24a98-104">Syntax</span></span>  
  
```  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24a98-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="24a98-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="24a98-106">[out] Çağrı zincirini temsil eden bir Icordebugchain nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="24a98-106">[out] A pointer to the address of an ICorDebugChain object that represents the calling chain.</span></span>  
  
 <span data-ttu-id="24a98-107">(Bu zincir veya hata ayıklayıcı çağrı yığınını başlatılmış durumda olurdu gibi) Bu zincir kendiliğinden çağrıldı, `ppChain` null olacaktır.</span><span class="sxs-lookup"><span data-stu-id="24a98-107">If this chain was spontaneously called (as would be the case if this chain or the debugger initialized the call stack), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24a98-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="24a98-108">Remarks</span></span>  
 <span data-ttu-id="24a98-109">Çağrı zincirinin çağrı iş parçacıkları arasında sıralanmış farklı bir iş parçacığı üzerinde olabilir.</span><span class="sxs-lookup"><span data-stu-id="24a98-109">The calling chain may be on a different thread, if the call was marshaled across threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24a98-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="24a98-110">Requirements</span></span>  
 <span data-ttu-id="24a98-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24a98-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24a98-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="24a98-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24a98-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24a98-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24a98-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24a98-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
