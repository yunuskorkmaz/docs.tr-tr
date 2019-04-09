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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd16db8c009fe81f2674a8bf9c7ad3a2a4827777
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092857"
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="5c0d0-102">ICorDebugNativeFrame::CanSetIP Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c0d0-102">ICorDebugNativeFrame::CanSetIP Method</span></span>
<span data-ttu-id="5c0d0-103">Yönerge işaretçisi (IP) belirtilen uzaklık konuma yerel kodda ayarlamak güvenli olup olmadığını belirten bir HRESULT alır.</span><span class="sxs-lookup"><span data-stu-id="5c0d0-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c0d0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c0d0-104">Syntax</span></span>  
  
```  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c0d0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5c0d0-105">Parameters</span></span>  
 `nOffset`  
 <span data-ttu-id="5c0d0-106">[in] Yönerge işaretçisi için istenen ayar.</span><span class="sxs-lookup"><span data-stu-id="5c0d0-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c0d0-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c0d0-107">Remarks</span></span>  
 <span data-ttu-id="5c0d0-108">Kullanım `CanSetIP` yöntemi çağrılmadan önce [Icordebugnativeframe::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5c0d0-108">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="5c0d0-109">Varsa `CanSetIP` herhangi HRESULT döndürür S_OK dışında yine de çağırabilirsiniz `ICorDebugNativeFrame::SetIP`, ancak hata ayıklayıcı hata ayıklaması yapılan kod güvenli ve doğru yürütmeyi devam edeceğini garanti yoktur.</span><span class="sxs-lookup"><span data-stu-id="5c0d0-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c0d0-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c0d0-110">Requirements</span></span>  
 <span data-ttu-id="5c0d0-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c0d0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c0d0-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c0d0-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c0d0-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c0d0-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5c0d0-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="5c0d0-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5c0d0-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c0d0-115">See also</span></span>
