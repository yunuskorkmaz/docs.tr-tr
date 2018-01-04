---
title: ICorDebugValue3 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue3
helpviewer_keywords: ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a470113dc54876937850294f6d99fc15a2cf98e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="42d2d-102">ICorDebugValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="42d2d-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="42d2d-103">2 GB'den daha büyük boyutlu diziler için destek sağlamak için "ICorDebugValue" ve "ICorDebugValue2" arabirimleri genişletir.</span><span class="sxs-lookup"><span data-stu-id="42d2d-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="42d2d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="42d2d-104">Methods</span></span>  
  
|<span data-ttu-id="42d2d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="42d2d-105">Method</span></span>|<span data-ttu-id="42d2d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42d2d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="42d2d-107">GetSize64 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="42d2d-107">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)|<span data-ttu-id="42d2d-108">Bu bayt cinsinden boyutu alır `ICorDebugValue3` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="42d2d-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42d2d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="42d2d-109">Remarks</span></span>  
 <span data-ttu-id="42d2d-110">[Icordebugvalue::getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) yöntemi 2.147.483.647 bayt 0'dan aralıkları bir nesne boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="42d2d-110">The [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="42d2d-111">İçinde [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], 2 GB diziler boyutunu aşabilir.</span><span class="sxs-lookup"><span data-stu-id="42d2d-111">In the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="42d2d-112">`ICorDebugValue3` Arabirimi bu diziler boyutunu belirlemek etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="42d2d-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42d2d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="42d2d-113">Requirements</span></span>  
 <span data-ttu-id="42d2d-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42d2d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42d2d-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42d2d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42d2d-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42d2d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42d2d-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42d2d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42d2d-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="42d2d-118">See Also</span></span>  
    
    
 [<span data-ttu-id="42d2d-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="42d2d-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="42d2d-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="42d2d-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
