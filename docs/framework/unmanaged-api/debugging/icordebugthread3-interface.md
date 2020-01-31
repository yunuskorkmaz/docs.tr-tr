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
ms.openlocfilehash: 19bd869aec7e4d046890d2314f5142753ba0b112
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791386"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="37ba5-102">ICorDebugThread3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="37ba5-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="37ba5-103">[Icordebugstackyürüme](icordebugstackwalk-interface.md) ve ilgili arabirimlere giriş noktası sağlar.</span><span class="sxs-lookup"><span data-stu-id="37ba5-103">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="37ba5-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="37ba5-104">Methods</span></span>  
  
|<span data-ttu-id="37ba5-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="37ba5-105">Method</span></span>|<span data-ttu-id="37ba5-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="37ba5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="37ba5-107">CreateStackWalk Yöntemi</span><span class="sxs-lookup"><span data-stu-id="37ba5-107">CreateStackWalk Method</span></span>](icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="37ba5-108">Yığınını aşağı doğru bırakmak istediğiniz iş parçacığı için [ıcordebugstackyürüme](icordebugstackwalk-interface.md) nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="37ba5-108">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="37ba5-109">GetActiveInternalFrames Yöntemi</span><span class="sxs-lookup"><span data-stu-id="37ba5-109">GetActiveInternalFrames Method</span></span>](icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="37ba5-110">Yığında iç çerçeveler ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) nesneleri) dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="37ba5-110">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37ba5-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="37ba5-111">Remarks</span></span>  
 <span data-ttu-id="37ba5-112">`ICorDebugThread3`, ICorDebugThread arabirimine yönelik bir mantıksal uzantıdır.</span><span class="sxs-lookup"><span data-stu-id="37ba5-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="37ba5-113">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="37ba5-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37ba5-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="37ba5-114">Requirements</span></span>  
 <span data-ttu-id="37ba5-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37ba5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37ba5-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="37ba5-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37ba5-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="37ba5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37ba5-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37ba5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37ba5-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37ba5-119">See also</span></span>

- [<span data-ttu-id="37ba5-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="37ba5-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="37ba5-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="37ba5-121">Debugging</span></span>](index.md)
