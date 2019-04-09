---
title: ICorDebugInternalFrame2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2
helpviewer_keywords:
- ICorDebugInternalFrame2 interface [.NET Framework debugging]
ms.assetid: d4755569-85b8-4ff4-bf50-0e608e76429f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2cf75de6a71cfbe25cbde281f837060b88e93753
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087241"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="97e1c-102">ICorDebugInternalFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="97e1c-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="97e1c-103">Yığın adresi ve Icordebugframe nesneleri ile ilgili olarak da dahil olmak üzere, iç çerçeveler hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="97e1c-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="97e1c-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="97e1c-104">Methods</span></span>  
  
|<span data-ttu-id="97e1c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="97e1c-105">Method</span></span>|<span data-ttu-id="97e1c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="97e1c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="97e1c-107">GetFrameAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="97e1c-107">GetFrameAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="97e1c-108">İç çerçevenin yığın adresi döndürür.</span><span class="sxs-lookup"><span data-stu-id="97e1c-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="97e1c-109">IsCloserToLeaf Yöntemi</span><span class="sxs-lookup"><span data-stu-id="97e1c-109">IsCloserToLeaf Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="97e1c-110">Denetler olmadığını `this` iç çerçeve belirtilen Icordebugframe nesneden yaprağa yakın.</span><span class="sxs-lookup"><span data-stu-id="97e1c-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97e1c-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="97e1c-111">Remarks</span></span>  
 <span data-ttu-id="97e1c-112">Icordebugınternalframe arabirimi bu arabirim genişletir.</span><span class="sxs-lookup"><span data-stu-id="97e1c-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="97e1c-113">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="97e1c-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97e1c-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97e1c-114">Requirements</span></span>  
 <span data-ttu-id="97e1c-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97e1c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97e1c-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="97e1c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97e1c-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97e1c-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="97e1c-118">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="97e1c-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="97e1c-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97e1c-119">See also</span></span>

- [<span data-ttu-id="97e1c-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="97e1c-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="97e1c-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="97e1c-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
