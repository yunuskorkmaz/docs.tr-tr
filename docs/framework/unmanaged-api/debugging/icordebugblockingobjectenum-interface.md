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
ms.openlocfilehash: 91e4967d6820f8f059262e7a18add072332c509d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532795"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="d4557-102">ICorDebugBlockingObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4557-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="d4557-103">Bir listesi için bir numaralandırıcı sağlar [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapıları.</span><span class="sxs-lookup"><span data-stu-id="d4557-103">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="d4557-104">Icordebugenum arabirimi öğesinin arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="d4557-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d4557-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d4557-105">Methods</span></span>  
  
|<span data-ttu-id="d4557-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d4557-106">Method</span></span>|<span data-ttu-id="d4557-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4557-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d4557-108">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4557-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="d4557-109">Bir listesini numaralandırır [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapıları.</span><span class="sxs-lookup"><span data-stu-id="d4557-109">Enumerates through a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4557-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4557-110">Remarks</span></span>  
 <span data-ttu-id="d4557-111">Her `CorDebugBlockingObject` yapısı, bir iş parçacığını engelleme nesneyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d4557-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4557-112">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="d4557-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4557-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4557-113">Requirements</span></span>  
 <span data-ttu-id="d4557-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4557-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4557-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4557-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4557-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4557-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4557-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4557-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4557-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4557-118">See also</span></span>
- [<span data-ttu-id="d4557-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d4557-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="d4557-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="d4557-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
