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
ms.openlocfilehash: 55036fcdbd186f91c0e94fb05f3023cf614751f7
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894246"
---
# <a name="icordebugchainismanaged-method"></a><span data-ttu-id="1ffbd-102">ICorDebugChain::IsManaged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ffbd-102">ICorDebugChain::IsManaged Method</span></span>
<span data-ttu-id="1ffbd-103">Bu zincirin yönetilen kodu çalıştırıp çalıştırmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="1ffbd-103">Gets a value that indicates whether this chain is running managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ffbd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ffbd-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL               *pManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ffbd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1ffbd-105">Parameters</span></span>  
 `pManaged`  
 <span data-ttu-id="1ffbd-106">dışı `true` bu zincir yönetilen kod çalıştırıyorsa; Aksi takdirde `false`,.</span><span class="sxs-lookup"><span data-stu-id="1ffbd-106">[out] `true` if this chain is running managed code; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ffbd-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ffbd-107">Requirements</span></span>  
 <span data-ttu-id="1ffbd-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ffbd-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ffbd-109">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1ffbd-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ffbd-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1ffbd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ffbd-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ffbd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
