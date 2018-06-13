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
ms.openlocfilehash: 548a8a7743c02be5734b677010627f847c5bc4b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421993"
---
# <a name="icordebugstackwalkgetframe-method"></a><span data-ttu-id="277b3-102">ICorDebugStackWalk::GetFrame Metodu</span><span class="sxs-lookup"><span data-stu-id="277b3-102">ICorDebugStackWalk::GetFrame Method</span></span>
<span data-ttu-id="277b3-103">Geçerli çerçeve alır [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="277b3-103">Gets the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="277b3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="277b3-104">Syntax</span></span>  
  
```  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="277b3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="277b3-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="277b3-106">[in] Geçerli yığın çerçevesinde temsil eden oluşturulan çerçeve nesnesinin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="277b3-106">[in] A pointer to the address of the created frame object that represents the current frame in the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="277b3-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="277b3-107">Return Value</span></span>  
 <span data-ttu-id="277b3-108">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="277b3-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="277b3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="277b3-109">HRESULT</span></span>|<span data-ttu-id="277b3-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="277b3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="277b3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="277b3-111">S_OK</span></span>|<span data-ttu-id="277b3-112">Çalışma zamanı, geçerli çerçeve başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="277b3-112">The runtime successfully returned the current frame.</span></span>|  
|<span data-ttu-id="277b3-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="277b3-113">E_FAIL</span></span>|<span data-ttu-id="277b3-114">Geçerli çerçeve döndürülmedi.</span><span class="sxs-lookup"><span data-stu-id="277b3-114">The current frame was not returned.</span></span>|  
|<span data-ttu-id="277b3-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="277b3-115">S_FALSE</span></span>|<span data-ttu-id="277b3-116">Geçerli bir yerel yığın çerçevesi çerçevedir.</span><span class="sxs-lookup"><span data-stu-id="277b3-116">The current frame is a native stack frame.</span></span>|  
|<span data-ttu-id="277b3-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="277b3-117">E_INVALIDARG</span></span>|<span data-ttu-id="277b3-118">`pFrame` null şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="277b3-118">`pFrame` is null.</span></span>|  
|<span data-ttu-id="277b3-119">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="277b3-119">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="277b3-120">Çerçeve işaretçisi yığının sonuna zaten; Bu nedenle, hiçbir ek çerçeve erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="277b3-120">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="277b3-121">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="277b3-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="277b3-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="277b3-122">Remarks</span></span>  
 <span data-ttu-id="277b3-123">`ICorDebugStackWalk` yalnızca gerçek yığın çerçeveleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="277b3-123">`ICorDebugStackWalk` returns only actual stack frames.</span></span> <span data-ttu-id="277b3-124">Kullanım [Icordebugthread3::getactiveınternalframes](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) iç çerçeveler döndürülecek yöntemi.</span><span class="sxs-lookup"><span data-stu-id="277b3-124">Use the [ICorDebugThread3::GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return internal frames.</span></span> <span data-ttu-id="277b3-125">İç çerçeveler yığına geçici verileri depolamak için çalışma zamanı tarafından gönderilen veri yapılarını dışında (.)</span><span class="sxs-lookup"><span data-stu-id="277b3-125">(Internal frames are data structures pushed onto the stack by the runtime to store temporary data.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="277b3-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="277b3-126">Requirements</span></span>  
 <span data-ttu-id="277b3-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="277b3-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="277b3-128">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="277b3-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="277b3-129">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="277b3-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="277b3-130">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="277b3-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="277b3-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="277b3-131">See Also</span></span>  
 [<span data-ttu-id="277b3-132">ICorDebugStackWalk Arabirimi</span><span class="sxs-lookup"><span data-stu-id="277b3-132">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 [<span data-ttu-id="277b3-133">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="277b3-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="277b3-134">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="277b3-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
