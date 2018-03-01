---
title: ICorDebugILFrame3 Arabirimi
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
- ICorDebugILFrame3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 15212cb5-93d4-4025-bec9-d4b9919eb1fe
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1096942775dd579fa530415873694b3e6e67a74a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="8db53-102">ICorDebugILFrame3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8db53-102">ICorDebugILFrame3 Interface</span></span>
<span data-ttu-id="8db53-103">İşlevin dönüş değerini içeren bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="8db53-103">Provides a method that encapsulates the return value of a function.</span></span> <span data-ttu-id="8db53-104">`ICorDebugILFrame3`Icordebugılframe ve Icordebugılframe2 arabirimlerinin mantıksal bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="8db53-104">`ICorDebugILFrame3` is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8db53-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8db53-105">Methods</span></span>  
  
|<span data-ttu-id="8db53-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8db53-106">Method</span></span>|<span data-ttu-id="8db53-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8db53-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8db53-108">GetReturnValueForILOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8db53-108">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="8db53-109">Bir işlevin dönüş değeri yalıtan bir Icordebugvalue nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="8db53-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8db53-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8db53-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8db53-111">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8db53-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8db53-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8db53-112">Requirements</span></span>  
 <span data-ttu-id="8db53-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8db53-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8db53-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8db53-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8db53-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8db53-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8db53-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8db53-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8db53-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8db53-117">See Also</span></span>  
 [<span data-ttu-id="8db53-118">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8db53-118">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [<span data-ttu-id="8db53-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8db53-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
