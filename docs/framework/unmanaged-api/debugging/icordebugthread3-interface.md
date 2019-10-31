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
ms.openlocfilehash: 7cddf860f044e8493a0fdf6023b2853ac16c5b14
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137499"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="91096-102">ICorDebugThread3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="91096-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="91096-103">[Icordebugstackyürüme](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) ve ilgili arabirimlere giriş noktası sağlar.</span><span class="sxs-lookup"><span data-stu-id="91096-103">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="91096-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="91096-104">Methods</span></span>  
  
|<span data-ttu-id="91096-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="91096-105">Method</span></span>|<span data-ttu-id="91096-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91096-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="91096-107">CreateStackWalk Yöntemi</span><span class="sxs-lookup"><span data-stu-id="91096-107">CreateStackWalk Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="91096-108">Yığınını aşağı doğru bırakmak istediğiniz iş parçacığı için [ıcordebugstackyürüme](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="91096-108">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="91096-109">GetActiveInternalFrames Yöntemi</span><span class="sxs-lookup"><span data-stu-id="91096-109">GetActiveInternalFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="91096-110">Yığında iç çerçeveler ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) nesneleri) dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="91096-110">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91096-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="91096-111">Remarks</span></span>  
 <span data-ttu-id="91096-112">`ICorDebugThread3`, ICorDebugThread arabirimine yönelik bir mantıksal uzantıdır.</span><span class="sxs-lookup"><span data-stu-id="91096-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91096-113">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="91096-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91096-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="91096-114">Requirements</span></span>  
 <span data-ttu-id="91096-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91096-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91096-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="91096-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91096-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="91096-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91096-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91096-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91096-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91096-119">See also</span></span>

- [<span data-ttu-id="91096-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="91096-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="91096-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="91096-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
