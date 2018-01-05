---
title: Icordebugobjectvalue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectValue
helpviewer_keywords: ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6dfde9f212936b1a0d0f5a6e76eafd4a2e62356c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugobjectvalue-interface1"></a><span data-ttu-id="855ef-102">Icordebugobjectvalue Interface1</span><span class="sxs-lookup"><span data-stu-id="855ef-102">ICorDebugObjectValue Interface1</span></span>
<span data-ttu-id="855ef-103">"Bir nesne içeren bir değeri temsil eden Icordebugvalue" sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="855ef-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="855ef-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="855ef-104">Methods</span></span>  
  
|<span data-ttu-id="855ef-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="855ef-105">Method</span></span>|<span data-ttu-id="855ef-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="855ef-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="855ef-107">GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="855ef-107">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="855ef-108">Ortak dil çalışma zamanı (CLR) bir arabirim işaretçisi alır <xref:System.Type> nesnenin bu `ICorDebugObjectValue` başvuruları.</span><span class="sxs-lookup"><span data-stu-id="855ef-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="855ef-109">GetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="855ef-109">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="855ef-110">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="855ef-110">Not implemented.</span></span>|  
|[<span data-ttu-id="855ef-111">GetFieldValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="855ef-111">GetFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="855ef-112">Bir arabirim işaretçisi alır bir [Icordebugvalue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) , belirtilen sınıf belirtilen alanının değerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="855ef-112">Gets an interface pointer to an [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="855ef-113">GetManagedCopy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="855ef-113">GetManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="855ef-114">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="855ef-114">Obsolete.</span></span> <span data-ttu-id="855ef-115">Bu yöntemi çağırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="855ef-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="855ef-116">GetVirtualMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="855ef-116">GetVirtualMethod Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="855ef-117">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="855ef-117">Not implemented.</span></span>|  
|[<span data-ttu-id="855ef-118">IsValueClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="855ef-118">IsValueClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="855ef-119">Nesne bu tarafından başvurulan olup olmadığını belirten bir değer alır `ICorDebugObjectValue` değer türü değil.</span><span class="sxs-lookup"><span data-stu-id="855ef-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="855ef-120">SetFromManagedCopy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="855ef-120">SetFromManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="855ef-121">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="855ef-121">Obsolete.</span></span> <span data-ttu-id="855ef-122">Bu yöntemi çağırmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="855ef-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="855ef-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="855ef-123">Remarks</span></span>  
 <span data-ttu-id="855ef-124">Bir `ICorDebugObjectValue` ayıklanacak işlemi devam kadar geçerli kalır.</span><span class="sxs-lookup"><span data-stu-id="855ef-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="855ef-125">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="855ef-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="855ef-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="855ef-126">Requirements</span></span>  
 <span data-ttu-id="855ef-127">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="855ef-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="855ef-128">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="855ef-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="855ef-129">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="855ef-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="855ef-130">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="855ef-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="855ef-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="855ef-131">See Also</span></span>  
 [<span data-ttu-id="855ef-132">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="855ef-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 
