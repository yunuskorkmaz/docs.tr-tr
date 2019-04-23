---
title: ICorDebugStackWalk::GetFrame Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetFrame Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetFrame
helpviewer_keywords:
- GetFrame method [.NET Framework debugging]
- ICorDebugStackWalk::GetFrame method [.NET Framework debugging]
ms.assetid: 4083b505-5b59-44fb-8c5d-129db6a96c10
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 253a25fdfc1f00adbc20388660caf6c227030a1b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111247"
---
# <a name="icordebugstackwalkgetframe-method"></a><span data-ttu-id="0cf64-102">ICorDebugStackWalk::GetFrame Metodu</span><span class="sxs-lookup"><span data-stu-id="0cf64-102">ICorDebugStackWalk::GetFrame Method</span></span>
<span data-ttu-id="0cf64-103">Geçerli çerçevenin alır [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="0cf64-103">Gets the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cf64-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0cf64-104">Syntax</span></span>  
  
```  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0cf64-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0cf64-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="0cf64-106">[in] Geçerli yığındaki çerçeveye temsil eden oluşturulmuş bir çerçeve nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0cf64-106">[in] A pointer to the address of the created frame object that represents the current frame in the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0cf64-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0cf64-107">Return Value</span></span>  
 <span data-ttu-id="0cf64-108">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="0cf64-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0cf64-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0cf64-109">HRESULT</span></span>|<span data-ttu-id="0cf64-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0cf64-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0cf64-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0cf64-111">S_OK</span></span>|<span data-ttu-id="0cf64-112">Çalışma zamanı, geçerli çerçeve başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0cf64-112">The runtime successfully returned the current frame.</span></span>|  
|<span data-ttu-id="0cf64-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0cf64-113">E_FAIL</span></span>|<span data-ttu-id="0cf64-114">Geçerli çerçevenin döndürülmedi.</span><span class="sxs-lookup"><span data-stu-id="0cf64-114">The current frame was not returned.</span></span>|  
|<span data-ttu-id="0cf64-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="0cf64-115">S_FALSE</span></span>|<span data-ttu-id="0cf64-116">Geçerli bir yerel yığın çerçevesi çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="0cf64-116">The current frame is a native stack frame.</span></span>|  
|<span data-ttu-id="0cf64-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0cf64-117">E_INVALIDARG</span></span>|<span data-ttu-id="0cf64-118">`pFrame` NULL olur.</span><span class="sxs-lookup"><span data-stu-id="0cf64-118">`pFrame` is null.</span></span>|  
|<span data-ttu-id="0cf64-119">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="0cf64-119">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="0cf64-120">Çerçeve işaretçisini yığının sonuna bulunur. Bu nedenle, hiçbir ek çerçeveler erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="0cf64-120">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="0cf64-121">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="0cf64-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cf64-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0cf64-122">Remarks</span></span>  
 <span data-ttu-id="0cf64-123">`ICorDebugStackWalk` yalnızca gerçek bir yığın çerçevesine döndürür.</span><span class="sxs-lookup"><span data-stu-id="0cf64-123">`ICorDebugStackWalk` returns only actual stack frames.</span></span> <span data-ttu-id="0cf64-124">Kullanım [Icordebugthread3::getactiveınternalframes](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) iç çerçeveler döndürmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0cf64-124">Use the [ICorDebugThread3::GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return internal frames.</span></span> <span data-ttu-id="0cf64-125">(İç çerçeveler yığınına geçici verileri depolamak için çalışma zamanı tarafından gönderilen veri yapılarını içindir.)</span><span class="sxs-lookup"><span data-stu-id="0cf64-125">(Internal frames are data structures pushed onto the stack by the runtime to store temporary data.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cf64-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0cf64-126">Requirements</span></span>  
 <span data-ttu-id="0cf64-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cf64-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cf64-128">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0cf64-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0cf64-129">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0cf64-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0cf64-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cf64-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cf64-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cf64-131">See also</span></span>

- [<span data-ttu-id="0cf64-132">ICorDebugStackWalk Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0cf64-132">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [<span data-ttu-id="0cf64-133">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0cf64-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="0cf64-134">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="0cf64-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
