---
description: 'Daha fazla bilgi edinin: ICorDebugInternalFrame2 Interface'
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
ms.openlocfilehash: 3edc666c043513562b2fcece478b2879f294ce33
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791107"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="49137-103">ICorDebugInternalFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="49137-103">ICorDebugInternalFrame2 Interface</span></span>

<span data-ttu-id="49137-104">Yığın adresi ve ICorDebugFrame nesneleriyle ilişkili konum dahil olmak üzere iç çerçeveler hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="49137-104">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="49137-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="49137-105">Methods</span></span>  
  
|<span data-ttu-id="49137-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="49137-106">Method</span></span>|<span data-ttu-id="49137-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49137-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="49137-108">GetFrameAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="49137-108">GetFrameAddress Method</span></span>](icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="49137-109">İç çerçevenin yığın adresini döndürür.</span><span class="sxs-lookup"><span data-stu-id="49137-109">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="49137-110">IsCloserToLeaf Yöntemi</span><span class="sxs-lookup"><span data-stu-id="49137-110">IsCloserToLeaf Method</span></span>](icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="49137-111">`this`İç karenin belirtilen ICorDebugFrame nesnesinden daha yakın olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="49137-111">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49137-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="49137-112">Remarks</span></span>  

 <span data-ttu-id="49137-113">Bu arabirim, ICorDebugInternalFrame arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="49137-113">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49137-114">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="49137-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49137-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="49137-115">Requirements</span></span>  

 <span data-ttu-id="49137-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49137-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49137-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="49137-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49137-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="49137-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49137-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49137-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49137-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49137-120">See also</span></span>

- [<span data-ttu-id="49137-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="49137-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="49137-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="49137-122">Debugging</span></span>](index.md)
