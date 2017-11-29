---
title: ICorDebugInternalFrame2 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugInternalFrame2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugInternalFrame2
helpviewer_keywords: ICorDebugInternalFrame2 interface [.NET Framework debugging]
ms.assetid: d4755569-85b8-4ff4-bf50-0e608e76429f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b612cb2fb8b2a84555ccf36a8537ebecff673d47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="f6abe-102">ICorDebugInternalFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f6abe-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="f6abe-103">Yığın adresi ve Icordebugframe nesneleri ile ilgili olarak konumu gibi iç çerçeveler hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f6abe-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f6abe-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f6abe-104">Methods</span></span>  
  
|<span data-ttu-id="f6abe-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f6abe-105">Method</span></span>|<span data-ttu-id="f6abe-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6abe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f6abe-107">GetFrameAddress yöntemi</span><span class="sxs-lookup"><span data-stu-id="f6abe-107">GetFrameAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="f6abe-108">İç çerçeve yığını adresini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6abe-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="f6abe-109">Isclosertoleaf yöntemi</span><span class="sxs-lookup"><span data-stu-id="f6abe-109">IsCloserToLeaf Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="f6abe-110">Denetler olup olmadığını `this` iç kare belirtilen Icordebugframe nesne yaprak daha yakın olur.</span><span class="sxs-lookup"><span data-stu-id="f6abe-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6abe-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f6abe-111">Remarks</span></span>  
 <span data-ttu-id="f6abe-112">Bu arabirim Icordebugınternalframe arabirimi genişletir.</span><span class="sxs-lookup"><span data-stu-id="f6abe-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6abe-113">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f6abe-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6abe-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f6abe-114">Requirements</span></span>  
 <span data-ttu-id="f6abe-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6abe-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6abe-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f6abe-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6abe-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6abe-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6abe-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6abe-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6abe-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6abe-119">See Also</span></span>  
 [<span data-ttu-id="f6abe-120">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f6abe-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="f6abe-121">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="f6abe-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
