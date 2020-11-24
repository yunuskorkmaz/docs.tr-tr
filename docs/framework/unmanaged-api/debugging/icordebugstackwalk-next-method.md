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
ms.openlocfilehash: 497dda473e6510cfa31405b2066c63b1a70dd5e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677329"
---
# <a name="icordebugstackwalknext-method"></a><span data-ttu-id="a17da-102">ICorDebugStackWalk::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a17da-102">ICorDebugStackWalk::Next Method</span></span>

<span data-ttu-id="a17da-103">[Icordebugstackyürüme](icordebugstackwalk-interface.md) nesnesini sonraki çerçeveye kaydırır.</span><span class="sxs-lookup"><span data-stu-id="a17da-103">Moves the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object to the next frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a17da-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a17da-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a17da-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a17da-105">Return Value</span></span>  

 <span data-ttu-id="a17da-106">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="a17da-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a17da-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a17da-107">HRESULT</span></span>|<span data-ttu-id="a17da-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a17da-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a17da-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="a17da-109">S_OK</span></span>|<span data-ttu-id="a17da-110">Çalışma zamanı bir sonraki çerçeveye başarıyla geri alınıyor (bkz. notlar).</span><span class="sxs-lookup"><span data-stu-id="a17da-110">The runtime successfully unwound to the next frame (see Remarks).</span></span>|  
|<span data-ttu-id="a17da-111">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a17da-111">E_FAIL</span></span>|<span data-ttu-id="a17da-112">`ICorDebugStackWalk`Nesne gelişmiş olamaz.</span><span class="sxs-lookup"><span data-stu-id="a17da-112">The `ICorDebugStackWalk` object could not be advanced.</span></span>|  
|<span data-ttu-id="a17da-113">CORDBG_S_AT_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="a17da-113">CORDBG_S_AT_END_OF_STACK</span></span>|<span data-ttu-id="a17da-114">Bu geriye doğru bir sonuç olarak yığının sonuna ulaşıldı.</span><span class="sxs-lookup"><span data-stu-id="a17da-114">The end of the stack was reached as a result of this unwind.</span></span>|  
|<span data-ttu-id="a17da-115">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="a17da-115">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="a17da-116">Çerçeve işaretçisi zaten yığının sonunda. Bu nedenle, ek çerçevelere erişilemez.</span><span class="sxs-lookup"><span data-stu-id="a17da-116">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="a17da-117">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="a17da-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a17da-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a17da-118">Remarks</span></span>  

 <span data-ttu-id="a17da-119">`Next`Yöntemi, `ICorDebugStackWalk` yalnızca çalışma zamanı geçerli çerçeveyi geriye doğru bir şekilde geri alıyorsa nesneyi çağıran çerçeveye ilerletir.</span><span class="sxs-lookup"><span data-stu-id="a17da-119">The `Next` method advances the `ICorDebugStackWalk` object to the calling frame only if the runtime can unwind the current frame.</span></span> <span data-ttu-id="a17da-120">Aksi halde, nesne, çalışma zamanının geriye doğru geri yükleyebilmesini sağlayan bir sonraki çerçeveye ilerler.</span><span class="sxs-lookup"><span data-stu-id="a17da-120">Otherwise, the object advances to the next frame that the runtime is able to unwind.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a17da-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a17da-121">Requirements</span></span>  

 <span data-ttu-id="a17da-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a17da-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a17da-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a17da-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a17da-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a17da-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a17da-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a17da-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a17da-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a17da-126">See also</span></span>

- [<span data-ttu-id="a17da-127">ICorDebugStackWalk Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a17da-127">ICorDebugStackWalk Interface</span></span>](icordebugstackwalk-interface.md)
- [<span data-ttu-id="a17da-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a17da-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a17da-129">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="a17da-129">Debugging</span></span>](index.md)
