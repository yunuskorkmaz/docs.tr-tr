---
description: ': ICorDebugAppDomain Arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 5f1ac20a7376a741da2e34de74c810c0f45e8293
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754207"
---
# <a name="icordebugappdomain-interface"></a><span data-ttu-id="7dd1c-103">ICorDebugAppDomain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7dd1c-103">ICorDebugAppDomain Interface</span></span>

<span data-ttu-id="7dd1c-104">Uygulama etki alanlarındaki hataları ayıklamak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7dd1c-104">Provides methods for debugging application domains.</span></span> <span data-ttu-id="7dd1c-105">Bu arabirim, ICorDebugController öğesinin bir alt sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="7dd1c-105">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7dd1c-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7dd1c-106">Methods</span></span>  
  
|<span data-ttu-id="7dd1c-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7dd1c-107">Method</span></span>|<span data-ttu-id="7dd1c-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7dd1c-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7dd1c-109">Attach Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7dd1c-109">Attach Method</span></span>](icordebugappdomain-attach-method.md)|<span data-ttu-id="7dd1c-110">Hata ayıklayıcıyı uygulama etki alanına iliştirir.</span><span class="sxs-lookup"><span data-stu-id="7dd1c-110">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="7dd1c-111">EnumerateAssemblies Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7dd1c-111">EnumerateAssemblies Method</span></span>](icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="7dd1c-112">Uygulama etki alanındaki derlemeler için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="7dd1c-112">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="7dd1c-113">EnumerateBreakpoints Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7dd1c-113">EnumerateBreakpoints Method</span></span>](icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="7dd1c-114">Uygulama etki alanındaki tüm etkin kesme noktaları için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="7dd1c-114">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="7dd1c-115">EnumerateSteppers Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7dd1c-115">EnumerateSteppers Method</span></span>](icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="7dd1c-116">Uygulama etki alanındaki tüm etkin stepdenetleyicileri için bir Numaralandırıcı alır.</span><span class="sxs-lookup"><span data-stu-id="7dd1c-116">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="7dd1c-117">GetID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7dd1c-117">GetId Method</span></span>](icordebugappdomain-getid-method.md)|<span data-ttu-id="7dd1c-118">Uygulama etki alanının benzersiz KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="7dd1c-118">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="7dd1c-119">GetModuleFromMetaDataInterface Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7dd1c-119">GetModuleFromMetaDataInterface Method</span></span>](icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="7dd1c-120">Belirtilen meta veri arabirimiyle ICorDebugModule nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="7dd1c-120">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="7dd1c-121">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7dd1c-121">GetName Method</span></span>](icordebugappdomain-getname-method.md)|<span data-ttu-id="7dd1c-122">Uygulama etki alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="7dd1c-122">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="7dd1c-123">GetObject Metodu</span><span class="sxs-lookup"><span data-stu-id="7dd1c-123">GetObject Method</span></span>](icordebugappdomain-getobject-method.md)|<span data-ttu-id="7dd1c-124">Ortak dil çalışma zamanı (CLR) uygulama etki alanına bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="7dd1c-124">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="7dd1c-125">GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7dd1c-125">GetProcess Method</span></span>](icordebugappdomain-getprocess-method.md)|<span data-ttu-id="7dd1c-126">Uygulama etki alanını içeren işlemi alır.</span><span class="sxs-lookup"><span data-stu-id="7dd1c-126">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="7dd1c-127">IsAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7dd1c-127">IsAttached Method</span></span>](icordebugappdomain-isattached-method.md)|<span data-ttu-id="7dd1c-128">Hata ayıklayıcının uygulama etki alanına eklenip eklenmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="7dd1c-128">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7dd1c-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7dd1c-129">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7dd1c-130">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="7dd1c-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dd1c-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7dd1c-131">Requirements</span></span>  

 <span data-ttu-id="7dd1c-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7dd1c-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7dd1c-133">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7dd1c-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7dd1c-134">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7dd1c-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7dd1c-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7dd1c-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dd1c-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7dd1c-136">See also</span></span>

- [<span data-ttu-id="7dd1c-137">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7dd1c-137">Debugging Interfaces</span></span>](debugging-interfaces.md)
