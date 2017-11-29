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
ms.openlocfilehash: 3948a4c404036235767f8de6747966709b75bc4c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="1b31e-102">ICorDebugValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b31e-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="1b31e-103">2 GB'den daha büyük boyutlu diziler için destek sağlamak için "ICorDebugValue" ve "ICorDebugValue2" arabirimleri genişletir.</span><span class="sxs-lookup"><span data-stu-id="1b31e-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1b31e-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1b31e-104">Methods</span></span>  
  
|<span data-ttu-id="1b31e-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1b31e-105">Method</span></span>|<span data-ttu-id="1b31e-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b31e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1b31e-107">GetSize64 yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b31e-107">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)|<span data-ttu-id="1b31e-108">Bu bayt cinsinden boyutu alır `ICorDebugValue3` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="1b31e-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b31e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b31e-109">Remarks</span></span>  
 <span data-ttu-id="1b31e-110">[Icordebugvalue::getsize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) yöntemi 2.147.483.647 bayt 0'dan aralıkları bir nesne boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="1b31e-110">The [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="1b31e-111">İçinde [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], 2 GB diziler boyutunu aşabilir.</span><span class="sxs-lookup"><span data-stu-id="1b31e-111">In the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="1b31e-112">`ICorDebugValue3` Arabirimi bu diziler boyutunu belirlemek etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="1b31e-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b31e-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b31e-113">Requirements</span></span>  
 <span data-ttu-id="1b31e-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b31e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b31e-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b31e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b31e-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b31e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b31e-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b31e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b31e-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1b31e-118">See Also</span></span>  
    
    
 [<span data-ttu-id="1b31e-119">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1b31e-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="1b31e-120">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="1b31e-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
