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
ms.openlocfilehash: 77210edfdc954f38ff06bc43a8b41a6abe8dc3d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131834"
---
# <a name="icordebugstackwalkgetframe-method"></a><span data-ttu-id="92d67-102">ICorDebugStackWalk::GetFrame Metodu</span><span class="sxs-lookup"><span data-stu-id="92d67-102">ICorDebugStackWalk::GetFrame Method</span></span>
<span data-ttu-id="92d67-103">[Icordebugstackyürüme](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) nesnesinde geçerli kareyi alır.</span><span class="sxs-lookup"><span data-stu-id="92d67-103">Gets the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92d67-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92d67-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92d67-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="92d67-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="92d67-106">'ndaki Oluşturulan çerçeve nesnesinin, yığındaki geçerli çerçeveyi temsil eden adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="92d67-106">[in] A pointer to the address of the created frame object that represents the current frame in the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92d67-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="92d67-107">Return Value</span></span>  
 <span data-ttu-id="92d67-108">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="92d67-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="92d67-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="92d67-109">HRESULT</span></span>|<span data-ttu-id="92d67-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92d67-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="92d67-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="92d67-111">S_OK</span></span>|<span data-ttu-id="92d67-112">Çalışma zamanı geçerli çerçeveyi başarıyla döndürdü.</span><span class="sxs-lookup"><span data-stu-id="92d67-112">The runtime successfully returned the current frame.</span></span>|  
|<span data-ttu-id="92d67-113">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="92d67-113">E_FAIL</span></span>|<span data-ttu-id="92d67-114">Geçerli çerçeve döndürülmedi.</span><span class="sxs-lookup"><span data-stu-id="92d67-114">The current frame was not returned.</span></span>|  
|<span data-ttu-id="92d67-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="92d67-115">S_FALSE</span></span>|<span data-ttu-id="92d67-116">Geçerli çerçeve bir yerel yığın çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="92d67-116">The current frame is a native stack frame.</span></span>|  
|<span data-ttu-id="92d67-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="92d67-117">E_INVALIDARG</span></span>|<span data-ttu-id="92d67-118">`pFrame` null.</span><span class="sxs-lookup"><span data-stu-id="92d67-118">`pFrame` is null.</span></span>|  
|<span data-ttu-id="92d67-119">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="92d67-119">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="92d67-120">Çerçeve işaretçisi zaten yığının sonunda. Bu nedenle, ek çerçevelere erişilemez.</span><span class="sxs-lookup"><span data-stu-id="92d67-120">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="92d67-121">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="92d67-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92d67-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92d67-122">Remarks</span></span>  
 <span data-ttu-id="92d67-123">`ICorDebugStackWalk` yalnızca gerçek yığın çerçevelerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="92d67-123">`ICorDebugStackWalk` returns only actual stack frames.</span></span> <span data-ttu-id="92d67-124">İç çerçeveler döndürmek için [ICorDebugThread3:: GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="92d67-124">Use the [ICorDebugThread3::GetActiveInternalFrames](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) method to return internal frames.</span></span> <span data-ttu-id="92d67-125">(İç çerçeveler, geçici verileri depolamak için çalışma zamanı tarafından yığına gönderilen veri yapılarıdır.)</span><span class="sxs-lookup"><span data-stu-id="92d67-125">(Internal frames are data structures pushed onto the stack by the runtime to store temporary data.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92d67-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92d67-126">Requirements</span></span>  
 <span data-ttu-id="92d67-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92d67-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92d67-128">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="92d67-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92d67-129">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="92d67-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92d67-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92d67-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92d67-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92d67-131">See also</span></span>

- [<span data-ttu-id="92d67-132">ICorDebugStackWalk Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92d67-132">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [<span data-ttu-id="92d67-133">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="92d67-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="92d67-134">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="92d67-134">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
