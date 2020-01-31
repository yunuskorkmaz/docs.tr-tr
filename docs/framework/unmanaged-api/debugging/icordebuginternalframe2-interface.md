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
ms.openlocfilehash: 9e333d71505a055cfe27df2c79a102c939bafc9d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788471"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="56c19-102">ICorDebugInternalFrame2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="56c19-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="56c19-103">Yığın adresi ve ICorDebugFrame nesneleriyle ilişkili konum dahil olmak üzere iç çerçeveler hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="56c19-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="56c19-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="56c19-104">Methods</span></span>  
  
|<span data-ttu-id="56c19-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="56c19-105">Method</span></span>|<span data-ttu-id="56c19-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56c19-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="56c19-107">GetFrameAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56c19-107">GetFrameAddress Method</span></span>](icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="56c19-108">İç çerçevenin yığın adresini döndürür.</span><span class="sxs-lookup"><span data-stu-id="56c19-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="56c19-109">IsCloserToLeaf Yöntemi</span><span class="sxs-lookup"><span data-stu-id="56c19-109">IsCloserToLeaf Method</span></span>](icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="56c19-110">`this` iç çerçevesinin belirtilen ICorDebugFrame nesnesinden daha yakın olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="56c19-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56c19-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56c19-111">Remarks</span></span>  
 <span data-ttu-id="56c19-112">Bu arabirim, ICorDebugInternalFrame arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="56c19-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="56c19-113">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="56c19-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56c19-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="56c19-114">Requirements</span></span>  
 <span data-ttu-id="56c19-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56c19-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56c19-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="56c19-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56c19-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="56c19-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56c19-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56c19-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56c19-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56c19-119">See also</span></span>

- [<span data-ttu-id="56c19-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="56c19-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="56c19-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="56c19-121">Debugging</span></span>](index.md)
