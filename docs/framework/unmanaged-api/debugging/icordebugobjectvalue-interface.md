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
ms.openlocfilehash: b782207503a2c3f739a30f68d509e6b481d2b6a4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129759"
---
# <a name="icordebugobjectvalue-interface"></a><span data-ttu-id="e137f-102">ICorDebugObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e137f-102">ICorDebugObjectValue Interface</span></span>

<span data-ttu-id="e137f-103">Bir nesnesi içeren bir değeri temsil eden "ICorDebugValue" öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e137f-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e137f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e137f-104">Methods</span></span>  
  
|<span data-ttu-id="e137f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e137f-105">Method</span></span>|<span data-ttu-id="e137f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e137f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e137f-107">GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e137f-107">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="e137f-108">Bu `ICorDebugObjectValue` başvurduğu nesnenin ortak dil çalışma zamanı (CLR) <xref:System.Type> için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="e137f-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="e137f-109">GetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e137f-109">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="e137f-110">Uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="e137f-110">Not implemented.</span></span>|  
|[<span data-ttu-id="e137f-111">GetFieldValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e137f-111">GetFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="e137f-112">Belirtilen sınıftaki belirtilen alanın değerini temsil eden bir [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="e137f-112">Gets an interface pointer to an [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="e137f-113">GetManagedCopy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e137f-113">GetManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="e137f-114">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="e137f-114">Obsolete.</span></span> <span data-ttu-id="e137f-115">Bu yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="e137f-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="e137f-116">GetVirtualMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e137f-116">GetVirtualMethod Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="e137f-117">Uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="e137f-117">Not implemented.</span></span>|  
|[<span data-ttu-id="e137f-118">IsValueClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e137f-118">IsValueClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="e137f-119">Bu `ICorDebugObjectValue` başvurduğu nesnenin bir değer türü olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="e137f-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="e137f-120">SetFromManagedCopy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e137f-120">SetFromManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="e137f-121">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="e137f-121">Obsolete.</span></span> <span data-ttu-id="e137f-122">Bu yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="e137f-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e137f-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e137f-123">Remarks</span></span>  
 <span data-ttu-id="e137f-124">Hata ayıklamakta olan işlem devam edene kadar `ICorDebugObjectValue` geçerli kalır.</span><span class="sxs-lookup"><span data-stu-id="e137f-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e137f-125">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="e137f-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e137f-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e137f-126">Requirements</span></span>  
 <span data-ttu-id="e137f-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e137f-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e137f-128">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e137f-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e137f-129">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e137f-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e137f-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e137f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e137f-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e137f-131">See also</span></span>

- [<span data-ttu-id="e137f-132">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e137f-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
