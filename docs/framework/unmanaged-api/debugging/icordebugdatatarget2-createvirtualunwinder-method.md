---
title: ICorDebugDataTarget2::CreateVirtualUnwinder Yöntemi
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
ms.openlocfilehash: 0967b1cda86eab35015279edeed9a6b9852036b6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713944"
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a><span data-ttu-id="3485b-102">ICorDebugDataTarget2::CreateVirtualUnwinder Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3485b-102">ICorDebugDataTarget2::CreateVirtualUnwinder Method</span></span>

<span data-ttu-id="3485b-103">Bir başlangıç bağlamından (bir iş parçacığının yaprağı olması gerekmez) geriye doğru geri sarıdan başlayan yeni bir Stack unwinder oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3485b-103">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3485b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3485b-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
## <a name="parameters"></a><span data-ttu-id="3485b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3485b-105">Parameters</span></span>  

 <span data-ttu-id="3485b-106">NativeThreadId</span><span class="sxs-lookup"><span data-stu-id="3485b-106">nativeThreadID</span></span>  
 <span data-ttu-id="3485b-107">'ndaki Yığını ölçeklendirme yapılacak iş parçacığının yerel iş parçacığı KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="3485b-107">[in] The native thread ID of the thread whose stack is to be unwound.</span></span>  
  
 <span data-ttu-id="3485b-108">contextFlags</span><span class="sxs-lookup"><span data-stu-id="3485b-108">contextFlags</span></span>  
 <span data-ttu-id="3485b-109">'ndaki İçeriğin hangi bölümlerinin tanımlandığını belirten bayraklar `initialContext` .</span><span class="sxs-lookup"><span data-stu-id="3485b-109">[in] Flags that specify which parts of the context are defined in `initialContext`.</span></span>  
  
 <span data-ttu-id="3485b-110">cbContext</span><span class="sxs-lookup"><span data-stu-id="3485b-110">cbContext</span></span>  
 <span data-ttu-id="3485b-111">'ndaki Boyutu `initialContext` .</span><span class="sxs-lookup"><span data-stu-id="3485b-111">[in] The size of `initialContext`.</span></span>  
  
 <span data-ttu-id="3485b-112">InitialContext</span><span class="sxs-lookup"><span data-stu-id="3485b-112">initialContext</span></span>  
 <span data-ttu-id="3485b-113">'ndaki Bağlamdaki veriler.</span><span class="sxs-lookup"><span data-stu-id="3485b-113">[in] The data in the context.</span></span>  
  
 <span data-ttu-id="3485b-114">ppUnwinder</span><span class="sxs-lookup"><span data-stu-id="3485b-114">ppUnwinder</span></span>  
 <span data-ttu-id="3485b-115">dışı Bir ICorDebugVirtualUnwinder Interface nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3485b-115">[out] A pointer to the address of an ICorDebugVirtualUnwinder interface object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3485b-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3485b-116">Return Value</span></span>  

 <span data-ttu-id="3485b-117">`S_OK` başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="3485b-117">`S_OK` if successful.</span></span> <span data-ttu-id="3485b-118">Diğer bir `HRESULT` hata olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3485b-118">Any other `HRESULT` indicates failure.</span></span> <span data-ttu-id="3485b-119">`HRESULT`Mscordbi tarafından alınan herhangi bir hata önemli kabul edilir ve [ICorDebug](icordebug-interface.md) yöntemlerinin döndürülmesine neden olur `CORDBG_E_DATA_TARGET_ERROR` .</span><span class="sxs-lookup"><span data-stu-id="3485b-119">Any failing `HRESULT` received by mscordbi is considered fatal and causes [ICorDebug](icordebug-interface.md) methods to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3485b-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3485b-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3485b-121">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3485b-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3485b-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3485b-122">Requirements</span></span>  

 <span data-ttu-id="3485b-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3485b-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3485b-124">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3485b-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3485b-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3485b-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3485b-126">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3485b-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3485b-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3485b-127">See also</span></span>

- [<span data-ttu-id="3485b-128">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3485b-128">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="3485b-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3485b-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
