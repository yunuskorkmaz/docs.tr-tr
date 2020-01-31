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
ms.openlocfilehash: 89576e2b3d5fb4df0cccfdd28c80a5cb67331597
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791895"
---
# <a name="icordebugstackwalkgetframe-method"></a><span data-ttu-id="53905-102">ICorDebugStackWalk::GetFrame Metodu</span><span class="sxs-lookup"><span data-stu-id="53905-102">ICorDebugStackWalk::GetFrame Method</span></span>
<span data-ttu-id="53905-103">[Icordebugstackyürüme](icordebugstackwalk-interface.md) nesnesinde geçerli kareyi alır.</span><span class="sxs-lookup"><span data-stu-id="53905-103">Gets the current frame in the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53905-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53905-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53905-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="53905-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="53905-106">'ndaki Oluşturulan çerçeve nesnesinin, yığındaki geçerli çerçeveyi temsil eden adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="53905-106">[in] A pointer to the address of the created frame object that represents the current frame in the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53905-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="53905-107">Return Value</span></span>  
 <span data-ttu-id="53905-108">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="53905-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="53905-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="53905-109">HRESULT</span></span>|<span data-ttu-id="53905-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53905-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="53905-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="53905-111">S_OK</span></span>|<span data-ttu-id="53905-112">Çalışma zamanı geçerli çerçeveyi başarıyla döndürdü.</span><span class="sxs-lookup"><span data-stu-id="53905-112">The runtime successfully returned the current frame.</span></span>|  
|<span data-ttu-id="53905-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="53905-113">E_FAIL</span></span>|<span data-ttu-id="53905-114">Geçerli çerçeve döndürülmedi.</span><span class="sxs-lookup"><span data-stu-id="53905-114">The current frame was not returned.</span></span>|  
|<span data-ttu-id="53905-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="53905-115">S_FALSE</span></span>|<span data-ttu-id="53905-116">Geçerli çerçeve bir yerel yığın çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="53905-116">The current frame is a native stack frame.</span></span>|  
|<span data-ttu-id="53905-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="53905-117">E_INVALIDARG</span></span>|<span data-ttu-id="53905-118">`pFrame` null.</span><span class="sxs-lookup"><span data-stu-id="53905-118">`pFrame` is null.</span></span>|  
|<span data-ttu-id="53905-119">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="53905-119">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="53905-120">Çerçeve işaretçisi zaten yığının sonunda. Bu nedenle, ek çerçevelere erişilemez.</span><span class="sxs-lookup"><span data-stu-id="53905-120">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="53905-121">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="53905-121">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53905-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="53905-122">Remarks</span></span>  
 <span data-ttu-id="53905-123">`ICorDebugStackWalk` yalnızca gerçek yığın çerçevelerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="53905-123">`ICorDebugStackWalk` returns only actual stack frames.</span></span> <span data-ttu-id="53905-124">İç çerçeveler döndürmek için [ICorDebugThread3:: GetActiveInternalFrames](icordebugthread3-getactiveinternalframes-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="53905-124">Use the [ICorDebugThread3::GetActiveInternalFrames](icordebugthread3-getactiveinternalframes-method.md) method to return internal frames.</span></span> <span data-ttu-id="53905-125">(İç çerçeveler, geçici verileri depolamak için çalışma zamanı tarafından yığına gönderilen veri yapılarıdır.)</span><span class="sxs-lookup"><span data-stu-id="53905-125">(Internal frames are data structures pushed onto the stack by the runtime to store temporary data.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53905-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="53905-126">Requirements</span></span>  
 <span data-ttu-id="53905-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53905-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53905-128">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="53905-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53905-129">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="53905-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53905-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53905-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53905-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53905-131">See also</span></span>

- [<span data-ttu-id="53905-132">ICorDebugStackWalk Arabirimi</span><span class="sxs-lookup"><span data-stu-id="53905-132">ICorDebugStackWalk Interface</span></span>](icordebugstackwalk-interface.md)
- [<span data-ttu-id="53905-133">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="53905-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="53905-134">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="53905-134">Debugging</span></span>](index.md)
