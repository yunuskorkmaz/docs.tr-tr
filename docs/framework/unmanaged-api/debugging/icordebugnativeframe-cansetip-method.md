---
title: ICorDebugNativeFrame::CanSetIP Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::CanSetIP
helpviewer_keywords:
- ICorDebugNativeFrame::CanSetIP method [.NET Framework debugging]
- CanSetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 13258ac6-f4e4-4f66-8fc3-f1244417a3c3
topic_type:
- apiref
ms.openlocfilehash: b3758ac1a84092b8bf2678f9cc2c19c9d9961690
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137320"
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="2e7e9-102">ICorDebugNativeFrame::CanSetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e7e9-102">ICorDebugNativeFrame::CanSetIP Method</span></span>
<span data-ttu-id="2e7e9-103">Yerel koddaki belirtilen konum konumuna yönerge işaretçisini (IP) ayarlamak için güvenli olup olmadığını belirten bir HRESULT alır.</span><span class="sxs-lookup"><span data-stu-id="2e7e9-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e7e9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e7e9-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e7e9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2e7e9-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="2e7e9-106">'ndaki Yönerge işaretçisi için istenen ayar.</span><span class="sxs-lookup"><span data-stu-id="2e7e9-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e7e9-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2e7e9-107">Remarks</span></span>  
 <span data-ttu-id="2e7e9-108">[ICorDebugNativeFrame:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) metodunu çağırmadan önce `CanSetIP` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2e7e9-108">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="2e7e9-109">`CanSetIP` S_OK dışında bir HRESULT döndürürse, yine de `ICorDebugNativeFrame::SetIP`çağırabilirsiniz, ancak hata ayıklamanın hata ayıklamakta olan kodun güvenli ve doğru yürütülmesine devam edeceğini garanti vermez.</span><span class="sxs-lookup"><span data-stu-id="2e7e9-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e7e9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e7e9-110">Requirements</span></span>  
 <span data-ttu-id="2e7e9-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e7e9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e7e9-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2e7e9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e7e9-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2e7e9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e7e9-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e7e9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e7e9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e7e9-115">See also</span></span>
