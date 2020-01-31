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
ms.openlocfilehash: b76d17337408653d130ee0cb8594e759bdade37c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791863"
---
# <a name="icordebugstackwalknext-method"></a><span data-ttu-id="55962-102">ICorDebugStackWalk::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55962-102">ICorDebugStackWalk::Next Method</span></span>
<span data-ttu-id="55962-103">[Icordebugstackyürüme](icordebugstackwalk-interface.md) nesnesini sonraki çerçeveye kaydırır.</span><span class="sxs-lookup"><span data-stu-id="55962-103">Moves the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object to the next frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55962-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55962-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="return-value"></a><span data-ttu-id="55962-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="55962-105">Return Value</span></span>  
 <span data-ttu-id="55962-106">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="55962-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="55962-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="55962-107">HRESULT</span></span>|<span data-ttu-id="55962-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55962-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="55962-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="55962-109">S_OK</span></span>|<span data-ttu-id="55962-110">Çalışma zamanı bir sonraki çerçeveye başarıyla geri alınıyor (bkz. notlar).</span><span class="sxs-lookup"><span data-stu-id="55962-110">The runtime successfully unwound to the next frame (see Remarks).</span></span>|  
|<span data-ttu-id="55962-111">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="55962-111">E_FAIL</span></span>|<span data-ttu-id="55962-112">`ICorDebugStackWalk` nesnesi gelişmiş bir nesne olamaz.</span><span class="sxs-lookup"><span data-stu-id="55962-112">The `ICorDebugStackWalk` object could not be advanced.</span></span>|  
|<span data-ttu-id="55962-113">CORDBG_S_AT_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="55962-113">CORDBG_S_AT_END_OF_STACK</span></span>|<span data-ttu-id="55962-114">Bu geriye doğru bir sonuç olarak yığının sonuna ulaşıldı.</span><span class="sxs-lookup"><span data-stu-id="55962-114">The end of the stack was reached as a result of this unwind.</span></span>|  
|<span data-ttu-id="55962-115">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="55962-115">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="55962-116">Çerçeve işaretçisi zaten yığının sonunda. Bu nedenle, ek çerçevelere erişilemez.</span><span class="sxs-lookup"><span data-stu-id="55962-116">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="55962-117">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="55962-117">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55962-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55962-118">Remarks</span></span>  
 <span data-ttu-id="55962-119">`Next` yöntemi, `ICorDebugStackWalk` nesnesini çağıran çerçeveye ilerletir ve yalnızca çalışma zamanı geçerli çerçeveyi geriye doğru geri alabilir.</span><span class="sxs-lookup"><span data-stu-id="55962-119">The `Next` method advances the `ICorDebugStackWalk` object to the calling frame only if the runtime can unwind the current frame.</span></span> <span data-ttu-id="55962-120">Aksi halde, nesne, çalışma zamanının geriye doğru geri yükleyebilmesini sağlayan bir sonraki çerçeveye ilerler.</span><span class="sxs-lookup"><span data-stu-id="55962-120">Otherwise, the object advances to the next frame that the runtime is able to unwind.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55962-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="55962-121">Requirements</span></span>  
 <span data-ttu-id="55962-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55962-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55962-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="55962-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55962-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="55962-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55962-125">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55962-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55962-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55962-126">See also</span></span>

- [<span data-ttu-id="55962-127">ICorDebugStackWalk Arabirimi</span><span class="sxs-lookup"><span data-stu-id="55962-127">ICorDebugStackWalk Interface</span></span>](icordebugstackwalk-interface.md)
- [<span data-ttu-id="55962-128">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="55962-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="55962-129">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="55962-129">Debugging</span></span>](index.md)
