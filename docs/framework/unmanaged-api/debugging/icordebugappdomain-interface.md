---
title: ICorDebugAppDomain Arabirimi
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
ms.openlocfilehash: 40619aa40f9924d94c82541eb8d30790e774a675
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141511"
---
# <a name="icordebugappdomain-interface"></a><span data-ttu-id="fccfa-102">ICorDebugAppDomain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fccfa-102">ICorDebugAppDomain Interface</span></span>

<span data-ttu-id="fccfa-103">Uygulama etki alanlarındaki hataları ayıklamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="fccfa-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="fccfa-104">Icordebugcontroller öğesinin arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="fccfa-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fccfa-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fccfa-105">Methods</span></span>  
  
|<span data-ttu-id="fccfa-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fccfa-106">Method</span></span>|<span data-ttu-id="fccfa-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fccfa-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fccfa-108">Attach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fccfa-108">Attach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|<span data-ttu-id="fccfa-109">Hata ayıklayıcı, uygulama etki alanına ekler.</span><span class="sxs-lookup"><span data-stu-id="fccfa-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="fccfa-110">EnumerateAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fccfa-110">EnumerateAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="fccfa-111">Bir numaralandırıcı için derlemeleri uygulama etki alanında alır.</span><span class="sxs-lookup"><span data-stu-id="fccfa-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="fccfa-112">EnumerateBreakpoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fccfa-112">EnumerateBreakpoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="fccfa-113">Bir numaralandırıcı, uygulama etki alanı için tüm etkin kesme noktalarını alır.</span><span class="sxs-lookup"><span data-stu-id="fccfa-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="fccfa-114">EnumerateSteppers Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fccfa-114">EnumerateSteppers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="fccfa-115">Bir numaralandırıcı, uygulama etki alanı için tüm etkin adımlayıcıların alır.</span><span class="sxs-lookup"><span data-stu-id="fccfa-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="fccfa-116">GetID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fccfa-116">GetId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|<span data-ttu-id="fccfa-117">Uygulama etki alanının benzersiz kimlik alır.</span><span class="sxs-lookup"><span data-stu-id="fccfa-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="fccfa-118">GetModuleFromMetaDataInterface Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fccfa-118">GetModuleFromMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="fccfa-119">Belirtilen meta veriler arabirimiyle Icordebugmodule nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="fccfa-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="fccfa-120">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fccfa-120">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|<span data-ttu-id="fccfa-121">Uygulama etki alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="fccfa-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="fccfa-122">GetObject Metodu</span><span class="sxs-lookup"><span data-stu-id="fccfa-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|<span data-ttu-id="fccfa-123">Ortak dil çalışma zamanı (CLR) uygulama etki alanı için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="fccfa-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="fccfa-124">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fccfa-124">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|<span data-ttu-id="fccfa-125">Uygulama etki alanını içeren işlemi alır.</span><span class="sxs-lookup"><span data-stu-id="fccfa-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="fccfa-126">IsAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fccfa-126">IsAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|<span data-ttu-id="fccfa-127">Hata ayıklayıcı uygulama etki alanına bağlı olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="fccfa-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fccfa-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fccfa-128">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fccfa-129">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="fccfa-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fccfa-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fccfa-130">Requirements</span></span>  
 <span data-ttu-id="fccfa-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fccfa-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fccfa-132">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fccfa-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fccfa-133">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fccfa-133">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="fccfa-134">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="fccfa-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fccfa-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fccfa-135">See also</span></span>

- [<span data-ttu-id="fccfa-136">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fccfa-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
