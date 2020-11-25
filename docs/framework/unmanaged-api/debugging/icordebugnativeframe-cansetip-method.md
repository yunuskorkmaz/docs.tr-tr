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
ms.openlocfilehash: 194065e53d550c9bbd0486de54462309a4d9ffa1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695757"
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="7e813-102">ICorDebugNativeFrame::CanSetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7e813-102">ICorDebugNativeFrame::CanSetIP Method</span></span>

<span data-ttu-id="7e813-103">Yerel koddaki belirtilen konum konumuna yönerge işaretçisini (IP) ayarlamak için güvenli olup olmadığını belirten bir HRESULT alır.</span><span class="sxs-lookup"><span data-stu-id="7e813-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e813-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7e813-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e813-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7e813-105">Parameters</span></span>  

 `nOffset`  
 <span data-ttu-id="7e813-106">'ndaki Yönerge işaretçisi için istenen ayar.</span><span class="sxs-lookup"><span data-stu-id="7e813-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e813-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e813-107">Remarks</span></span>  

 <span data-ttu-id="7e813-108">`CanSetIP` [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md) metodunu çağırmadan önce yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7e813-108">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="7e813-109">`CanSetIP`S_OK dışında BIR HRESULT döndürürse, yine de çağırabilirsiniz `ICorDebugNativeFrame::SetIP` , ancak hata ayıklayıcının hata ayıklamakta olan kodun güvenli ve doğru yürütülmesine devam edeceğini garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="7e813-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e813-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7e813-110">Requirements</span></span>  

 <span data-ttu-id="7e813-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e813-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e813-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7e813-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e813-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7e813-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e813-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e813-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e813-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e813-115">See also</span></span>
