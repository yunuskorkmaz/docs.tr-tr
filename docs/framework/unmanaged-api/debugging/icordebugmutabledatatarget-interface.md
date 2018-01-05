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
ms.workload: dotnet
ms.openlocfilehash: e638b01b30f7969ac3116c6c2725fb4cb3768a68
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmutabledatatarget-interface"></a><span data-ttu-id="25e16-102">ICorDebugMutableDataTarget arabirimi</span><span class="sxs-lookup"><span data-stu-id="25e16-102">ICorDebugMutableDataTarget Interface</span></span>
<span data-ttu-id="25e16-103">Genişletir [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) değişebilir veri hedefleri desteklemek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="25e16-103">Extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="25e16-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="25e16-104">Methods</span></span>  
  
|<span data-ttu-id="25e16-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="25e16-105">Method</span></span>|<span data-ttu-id="25e16-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="25e16-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="25e16-107">ContinueStatusChanged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25e16-107">ContinueStatusChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|<span data-ttu-id="25e16-108">Belirtilen iş parçacığı üzerinde bekleyen hata ayıklama olayı devamlılık durumunu değiştirir.</span><span class="sxs-lookup"><span data-stu-id="25e16-108">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>|  
|[<span data-ttu-id="25e16-109">SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25e16-109">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|<span data-ttu-id="25e16-110">Bir iş parçacığı bağlamının (kayıt değerlerini) ayarlar.</span><span class="sxs-lookup"><span data-stu-id="25e16-110">Sets the context (register values) for a thread.</span></span>|  
|[<span data-ttu-id="25e16-111">WriteVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25e16-111">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|<span data-ttu-id="25e16-112">Bellek, hedef işlem adres alanı yazar.</span><span class="sxs-lookup"><span data-stu-id="25e16-112">Writes memory into the target process address space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25e16-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="25e16-113">Remarks</span></span>  
 <span data-ttu-id="25e16-114">Bu uzantı [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) arabirimi hata ayıklama (örneğin, Canlı bozucu hata ayıklama gerçekleştirmek için) hedef işlem değiştirmek istediğiniz araçları tarafından uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="25e16-114">This extension to the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface can be implemented by debugging tools that wish to modify the target process (for example, to perform live invasive debugging).</span></span>  
  
 <span data-ttu-id="25e16-115">Bu yöntemlerin tümü, bir çekirdek denetleme tabanlı hata ayıklama işlev bu arabirimini uygulayan değil veya bu yöntemlere çağrılar başarısız kayıp olduğunu herkese açık isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="25e16-115">All of these methods are optional in the sense that no core inspection-based debugging functionality is lost by not implementing this interface or by the failure of calls to these methods.</span></span>  <span data-ttu-id="25e16-116">Herhangi bir hata `HRESULT` bu yöntemleri olarak kullanıma yayılır `HRESULT` Icordebug yöntemi çağrısından.</span><span class="sxs-lookup"><span data-stu-id="25e16-116">Any failure `HRESULT` from these methods will propagate out as the `HRESULT` from the ICorDebug method call.</span></span>  
  
 <span data-ttu-id="25e16-117">Tek bir Icordebug yöntemi çağrısı içinde birden çok mutations neden olabilir ve mutations işlemsel olarak uygulanır ilgili hiçbir mekanizması sağlamaya yönelik olduğunu unutmayın (tümü veya hiçbiri işlemini).</span><span class="sxs-lookup"><span data-stu-id="25e16-117">Note that a single ICorDebug method call may result in multiple mutations, and that there is no mechanism for ensuring related mutations are applied transactionally (all-or-none).</span></span>  <span data-ttu-id="25e16-118">Bunun anlamı başkalarının (aynı Icordebug çağrısı) başarıyla tamamlandıktan sonra bir mutation başarısız olursa, hedef işlem tutarsız bir durumda kalabilir ve hata ayıklama güvenilir olmayan bir duruma gelebilir.</span><span class="sxs-lookup"><span data-stu-id="25e16-118">This means that if a mutation fails after others (for the same ICorDebug call) have succeeded, the target process may be left in an inconsistent state and debugging may become unreliable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25e16-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="25e16-119">Requirements</span></span>  
 <span data-ttu-id="25e16-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25e16-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25e16-121">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="25e16-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25e16-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25e16-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25e16-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25e16-123">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25e16-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="25e16-124">See Also</span></span>  
 [<span data-ttu-id="25e16-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="25e16-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="25e16-126">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="25e16-126">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
