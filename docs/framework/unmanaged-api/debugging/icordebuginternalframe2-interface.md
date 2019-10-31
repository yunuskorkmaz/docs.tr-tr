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
ms.openlocfilehash: 5a451218e0fdc32132a4e79d091ada8355d32fe7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122696"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="808e9-102">ICorDebugInternalFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="808e9-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="808e9-103">Yığın adresi ve ICorDebugFrame nesneleriyle ilişkili konum dahil olmak üzere iç çerçeveler hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="808e9-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="808e9-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="808e9-104">Methods</span></span>  
  
|<span data-ttu-id="808e9-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="808e9-105">Method</span></span>|<span data-ttu-id="808e9-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="808e9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="808e9-107">GetFrameAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="808e9-107">GetFrameAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="808e9-108">İç çerçevenin yığın adresini döndürür.</span><span class="sxs-lookup"><span data-stu-id="808e9-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="808e9-109">IsCloserToLeaf Yöntemi</span><span class="sxs-lookup"><span data-stu-id="808e9-109">IsCloserToLeaf Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="808e9-110">`this` iç çerçevesinin belirtilen ICorDebugFrame nesnesinden daha yakın olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="808e9-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="808e9-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="808e9-111">Remarks</span></span>  
 <span data-ttu-id="808e9-112">Bu arabirim, ICorDebugInternalFrame arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="808e9-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="808e9-113">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="808e9-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="808e9-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="808e9-114">Requirements</span></span>  
 <span data-ttu-id="808e9-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="808e9-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="808e9-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="808e9-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="808e9-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="808e9-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="808e9-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="808e9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="808e9-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="808e9-119">See also</span></span>

- [<span data-ttu-id="808e9-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="808e9-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="808e9-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="808e9-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
