---
title: ICorDebugChain::IsManaged Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugChain.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::IsManaged
helpviewer_keywords:
- ICorDebugChain::IsManaged method [.NET Framework debugging]
- IsManaged method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 17b389a0-1a4d-4e8a-8613-9bc1769930f9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a27ea95ca78f7db8f67ec2a13f02767e67619e97
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488064"
---
# <a name="icordebugchainismanaged-method"></a><span data-ttu-id="16dde-102">ICorDebugChain::IsManaged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="16dde-102">ICorDebugChain::IsManaged Method</span></span>
<span data-ttu-id="16dde-103">Bu zincir yönetilen kod çalışır durumda olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="16dde-103">Gets a value that indicates whether this chain is running managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16dde-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16dde-104">Syntax</span></span>  
  
```  
HRESULT IsManaged (  
    [out] BOOL               *pManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16dde-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="16dde-105">Parameters</span></span>  
 `pManaged`  
 <span data-ttu-id="16dde-106">[out] `true` Bu zincir yönetilen kod; çalışıyorsa Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="16dde-106">[out] `true` if this chain is running managed code; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16dde-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16dde-107">Requirements</span></span>  
 <span data-ttu-id="16dde-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16dde-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16dde-109">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16dde-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16dde-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16dde-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16dde-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16dde-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
