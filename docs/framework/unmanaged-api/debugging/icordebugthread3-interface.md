---
description: 'Daha fazla bilgi edinin: ICorDebugThread3 Interface'
title: ICorDebugThread3 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugThread3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3
helpviewer_keywords:
- ICorDebugThread3 interface [.NET Framework debugging]
ms.assetid: eb2860ef-06cb-4968-a6c3-6d048ecda2a4
topic_type:
- apiref
ms.openlocfilehash: 88c668f1e08d0843f26d231937c85d80e03bee6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800974"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="36d6c-103">ICorDebugThread3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="36d6c-103">ICorDebugThread3 Interface</span></span>

<span data-ttu-id="36d6c-104">[Icordebugstackyürüme](icordebugstackwalk-interface.md) ve ilgili arabirimlere giriş noktası sağlar.</span><span class="sxs-lookup"><span data-stu-id="36d6c-104">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="36d6c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="36d6c-105">Methods</span></span>  
  
|<span data-ttu-id="36d6c-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="36d6c-106">Method</span></span>|<span data-ttu-id="36d6c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36d6c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="36d6c-108">CreateStackWalk Yöntemi</span><span class="sxs-lookup"><span data-stu-id="36d6c-108">CreateStackWalk Method</span></span>](icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="36d6c-109">Yığınını aşağı doğru bırakmak istediğiniz iş parçacığı için [ıcordebugstackyürüme](icordebugstackwalk-interface.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="36d6c-109">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="36d6c-110">GetActiveInternalFrames Yöntemi</span><span class="sxs-lookup"><span data-stu-id="36d6c-110">GetActiveInternalFrames Method</span></span>](icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="36d6c-111">Yığında iç çerçeveler ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) nesneleri) dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="36d6c-111">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36d6c-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="36d6c-112">Remarks</span></span>  

 <span data-ttu-id="36d6c-113">`ICorDebugThread3` , ICorDebugThread arabirimine yönelik mantıksal bir uzantıdır.</span><span class="sxs-lookup"><span data-stu-id="36d6c-113">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36d6c-114">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="36d6c-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36d6c-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="36d6c-115">Requirements</span></span>  

 <span data-ttu-id="36d6c-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36d6c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36d6c-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="36d6c-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36d6c-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="36d6c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36d6c-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36d6c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36d6c-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36d6c-120">See also</span></span>

- [<span data-ttu-id="36d6c-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="36d6c-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="36d6c-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="36d6c-122">Debugging</span></span>](index.md)
