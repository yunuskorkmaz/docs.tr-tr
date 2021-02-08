---
description: ': Icordebugmutabledatatarget arabirimi hakkında daha fazla bilgi edinin'
title: ICorDebugMutableDataTarget Arabirimi
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
ms.openlocfilehash: 387c5317bea015459e306994c36761571b427628
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790704"
---
# <a name="icordebugmutabledatatarget-interface"></a><span data-ttu-id="cfae8-103">ICorDebugMutableDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cfae8-103">ICorDebugMutableDataTarget Interface</span></span>

<span data-ttu-id="cfae8-104">[ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimini, değişebilir veri hedeflerini destekleyecek şekilde genişletir.</span><span class="sxs-lookup"><span data-stu-id="cfae8-104">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cfae8-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cfae8-105">Methods</span></span>  
  
|<span data-ttu-id="cfae8-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="cfae8-106">Method</span></span>|<span data-ttu-id="cfae8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cfae8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cfae8-108">ContinueStatusChanged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cfae8-108">ContinueStatusChanged Method</span></span>](icordebugmutabledatatarget-continuestatuschanged-method.md)|<span data-ttu-id="cfae8-109">Belirtilen iş parçacığında bekleyen hata ayıklama olayının devamlılık durumunu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="cfae8-109">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>|  
|[<span data-ttu-id="cfae8-110">SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cfae8-110">SetThreadContext Method</span></span>](icordebugmutabledatatarget-setthreadcontext-method.md)|<span data-ttu-id="cfae8-111">Bir iş parçacığının bağlamını (kayıt değerlerini) ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cfae8-111">Sets the context (register values) for a thread.</span></span>|  
|[<span data-ttu-id="cfae8-112">WriteVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cfae8-112">WriteVirtual Method</span></span>](icordebugmutabledatatarget-writevirtual-method.md)|<span data-ttu-id="cfae8-113">Belleği hedef işlem adres alanına yazar.</span><span class="sxs-lookup"><span data-stu-id="cfae8-113">Writes memory into the target process address space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfae8-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cfae8-114">Remarks</span></span>  

 <span data-ttu-id="cfae8-115">[ICorDebugDataTarget](icordebugdatatarget-interface.md) arabirimine olan bu uzantı, hedef işlemi değiştirmek isteyen hata ayıklama araçlarıyla (örneğin, canlı bir hata ayıklama işlemi gerçekleştirmek için) uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="cfae8-115">This extension to the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface can be implemented by debugging tools that wish to modify the target process (for example, to perform live invasive debugging).</span></span>  
  
 <span data-ttu-id="cfae8-116">Bu yöntemlerin hepsi, bu arabirimi uygulamayarak veya bu yöntemlere yapılan çağrılar başarısız olmadan hiçbir çekirdek İnceleme tabanlı hata ayıklama işlevinin kaybedilmediğinden emin olmak için isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="cfae8-116">All of these methods are optional in the sense that no core inspection-based debugging functionality is lost by not implementing this interface or by the failure of calls to these methods.</span></span>  <span data-ttu-id="cfae8-117">Bu yöntemlerden herhangi bir hata `HRESULT` , `HRESULT` ICorDebug yöntem çağrısından olarak yayılır.</span><span class="sxs-lookup"><span data-stu-id="cfae8-117">Any failure `HRESULT` from these methods will propagate out as the `HRESULT` from the ICorDebug method call.</span></span>  
  
 <span data-ttu-id="cfae8-118">Tek bir ICorDebug yöntemi çağrısının birden çok mutasyonda neden olabileceğini ve ilgili mutasyonların işlem için (tümü-veya-hiçbiri) uygulanmasını sağlamak için hiçbir mekanizma olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="cfae8-118">Note that a single ICorDebug method call may result in multiple mutations, and that there is no mechanism for ensuring related mutations are applied transactionally (all-or-none).</span></span>  <span data-ttu-id="cfae8-119">Bu, diğerleri (aynı ICorDebug çağrısı için) başarılı olduktan sonra başarısız olursa, hedef işlem tutarsız bir durumda kalabilir ve hata ayıklama güvenilir hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="cfae8-119">This means that if a mutation fails after others (for the same ICorDebug call) have succeeded, the target process may be left in an inconsistent state and debugging may become unreliable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfae8-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cfae8-120">Requirements</span></span>  

 <span data-ttu-id="cfae8-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfae8-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfae8-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cfae8-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cfae8-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cfae8-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfae8-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfae8-124">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfae8-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfae8-125">See also</span></span>

- [<span data-ttu-id="cfae8-126">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cfae8-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="cfae8-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="cfae8-127">Debugging</span></span>](index.md)
