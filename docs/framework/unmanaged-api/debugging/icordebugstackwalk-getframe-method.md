---
title: ICorDebugStackWalk::GetFrame Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStackWalk.GetFrame Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStackWalk::GetFrame
helpviewer_keywords:
- GetFrame method [.NET Framework debugging]
- ICorDebugStackWalk::GetFrame method [.NET Framework debugging]
ms.assetid: 4083b505-5b59-44fb-8c5d-129db6a96c10
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bef8cfc13727913e9311b5ce847190fe5544dc18
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugstackwalkgetframe-method"></a><span data-ttu-id="fac9b-102">ICorDebugStackWalk::GetFrame Metodu</span><span class="sxs-lookup"><span data-stu-id="fac9b-102">ICorDebugStackWalk::GetFrame Method</span></span>
<span data-ttu-id="fac9b-103">Geçerli çerçeve alır [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="fac9b-103">Gets the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fac9b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fac9b-104">Syntax</span></span>  
  
```  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fac9b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fac9b-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="fac9b-106">[in] Geçerli yığın çerçevesinde temsil eden oluşturulan çerçeve nesnesinin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fac9b-106">[in] A pointer to the address of the created frame object that represents the current frame in the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fac9b-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fac9b-107">Return Value</span></span>  
 <span data-ttu-id="fac9b-108">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="fac9b-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="fac9b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fac9b-109">HRESULT</span></span>|<span data-ttu-id="fac9b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fac9b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fac9b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="fac9b-111">S_OK</span></span>|<span data-ttu-id="fac9b-112">Çalışma zamanı, geçerli çerçeve başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="fac9b-112">The runtime successfully returned the current frame.</span></span>|  
|<span data-ttu-id="fac9b-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fac9b-113">E_FAIL</span></span>|<span data-ttu-id="fac9b-114">Geçerli çerçeve döndürülmedi.</span><span class="sxs-lookup"><span data-stu-id="fac9b-114">The current frame was not returned.</span></span>|  
|<span data-ttu-id="fac9b-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="fac9b-115">S_FALSE</span></span>|<span data-ttu-id="fac9b-116">Geçerli bir yerel yığın çerçevesi çerçevedir.</span><span class="sxs-lookup"><span data-stu-id="fac9b-116">The current frame is a native stack frame.</span></span>|  
|<span data-ttu-id="fac9b-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="fac9b-117">E_INVALIDARG</span></span>|<span data-ttu-id="fac9b-118">`pFrame`null şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="fac9b-118">`pFrame` is null.</span></span>|  
|<span data-ttu-id="fac9b-119">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="fac9b-119">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="fac9b-120">Çerçeve işaretçisi yığının sonuna zaten; Bu nedenle, hiçbir ek çerçeve erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="fac9b-120">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="fac9b-121">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="fac9b-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fac9b-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fac9b-122">Remarks</span></span>  
 <span data-ttu-id="fac9b-123">`ICorDebugStackWalk`yalnızca gerçek yığın çerçeveleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="fac9b-123">`ICorDebugStackWalk` returns only actual stack frames.</span></span> <span data-ttu-id="fac9b-124">Kullanım [Icordebugthread3::getactiveınternalframes](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) iç çerçeveler döndürülecek yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fac9b-124">Use the [ICorDebugThread3::GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return internal frames.</span></span> <span data-ttu-id="fac9b-125">İç çerçeveler yığına geçici verileri depolamak için çalışma zamanı tarafından gönderilen veri yapılarını dışında (.)</span><span class="sxs-lookup"><span data-stu-id="fac9b-125">(Internal frames are data structures pushed onto the stack by the runtime to store temporary data.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fac9b-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fac9b-126">Requirements</span></span>  
 <span data-ttu-id="fac9b-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fac9b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fac9b-128">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fac9b-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fac9b-129">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fac9b-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fac9b-130">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fac9b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fac9b-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fac9b-131">See Also</span></span>  
 [<span data-ttu-id="fac9b-132">Icordebugstackwalk arabirimi</span><span class="sxs-lookup"><span data-stu-id="fac9b-132">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 [<span data-ttu-id="fac9b-133">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fac9b-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="fac9b-134">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="fac9b-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
