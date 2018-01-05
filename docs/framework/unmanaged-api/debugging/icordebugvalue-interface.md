---
title: Icordebugvalue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue
helpviewer_keywords: ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c3464b4ad963b2fe764cefc5868440b7748f8c4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvalue-interface1"></a><span data-ttu-id="5c19c-102">Icordebugvalue Interface1</span><span class="sxs-lookup"><span data-stu-id="5c19c-102">ICorDebugValue Interface1</span></span>
<span data-ttu-id="5c19c-103">Ayıklanacak işlemindeki bir değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5c19c-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="5c19c-104">Değer bir okuma veya yazma değeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="5c19c-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5c19c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5c19c-105">Methods</span></span>  
  
|<span data-ttu-id="5c19c-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="5c19c-106">Method</span></span>|<span data-ttu-id="5c19c-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5c19c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5c19c-108">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c19c-108">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="5c19c-109">Bu metot şu anda uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="5c19c-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="5c19c-110">GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c19c-110">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|<span data-ttu-id="5c19c-111">Bu adresini alır `ICorDebugValue` hata ayıklaması sürecinde nesne.</span><span class="sxs-lookup"><span data-stu-id="5c19c-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="5c19c-112">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c19c-112">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|<span data-ttu-id="5c19c-113">Bu bayt cinsinden boyutu alır `ICorDebugValue` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="5c19c-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="5c19c-114">GetType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c19c-114">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|<span data-ttu-id="5c19c-115">Bu temel türünü alır `ICorDebugValue` nesnesi.</span><span class="sxs-lookup"><span data-stu-id="5c19c-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c19c-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c19c-116">Remarks</span></span>  
 <span data-ttu-id="5c19c-117">Genel olarak, bu döndürüldüğünde bir değer nesnesi sahipliğini geçirilir.</span><span class="sxs-lookup"><span data-stu-id="5c19c-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="5c19c-118">Alıcı nesnesiyle tamamlandığında, bir başvuru nesneden kaldırmak için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="5c19c-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="5c19c-119">İşlem çıktıktan sonra değeri gelen alındığı bağlı olarak, değeri geçerli sürdürülemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="5c19c-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="5c19c-120">Bu nedenle, genel olarak, değerin bir çağrıyla tutulması döndürmemelidir [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5c19c-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c19c-121">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="5c19c-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c19c-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c19c-122">Requirements</span></span>  
 <span data-ttu-id="5c19c-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c19c-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c19c-124">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c19c-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c19c-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c19c-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c19c-126">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c19c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c19c-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5c19c-127">See Also</span></span>  
    
    
    
    
 [<span data-ttu-id="5c19c-128">ICorDebugValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c19c-128">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 [<span data-ttu-id="5c19c-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5c19c-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
