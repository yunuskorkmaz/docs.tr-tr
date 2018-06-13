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
ms.openlocfilehash: 367c43dc08722288dc3b32b5133f7770ffc3a27c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423110"
---
# <a name="icordebugstackwalknext-method"></a><span data-ttu-id="884d5-102">ICorDebugStackWalk::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="884d5-102">ICorDebugStackWalk::Next Method</span></span>
<span data-ttu-id="884d5-103">Taşır [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) sonraki çerçeveye nesne.</span><span class="sxs-lookup"><span data-stu-id="884d5-103">Moves the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object to the next frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="884d5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="884d5-104">Syntax</span></span>  
  
```  
HRESULT Next();  
```  
  
## <a name="return-value"></a><span data-ttu-id="884d5-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="884d5-105">Return Value</span></span>  
 <span data-ttu-id="884d5-106">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="884d5-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="884d5-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="884d5-107">HRESULT</span></span>|<span data-ttu-id="884d5-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="884d5-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="884d5-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="884d5-109">S_OK</span></span>|<span data-ttu-id="884d5-110">Çalışma zamanı başarıyla sonraki çerçeveye sapmasına (açıklamalar bakın).</span><span class="sxs-lookup"><span data-stu-id="884d5-110">The runtime successfully unwound to the next frame (see Remarks).</span></span>|  
|<span data-ttu-id="884d5-111">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="884d5-111">E_FAIL</span></span>|<span data-ttu-id="884d5-112">`ICorDebugStackWalk` Nesne değil Gelişmiş.</span><span class="sxs-lookup"><span data-stu-id="884d5-112">The `ICorDebugStackWalk` object could not be advanced.</span></span>|  
|<span data-ttu-id="884d5-113">CORDBG_S_AT_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="884d5-113">CORDBG_S_AT_END_OF_STACK</span></span>|<span data-ttu-id="884d5-114">Bu bırakma sonucunda yığının sonuna ulaşıldı.</span><span class="sxs-lookup"><span data-stu-id="884d5-114">The end of the stack was reached as a result of this unwind.</span></span>|  
|<span data-ttu-id="884d5-115">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="884d5-115">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="884d5-116">Çerçeve işaretçisi yığının sonuna zaten; Bu nedenle, hiçbir ek çerçeve erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="884d5-116">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="884d5-117">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="884d5-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="884d5-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="884d5-118">Remarks</span></span>  
 <span data-ttu-id="884d5-119">`Next` Yöntemi gelişmeleri `ICorDebugStackWalk` yalnızca çalışma zamanı geçerli çerçeve geriye doğru izleme, arama çerçeveye nesne.</span><span class="sxs-lookup"><span data-stu-id="884d5-119">The `Next` method advances the `ICorDebugStackWalk` object to the calling frame only if the runtime can unwind the current frame.</span></span> <span data-ttu-id="884d5-120">Aksi halde, çalışma zamanı bırakma yapabiliyor sonraki çerçeveye nesne ilerler.</span><span class="sxs-lookup"><span data-stu-id="884d5-120">Otherwise, the object advances to the next frame that the runtime is able to unwind.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="884d5-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="884d5-121">Requirements</span></span>  
 <span data-ttu-id="884d5-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="884d5-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="884d5-123">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="884d5-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="884d5-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="884d5-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="884d5-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="884d5-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="884d5-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="884d5-126">See Also</span></span>  
 [<span data-ttu-id="884d5-127">ICorDebugStackWalk Arabirimi</span><span class="sxs-lookup"><span data-stu-id="884d5-127">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 [<span data-ttu-id="884d5-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="884d5-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="884d5-129">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="884d5-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
