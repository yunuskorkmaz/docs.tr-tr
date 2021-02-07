---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugAssembly2:: IsFullyTrusted yöntemi'
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
ms.openlocfilehash: bc1c4d9a4fa84bac3469aafe8aaa061473e50413
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754114"
---
# <a name="icordebugassembly2isfullytrusted-method"></a><span data-ttu-id="9a1e2-103">ICorDebugAssembly2::IsFullyTrusted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9a1e2-103">ICorDebugAssembly2::IsFullyTrusted Method</span></span>

<span data-ttu-id="9a1e2-104">Derlemeye çalışma zamanı güvenlik sistemi tarafından tam güven verilip verilmediğini gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="9a1e2-104">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a1e2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a1e2-105">Syntax</span></span>  
  
```cpp  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a1e2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9a1e2-106">Parameters</span></span>  

 `pbFullyTrusted`  
 <span data-ttu-id="9a1e2-107">[out] `true` derlemeye çalışma zamanı güvenlik sistemi tarafından tam güven verildiyse; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="9a1e2-107">[out] `true` if the assembly has been granted full trust by the runtime security system; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a1e2-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a1e2-108">Remarks</span></span>  

 <span data-ttu-id="9a1e2-109">Bu yöntem, derleme için güvenlik ilkesi henüz çözümlenmemişse, yani derlemede hiçbir kod henüz çalıştırılmadıysa, bir HRESULT CORDBG_E_NOTREADY döndürür.</span><span class="sxs-lookup"><span data-stu-id="9a1e2-109">This method returns an HRESULT of CORDBG_E_NOTREADY if the security policy for the assembly has not yet been resolved, that is, if no code in the assembly has been run yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a1e2-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a1e2-110">Requirements</span></span>  

 <span data-ttu-id="9a1e2-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a1e2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a1e2-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9a1e2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a1e2-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9a1e2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a1e2-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a1e2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
