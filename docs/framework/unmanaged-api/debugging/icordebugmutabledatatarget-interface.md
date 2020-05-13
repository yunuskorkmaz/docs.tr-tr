---
title: ICorDebugMutableDataTarget Arabirimi
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
ms.openlocfilehash: fcf7521f8261c8f8f84c7a9a9deb4b7a7d739c6e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210013"
---
# <a name="icordebugmutabledatatarget-interface"></a><span data-ttu-id="c7886-102">ICorDebugMutableDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7886-102">ICorDebugMutableDataTarget Interface</span></span>
<span data-ttu-id="c7886-103">[ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimini, değişebilir veri hedeflerini destekleyecek şekilde genişletir.</span><span class="sxs-lookup"><span data-stu-id="c7886-103">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c7886-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c7886-104">Methods</span></span>  
  
|<span data-ttu-id="c7886-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c7886-105">Method</span></span>|<span data-ttu-id="c7886-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7886-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c7886-107">ContinueStatusChanged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c7886-107">ContinueStatusChanged Method</span></span>](icordebugmutabledatatarget-continuestatuschanged-method.md)|<span data-ttu-id="c7886-108">Belirtilen iş parçacığında bekleyen hata ayıklama olayının devamlılık durumunu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="c7886-108">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>|  
|[<span data-ttu-id="c7886-109">SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c7886-109">SetThreadContext Method</span></span>](icordebugmutabledatatarget-setthreadcontext-method.md)|<span data-ttu-id="c7886-110">Bir iş parçacığının bağlamını (kayıt değerlerini) ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c7886-110">Sets the context (register values) for a thread.</span></span>|  
|[<span data-ttu-id="c7886-111">WriteVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c7886-111">WriteVirtual Method</span></span>](icordebugmutabledatatarget-writevirtual-method.md)|<span data-ttu-id="c7886-112">Belleği hedef işlem adres alanına yazar.</span><span class="sxs-lookup"><span data-stu-id="c7886-112">Writes memory into the target process address space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7886-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7886-113">Remarks</span></span>  
 <span data-ttu-id="c7886-114">[ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimine olan bu uzantı, hedef işlemi değiştirmek isteyen hata ayıklama araçlarıyla (örneğin, canlı bir hata ayıklama işlemi gerçekleştirmek için) uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="c7886-114">This extension to the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface can be implemented by debugging tools that wish to modify the target process (for example, to perform live invasive debugging).</span></span>  
  
 <span data-ttu-id="c7886-115">Bu yöntemlerin hepsi, bu arabirimi uygulamayarak veya bu yöntemlere yapılan çağrılar başarısız olmadan hiçbir çekirdek İnceleme tabanlı hata ayıklama işlevinin kaybedilmediğinden emin olmak için isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c7886-115">All of these methods are optional in the sense that no core inspection-based debugging functionality is lost by not implementing this interface or by the failure of calls to these methods.</span></span>  <span data-ttu-id="c7886-116">Bu yöntemlerden herhangi bir hata `HRESULT` , `HRESULT` ICorDebug yöntem çağrısından olarak yayılır.</span><span class="sxs-lookup"><span data-stu-id="c7886-116">Any failure `HRESULT` from these methods will propagate out as the `HRESULT` from the ICorDebug method call.</span></span>  
  
 <span data-ttu-id="c7886-117">Tek bir ICorDebug yöntemi çağrısının birden çok mutasyonda neden olabileceğini ve ilgili mutasyonların işlem için (tümü-veya-hiçbiri) uygulanmasını sağlamak için hiçbir mekanizma olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c7886-117">Note that a single ICorDebug method call may result in multiple mutations, and that there is no mechanism for ensuring related mutations are applied transactionally (all-or-none).</span></span>  <span data-ttu-id="c7886-118">Bu, diğerleri (aynı ICorDebug çağrısı için) başarılı olduktan sonra başarısız olursa, hedef işlem tutarsız bir durumda kalabilir ve hata ayıklama güvenilir hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="c7886-118">This means that if a mutation fails after others (for the same ICorDebug call) have succeeded, the target process may be left in an inconsistent state and debugging may become unreliable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7886-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7886-119">Requirements</span></span>  
 <span data-ttu-id="c7886-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7886-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7886-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c7886-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7886-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c7886-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7886-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7886-123">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7886-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7886-124">See also</span></span>

- [<span data-ttu-id="c7886-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c7886-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c7886-126">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c7886-126">Debugging</span></span>](index.md)
