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
ms.openlocfilehash: 11693416d0a3e0afe80c2356ff0a12ecea0d8d15
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959307"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="b0bed-102">ICorDebugBlockingObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0bed-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="b0bed-103">[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapılarının listesi için bir Numaralandırıcı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b0bed-103">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="b0bed-104">Bu arabirim, ıcordebuggenum arabiriminin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="b0bed-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b0bed-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b0bed-105">Methods</span></span>  
  
|<span data-ttu-id="b0bed-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b0bed-106">Method</span></span>|<span data-ttu-id="b0bed-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b0bed-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b0bed-108">Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0bed-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="b0bed-109">[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) yapılarının listesini sıralar.</span><span class="sxs-lookup"><span data-stu-id="b0bed-109">Enumerates through a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0bed-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0bed-110">Remarks</span></span>  
 <span data-ttu-id="b0bed-111">Her `CorDebugBlockingObject` yapı, bir iş parçacığını engelleyen bir nesneyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b0bed-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b0bed-112">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="b0bed-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0bed-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b0bed-113">Requirements</span></span>  
 <span data-ttu-id="b0bed-114">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0bed-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0bed-115">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b0bed-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0bed-116">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b0bed-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0bed-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0bed-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0bed-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0bed-118">See also</span></span>

- [<span data-ttu-id="b0bed-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b0bed-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b0bed-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="b0bed-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
