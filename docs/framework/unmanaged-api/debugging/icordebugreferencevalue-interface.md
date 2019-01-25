---
title: Icordebugreferencevalue arabirimi1
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
ms.openlocfilehash: 3dbe5388d7c18202f4b89269141d33463edb07a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544279"
---
# <a name="icordebugreferencevalue-interface1"></a><span data-ttu-id="f8110-102">Icordebugreferencevalue arabirimi1</span><span class="sxs-lookup"><span data-stu-id="f8110-102">ICorDebugReferenceValue Interface1</span></span>
<span data-ttu-id="f8110-103">Bir nesneye bir başvurusu olan bir değer yönetmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8110-103">Provides methods that manage a value that is a reference to an object.</span></span> <span data-ttu-id="f8110-104">(Diğer bir deyişle, bu arabirim işaretçisi yönetme yöntemleri sağlar.) Bu arabirim "ICorDebugValue" uygular.</span><span class="sxs-lookup"><span data-stu-id="f8110-104">(That is, this interface provides methods that manage a pointer.) This interface implements "ICorDebugValue".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f8110-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f8110-105">Methods</span></span>  
  
|<span data-ttu-id="f8110-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f8110-106">Method</span></span>|<span data-ttu-id="f8110-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f8110-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f8110-108">Dereference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f8110-108">Dereference Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|<span data-ttu-id="f8110-109">Başvurulan nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="f8110-109">Gets the object that is referenced.</span></span>|  
|[<span data-ttu-id="f8110-110">DereferenceStrong Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f8110-110">DereferenceStrong Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|<span data-ttu-id="f8110-111">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="f8110-111">Not implemented.</span></span> <span data-ttu-id="f8110-112">Bu yöntemi çağırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f8110-112">Do not call this method.</span></span>|  
|[<span data-ttu-id="f8110-113">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f8110-113">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|<span data-ttu-id="f8110-114">Başvurulan nesnenin geçerli bellek adresini alır.</span><span class="sxs-lookup"><span data-stu-id="f8110-114">Gets the current memory address of the referenced object.</span></span>|  
|[<span data-ttu-id="f8110-115">IsNull Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f8110-115">IsNull Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|<span data-ttu-id="f8110-116">Belirten bir değer alır olup bu `ICorDebugReferenceValue` null değeri, bu durumda olur `ICorDebugReferenceValue` bir nesneye işaret etmiyor.</span><span class="sxs-lookup"><span data-stu-id="f8110-116">Gets a value that indicates whether this `ICorDebugReferenceValue` is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>|  
|[<span data-ttu-id="f8110-117">SetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f8110-117">SetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|<span data-ttu-id="f8110-118">Geçerli bellek adresini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f8110-118">Sets the current memory address.</span></span> <span data-ttu-id="f8110-119">Diğer bir deyişle, bu yöntem bu ayarlar `ICorDebugReferenceValue` bir nesneye işaret edecek şekilde.</span><span class="sxs-lookup"><span data-stu-id="f8110-119">That is, this method sets this `ICorDebugReferenceValue` to point to an object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8110-120">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f8110-120">Remarks</span></span>  
 <span data-ttu-id="f8110-121">Hataları ayıklanan işlem devam ettirildiğinde, ortak dil çalışma zamanı (CLR) nesnelerde çöp toplama yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8110-121">The common language runtime (CLR) may do a garbage collection on objects when the debugged process is continued.</span></span> <span data-ttu-id="f8110-122">Çöp toplama nesneleri bellekte değiştirmemiz.</span><span class="sxs-lookup"><span data-stu-id="f8110-122">The garbage collection may move objects around in memory.</span></span> <span data-ttu-id="f8110-123">Bir `ICorDebugReferenceValue` ya da çöp toplama bilgilerini çöp toplamanın ardından güncelleştirilir ya da örtük olarak önce çöp toplama geçersiz iş Birliği yapacaktır.</span><span class="sxs-lookup"><span data-stu-id="f8110-123">An `ICorDebugReferenceValue` will either cooperate with the garbage collection so that its information is updated after the garbage collection, or it will be invalidated implicitly before the garbage collection.</span></span>  
  
 <span data-ttu-id="f8110-124">`ICorDebugReferenceValue` Hataları ayıklanan işlem devam sonra nesnesi örtük olarak geçersiz kılınan olabilir.</span><span class="sxs-lookup"><span data-stu-id="f8110-124">The `ICorDebugReferenceValue` object may be implicitly invalidated after the debugged process has been continued.</span></span> <span data-ttu-id="f8110-125">Açıkça serbest veya ifşa kadar türetilmiş "Icordebughandlevalue" geçersiz değil.</span><span class="sxs-lookup"><span data-stu-id="f8110-125">The derived "ICorDebugHandleValue" is not invalidated until it is explicitly released or exposed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8110-126">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="f8110-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8110-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f8110-127">Requirements</span></span>  
 <span data-ttu-id="f8110-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8110-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8110-129">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8110-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8110-130">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8110-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8110-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8110-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8110-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8110-132">See also</span></span>


- [<span data-ttu-id="f8110-133">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f8110-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
