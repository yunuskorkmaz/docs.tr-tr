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
ms.openlocfilehash: 2377773b471b387376f0284522ebe29d6b003ae3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910106"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="cfdd6-102">ICorDebugInternalFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cfdd6-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="cfdd6-103">Yığın adresi ve ICorDebugFrame nesneleriyle ilişkili konum dahil olmak üzere iç çerçeveler hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="cfdd6-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cfdd6-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cfdd6-104">Methods</span></span>  
  
|<span data-ttu-id="cfdd6-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cfdd6-105">Method</span></span>|<span data-ttu-id="cfdd6-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cfdd6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cfdd6-107">GetFrameAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cfdd6-107">GetFrameAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="cfdd6-108">İç çerçevenin yığın adresini döndürür.</span><span class="sxs-lookup"><span data-stu-id="cfdd6-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="cfdd6-109">IsCloserToLeaf Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cfdd6-109">IsCloserToLeaf Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="cfdd6-110">`this` İç karenin belirtilen ICorDebugFrame nesnesinden daha yakın olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="cfdd6-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfdd6-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cfdd6-111">Remarks</span></span>  
 <span data-ttu-id="cfdd6-112">Bu arabirim, ICorDebugInternalFrame arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="cfdd6-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cfdd6-113">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="cfdd6-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfdd6-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cfdd6-114">Requirements</span></span>  
 <span data-ttu-id="cfdd6-115">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfdd6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfdd6-116">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cfdd6-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cfdd6-117">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cfdd6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfdd6-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfdd6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfdd6-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfdd6-119">See also</span></span>

- [<span data-ttu-id="cfdd6-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cfdd6-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="cfdd6-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="cfdd6-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
