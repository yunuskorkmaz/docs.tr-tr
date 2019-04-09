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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59185880"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="cbb8d-102">ICorDebugThread3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cbb8d-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="cbb8d-103">Giriş noktası sağlar [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) ve karşılık gelen arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="cbb8d-103">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cbb8d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cbb8d-104">Methods</span></span>  
  
|<span data-ttu-id="cbb8d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cbb8d-105">Method</span></span>|<span data-ttu-id="cbb8d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cbb8d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cbb8d-107">CreateStackWalk Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cbb8d-107">CreateStackWalk Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="cbb8d-108">Oluşturur bir [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) yığın geriye doğru izleme istediğiniz iş parçacığı için nesne.</span><span class="sxs-lookup"><span data-stu-id="cbb8d-108">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="cbb8d-109">GetActiveInternalFrames Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cbb8d-109">GetActiveInternalFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="cbb8d-110">İç çerçeveler bir dizi döndürür ([Icordebugınternalframe2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) nesneleri) yığında.</span><span class="sxs-lookup"><span data-stu-id="cbb8d-110">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cbb8d-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cbb8d-111">Remarks</span></span>  
 `ICorDebugThread3` <span data-ttu-id="cbb8d-112">Icordebugthread arabirimi mantıksal uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="cbb8d-112">is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cbb8d-113">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="cbb8d-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbb8d-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cbb8d-114">Requirements</span></span>  
 <span data-ttu-id="cbb8d-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbb8d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbb8d-116">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cbb8d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cbb8d-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cbb8d-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="cbb8d-118">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="cbb8d-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cbb8d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbb8d-119">See also</span></span>

- [<span data-ttu-id="cbb8d-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cbb8d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="cbb8d-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="cbb8d-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
