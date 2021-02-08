---
description: ': Icordebugstackizlenecek yol:: GetFrame yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: b00ddb6a475aff4263a922f5a20b866cd0e1b2ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794747"
---
# <a name="icordebugstackwalkgetframe-method"></a><span data-ttu-id="2b443-103">ICorDebugStackWalk::GetFrame Metodu</span><span class="sxs-lookup"><span data-stu-id="2b443-103">ICorDebugStackWalk::GetFrame Method</span></span>

<span data-ttu-id="2b443-104">[Icordebugstackyürüme](icordebugstackwalk-interface.md) nesnesinde geçerli kareyi alır.</span><span class="sxs-lookup"><span data-stu-id="2b443-104">Gets the current frame in the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b443-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b443-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFrame([out] ICorDebugFrame ** pFrame);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b443-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2b443-106">Parameters</span></span>  

 `pFrame`  
 <span data-ttu-id="2b443-107">'ndaki Oluşturulan çerçeve nesnesinin, yığındaki geçerli çerçeveyi temsil eden adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2b443-107">[in] A pointer to the address of the created frame object that represents the current frame in the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b443-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2b443-108">Return Value</span></span>  

 <span data-ttu-id="2b443-109">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="2b443-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2b443-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2b443-110">HRESULT</span></span>|<span data-ttu-id="2b443-111">Description</span><span class="sxs-lookup"><span data-stu-id="2b443-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2b443-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="2b443-112">S_OK</span></span>|<span data-ttu-id="2b443-113">Çalışma zamanı geçerli çerçeveyi başarıyla döndürdü.</span><span class="sxs-lookup"><span data-stu-id="2b443-113">The runtime successfully returned the current frame.</span></span>|  
|<span data-ttu-id="2b443-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2b443-114">E_FAIL</span></span>|<span data-ttu-id="2b443-115">Geçerli çerçeve döndürülmedi.</span><span class="sxs-lookup"><span data-stu-id="2b443-115">The current frame was not returned.</span></span>|  
|<span data-ttu-id="2b443-116">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="2b443-116">S_FALSE</span></span>|<span data-ttu-id="2b443-117">Geçerli çerçeve bir yerel yığın çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="2b443-117">The current frame is a native stack frame.</span></span>|  
|<span data-ttu-id="2b443-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2b443-118">E_INVALIDARG</span></span>|<span data-ttu-id="2b443-119">`pFrame` null.</span><span class="sxs-lookup"><span data-stu-id="2b443-119">`pFrame` is null.</span></span>|  
|<span data-ttu-id="2b443-120">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="2b443-120">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="2b443-121">Çerçeve işaretçisi zaten yığının sonunda. Bu nedenle, ek çerçevelere erişilemez.</span><span class="sxs-lookup"><span data-stu-id="2b443-121">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="2b443-122">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="2b443-122">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b443-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2b443-123">Remarks</span></span>  

 <span data-ttu-id="2b443-124">`ICorDebugStackWalk` yalnızca gerçek yığın çerçevelerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="2b443-124">`ICorDebugStackWalk` returns only actual stack frames.</span></span> <span data-ttu-id="2b443-125">İç çerçeveler döndürmek için [ICorDebugThread3:: GetActiveInternalFrames](icordebugthread3-getactiveinternalframes-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="2b443-125">Use the [ICorDebugThread3::GetActiveInternalFrames](icordebugthread3-getactiveinternalframes-method.md) method to return internal frames.</span></span> <span data-ttu-id="2b443-126">(İç çerçeveler, geçici verileri depolamak için çalışma zamanı tarafından yığına gönderilen veri yapılarıdır.)</span><span class="sxs-lookup"><span data-stu-id="2b443-126">(Internal frames are data structures pushed onto the stack by the runtime to store temporary data.)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b443-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2b443-127">Requirements</span></span>  

 <span data-ttu-id="2b443-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b443-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b443-129">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2b443-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b443-130">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2b443-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b443-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b443-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b443-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b443-132">See also</span></span>

- [<span data-ttu-id="2b443-133">ICorDebugStackWalk Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2b443-133">ICorDebugStackWalk Interface</span></span>](icordebugstackwalk-interface.md)
- [<span data-ttu-id="2b443-134">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2b443-134">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2b443-135">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="2b443-135">Debugging</span></span>](index.md)
