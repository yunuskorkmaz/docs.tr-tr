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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988448"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="f03af-102">ICorDebugInternalFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f03af-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="f03af-103">Yığın adresi ve Icordebugframe nesneleri ile ilgili olarak da dahil olmak üzere, iç çerçeveler hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f03af-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f03af-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f03af-104">Methods</span></span>  
  
|<span data-ttu-id="f03af-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f03af-105">Method</span></span>|<span data-ttu-id="f03af-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f03af-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f03af-107">GetFrameAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f03af-107">GetFrameAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="f03af-108">İç çerçevenin yığın adresi döndürür.</span><span class="sxs-lookup"><span data-stu-id="f03af-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="f03af-109">IsCloserToLeaf Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f03af-109">IsCloserToLeaf Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="f03af-110">Denetler olmadığını `this` iç çerçeve belirtilen Icordebugframe nesneden yaprağa yakın.</span><span class="sxs-lookup"><span data-stu-id="f03af-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f03af-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f03af-111">Remarks</span></span>  
 <span data-ttu-id="f03af-112">Icordebugınternalframe arabirimi bu arabirim genişletir.</span><span class="sxs-lookup"><span data-stu-id="f03af-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f03af-113">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f03af-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f03af-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f03af-114">Requirements</span></span>  
 <span data-ttu-id="f03af-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f03af-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f03af-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f03af-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f03af-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f03af-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f03af-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f03af-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f03af-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f03af-119">See also</span></span>

- [<span data-ttu-id="f03af-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f03af-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f03af-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="f03af-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
