---
title: Icordebugmutabledatatarget arabirimi
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f63343b43481d1d91d1db30cd2ace3214c5590a9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492305"
---
# <a name="icordebugmutabledatatarget-interface"></a><span data-ttu-id="c87e0-102">Icordebugmutabledatatarget arabirimi</span><span class="sxs-lookup"><span data-stu-id="c87e0-102">ICorDebugMutableDataTarget Interface</span></span>
<span data-ttu-id="c87e0-103">Genişletir [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) değişebilir veri hedefleri desteklemek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="c87e0-103">Extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c87e0-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c87e0-104">Methods</span></span>  
  
|<span data-ttu-id="c87e0-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c87e0-105">Method</span></span>|<span data-ttu-id="c87e0-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c87e0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c87e0-107">ContinueStatusChanged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c87e0-107">ContinueStatusChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|<span data-ttu-id="c87e0-108">Belirtilen iş parçacığı üzerinde bekleyen hata ayıklama olayı için devamlılık durumu değişir.</span><span class="sxs-lookup"><span data-stu-id="c87e0-108">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>|  
|[<span data-ttu-id="c87e0-109">SetThreadContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c87e0-109">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|<span data-ttu-id="c87e0-110">Bir iş parçacığı bağlamı (yazmaç değerlerini) ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c87e0-110">Sets the context (register values) for a thread.</span></span>|  
|[<span data-ttu-id="c87e0-111">WriteVirtual Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c87e0-111">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|<span data-ttu-id="c87e0-112">Bellek, hedef işlemin adres alanına yazar.</span><span class="sxs-lookup"><span data-stu-id="c87e0-112">Writes memory into the target process address space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c87e0-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c87e0-113">Remarks</span></span>  
 <span data-ttu-id="c87e0-114">Bu uzantı için [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) arabirimi hata ayıklama (örneğin, Canlı bozucu hata ayıklama gerçekleştirmek için) hedef işlem değiştirmek istediğiniz araçları tarafından uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="c87e0-114">This extension to the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface can be implemented by debugging tools that wish to modify the target process (for example, to perform live invasive debugging).</span></span>  
  
 <span data-ttu-id="c87e0-115">Bu yöntemlerin tümü, hiçbir çekirdek denetleme tabanlı hata ayıklama işlevselliğini bu arabirimi uygulayan değil veya bu yöntemlere yapılan çağrılar başarısız kaybolmadığı algılama isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c87e0-115">All of these methods are optional in the sense that no core inspection-based debugging functionality is lost by not implementing this interface or by the failure of calls to these methods.</span></span>  <span data-ttu-id="c87e0-116">Herhangi bir hata `HRESULT` bu yöntemleri olarak kullanıma yayılır `HRESULT` Icordebug yöntem çağrısından.</span><span class="sxs-lookup"><span data-stu-id="c87e0-116">Any failure `HRESULT` from these methods will propagate out as the `HRESULT` from the ICorDebug method call.</span></span>  
  
 <span data-ttu-id="c87e0-117">Tek bir Icordebug yöntemi çağrısı birden çok mutations neden olabilir ve sağlamaya yönelik bir mekanizma bulunmamaktadır mutations işlemsel olarak uygulandığını ilgili not (tümü veya hiçbiri işlemini).</span><span class="sxs-lookup"><span data-stu-id="c87e0-117">Note that a single ICorDebug method call may result in multiple mutations, and that there is no mechanism for ensuring related mutations are applied transactionally (all-or-none).</span></span>  <span data-ttu-id="c87e0-118">Başka bir deyişle, diğerleri (için aynı Icordebug çağrısı) başarıyla tamamlandıktan sonra bir Mutasyon başarısız olursa, hedef işlem tutarsız bir durumda kalabilir ve hata ayıklama güvenilir olabilir.</span><span class="sxs-lookup"><span data-stu-id="c87e0-118">This means that if a mutation fails after others (for the same ICorDebug call) have succeeded, the target process may be left in an inconsistent state and debugging may become unreliable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c87e0-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c87e0-119">Requirements</span></span>  
 <span data-ttu-id="c87e0-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c87e0-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c87e0-121">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c87e0-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c87e0-122">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c87e0-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c87e0-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c87e0-123">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c87e0-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c87e0-124">See also</span></span>
- [<span data-ttu-id="c87e0-125">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c87e0-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="c87e0-126">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c87e0-126">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
