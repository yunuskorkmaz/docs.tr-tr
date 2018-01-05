---
title: ICorDebugProcess8 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7ab1a70f-ec11-46ff-8869-cd8ca679cc51
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2985352cf8b209e98f749fbe40170e49014c9d9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess8-interface"></a><span data-ttu-id="b9bc2-102">ICorDebugProcess8 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b9bc2-102">ICorDebugProcess8 Interface</span></span>
<span data-ttu-id="b9bc2-103">[Desteklenen [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] ve sonraki sürümlerinde]</span><span class="sxs-lookup"><span data-stu-id="b9bc2-103">[Supported in the [!INCLUDE[net_v46](../../../../includes/net-v46-md.md)] and later versions]</span></span>  
  
 <span data-ttu-id="b9bc2-104">Mantıksal olarak etkinleştirme veya devre dışı belirli türlerdeki Icordebugprocess arabirimi genişletiyor [Icordebugmanagedcallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) özel durum geri aramalar.</span><span class="sxs-lookup"><span data-stu-id="b9bc2-104">Logically extends the ICorDebugProcess interface to enable or disable certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b9bc2-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b9bc2-105">Methods</span></span>  
  
|<span data-ttu-id="b9bc2-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b9bc2-106">Method</span></span>|<span data-ttu-id="b9bc2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b9bc2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b9bc2-108">EnableExceptionCallbacksOutsideOfMyCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b9bc2-108">EnableExceptionCallbacksOutsideOfMyCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-enableexceptioncallbacksoutsideofmycode-method.md)|<span data-ttu-id="b9bc2-109">Etkinleştirir ya da belirli türlerdeki devre dışı bırakır [Icordebugmanagedcallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) özel durum geri aramalar.</span><span class="sxs-lookup"><span data-stu-id="b9bc2-109">Enables or disables certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9bc2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b9bc2-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9bc2-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b9bc2-111">Requirements</span></span>  
 <span data-ttu-id="b9bc2-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9bc2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9bc2-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9bc2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9bc2-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9bc2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9bc2-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9bc2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9bc2-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b9bc2-116">See Also</span></span>  
 [<span data-ttu-id="b9bc2-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b9bc2-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b9bc2-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="b9bc2-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
