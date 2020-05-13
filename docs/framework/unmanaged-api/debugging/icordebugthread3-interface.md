---
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
ms.openlocfilehash: dc556dfb59e999ed9b7fc5f35c603dc26c35f314
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378716"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="5aa24-102">ICorDebugThread3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5aa24-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="5aa24-103">[Icordebugstackyürüme](icordebugstackwalk-interface.md) ve ilgili arabirimlere giriş noktası sağlar.</span><span class="sxs-lookup"><span data-stu-id="5aa24-103">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5aa24-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5aa24-104">Methods</span></span>  
  
|<span data-ttu-id="5aa24-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5aa24-105">Method</span></span>|<span data-ttu-id="5aa24-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5aa24-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5aa24-107">CreateStackWalk Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5aa24-107">CreateStackWalk Method</span></span>](icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="5aa24-108">Yığınını aşağı doğru bırakmak istediğiniz iş parçacığı için [ıcordebugstackyürüme](icordebugstackwalk-interface.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5aa24-108">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="5aa24-109">GetActiveInternalFrames Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5aa24-109">GetActiveInternalFrames Method</span></span>](icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="5aa24-110">Yığında iç çerçeveler ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) nesneleri) dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5aa24-110">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5aa24-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5aa24-111">Remarks</span></span>  
 <span data-ttu-id="5aa24-112">`ICorDebugThread3`, ICorDebugThread arabirimine yönelik mantıksal bir uzantıdır.</span><span class="sxs-lookup"><span data-stu-id="5aa24-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5aa24-113">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="5aa24-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5aa24-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5aa24-114">Requirements</span></span>  
 <span data-ttu-id="5aa24-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5aa24-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5aa24-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5aa24-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5aa24-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5aa24-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5aa24-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5aa24-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5aa24-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5aa24-119">See also</span></span>

- [<span data-ttu-id="5aa24-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5aa24-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5aa24-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="5aa24-121">Debugging</span></span>](index.md)
