---
title: ICorDebugStackWalk::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::Next
helpviewer_keywords:
- ICorDebugStackWalk::Next method [.NET Framework debugging]
- Next method, ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 189c36be-028c-4fba-a002-5edfb8fcd07f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 724db50285532c20132fbfd5262df26227db6742
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782674"
---
# <a name="icordebugstackwalknext-method"></a><span data-ttu-id="8899f-102">ICorDebugStackWalk::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8899f-102">ICorDebugStackWalk::Next Method</span></span>
<span data-ttu-id="8899f-103">Taşır [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) sonraki kareye nesne.</span><span class="sxs-lookup"><span data-stu-id="8899f-103">Moves the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object to the next frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8899f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8899f-104">Syntax</span></span>  
  
```  
HRESULT Next();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8899f-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8899f-105">Return Value</span></span>  
 <span data-ttu-id="8899f-106">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="8899f-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8899f-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8899f-107">HRESULT</span></span>|<span data-ttu-id="8899f-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8899f-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8899f-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="8899f-109">S_OK</span></span>|<span data-ttu-id="8899f-110">Çalışma zamanı başarıyla sonraki kareye sapmasına (bkz. Notlar).</span><span class="sxs-lookup"><span data-stu-id="8899f-110">The runtime successfully unwound to the next frame (see Remarks).</span></span>|  
|<span data-ttu-id="8899f-111">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8899f-111">E_FAIL</span></span>|<span data-ttu-id="8899f-112">`ICorDebugStackWalk` Nesnesi değil Gelişmiş.</span><span class="sxs-lookup"><span data-stu-id="8899f-112">The `ICorDebugStackWalk` object could not be advanced.</span></span>|  
|<span data-ttu-id="8899f-113">CORDBG_S_AT_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="8899f-113">CORDBG_S_AT_END_OF_STACK</span></span>|<span data-ttu-id="8899f-114">Yığının sonunun sonucu olarak bu bırakma ulaşıldı.</span><span class="sxs-lookup"><span data-stu-id="8899f-114">The end of the stack was reached as a result of this unwind.</span></span>|  
|<span data-ttu-id="8899f-115">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="8899f-115">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="8899f-116">Çerçeve işaretçisini yığının sonuna bulunur. Bu nedenle, hiçbir ek çerçeveler erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="8899f-116">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="8899f-117">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="8899f-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8899f-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8899f-118">Remarks</span></span>  
 <span data-ttu-id="8899f-119">`Next` Yöntemi geliştirmeleri `ICorDebugStackWalk` çağıran çerçevenin çalışma zamanı geçerli çerçeve yalnızca geriye doğru izleyebilirsiniz, nesne.</span><span class="sxs-lookup"><span data-stu-id="8899f-119">The `Next` method advances the `ICorDebugStackWalk` object to the calling frame only if the runtime can unwind the current frame.</span></span> <span data-ttu-id="8899f-120">Aksi takdirde, nesne çalışma zamanı geriye doğru izleme olanağına sahip sonraki kareye ilerler.</span><span class="sxs-lookup"><span data-stu-id="8899f-120">Otherwise, the object advances to the next frame that the runtime is able to unwind.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8899f-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8899f-121">Requirements</span></span>  
 <span data-ttu-id="8899f-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8899f-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8899f-123">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8899f-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8899f-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8899f-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8899f-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8899f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8899f-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8899f-126">See also</span></span>

- [<span data-ttu-id="8899f-127">ICorDebugStackWalk Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8899f-127">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)
- [<span data-ttu-id="8899f-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8899f-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="8899f-129">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="8899f-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
