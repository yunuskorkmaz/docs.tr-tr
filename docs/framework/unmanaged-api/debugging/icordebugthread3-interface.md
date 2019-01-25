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
ms.openlocfilehash: d5f4cecda80238e7a53cf2aa2a8219c49c2b3f9b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531726"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="63a66-102">ICorDebugThread3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="63a66-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="63a66-103">Giriş noktası sağlar [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) ve karşılık gelen arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="63a66-103">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63a66-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="63a66-104">Methods</span></span>  
  
|<span data-ttu-id="63a66-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="63a66-105">Method</span></span>|<span data-ttu-id="63a66-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63a66-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63a66-107">CreateStackWalk Yöntemi</span><span class="sxs-lookup"><span data-stu-id="63a66-107">CreateStackWalk Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="63a66-108">Oluşturur bir [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) yığın geriye doğru izleme istediğiniz iş parçacığı için nesne.</span><span class="sxs-lookup"><span data-stu-id="63a66-108">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="63a66-109">GetActiveInternalFrames Yöntemi</span><span class="sxs-lookup"><span data-stu-id="63a66-109">GetActiveInternalFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="63a66-110">İç çerçeveler bir dizi döndürür ([Icordebugınternalframe2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) nesneleri) yığında.</span><span class="sxs-lookup"><span data-stu-id="63a66-110">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63a66-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63a66-111">Remarks</span></span>  
 <span data-ttu-id="63a66-112">`ICorDebugThread3` Icordebugthread arabirimi mantıksal uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="63a66-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63a66-113">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="63a66-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63a66-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="63a66-114">Requirements</span></span>  
 <span data-ttu-id="63a66-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63a66-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63a66-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63a66-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63a66-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63a66-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63a66-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63a66-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63a66-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63a66-119">See also</span></span>
- [<span data-ttu-id="63a66-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="63a66-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="63a66-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="63a66-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
