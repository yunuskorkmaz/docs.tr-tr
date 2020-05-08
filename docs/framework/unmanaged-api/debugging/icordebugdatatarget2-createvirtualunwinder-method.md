---
title: ICorDebugDataTarget2::CreateVirtualUnwinder Yöntemi
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
ms.openlocfilehash: 7a479fba9bbcf28c60474fffc6219af23e62c251
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976505"
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a><span data-ttu-id="2c895-102">ICorDebugDataTarget2::CreateVirtualUnwinder Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c895-102">ICorDebugDataTarget2::CreateVirtualUnwinder Method</span></span>
<span data-ttu-id="2c895-103">Bir başlangıç bağlamından (bir iş parçacığının yaprağı olması gerekmez) geriye doğru geri sarıdan başlayan yeni bir Stack unwinder oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2c895-103">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c895-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c895-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c895-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2c895-105">Parameters</span></span>  
 <span data-ttu-id="2c895-106">NativeThreadId</span><span class="sxs-lookup"><span data-stu-id="2c895-106">nativeThreadID</span></span>  
 <span data-ttu-id="2c895-107">'ndaki Yığını ölçeklendirme yapılacak iş parçacığının yerel iş parçacığı KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="2c895-107">[in] The native thread ID of the thread whose stack is to be unwound.</span></span>  
  
 <span data-ttu-id="2c895-108">contextFlags</span><span class="sxs-lookup"><span data-stu-id="2c895-108">contextFlags</span></span>  
 <span data-ttu-id="2c895-109">'ndaki İçeriğin hangi bölümlerinin tanımlandığını belirten bayraklar `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="2c895-109">[in] Flags that specify which parts of the context are defined in `initialContext`.</span></span>  
  
 <span data-ttu-id="2c895-110">cbContext</span><span class="sxs-lookup"><span data-stu-id="2c895-110">cbContext</span></span>  
 <span data-ttu-id="2c895-111">'ndaki Boyutu `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="2c895-111">[in] The size of `initialContext`.</span></span>  
  
 <span data-ttu-id="2c895-112">InitialContext</span><span class="sxs-lookup"><span data-stu-id="2c895-112">initialContext</span></span>  
 <span data-ttu-id="2c895-113">'ndaki Bağlamdaki veriler.</span><span class="sxs-lookup"><span data-stu-id="2c895-113">[in] The data in the context.</span></span>  
  
 <span data-ttu-id="2c895-114">ppUnwinder</span><span class="sxs-lookup"><span data-stu-id="2c895-114">ppUnwinder</span></span>  
 <span data-ttu-id="2c895-115">dışı Bir ICorDebugVirtualUnwinder Interface nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2c895-115">[out] A pointer to the address of an ICorDebugVirtualUnwinder interface object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c895-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2c895-116">Return Value</span></span>  
 <span data-ttu-id="2c895-117">`S_OK`başarılı olursa.</span><span class="sxs-lookup"><span data-stu-id="2c895-117">`S_OK` if successful.</span></span> <span data-ttu-id="2c895-118">Diğer `HRESULT` bir hata olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2c895-118">Any other `HRESULT` indicates failure.</span></span> <span data-ttu-id="2c895-119">Mscordbi tarafından alınan herhangi bir hata `HRESULT` önemli kabul edilir ve [ICorDebug](icordebug-interface.md) yöntemlerinin döndürülmesine `CORDBG_E_DATA_TARGET_ERROR`neden olur.</span><span class="sxs-lookup"><span data-stu-id="2c895-119">Any failing `HRESULT` received by mscordbi is considered fatal and causes [ICorDebug](icordebug-interface.md) methods to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c895-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2c895-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2c895-121">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2c895-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c895-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c895-122">Requirements</span></span>  
 <span data-ttu-id="2c895-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c895-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c895-124">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2c895-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c895-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2c895-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c895-126">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c895-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c895-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c895-127">See also</span></span>

- [<span data-ttu-id="2c895-128">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c895-128">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="2c895-129">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2c895-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
