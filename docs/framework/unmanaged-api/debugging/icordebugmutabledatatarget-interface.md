---
title: ICorDebugMutableDataTarget arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ef1c0b7a56f6bd1f7e87650b72dfe8b1411ef7f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmutabledatatarget-interface"></a><span data-ttu-id="7a70f-102">ICorDebugMutableDataTarget arabirimi</span><span class="sxs-lookup"><span data-stu-id="7a70f-102">ICorDebugMutableDataTarget Interface</span></span>
<span data-ttu-id="7a70f-103">Genişletir [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) değişebilir veri hedefleri desteklemek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="7a70f-103">Extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7a70f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7a70f-104">Methods</span></span>  
  
|<span data-ttu-id="7a70f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7a70f-105">Method</span></span>|<span data-ttu-id="7a70f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7a70f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7a70f-107">ContinueStatusChanged yöntemi</span><span class="sxs-lookup"><span data-stu-id="7a70f-107">ContinueStatusChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|<span data-ttu-id="7a70f-108">Belirtilen iş parçacığı üzerinde bekleyen hata ayıklama olayı devamlılık durumunu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="7a70f-108">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>|  
|[<span data-ttu-id="7a70f-109">SetThreadContext yöntemi</span><span class="sxs-lookup"><span data-stu-id="7a70f-109">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|<span data-ttu-id="7a70f-110">Bir iş parçacığı bağlamının (kayıt değerlerini) ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7a70f-110">Sets the context (register values) for a thread.</span></span>|  
|[<span data-ttu-id="7a70f-111">WriteVirtual yöntemi</span><span class="sxs-lookup"><span data-stu-id="7a70f-111">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|<span data-ttu-id="7a70f-112">Bellek, hedef işlem adres alanı yazar.</span><span class="sxs-lookup"><span data-stu-id="7a70f-112">Writes memory into the target process address space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a70f-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7a70f-113">Remarks</span></span>  
 <span data-ttu-id="7a70f-114">Bu uzantı [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) arabirimi hata ayıklama (örneğin, Canlı bozucu hata ayıklama gerçekleştirmek için) hedef işlem değiştirmek istediğiniz araçları tarafından uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="7a70f-114">This extension to the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface can be implemented by debugging tools that wish to modify the target process (for example, to perform live invasive debugging).</span></span>  
  
 <span data-ttu-id="7a70f-115">Bu yöntemlerin tümü, bir çekirdek denetleme tabanlı hata ayıklama işlev bu arabirimini uygulayan değil veya bu yöntemlere çağrılar başarısız kayıp olduğunu herkese açık isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7a70f-115">All of these methods are optional in the sense that no core inspection-based debugging functionality is lost by not implementing this interface or by the failure of calls to these methods.</span></span>  <span data-ttu-id="7a70f-116">Herhangi bir hata `HRESULT` bu yöntemleri olarak kullanıma yayılır `HRESULT` Icordebug yöntemi çağrısından.</span><span class="sxs-lookup"><span data-stu-id="7a70f-116">Any failure `HRESULT` from these methods will propagate out as the `HRESULT` from the ICorDebug method call.</span></span>  
  
 <span data-ttu-id="7a70f-117">Tek bir Icordebug yöntemi çağrısı içinde birden çok mutations neden olabilir ve mutations işlemsel olarak uygulanır ilgili hiçbir mekanizması sağlamaya yönelik olduğunu unutmayın (tümü veya hiçbiri işlemini).</span><span class="sxs-lookup"><span data-stu-id="7a70f-117">Note that a single ICorDebug method call may result in multiple mutations, and that there is no mechanism for ensuring related mutations are applied transactionally (all-or-none).</span></span>  <span data-ttu-id="7a70f-118">Bunun anlamı başkalarının (aynı Icordebug çağrısı) başarıyla tamamlandıktan sonra bir mutation başarısız olursa, hedef işlem tutarsız bir durumda kalabilir ve hata ayıklama güvenilir olmayan bir duruma gelebilir.</span><span class="sxs-lookup"><span data-stu-id="7a70f-118">This means that if a mutation fails after others (for the same ICorDebug call) have succeeded, the target process may be left in an inconsistent state and debugging may become unreliable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a70f-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7a70f-119">Requirements</span></span>  
 <span data-ttu-id="7a70f-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a70f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a70f-121">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a70f-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a70f-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a70f-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a70f-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a70f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a70f-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7a70f-124">See Also</span></span>  
 [<span data-ttu-id="7a70f-125">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7a70f-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="7a70f-126">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="7a70f-126">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
