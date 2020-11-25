---
title: ICorDebugAssembly2::IsFullyTrusted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly2.IsFullyTrusted
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly2::IsFullyTrusted
helpviewer_keywords:
- ICorDebugAssembly2::IsFullyTrusted method [.NET Framework debugging]
- IsFullyTrusted method [.NET Framework debugging]
ms.assetid: 26cbd27d-12bf-444a-8197-ccd14d37dda3
topic_type:
- apiref
ms.openlocfilehash: 8a2a6be0db76f5ee2c7fa67c2038e0a5c845bd0f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719716"
---
# <a name="icordebugassembly2isfullytrusted-method"></a><span data-ttu-id="658db-102">ICorDebugAssembly2::IsFullyTrusted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="658db-102">ICorDebugAssembly2::IsFullyTrusted Method</span></span>

<span data-ttu-id="658db-103">Derlemeye çalışma zamanı güvenlik sistemi tarafından tam güven verilip verilmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="658db-103">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="658db-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="658db-104">Syntax</span></span>  
  
```cpp  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="658db-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="658db-105">Parameters</span></span>  

 `pbFullyTrusted`  
 <span data-ttu-id="658db-106">[out] `true` derlemeye çalışma zamanı güvenlik sistemi tarafından tam güven verildiyse; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="658db-106">[out] `true` if the assembly has been granted full trust by the runtime security system; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="658db-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="658db-107">Remarks</span></span>  

 <span data-ttu-id="658db-108">Bu yöntem, derleme için güvenlik ilkesi henüz çözümlenmemişse, yani derlemede hiçbir kod henüz çalıştırılmadıysa, bir HRESULT CORDBG_E_NOTREADY döndürür.</span><span class="sxs-lookup"><span data-stu-id="658db-108">This method returns an HRESULT of CORDBG_E_NOTREADY if the security policy for the assembly has not yet been resolved, that is, if no code in the assembly has been run yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="658db-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="658db-109">Requirements</span></span>  

 <span data-ttu-id="658db-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="658db-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="658db-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="658db-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="658db-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="658db-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="658db-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="658db-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
