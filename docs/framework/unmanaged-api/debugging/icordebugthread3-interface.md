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
ms.openlocfilehash: 1d34a3395605505ca0ebda072e33d8083d51123a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59185880"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="23076-102">ICorDebugThread3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="23076-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="23076-103">Giriş noktası sağlar [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) ve karşılık gelen arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="23076-103">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="23076-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="23076-104">Methods</span></span>  
  
|<span data-ttu-id="23076-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="23076-105">Method</span></span>|<span data-ttu-id="23076-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23076-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="23076-107">CreateStackWalk Yöntemi</span><span class="sxs-lookup"><span data-stu-id="23076-107">CreateStackWalk Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="23076-108">Oluşturur bir [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) yığın geriye doğru izleme istediğiniz iş parçacığı için nesne.</span><span class="sxs-lookup"><span data-stu-id="23076-108">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="23076-109">GetActiveInternalFrames Yöntemi</span><span class="sxs-lookup"><span data-stu-id="23076-109">GetActiveInternalFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="23076-110">İç çerçeveler bir dizi döndürür ([Icordebugınternalframe2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) nesneleri) yığında.</span><span class="sxs-lookup"><span data-stu-id="23076-110">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23076-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="23076-111">Remarks</span></span>  
 <span data-ttu-id="23076-112">`ICorDebugThread3` Icordebugthread arabirimi mantıksal uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="23076-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23076-113">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="23076-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23076-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="23076-114">Requirements</span></span>  
 <span data-ttu-id="23076-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23076-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23076-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="23076-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23076-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23076-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23076-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23076-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23076-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23076-119">See also</span></span>

- [<span data-ttu-id="23076-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="23076-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="23076-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="23076-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
