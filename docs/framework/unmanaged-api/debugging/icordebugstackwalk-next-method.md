---
description: 'Şu konuda daha fazla bilgi edinin: ıcordebugstackizlenecek yol:: Next yöntemi'
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
ms.openlocfilehash: 27a48ca40f6b43cae32511b71b73e68d88eb60c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717764"
---
# <a name="icordebugstackwalknext-method"></a><span data-ttu-id="68135-103">ICorDebugStackWalk::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68135-103">ICorDebugStackWalk::Next Method</span></span>

<span data-ttu-id="68135-104">[Icordebugstackyürüme](icordebugstackwalk-interface.md) nesnesini sonraki çerçeveye kaydırır.</span><span class="sxs-lookup"><span data-stu-id="68135-104">Moves the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object to the next frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68135-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="68135-105">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="return-value"></a><span data-ttu-id="68135-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="68135-106">Return Value</span></span>  

 <span data-ttu-id="68135-107">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="68135-107">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="68135-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="68135-108">HRESULT</span></span>|<span data-ttu-id="68135-109">Description</span><span class="sxs-lookup"><span data-stu-id="68135-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="68135-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="68135-110">S_OK</span></span>|<span data-ttu-id="68135-111">Çalışma zamanı bir sonraki çerçeveye başarıyla geri alınıyor (bkz. notlar).</span><span class="sxs-lookup"><span data-stu-id="68135-111">The runtime successfully unwound to the next frame (see Remarks).</span></span>|  
|<span data-ttu-id="68135-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="68135-112">E_FAIL</span></span>|<span data-ttu-id="68135-113">`ICorDebugStackWalk`Nesne gelişmiş olamaz.</span><span class="sxs-lookup"><span data-stu-id="68135-113">The `ICorDebugStackWalk` object could not be advanced.</span></span>|  
|<span data-ttu-id="68135-114">CORDBG_S_AT_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="68135-114">CORDBG_S_AT_END_OF_STACK</span></span>|<span data-ttu-id="68135-115">Bu geriye doğru bir sonuç olarak yığının sonuna ulaşıldı.</span><span class="sxs-lookup"><span data-stu-id="68135-115">The end of the stack was reached as a result of this unwind.</span></span>|  
|<span data-ttu-id="68135-116">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="68135-116">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="68135-117">Çerçeve işaretçisi zaten yığının sonunda. Bu nedenle, ek çerçevelere erişilemez.</span><span class="sxs-lookup"><span data-stu-id="68135-117">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="68135-118">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="68135-118">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68135-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68135-119">Remarks</span></span>  

 <span data-ttu-id="68135-120">`Next`Yöntemi, `ICorDebugStackWalk` yalnızca çalışma zamanı geçerli çerçeveyi geriye doğru bir şekilde geri alıyorsa nesneyi çağıran çerçeveye ilerletir.</span><span class="sxs-lookup"><span data-stu-id="68135-120">The `Next` method advances the `ICorDebugStackWalk` object to the calling frame only if the runtime can unwind the current frame.</span></span> <span data-ttu-id="68135-121">Aksi halde, nesne, çalışma zamanının geriye doğru geri yükleyebilmesini sağlayan bir sonraki çerçeveye ilerler.</span><span class="sxs-lookup"><span data-stu-id="68135-121">Otherwise, the object advances to the next frame that the runtime is able to unwind.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68135-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68135-122">Requirements</span></span>  

 <span data-ttu-id="68135-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68135-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68135-124">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="68135-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68135-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="68135-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68135-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68135-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68135-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68135-127">See also</span></span>

- [<span data-ttu-id="68135-128">ICorDebugStackWalk Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68135-128">ICorDebugStackWalk Interface</span></span>](icordebugstackwalk-interface.md)
- [<span data-ttu-id="68135-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="68135-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="68135-130">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="68135-130">Debugging</span></span>](index.md)
