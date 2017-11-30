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
ms.openlocfilehash: 421cff28e84106c0859889e6f9e99e870b469a98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a><span data-ttu-id="3da01-102">ICorDebugDataTarget2::CreateVirtualUnwinder Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3da01-102">ICorDebugDataTarget2::CreateVirtualUnwinder Method</span></span>
<span data-ttu-id="3da01-103">Geriye doğru izleme (hangi mutlaka bir iş parçacığı yaprak olmayan) bir ilk bağlamından başlayan yeni bir yığın unwinder oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3da01-103">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3da01-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3da01-104">Syntax</span></span>  
  
```  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3da01-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3da01-105">Parameters</span></span>  
 <span data-ttu-id="3da01-106">nativeThreadID</span><span class="sxs-lookup"><span data-stu-id="3da01-106">nativeThreadID</span></span>  
 <span data-ttu-id="3da01-107">[in] Yığın olduğu olması için iş parçacığı yerel iş parçacığı kimliği unwound.</span><span class="sxs-lookup"><span data-stu-id="3da01-107">[in] The native thread ID of the thread whose stack is to be unwound.</span></span>  
  
 <span data-ttu-id="3da01-108">contextFlags</span><span class="sxs-lookup"><span data-stu-id="3da01-108">contextFlags</span></span>  
 <span data-ttu-id="3da01-109">[in] Bağlam hangi kısımlarının tanımlanan belirtin bayrakları `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="3da01-109">[in] Flags that specify which parts of the context are defined in `initialContext`.</span></span>  
  
 <span data-ttu-id="3da01-110">cbContext</span><span class="sxs-lookup"><span data-stu-id="3da01-110">cbContext</span></span>  
 <span data-ttu-id="3da01-111">[in] Boyutunu `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="3da01-111">[in] The size of `initialContext`.</span></span>  
  
 <span data-ttu-id="3da01-112">initialContext</span><span class="sxs-lookup"><span data-stu-id="3da01-112">initialContext</span></span>  
 <span data-ttu-id="3da01-113">[in] Bağlam verileri.</span><span class="sxs-lookup"><span data-stu-id="3da01-113">[in] The data in the context.</span></span>  
  
 <span data-ttu-id="3da01-114">ppUnwinder</span><span class="sxs-lookup"><span data-stu-id="3da01-114">ppUnwinder</span></span>  
 <span data-ttu-id="3da01-115">[out] Icordebugvirtualunwinder arabirimi nesnenin adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3da01-115">[out] A pointer to the address of an ICorDebugVirtualUnwinder interface object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3da01-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3da01-116">Return Value</span></span>  
 <span data-ttu-id="3da01-117">`S_OK`başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="3da01-117">`S_OK` if successful.</span></span> <span data-ttu-id="3da01-118">Diğer `HRESULT` başarısız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3da01-118">Any other `HRESULT` indicates failure.</span></span> <span data-ttu-id="3da01-119">Tüm başarısız `HRESULT` mscordbi tarafından alınan önemli kabul edilir ve neden [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) dönmek için yöntemleri `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="3da01-119">Any failing `HRESULT` received by mscordbi is considered fatal and causes [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3da01-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3da01-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3da01-121">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3da01-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3da01-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3da01-122">Requirements</span></span>  
 <span data-ttu-id="3da01-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3da01-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3da01-124">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3da01-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3da01-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3da01-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3da01-126">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3da01-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3da01-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3da01-127">See Also</span></span>  
 [<span data-ttu-id="3da01-128">Icordebugdatatarget2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="3da01-128">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="3da01-129">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3da01-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
