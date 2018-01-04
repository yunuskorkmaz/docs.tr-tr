---
title: "ICorDebugDataTarget2::CreateVirtualUnwinder Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bffbf95fc38cba6f311e0641b35e2696bd34099
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a><span data-ttu-id="9e2be-102">ICorDebugDataTarget2::CreateVirtualUnwinder Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9e2be-102">ICorDebugDataTarget2::CreateVirtualUnwinder Method</span></span>
<span data-ttu-id="9e2be-103">Geriye doğru izleme (hangi mutlaka bir iş parçacığı yaprak olmayan) bir ilk bağlamından başlayan yeni bir yığın unwinder oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9e2be-103">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e2be-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e2be-104">Syntax</span></span>  
  
```  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e2be-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9e2be-105">Parameters</span></span>  
 <span data-ttu-id="9e2be-106">nativeThreadID</span><span class="sxs-lookup"><span data-stu-id="9e2be-106">nativeThreadID</span></span>  
 <span data-ttu-id="9e2be-107">[in] Yığın olduğu olması için iş parçacığı yerel iş parçacığı kimliği unwound.</span><span class="sxs-lookup"><span data-stu-id="9e2be-107">[in] The native thread ID of the thread whose stack is to be unwound.</span></span>  
  
 <span data-ttu-id="9e2be-108">contextFlags</span><span class="sxs-lookup"><span data-stu-id="9e2be-108">contextFlags</span></span>  
 <span data-ttu-id="9e2be-109">[in] Bağlam hangi kısımlarının tanımlanan belirtin bayrakları `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="9e2be-109">[in] Flags that specify which parts of the context are defined in `initialContext`.</span></span>  
  
 <span data-ttu-id="9e2be-110">cbContext</span><span class="sxs-lookup"><span data-stu-id="9e2be-110">cbContext</span></span>  
 <span data-ttu-id="9e2be-111">[in] Boyutunu `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="9e2be-111">[in] The size of `initialContext`.</span></span>  
  
 <span data-ttu-id="9e2be-112">initialContext</span><span class="sxs-lookup"><span data-stu-id="9e2be-112">initialContext</span></span>  
 <span data-ttu-id="9e2be-113">[in] Bağlam verileri.</span><span class="sxs-lookup"><span data-stu-id="9e2be-113">[in] The data in the context.</span></span>  
  
 <span data-ttu-id="9e2be-114">ppUnwinder</span><span class="sxs-lookup"><span data-stu-id="9e2be-114">ppUnwinder</span></span>  
 <span data-ttu-id="9e2be-115">[out] Icordebugvirtualunwinder arabirimi nesnenin adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9e2be-115">[out] A pointer to the address of an ICorDebugVirtualUnwinder interface object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e2be-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9e2be-116">Return Value</span></span>  
 <span data-ttu-id="9e2be-117">`S_OK`başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="9e2be-117">`S_OK` if successful.</span></span> <span data-ttu-id="9e2be-118">Diğer `HRESULT` başarısız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e2be-118">Any other `HRESULT` indicates failure.</span></span> <span data-ttu-id="9e2be-119">Tüm başarısız `HRESULT` mscordbi tarafından alınan önemli kabul edilir ve neden [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) dönmek için yöntemleri `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="9e2be-119">Any failing `HRESULT` received by mscordbi is considered fatal and causes [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e2be-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e2be-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e2be-121">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9e2be-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e2be-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9e2be-122">Requirements</span></span>  
 <span data-ttu-id="9e2be-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e2be-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e2be-124">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e2be-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e2be-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e2be-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e2be-126">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e2be-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e2be-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e2be-127">See Also</span></span>  
 [<span data-ttu-id="9e2be-128">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e2be-128">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="9e2be-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9e2be-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
