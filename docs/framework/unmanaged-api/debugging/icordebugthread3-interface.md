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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9622716e3a2cca7e3af0b1e1b134458a50ad1bec
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962973"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="ad037-102">ICorDebugThread3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad037-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="ad037-103">[Icordebugstackyürüme](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) ve ilgili arabirimlere giriş noktası sağlar.</span><span class="sxs-lookup"><span data-stu-id="ad037-103">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ad037-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ad037-104">Methods</span></span>  
  
|<span data-ttu-id="ad037-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ad037-105">Method</span></span>|<span data-ttu-id="ad037-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad037-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ad037-107">CreateStackWalk Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad037-107">CreateStackWalk Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="ad037-108">Yığınını aşağı doğru bırakmak istediğiniz iş parçacığı için [ıcordebugstackyürüme](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ad037-108">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="ad037-109">GetActiveInternalFrames Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ad037-109">GetActiveInternalFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="ad037-110">Yığında iç çerçeveler ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) nesneleri) dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ad037-110">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad037-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad037-111">Remarks</span></span>  
 <span data-ttu-id="ad037-112">`ICorDebugThread3`, ICorDebugThread arabirimine yönelik mantıksal bir uzantıdır.</span><span class="sxs-lookup"><span data-stu-id="ad037-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ad037-113">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="ad037-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad037-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad037-114">Requirements</span></span>  
 <span data-ttu-id="ad037-115">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad037-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad037-116">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ad037-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad037-117">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ad037-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad037-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad037-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad037-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad037-119">See also</span></span>

- [<span data-ttu-id="ad037-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ad037-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ad037-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ad037-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
