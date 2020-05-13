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
ms.openlocfilehash: ce3ca4745727a1738fdc1a526480d70ffc55ccf8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209909"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="e814d-102">ICorDebugInternalFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e814d-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="e814d-103">Yığın adresi ve ICorDebugFrame nesneleriyle ilişkili konum dahil olmak üzere iç çerçeveler hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e814d-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e814d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e814d-104">Methods</span></span>  
  
|<span data-ttu-id="e814d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e814d-105">Method</span></span>|<span data-ttu-id="e814d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e814d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e814d-107">GetFrameAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e814d-107">GetFrameAddress Method</span></span>](icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="e814d-108">İç çerçevenin yığın adresini döndürür.</span><span class="sxs-lookup"><span data-stu-id="e814d-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="e814d-109">IsCloserToLeaf Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e814d-109">IsCloserToLeaf Method</span></span>](icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="e814d-110">`this`İç karenin belirtilen ICorDebugFrame nesnesinden daha yakın olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="e814d-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e814d-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e814d-111">Remarks</span></span>  
 <span data-ttu-id="e814d-112">Bu arabirim, ICorDebugInternalFrame arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="e814d-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e814d-113">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="e814d-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e814d-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e814d-114">Requirements</span></span>  
 <span data-ttu-id="e814d-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e814d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e814d-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e814d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e814d-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e814d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e814d-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e814d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e814d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e814d-119">See also</span></span>

- [<span data-ttu-id="e814d-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e814d-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e814d-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="e814d-121">Debugging</span></span>](index.md)
