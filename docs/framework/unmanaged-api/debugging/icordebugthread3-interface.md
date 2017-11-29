---
title: ICorDebugThread3 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread3
helpviewer_keywords: ICorDebugThread3 interface [.NET Framework debugging]
ms.assetid: eb2860ef-06cb-4968-a6c3-6d048ecda2a4
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ed505cacc5286d27bc9a94eaa192dc6b889eb525
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="0ade1-102">ICorDebugThread3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ade1-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="0ade1-103">Giriş noktası sağlar [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) ve karşılık gelen arabirimler.</span><span class="sxs-lookup"><span data-stu-id="0ade1-103">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0ade1-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0ade1-104">Methods</span></span>  
  
|<span data-ttu-id="0ade1-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0ade1-105">Method</span></span>|<span data-ttu-id="0ade1-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0ade1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0ade1-107">CreateStackWalk yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ade1-107">CreateStackWalk Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="0ade1-108">Oluşturur bir [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) yığını geriye doğru izleme istediğiniz iş parçacığı için nesne.</span><span class="sxs-lookup"><span data-stu-id="0ade1-108">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="0ade1-109">Getactiveınternalframes yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ade1-109">GetActiveInternalFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="0ade1-110">İç çerçeveleri bir dizi döndürür ([Icordebugınternalframe2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) nesneler) yığında.</span><span class="sxs-lookup"><span data-stu-id="0ade1-110">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ade1-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ade1-111">Remarks</span></span>  
 <span data-ttu-id="0ade1-112">`ICorDebugThread3`Icordebugthread arabirimi için mantıksal bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="0ade1-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ade1-113">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0ade1-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ade1-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0ade1-114">Requirements</span></span>  
 <span data-ttu-id="0ade1-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ade1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ade1-116">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ade1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ade1-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ade1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ade1-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ade1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ade1-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0ade1-119">See Also</span></span>  
 [<span data-ttu-id="0ade1-120">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0ade1-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="0ade1-121">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="0ade1-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
