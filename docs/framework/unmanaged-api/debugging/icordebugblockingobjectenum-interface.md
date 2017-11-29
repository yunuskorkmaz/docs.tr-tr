---
title: ICorDebugBlockingObjectEnum Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBlockingObjectEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBlockingObjectEnum
helpviewer_keywords: ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
ms.assetid: 208e5c2d-3f3f-404e-8b3c-7cccc14ddb16
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b62da4047029881ddffff5faee9f06072407bfc6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="8cf56-102">ICorDebugBlockingObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8cf56-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="8cf56-103">Bir listesi için bir numaralandırıcı sağlar [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapıları.</span><span class="sxs-lookup"><span data-stu-id="8cf56-103">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="8cf56-104">Bu arabirim Icordebugenum arabirimi sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="8cf56-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8cf56-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8cf56-105">Methods</span></span>  
  
|<span data-ttu-id="8cf56-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8cf56-106">Method</span></span>|<span data-ttu-id="8cf56-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8cf56-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8cf56-108">Next yöntemi</span><span class="sxs-lookup"><span data-stu-id="8cf56-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="8cf56-109">Bir listesini numaralandırır [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapıları.</span><span class="sxs-lookup"><span data-stu-id="8cf56-109">Enumerates through a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8cf56-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8cf56-110">Remarks</span></span>  
 <span data-ttu-id="8cf56-111">Her `CorDebugBlockingObject` yapısı bir iş parçacığı engelleme nesneyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8cf56-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8cf56-112">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8cf56-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cf56-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8cf56-113">Requirements</span></span>  
 <span data-ttu-id="8cf56-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cf56-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cf56-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8cf56-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8cf56-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8cf56-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8cf56-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cf56-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cf56-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8cf56-118">See Also</span></span>  
 [<span data-ttu-id="8cf56-119">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8cf56-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8cf56-120">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="8cf56-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
