---
title: ICorDebugDataTarget2::CreateVirtualUnwinder Yöntemi
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3782686f3caad6859aa81957f10e585265be340
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585491"
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a><span data-ttu-id="b4a46-102">ICorDebugDataTarget2::CreateVirtualUnwinder Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b4a46-102">ICorDebugDataTarget2::CreateVirtualUnwinder Method</span></span>
<span data-ttu-id="b4a46-103">(Bu mutlaka bir iş parçacığının yaprak olmayan) bir ilk bağlamından geriye doğru izleme başlayan yeni bir yığın unwinder oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b4a46-103">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4a46-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b4a46-104">Syntax</span></span>  
  
```  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4a46-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b4a46-105">Parameters</span></span>  
 <span data-ttu-id="b4a46-106">nativeThreadID</span><span class="sxs-lookup"><span data-stu-id="b4a46-106">nativeThreadID</span></span>  
 <span data-ttu-id="b4a46-107">[in] Yerel iş parçacığı kimliği olan yığınıdır olacak şekilde iş parçacığının geriye doğru.</span><span class="sxs-lookup"><span data-stu-id="b4a46-107">[in] The native thread ID of the thread whose stack is to be unwound.</span></span>  
  
 <span data-ttu-id="b4a46-108">contextFlags</span><span class="sxs-lookup"><span data-stu-id="b4a46-108">contextFlags</span></span>  
 <span data-ttu-id="b4a46-109">[in] Hangi parçalarının bağlam içinde tanımlanan belirten bayrakları `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="b4a46-109">[in] Flags that specify which parts of the context are defined in `initialContext`.</span></span>  
  
 <span data-ttu-id="b4a46-110">cbContext</span><span class="sxs-lookup"><span data-stu-id="b4a46-110">cbContext</span></span>  
 <span data-ttu-id="b4a46-111">[in] Boyutu `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="b4a46-111">[in] The size of `initialContext`.</span></span>  
  
 <span data-ttu-id="b4a46-112">initialContext</span><span class="sxs-lookup"><span data-stu-id="b4a46-112">initialContext</span></span>  
 <span data-ttu-id="b4a46-113">[in] Bağlam verileri.</span><span class="sxs-lookup"><span data-stu-id="b4a46-113">[in] The data in the context.</span></span>  
  
 <span data-ttu-id="b4a46-114">ppUnwinder</span><span class="sxs-lookup"><span data-stu-id="b4a46-114">ppUnwinder</span></span>  
 <span data-ttu-id="b4a46-115">[out] Icordebugvirtualunwinder arabirimi nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b4a46-115">[out] A pointer to the address of an ICorDebugVirtualUnwinder interface object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4a46-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b4a46-116">Return Value</span></span>  
 <span data-ttu-id="b4a46-117">`S_OK` başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="b4a46-117">`S_OK` if successful.</span></span> <span data-ttu-id="b4a46-118">Diğer `HRESULT` başarısız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b4a46-118">Any other `HRESULT` indicates failure.</span></span> <span data-ttu-id="b4a46-119">Tüm başarısız `HRESULT` mscordbi tarafından alınan önemli kabul edilir ve neden [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) döndürülecek yöntemleri `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="b4a46-119">Any failing `HRESULT` received by mscordbi is considered fatal and causes [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4a46-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b4a46-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4a46-121">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b4a46-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4a46-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b4a46-122">Requirements</span></span>  
 <span data-ttu-id="b4a46-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4a46-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4a46-124">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4a46-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4a46-125">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4a46-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4a46-126">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4a46-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4a46-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4a46-127">See also</span></span>
- [<span data-ttu-id="b4a46-128">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b4a46-128">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="b4a46-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b4a46-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
