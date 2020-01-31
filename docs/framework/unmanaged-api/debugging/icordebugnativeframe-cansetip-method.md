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
ms.openlocfilehash: d266ec7f82d7d4c7c66f137aafc1c8865d6f8889
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792800"
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="47d87-102">ICorDebugNativeFrame::CanSetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="47d87-102">ICorDebugNativeFrame::CanSetIP Method</span></span>
<span data-ttu-id="47d87-103">Yerel koddaki belirtilen konum konumuna yönerge işaretçisini (IP) ayarlamak için güvenli olup olmadığını belirten bir HRESULT alır.</span><span class="sxs-lookup"><span data-stu-id="47d87-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47d87-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47d87-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47d87-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="47d87-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="47d87-106">'ndaki Yönerge işaretçisi için istenen ayar.</span><span class="sxs-lookup"><span data-stu-id="47d87-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47d87-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="47d87-107">Remarks</span></span>  
 <span data-ttu-id="47d87-108">[ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md) metodunu çağırmadan önce `CanSetIP` yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="47d87-108">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="47d87-109">`CanSetIP` S_OK dışında herhangi bir HRESULT döndürürse `ICorDebugNativeFrame::SetIP`yine de çağırabilirsiniz, ancak hata ayıklayıcının hata ayıklamakta olan kodun güvenli ve doğru yürütülmesine devam edeceğini garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="47d87-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47d87-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="47d87-110">Requirements</span></span>  
 <span data-ttu-id="47d87-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47d87-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47d87-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="47d87-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47d87-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="47d87-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47d87-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47d87-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47d87-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47d87-115">See also</span></span>
