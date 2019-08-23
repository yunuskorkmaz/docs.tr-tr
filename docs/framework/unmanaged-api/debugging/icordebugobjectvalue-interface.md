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
ms.openlocfilehash: a4ca59aac075a42294026ad54c5d5dd4dbf7fda4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943331"
---
# <a name="icordebugobjectvalue-interface"></a><span data-ttu-id="af8fe-102">ICorDebugObjectValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="af8fe-102">ICorDebugObjectValue Interface</span></span>

<span data-ttu-id="af8fe-103">Bir nesnesi içeren bir değeri temsil eden "ICorDebugValue" öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="af8fe-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="af8fe-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="af8fe-104">Methods</span></span>  
  
|<span data-ttu-id="af8fe-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="af8fe-105">Method</span></span>|<span data-ttu-id="af8fe-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="af8fe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="af8fe-107">GetClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="af8fe-107">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="af8fe-108"><xref:System.Type> Bu`ICorDebugObjectValue` başvuruda bulunan nesnenin ortak dil çalışma zamanına (CLR) yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="af8fe-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="af8fe-109">GetContext Yöntemi</span><span class="sxs-lookup"><span data-stu-id="af8fe-109">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="af8fe-110">Uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="af8fe-110">Not implemented.</span></span>|  
|[<span data-ttu-id="af8fe-111">GetFieldValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="af8fe-111">GetFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="af8fe-112">Belirtilen sınıftaki belirtilen alanın değerini temsil eden bir [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="af8fe-112">Gets an interface pointer to an [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="af8fe-113">GetManagedCopy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="af8fe-113">GetManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="af8fe-114">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="af8fe-114">Obsolete.</span></span> <span data-ttu-id="af8fe-115">Bu yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="af8fe-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="af8fe-116">GetVirtualMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="af8fe-116">GetVirtualMethod Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="af8fe-117">Uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="af8fe-117">Not implemented.</span></span>|  
|[<span data-ttu-id="af8fe-118">IsValueClass Yöntemi</span><span class="sxs-lookup"><span data-stu-id="af8fe-118">IsValueClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="af8fe-119">Bu `ICorDebugObjectValue` nesnenin başvurduğu nesnenin bir değer türü olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="af8fe-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="af8fe-120">SetFromManagedCopy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="af8fe-120">SetFromManagedCopy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="af8fe-121">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="af8fe-121">Obsolete.</span></span> <span data-ttu-id="af8fe-122">Bu yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="af8fe-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af8fe-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af8fe-123">Remarks</span></span>  
 <span data-ttu-id="af8fe-124">Hata ayıklamakta olan işlem devam edene kadar geçerli kalır.`ICorDebugObjectValue`</span><span class="sxs-lookup"><span data-stu-id="af8fe-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="af8fe-125">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="af8fe-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af8fe-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="af8fe-126">Requirements</span></span>  
 <span data-ttu-id="af8fe-127">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af8fe-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af8fe-128">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="af8fe-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af8fe-129">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="af8fe-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af8fe-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af8fe-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af8fe-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af8fe-131">See also</span></span>

- [<span data-ttu-id="af8fe-132">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="af8fe-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
