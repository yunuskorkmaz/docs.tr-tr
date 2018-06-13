---
title: Icordebugreferencevalue Interface1
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
ms.openlocfilehash: b6cdfa9f3717e4025ff6f4fe6da3c1457cdebf7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422337"
---
# <a name="icordebugreferencevalue-interface1"></a><span data-ttu-id="6ecda-102">Icordebugreferencevalue Interface1</span><span class="sxs-lookup"><span data-stu-id="6ecda-102">ICorDebugReferenceValue Interface1</span></span>
<span data-ttu-id="6ecda-103">Bir nesneye bir başvurusu olan bir değer yönetme yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ecda-103">Provides methods that manage a value that is a reference to an object.</span></span> <span data-ttu-id="6ecda-104">(Diğer bir deyişle, bu arabirim bir işaretçi yönetme yöntemleri sağlar.) Bu arabirim "ICorDebugValue" uygular.</span><span class="sxs-lookup"><span data-stu-id="6ecda-104">(That is, this interface provides methods that manage a pointer.) This interface implements "ICorDebugValue".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6ecda-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6ecda-105">Methods</span></span>  
  
|<span data-ttu-id="6ecda-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6ecda-106">Method</span></span>|<span data-ttu-id="6ecda-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6ecda-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6ecda-108">Dereference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ecda-108">Dereference Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|<span data-ttu-id="6ecda-109">Başvurulan nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="6ecda-109">Gets the object that is referenced.</span></span>|  
|[<span data-ttu-id="6ecda-110">DereferenceStrong Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ecda-110">DereferenceStrong Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|<span data-ttu-id="6ecda-111">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="6ecda-111">Not implemented.</span></span> <span data-ttu-id="6ecda-112">Bu yöntemi çağırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6ecda-112">Do not call this method.</span></span>|  
|[<span data-ttu-id="6ecda-113">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ecda-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|<span data-ttu-id="6ecda-114">Başvurulan nesnenin geçerli bellek adresini alır.</span><span class="sxs-lookup"><span data-stu-id="6ecda-114">Gets the current memory address of the referenced object.</span></span>|  
|[<span data-ttu-id="6ecda-115">IsNull Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ecda-115">IsNull Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|<span data-ttu-id="6ecda-116">Gösteren bir değer alır olup olmadığını bu `ICorDebugReferenceValue` bir null değer; bu durumda olur `ICorDebugReferenceValue` bir nesneye işaret etmiyor.</span><span class="sxs-lookup"><span data-stu-id="6ecda-116">Gets a value that indicates whether this `ICorDebugReferenceValue` is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>|  
|[<span data-ttu-id="6ecda-117">SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ecda-117">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|<span data-ttu-id="6ecda-118">Geçerli bellek adresini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6ecda-118">Sets the current memory address.</span></span> <span data-ttu-id="6ecda-119">Diğer bir deyişle, bu yöntem bu ayarlar `ICorDebugReferenceValue` bir nesneye işaret edecek şekilde.</span><span class="sxs-lookup"><span data-stu-id="6ecda-119">That is, this method sets this `ICorDebugReferenceValue` to point to an object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ecda-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6ecda-120">Remarks</span></span>  
 <span data-ttu-id="6ecda-121">Ortak dil çalışma zamanı (CLR) nesnelerde çöp toplama ne ve hata ayıklaması işlemi devam.</span><span class="sxs-lookup"><span data-stu-id="6ecda-121">The common language runtime (CLR) may do a garbage collection on objects when the debugged process is continued.</span></span> <span data-ttu-id="6ecda-122">Çöp toplama nesneleri bellekte gezinme.</span><span class="sxs-lookup"><span data-stu-id="6ecda-122">The garbage collection may move objects around in memory.</span></span> <span data-ttu-id="6ecda-123">Bir `ICorDebugReferenceValue` ya da kendi bilgilerini sonra atık toplama güncelleştirilir ya da örtük olarak önce çöp toplama geçersiz çöp toplama ile işbirliği.</span><span class="sxs-lookup"><span data-stu-id="6ecda-123">An `ICorDebugReferenceValue` will either cooperate with the garbage collection so that its information is updated after the garbage collection, or it will be invalidated implicitly before the garbage collection.</span></span>  
  
 <span data-ttu-id="6ecda-124">`ICorDebugReferenceValue` Hata ayıklaması işlemi devam sonra nesnesi örtük olarak geçersiz kılınan olabilir.</span><span class="sxs-lookup"><span data-stu-id="6ecda-124">The `ICorDebugReferenceValue` object may be implicitly invalidated after the debugged process has been continued.</span></span> <span data-ttu-id="6ecda-125">Açıkça serbest veya kullanıma sunulan kadar türetilmiş "Icordebughandlevalue" geçersiz kılınan değil.</span><span class="sxs-lookup"><span data-stu-id="6ecda-125">The derived "ICorDebugHandleValue" is not invalidated until it is explicitly released or exposed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ecda-126">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="6ecda-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ecda-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6ecda-127">Requirements</span></span>  
 <span data-ttu-id="6ecda-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ecda-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ecda-129">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6ecda-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6ecda-130">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6ecda-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6ecda-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ecda-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ecda-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6ecda-132">See Also</span></span>  
    
    
 [<span data-ttu-id="6ecda-133">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6ecda-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
