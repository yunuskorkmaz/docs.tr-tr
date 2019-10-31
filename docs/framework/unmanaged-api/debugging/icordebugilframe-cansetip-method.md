---
title: ICorDebugILFrame::CanSetIP Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::CanSetIP
helpviewer_keywords:
- CanSetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::CanSetIP method [.NET Framework debugging]
ms.assetid: 16caf02f-c71e-486c-90b0-f0e54357d8f0
topic_type:
- apiref
ms.openlocfilehash: 57d83d1f301cbfd43f8f553d9aef4beb3baf95f8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131078"
---
# <a name="icordebugilframecansetip-method"></a><span data-ttu-id="6e878-102">ICorDebugILFrame::CanSetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e878-102">ICorDebugILFrame::CanSetIP Method</span></span>
<span data-ttu-id="6e878-103">Microsoft ara dili (MSIL) kodunda belirtilen konum konumuna yönerge işaretçisini ayarlamak için güvenli olup olmadığını belirten bir HRESULT alır.</span><span class="sxs-lookup"><span data-stu-id="6e878-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer to the specified offset location in Microsoft Intermediate Language (MSIL) code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e878-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e878-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32   nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e878-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6e878-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="6e878-106">'ndaki Yönerge işaretçisi için istenen ayar.</span><span class="sxs-lookup"><span data-stu-id="6e878-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e878-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e878-107">Remarks</span></span>  
 <span data-ttu-id="6e878-108">[ICorDebugILFrame:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) metodunu çağırmadan önce `CanSetIP` metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="6e878-108">Use the `CanSetIP` method before calling the [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) method.</span></span> <span data-ttu-id="6e878-109">`CanSetIP` S_OK dışında bir HRESULT döndürürse, yine de `ICorDebugILFrame::SetIP`çağırabilirsiniz, ancak hata ayıklamanın hata ayıklamakta olan kodun güvenli ve doğru yürütülmesine devam edeceğini garanti vermez.</span><span class="sxs-lookup"><span data-stu-id="6e878-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugILFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e878-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e878-110">Requirements</span></span>  
 <span data-ttu-id="6e878-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e878-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e878-112">**Üst bilgi:** CorDebug. IDL, CorDebug, h</span><span class="sxs-lookup"><span data-stu-id="6e878-112">**Header:** CorDebug.idl, CorDebug,h</span></span>  
  
 <span data-ttu-id="6e878-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6e878-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e878-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e878-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
