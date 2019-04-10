---
title: ICorDebugObjectValue Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue
helpviewer_keywords:
- ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0ac91681313b60ebfcaf725dcc2e0d6547e3c1b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222620"
---
# <a name="icordebugobjectvalue-interface"></a><span data-ttu-id="e5093-102">ICorDebugObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e5093-102">ICorDebugObjectValue Interface</span></span>

<span data-ttu-id="e5093-103">"Bir nesne içeren bir değeri temsil eden Icordebugvalue" öğesinin.</span><span class="sxs-lookup"><span data-stu-id="e5093-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e5093-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e5093-104">Methods</span></span>  
  
|<span data-ttu-id="e5093-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e5093-105">Method</span></span>|<span data-ttu-id="e5093-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5093-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e5093-107">GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5093-107">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="e5093-108">Ortak dil çalışma zamanı (CLR) bir arabirim işaretçisi alır <xref:System.Type> nesnenin bu `ICorDebugObjectValue` başvuruları.</span><span class="sxs-lookup"><span data-stu-id="e5093-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="e5093-109">GetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5093-109">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="e5093-110">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="e5093-110">Not implemented.</span></span>|  
|[<span data-ttu-id="e5093-111">GetFieldValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5093-111">GetFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="e5093-112">Bir arabirim işaretçisi alır bir [Icordebugvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) , belirtilen sınıfın belirtilen alanın değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e5093-112">Gets an interface pointer to an [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="e5093-113">GetManagedCopy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5093-113">GetManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="e5093-114">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="e5093-114">Obsolete.</span></span> <span data-ttu-id="e5093-115">Bu yöntemi çağırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e5093-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="e5093-116">GetVirtualMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5093-116">GetVirtualMethod Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="e5093-117">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="e5093-117">Not implemented.</span></span>|  
|[<span data-ttu-id="e5093-118">IsValueClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5093-118">IsValueClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="e5093-119">Bu tarafından başvurulan nesne olup olmadığını gösteren bir değer alır `ICorDebugObjectValue` bir değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="e5093-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="e5093-120">SetFromManagedCopy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e5093-120">SetFromManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="e5093-121">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="e5093-121">Obsolete.</span></span> <span data-ttu-id="e5093-122">Bu yöntemi çağırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e5093-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5093-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e5093-123">Remarks</span></span>  
 <span data-ttu-id="e5093-124">Bir `ICorDebugObjectValue` ayıklanan işlemin devam kadar geçerli kalır.</span><span class="sxs-lookup"><span data-stu-id="e5093-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5093-125">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e5093-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5093-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e5093-126">Requirements</span></span>  
 <span data-ttu-id="e5093-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5093-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5093-128">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5093-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5093-129">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5093-129">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e5093-130">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="e5093-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e5093-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5093-131">See also</span></span>

- [<span data-ttu-id="e5093-132">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e5093-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
