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
ms.openlocfilehash: 9abcb765357a0f305ae5acae77a4a13b07a003a3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134681"
---
# <a name="icordebugappdomain-interface"></a><span data-ttu-id="e55ed-102">ICorDebugAppDomain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e55ed-102">ICorDebugAppDomain Interface</span></span>

<span data-ttu-id="e55ed-103">Uygulama etki alanlarındaki hataları ayıklamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e55ed-103">Provides methods for debugging application domains.</span></span> <span data-ttu-id="e55ed-104">Bu arabirim, ICorDebugController öğesinin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="e55ed-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e55ed-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e55ed-105">Methods</span></span>  
  
|<span data-ttu-id="e55ed-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e55ed-106">Method</span></span>|<span data-ttu-id="e55ed-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e55ed-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e55ed-108">Attach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e55ed-108">Attach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|<span data-ttu-id="e55ed-109">Hata ayıklayıcıyı uygulama etki alanına iliştirir.</span><span class="sxs-lookup"><span data-stu-id="e55ed-109">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="e55ed-110">EnumerateAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e55ed-110">EnumerateAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="e55ed-111">Uygulama etki alanındaki derlemeler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="e55ed-111">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="e55ed-112">EnumerateBreakpoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e55ed-112">EnumerateBreakpoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="e55ed-113">Uygulama etki alanındaki tüm etkin kesme noktaları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="e55ed-113">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="e55ed-114">EnumerateSteppers Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e55ed-114">EnumerateSteppers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="e55ed-115">Uygulama etki alanındaki tüm etkin stepdenetleyicileri için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="e55ed-115">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="e55ed-116">GetId Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e55ed-116">GetId Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|<span data-ttu-id="e55ed-117">Uygulama etki alanının benzersiz KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="e55ed-117">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="e55ed-118">GetModuleFromMetaDataInterface Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e55ed-118">GetModuleFromMetaDataInterface Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="e55ed-119">Belirtilen meta veri arabirimiyle ICorDebugModule nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="e55ed-119">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="e55ed-120">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e55ed-120">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|<span data-ttu-id="e55ed-121">Uygulama etki alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="e55ed-121">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="e55ed-122">GetObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e55ed-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|<span data-ttu-id="e55ed-123">Ortak dil çalışma zamanı (CLR) uygulama etki alanına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="e55ed-123">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="e55ed-124">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e55ed-124">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|<span data-ttu-id="e55ed-125">Uygulama etki alanını içeren işlemi alır.</span><span class="sxs-lookup"><span data-stu-id="e55ed-125">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="e55ed-126">IsAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e55ed-126">IsAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|<span data-ttu-id="e55ed-127">Hata ayıklayıcının uygulama etki alanına eklenip eklenmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="e55ed-127">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e55ed-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e55ed-128">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e55ed-129">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="e55ed-129">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e55ed-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e55ed-130">Requirements</span></span>  
 <span data-ttu-id="e55ed-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e55ed-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e55ed-132">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e55ed-132">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e55ed-133">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e55ed-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e55ed-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e55ed-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e55ed-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e55ed-135">See also</span></span>

- [<span data-ttu-id="e55ed-136">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e55ed-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
