---
title: Icordebugappdomain Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain
api_location: corguids.lib
api_type: COM
f1_keywords: ICorDebugAppDomain
helpviewer_keywords: ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 19cf38920ed818dfbba9cd83bd64fdc408281e0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomain-interface1"></a><span data-ttu-id="4b994-102">Icordebugappdomain Interface1</span><span class="sxs-lookup"><span data-stu-id="4b994-102">ICorDebugAppDomain Interface1</span></span>
<span data-ttu-id="4b994-103">Uygulama etki alanlarındaki hataları ayıklamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b994-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="4b994-104">Bu arabirim Icordebugcontroller sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="4b994-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4b994-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4b994-105">Methods</span></span>  
  
|<span data-ttu-id="4b994-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4b994-106">Method</span></span>|<span data-ttu-id="4b994-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b994-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4b994-108">Attach yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b994-108">Attach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|<span data-ttu-id="4b994-109">Hata ayıklayıcı uygulama etki alanına ekler.</span><span class="sxs-lookup"><span data-stu-id="4b994-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="4b994-110">EnumerateAssemblies yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b994-110">EnumerateAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="4b994-111">Bir numaralandırıcı derlemeler için uygulama etki alanında alır.</span><span class="sxs-lookup"><span data-stu-id="4b994-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="4b994-112">EnumerateBreakpoints yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b994-112">EnumerateBreakpoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="4b994-113">Bir numaralandırıcı uygulama etki alanı için tüm etkin kesme noktalarını alır.</span><span class="sxs-lookup"><span data-stu-id="4b994-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="4b994-114">EnumerateSteppers yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b994-114">EnumerateSteppers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="4b994-115">Bir numaralandırıcı uygulama etki alanı için tüm etkin adımlayıcıların alır.</span><span class="sxs-lookup"><span data-stu-id="4b994-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="4b994-116">GetID yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b994-116">GetId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|<span data-ttu-id="4b994-117">Uygulama etki alanı benzersiz Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="4b994-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="4b994-118">Getmodulefrommetadataınterface yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b994-118">GetModuleFromMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="4b994-119">Belirtilen meta veriler arabirimi Icordebugmodule nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="4b994-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="4b994-120">GetName yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b994-120">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|<span data-ttu-id="4b994-121">Uygulama etki alanı adını alır.</span><span class="sxs-lookup"><span data-stu-id="4b994-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="4b994-122">GetObject yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b994-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|<span data-ttu-id="4b994-123">Ortak dil çalışma zamanı (CLR) uygulama etki alanı için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="4b994-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="4b994-124">GetProcess yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b994-124">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|<span data-ttu-id="4b994-125">Uygulama etki alanını içeren işlem alır.</span><span class="sxs-lookup"><span data-stu-id="4b994-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="4b994-126">Isattached yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b994-126">IsAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|<span data-ttu-id="4b994-127">Hata ayıklayıcı uygulama etki alanına bağlı olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="4b994-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b994-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b994-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b994-129">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="4b994-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b994-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4b994-130">Requirements</span></span>  
 <span data-ttu-id="4b994-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b994-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b994-132">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b994-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b994-133">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b994-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b994-134">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b994-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b994-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4b994-135">See Also</span></span>  
 [<span data-ttu-id="4b994-136">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4b994-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
