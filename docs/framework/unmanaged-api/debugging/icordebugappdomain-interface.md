---
title: Icordebugappdomain arabirimi1
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9588ac26c698a8369f1ae4be89af7440a2dd1de4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546312"
---
# <a name="icordebugappdomain-interface1"></a><span data-ttu-id="7ba7f-102">Icordebugappdomain arabirimi1</span><span class="sxs-lookup"><span data-stu-id="7ba7f-102">ICorDebugAppDomain Interface1</span></span>
<span data-ttu-id="7ba7f-103">Uygulama etki alanlarındaki hataları ayıklamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ba7f-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="7ba7f-104">Icordebugcontroller öğesinin arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="7ba7f-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7ba7f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7ba7f-105">Methods</span></span>  
  
|<span data-ttu-id="7ba7f-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7ba7f-106">Method</span></span>|<span data-ttu-id="7ba7f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ba7f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7ba7f-108">Attach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ba7f-108">Attach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|<span data-ttu-id="7ba7f-109">Hata ayıklayıcı, uygulama etki alanına ekler.</span><span class="sxs-lookup"><span data-stu-id="7ba7f-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="7ba7f-110">EnumerateAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ba7f-110">EnumerateAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="7ba7f-111">Bir numaralandırıcı için derlemeleri uygulama etki alanında alır.</span><span class="sxs-lookup"><span data-stu-id="7ba7f-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="7ba7f-112">EnumerateBreakpoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ba7f-112">EnumerateBreakpoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="7ba7f-113">Bir numaralandırıcı, uygulama etki alanı için tüm etkin kesme noktalarını alır.</span><span class="sxs-lookup"><span data-stu-id="7ba7f-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="7ba7f-114">EnumerateSteppers Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ba7f-114">EnumerateSteppers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="7ba7f-115">Bir numaralandırıcı, uygulama etki alanı için tüm etkin adımlayıcıların alır.</span><span class="sxs-lookup"><span data-stu-id="7ba7f-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="7ba7f-116">GetId Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ba7f-116">GetId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|<span data-ttu-id="7ba7f-117">Uygulama etki alanının benzersiz kimlik alır.</span><span class="sxs-lookup"><span data-stu-id="7ba7f-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="7ba7f-118">GetModuleFromMetaDataInterface Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ba7f-118">GetModuleFromMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="7ba7f-119">Belirtilen meta veriler arabirimiyle Icordebugmodule nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="7ba7f-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="7ba7f-120">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ba7f-120">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|<span data-ttu-id="7ba7f-121">Uygulama etki alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="7ba7f-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="7ba7f-122">GetObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ba7f-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|<span data-ttu-id="7ba7f-123">Ortak dil çalışma zamanı (CLR) uygulama etki alanı için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="7ba7f-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="7ba7f-124">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ba7f-124">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|<span data-ttu-id="7ba7f-125">Uygulama etki alanını içeren işlemi alır.</span><span class="sxs-lookup"><span data-stu-id="7ba7f-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="7ba7f-126">IsAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ba7f-126">IsAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|<span data-ttu-id="7ba7f-127">Hata ayıklayıcı uygulama etki alanına bağlı olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="7ba7f-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ba7f-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ba7f-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ba7f-129">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7ba7f-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ba7f-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ba7f-130">Requirements</span></span>  
 <span data-ttu-id="7ba7f-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ba7f-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ba7f-132">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7ba7f-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ba7f-133">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ba7f-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ba7f-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ba7f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ba7f-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ba7f-135">See also</span></span>
- [<span data-ttu-id="7ba7f-136">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7ba7f-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
