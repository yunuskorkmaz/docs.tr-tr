---
title: ICorDebugReferenceValue Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue
helpviewer_keywords:
- ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67006603747abd89f1b635c065860dcbe1c47a29
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965641"
---
# <a name="icordebugreferencevalue-interface"></a><span data-ttu-id="ed13f-102">ICorDebugReferenceValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ed13f-102">ICorDebugReferenceValue Interface</span></span>
<span data-ttu-id="ed13f-103">Bir nesne başvurusu olan bir değeri yöneten yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed13f-103">Provides methods that manage a value that is a reference to an object.</span></span> <span data-ttu-id="ed13f-104">(Diğer bir deyişle, bu arabirim bir işaretçiyi yöneten yöntemler sağlar.) Bu arabirim "ICorDebugValue" uygular.</span><span class="sxs-lookup"><span data-stu-id="ed13f-104">(That is, this interface provides methods that manage a pointer.) This interface implements "ICorDebugValue".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ed13f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ed13f-105">Methods</span></span>  
  
|<span data-ttu-id="ed13f-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ed13f-106">Method</span></span>|<span data-ttu-id="ed13f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ed13f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ed13f-108">Dereference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed13f-108">Dereference Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|<span data-ttu-id="ed13f-109">Başvurulan nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="ed13f-109">Gets the object that is referenced.</span></span>|  
|[<span data-ttu-id="ed13f-110">DereferenceStrong Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed13f-110">DereferenceStrong Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|<span data-ttu-id="ed13f-111">Uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="ed13f-111">Not implemented.</span></span> <span data-ttu-id="ed13f-112">Bu yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="ed13f-112">Do not call this method.</span></span>|  
|[<span data-ttu-id="ed13f-113">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed13f-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|<span data-ttu-id="ed13f-114">Başvurulan nesnenin geçerli bellek adresini alır.</span><span class="sxs-lookup"><span data-stu-id="ed13f-114">Gets the current memory address of the referenced object.</span></span>|  
|[<span data-ttu-id="ed13f-115">IsNull Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed13f-115">IsNull Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|<span data-ttu-id="ed13f-116">Bunun null bir değer olup olmadığını belirten `ICorDebugReferenceValue` bir değer alır, bu `ICorDebugReferenceValue` durumda bir nesneyi işaret etmez.</span><span class="sxs-lookup"><span data-stu-id="ed13f-116">Gets a value that indicates whether this `ICorDebugReferenceValue` is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>|  
|[<span data-ttu-id="ed13f-117">SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ed13f-117">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|<span data-ttu-id="ed13f-118">Geçerli bellek adresini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ed13f-118">Sets the current memory address.</span></span> <span data-ttu-id="ed13f-119">Diğer bir deyişle, bu yöntem bunu `ICorDebugReferenceValue` bir nesnesine işaret etmek üzere ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ed13f-119">That is, this method sets this `ICorDebugReferenceValue` to point to an object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed13f-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ed13f-120">Remarks</span></span>  
 <span data-ttu-id="ed13f-121">Ortak dil çalışma zamanı (CLR), hata ayıklama işlemi devam eden nesneler üzerinde çöp toplama işlemi yapamayabilir.</span><span class="sxs-lookup"><span data-stu-id="ed13f-121">The common language runtime (CLR) may do a garbage collection on objects when the debugged process is continued.</span></span> <span data-ttu-id="ed13f-122">Çöp toplama, nesneleri belleğin etrafında taşıyabilir.</span><span class="sxs-lookup"><span data-stu-id="ed13f-122">The garbage collection may move objects around in memory.</span></span> <span data-ttu-id="ed13f-123">`ICorDebugReferenceValue` , Bilgileri çöp toplamadan sonra güncelleştirilmesini sağlamak için çöp koleksiyonuyla birlikte çalışır veya çöp toplamadan önce örtülü olarak geçersiz kılınacaktır.</span><span class="sxs-lookup"><span data-stu-id="ed13f-123">An `ICorDebugReferenceValue` will either cooperate with the garbage collection so that its information is updated after the garbage collection, or it will be invalidated implicitly before the garbage collection.</span></span>  
  
 <span data-ttu-id="ed13f-124">Hata ayıklama işlemi devam ettikten sonra nesneörtükolarakgeçersizkılınabilir.`ICorDebugReferenceValue`</span><span class="sxs-lookup"><span data-stu-id="ed13f-124">The `ICorDebugReferenceValue` object may be implicitly invalidated after the debugged process has been continued.</span></span> <span data-ttu-id="ed13f-125">Türetilmiş "ıcorıı Ghandlevalue", açık veya kullanıma sunuluncaya kadar geçersiz kılınmaz.</span><span class="sxs-lookup"><span data-stu-id="ed13f-125">The derived "ICorDebugHandleValue" is not invalidated until it is explicitly released or exposed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ed13f-126">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="ed13f-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed13f-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ed13f-127">Requirements</span></span>  
 <span data-ttu-id="ed13f-128">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed13f-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed13f-129">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ed13f-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed13f-130">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ed13f-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed13f-131">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed13f-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed13f-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ed13f-132">See also</span></span>

- [<span data-ttu-id="ed13f-133">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ed13f-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
