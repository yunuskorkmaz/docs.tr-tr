---
title: ICorDebugBlockingObjectEnum Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum
helpviewer_keywords:
- ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
ms.assetid: 208e5c2d-3f3f-404e-8b3c-7cccc14ddb16
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a23d21d0ed8c6a6a226d5e58eafb7bde65a4896
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645441"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="3404c-102">ICorDebugBlockingObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3404c-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="3404c-103">Bir listesi için bir numaralandırıcı sağlar [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapıları.</span><span class="sxs-lookup"><span data-stu-id="3404c-103">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="3404c-104">Icordebugenum arabirimi öğesinin arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="3404c-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3404c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3404c-105">Methods</span></span>  
  
|<span data-ttu-id="3404c-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3404c-106">Method</span></span>|<span data-ttu-id="3404c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3404c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3404c-108">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3404c-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="3404c-109">Bir listesini numaralandırır [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapıları.</span><span class="sxs-lookup"><span data-stu-id="3404c-109">Enumerates through a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3404c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3404c-110">Remarks</span></span>  
 <span data-ttu-id="3404c-111">Her `CorDebugBlockingObject` yapısı, bir iş parçacığını engelleme nesneyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3404c-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3404c-112">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="3404c-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3404c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3404c-113">Requirements</span></span>  
 <span data-ttu-id="3404c-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3404c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3404c-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3404c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3404c-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3404c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3404c-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3404c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3404c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3404c-118">See also</span></span>

- [<span data-ttu-id="3404c-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3404c-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="3404c-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="3404c-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
