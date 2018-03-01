---
title: ICorDebugBlockingObjectEnum Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d35d4ee2ce3c1b7b0f54d78dba8b8639c522d509
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="f642b-102">ICorDebugBlockingObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f642b-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="f642b-103">Bir listesi için bir numaralandırıcı sağlar [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapıları.</span><span class="sxs-lookup"><span data-stu-id="f642b-103">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="f642b-104">Bu arabirim Icordebugenum arabirimi sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="f642b-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f642b-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f642b-105">Methods</span></span>  
  
|<span data-ttu-id="f642b-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f642b-106">Method</span></span>|<span data-ttu-id="f642b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f642b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f642b-108">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f642b-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="f642b-109">Bir listesini numaralandırır [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapıları.</span><span class="sxs-lookup"><span data-stu-id="f642b-109">Enumerates through a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f642b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f642b-110">Remarks</span></span>  
 <span data-ttu-id="f642b-111">Her `CorDebugBlockingObject` yapısı bir iş parçacığı engelleme nesneyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f642b-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f642b-112">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f642b-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f642b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f642b-113">Requirements</span></span>  
 <span data-ttu-id="f642b-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f642b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f642b-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f642b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f642b-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f642b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f642b-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f642b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f642b-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f642b-118">See Also</span></span>  
 [<span data-ttu-id="f642b-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f642b-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="f642b-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="f642b-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
