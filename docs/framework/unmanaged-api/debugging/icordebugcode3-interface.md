---
title: ICorDebugCode3 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode3
helpviewer_keywords: ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ee60d052c65df64b1a753166b301ba0012cdc8e4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="15403-102">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="15403-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="15403-103">Yönetilen bir dönüş değeri hakkında bilgi sağlamak için "ICorDebugCode" ve "ICorDebugCode2" genişleten bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="15403-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="15403-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="15403-104">Methods</span></span>  
  
|<span data-ttu-id="15403-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="15403-105">Method</span></span>|<span data-ttu-id="15403-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15403-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="15403-107">GetReturnValueLiveOffset yöntemi</span><span class="sxs-lookup"><span data-stu-id="15403-107">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="15403-108">Belirtilen bir IL uzaklığı, hata ayıklayıcı dönüş değeri bir işleve alabilmesi adına, bir kesme noktası nereye yerleştirileceğini yerel uzaklıkları alır.</span><span class="sxs-lookup"><span data-stu-id="15403-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15403-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15403-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15403-110">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="15403-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15403-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15403-111">Requirements</span></span>  
 <span data-ttu-id="15403-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15403-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15403-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="15403-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="15403-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15403-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15403-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15403-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15403-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="15403-116">See Also</span></span>  
    
    
    
 [<span data-ttu-id="15403-117">Icordebugılframe3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="15403-117">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 [<span data-ttu-id="15403-118">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="15403-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
