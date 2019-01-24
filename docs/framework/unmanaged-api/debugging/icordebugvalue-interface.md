---
title: Icordebugvalue arabirimi1
ms.date: 03/30/2017
api_name:
- ICorDebugValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue
helpviewer_keywords:
- ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41afc2e4305034340ad408e52ce08372bf8962dd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54507453"
---
# <a name="icordebugvalue-interface1"></a><span data-ttu-id="8fb29-102">Icordebugvalue arabirimi1</span><span class="sxs-lookup"><span data-stu-id="8fb29-102">ICorDebugValue Interface1</span></span>
<span data-ttu-id="8fb29-103">Hatası ayıklanmakta olan işlemindeki bir değeri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8fb29-103">Represents a value in the process being debugged.</span></span> <span data-ttu-id="8fb29-104">Değer, bir okuma veya yazma değeri olabilir.</span><span class="sxs-lookup"><span data-stu-id="8fb29-104">The value can be a read or a write value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8fb29-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8fb29-105">Methods</span></span>  
  
|<span data-ttu-id="8fb29-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8fb29-106">Method</span></span>|<span data-ttu-id="8fb29-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8fb29-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8fb29-108">CreateBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8fb29-108">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|<span data-ttu-id="8fb29-109">Bu yöntem henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="8fb29-109">This method is not currently implemented.</span></span>|  
|[<span data-ttu-id="8fb29-110">GetAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8fb29-110">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|<span data-ttu-id="8fb29-111">Bu adresini alır `ICorDebugValue` ayıklanan sürecinde olan nesne.</span><span class="sxs-lookup"><span data-stu-id="8fb29-111">Gets the address of this `ICorDebugValue` object, which is in the process of being debugged.</span></span>|  
|[<span data-ttu-id="8fb29-112">GetSize Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8fb29-112">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|<span data-ttu-id="8fb29-113">Bu bayt cinsinden boyutunu alır `ICorDebugValue` nesne.</span><span class="sxs-lookup"><span data-stu-id="8fb29-113">Gets the size, in bytes, of this `ICorDebugValue` object.</span></span>|  
|[<span data-ttu-id="8fb29-114">GetType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8fb29-114">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|<span data-ttu-id="8fb29-115">Bu temel türünü alır `ICorDebugValue` nesne.</span><span class="sxs-lookup"><span data-stu-id="8fb29-115">Gets the primitive type of this `ICorDebugValue` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8fb29-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8fb29-116">Remarks</span></span>  
 <span data-ttu-id="8fb29-117">Genel olarak, bu iade edildiğinde bir değer nesnesini sahipliğini geçirilir.</span><span class="sxs-lookup"><span data-stu-id="8fb29-117">In general, ownership of a value object is passed when it is returned.</span></span> <span data-ttu-id="8fb29-118">Alıcı, nesneyle tamamlandığında, bir başvuru nesneden kaldırmak için sorumludur.</span><span class="sxs-lookup"><span data-stu-id="8fb29-118">The recipient is responsible for removing a reference from the object when it is finished with the object.</span></span>  
  
 <span data-ttu-id="8fb29-119">İşlem çıktıktan sonra nerede değeri öğesinden alınan bağlı olarak, değeri geçerli sürdürülemeyebilir.</span><span class="sxs-lookup"><span data-stu-id="8fb29-119">Depending on where the value was retrieved from, the value may not remain valid after the process is resumed.</span></span> <span data-ttu-id="8fb29-120">Bu nedenle, genel olarak, değerin bir çağrıyla tutulması olmamalıdır [Icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8fb29-120">So, in general, the value shouldn't be held across a call of the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8fb29-121">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8fb29-121">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fb29-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8fb29-122">Requirements</span></span>  
 <span data-ttu-id="8fb29-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fb29-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fb29-124">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8fb29-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8fb29-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8fb29-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8fb29-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fb29-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fb29-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fb29-127">See also</span></span>




- [<span data-ttu-id="8fb29-128">ICorDebugValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8fb29-128">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [<span data-ttu-id="8fb29-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8fb29-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
