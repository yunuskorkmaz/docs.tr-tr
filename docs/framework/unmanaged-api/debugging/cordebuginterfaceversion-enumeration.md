---
title: CorDebugInterfaceVersion Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugInterfaceVersion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInterfaceVersion
helpviewer_keywords:
- CorDebugInterfaceVersion enumeration [.NET Framework debugging]
ms.assetid: 7d1e6cd9-2a15-41c6-9b68-008705a4ed90
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df57cd5a2121c216fc23b9c608de091b002147e5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101770"
---
# <a name="cordebuginterfaceversion-enumeration"></a><span data-ttu-id="64ed5-102">CorDebugInterfaceVersion Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="64ed5-102">CorDebugInterfaceVersion Enumeration</span></span>
<span data-ttu-id="64ed5-103">Bir arabirim, .NET Framework sürümünü veya bir arabirim içinde tanıtılan .NET Framework sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="64ed5-103">Specifies an interface, a version of the .NET Framework, or a version of the .NET Framework in which an interface was introduced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64ed5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64ed5-104">Syntax</span></span>  
  
```  
typedef enum CorDebugInterfaceVersion {  
  
    CorDebugInvalidVersion            = 0,  
    CorDebugVersion_1_0               = CorDebugInvalidVersion + 1,  
  
    ver_ICorDebugManagedCallback      = CorDebugVersion_1_0,  
    ver_ICorDebugUnmanagedCallback    = CorDebugVersion_1_0,  
    ver_ICorDebug                     = CorDebugVersion_1_0,  
    ver_ICorDebugController           = CorDebugVersion_1_0,  
    ver_ICorDebugAppDomain            = CorDebugVersion_1_0,  
    ver_ICorDebugAssembly             = CorDebugVersion_1_0,  
    ver_ICorDebugProcess              = CorDebugVersion_1_0,  
    ver_ICorDebugBreakpoint           = CorDebugVersion_1_0,  
    ver_ICorDebugFunctionBreakpoint   = CorDebugVersion_1_0,  
    ver_ICorDebugModuleBreakpoint     = CorDebugVersion_1_0,  
    ver_ICorDebugValueBreakpoint      = CorDebugVersion_1_0,  
    ver_ICorDebugStepper              = CorDebugVersion_1_0,  
    ver_ICorDebugRegisterSet          = CorDebugVersion_1_0,  
    ver_ICorDebugThread               = CorDebugVersion_1_0,  
    ver_ICorDebugChain                = CorDebugVersion_1_0,  
    ver_ICorDebugFrame                = CorDebugVersion_1_0,  
    ver_ICorDebugILFrame              = CorDebugVersion_1_0,  
    ver_ICorDebugNativeFrame          = CorDebugVersion_1_0,  
    ver_ICorDebugModule               = CorDebugVersion_1_0,  
    ver_ICorDebugFunction             = CorDebugVersion_1_0,  
    ver_ICorDebugCode                 = CorDebugVersion_1_0,  
    ver_ICorDebugClass                = CorDebugVersion_1_0,  
    ver_ICorDebugEval                 = CorDebugVersion_1_0,  
    ver_ICorDebugValue                = CorDebugVersion_1_0,  
    ver_ICorDebugGenericValue         = CorDebugVersion_1_0,  
    ver_ICorDebugReferenceValue       = CorDebugVersion_1_0,  
    ver_ICorDebugHeapValue            = CorDebugVersion_1_0,  
    ver_ICorDebugObjectValue          = CorDebugVersion_1_0,  
    ver_ICorDebugBoxValue             = CorDebugVersion_1_0,  
    ver_ICorDebugStringValue          = CorDebugVersion_1_0,  
    ver_ICorDebugArrayValue           = CorDebugVersion_1_0,  
    ver_ICorDebugContext              = CorDebugVersion_1_0,  
    ver_ICorDebugEnum                 = CorDebugVersion_1_0,  
    ver_ICorDebugObjectEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugBreakpointEnum       = CorDebugVersion_1_0,  
    ver_ICorDebugStepperEnum          = CorDebugVersion_1_0,  
    ver_ICorDebugProcessEnum          = CorDebugVersion_1_0,  
    ver_ICorDebugThreadEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugFrameEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugChainEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugModuleEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugValueEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugCodeEnum             = CorDebugVersion_1_0,  
    ver_ICorDebugTypeEnum             = CorDebugVersion_1_0,  
    ver_ICorDebugErrorInfoEnum        = CorDebugVersion_1_0,  
    ver_ICorDebugAppDomainEnum        = CorDebugVersion_1_0,  
    ver_ICorDebugAssemblyEnum         = CorDebugVersion_1_0,  
    ver_ICorDebugEditAndContinueErrorInfo   
                                      = CorDebugVersion_1_0,  
    ver_ICorDebugEditAndContinueSnapshot   
                                      = CorDebugVersion_1_0,  
  
    CorDebugVersion_1_1               = CorDebugVersion_1_0 + 1,  
    // No interface definitions in version 1.1.  
  
    CorDebugVersion_2_0 = CorDebugVersion_1_1 + 1,  
  
    ver_ICorDebugManagedCallback2    = CorDebugVersion_2_0,  
    ver_ICorDebugAppDomain2          = CorDebugVersion_2_0,  
    ver_ICorDebugProcess2            = CorDebugVersion_2_0,  
    ver_ICorDebugStepper2            = CorDebugVersion_2_0,  
    ver_ICorDebugRegisterSet2        = CorDebugVersion_2_0,  
    ver_ICorDebugThread2             = CorDebugVersion_2_0,  
    ver_ICorDebugILFrame2            = CorDebugVersion_2_0,  
    ver_ICorDebugModule2             = CorDebugVersion_2_0,  
    ver_ICorDebugFunction2           = CorDebugVersion_2_0,  
    ver_ICorDebugCode2               = CorDebugVersion_2_0,  
    ver_ICorDebugClass2              = CorDebugVersion_2_0,  
    ver_ICorDebugValue2              = CorDebugVersion_2_0,  
    ver_ICorDebugEval2               = CorDebugVersion_2_0,  
    ver_ICorDebugObjectValue2        = CorDebugVersion_2_0,  
  
    // CLR v4 - next major CLR version after CLR v2  
    // Includes Silverlight 4  
    CorDebugVersion_4_0 = CorDebugVersion_2_0 + 1,  
  
    ver_ICorDebugThread3             = CorDebugVersion_4_0,  
    ver_ICorDebugThread4             = CorDebugVersion_4_0,  
    ver_ICorDebugStackWalk           = CorDebugVersion_4_0,  
    ver_ICorDebugNativeFrame2        = CorDebugVersion_4_0,  
    ver_ICorDebugInternalFrame2      = CorDebugVersion_4_0,  
    ver_ICorDebugRuntimeUnwindableFrame = CorDebugVersion_4_0,  
    ver_ICorDebugHeapValue3          = CorDebugVersion_4_0,  
    ver_ICorDebugBlockingObjectEnum  = CorDebugVersion_4_0,  
    ver_ICorDebugValue3 = CorDebugVersion_4_0,  
  
    CorDebugVersion_4_5 = CorDebugVersion_4_0 + 1,  
  
    ver_ICorDebugComObjectValue = CorDebugVersion_4_5,  
    ver_ICorDebugAppDomain3 = CorDebugVersion_4_5,  
    ver_ICorDebugCode3 = CorDebugVersion_4_5,  
    ver_ICorDebugILFrame3 = CorDebugVersion_4_5,  
  
    CorDebugLatestVersion = CorDebugVersion_4_5  
  
} CorDebugInterfaceVersion;  
```  
  
## <a name="members"></a><span data-ttu-id="64ed5-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="64ed5-105">Members</span></span>  
 <span data-ttu-id="64ed5-106">Aşağıdaki tabloda, her bir değerden numaralandırma karşılık gelen arabirimi bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="64ed5-106">The following table provides links from each enumeration value to the corresponding interface.</span></span> <span data-ttu-id="64ed5-107">Ayrıca, tablo arabirimi içinde desteklenen .NET Framework'ün ilk sürümü gösterir.</span><span class="sxs-lookup"><span data-stu-id="64ed5-107">In addition, the table indicates the first version of the .NET Framework that the interface was supported in.</span></span>  
  
|<span data-ttu-id="64ed5-108">Üye</span><span class="sxs-lookup"><span data-stu-id="64ed5-108">Member</span></span>|<span data-ttu-id="64ed5-109">Belirler</span><span class="sxs-lookup"><span data-stu-id="64ed5-109">Specifies</span></span>|<span data-ttu-id="64ed5-110">.NET Framework sürümü</span><span class="sxs-lookup"><span data-stu-id="64ed5-110">.NET Framework version</span></span>|  
|------------|---------------|----------------------------|  
|`CorDebugInvalidVersion`|<span data-ttu-id="64ed5-111">.NET Framework sürümü geçersiz.</span><span class="sxs-lookup"><span data-stu-id="64ed5-111">The version of the .NET Framework is invalid.</span></span>|-|  
|`CorDebugVersion_1_0`|<span data-ttu-id="64ed5-112">Hizmet paketleri de dahil olmak üzere .NET Framework 1.0 sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="64ed5-112">The version of the .NET Framework, including all its service packs, is 1.0.</span></span>|<span data-ttu-id="64ed5-113">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-113">1.0</span></span>|  
|`CorDebugVersion_1_1`|<span data-ttu-id="64ed5-114">Tüm hizmet paketleri de dahil olmak üzere .NET Framework 1.1 sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="64ed5-114">The version of the .NET Framework, including all service packs, is 1.1.</span></span>|<span data-ttu-id="64ed5-115">1.1</span><span class="sxs-lookup"><span data-stu-id="64ed5-115">1.1</span></span>|  
|`CorDebugVersion_2_0`|<span data-ttu-id="64ed5-116">Tüm hizmet paketleri de dahil olmak üzere .NET Framework 2.0 sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="64ed5-116">The version of the .NET Framework, including all service packs, is 2.0.</span></span>|<span data-ttu-id="64ed5-117">2,0</span><span class="sxs-lookup"><span data-stu-id="64ed5-117">2.0</span></span>|  
|`CorDebugVersion_4_0`|<span data-ttu-id="64ed5-118">Tüm hizmet paketleri de dahil olmak üzere .NET Framework sürüm 4'tür.</span><span class="sxs-lookup"><span data-stu-id="64ed5-118">The version of the .NET Framework, including all service packs, is 4.</span></span>|<span data-ttu-id="64ed5-119">4</span><span class="sxs-lookup"><span data-stu-id="64ed5-119">4</span></span>|  
|`CorDebugVersion_4_5`|<span data-ttu-id="64ed5-120">Tüm hizmet paketleri de dahil olmak üzere .NET Framework 4.5 sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="64ed5-120">The version of the .NET Framework, including all service packs, is 4.5.</span></span>|<span data-ttu-id="64ed5-121">4,5</span><span class="sxs-lookup"><span data-stu-id="64ed5-121">4.5</span></span>|  
|`ver_ICorDebugManagedCallback`|[<span data-ttu-id="64ed5-122">Icordebugmanagedcallback</span><span class="sxs-lookup"><span data-stu-id="64ed5-122">ICorDebugManagedCallback</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)|<span data-ttu-id="64ed5-123">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-123">1.0</span></span>|  
|`ver_ICorDebugUnmanagedCallback`|[<span data-ttu-id="64ed5-124">Icordebugunmanagedcallback</span><span class="sxs-lookup"><span data-stu-id="64ed5-124">ICorDebugUnmanagedCallback</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)|<span data-ttu-id="64ed5-125">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-125">1.0</span></span>|  
|`ver_ICorDebug`|[<span data-ttu-id="64ed5-126">Icordebug</span><span class="sxs-lookup"><span data-stu-id="64ed5-126">ICorDebug</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)|<span data-ttu-id="64ed5-127">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-127">1.0</span></span>|  
|`ver_ICorDebugController`|[<span data-ttu-id="64ed5-128">Icordebugcontroller</span><span class="sxs-lookup"><span data-stu-id="64ed5-128">ICorDebugController</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)|<span data-ttu-id="64ed5-129">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-129">1.0</span></span>|  
|`ver_ICorDebugAppDomain`|[<span data-ttu-id="64ed5-130">Icordebugappdomain</span><span class="sxs-lookup"><span data-stu-id="64ed5-130">ICorDebugAppDomain</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)|<span data-ttu-id="64ed5-131">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-131">1.0</span></span>|  
|`ver_ICorDebugAssembly`|[<span data-ttu-id="64ed5-132">Icordebugassembly</span><span class="sxs-lookup"><span data-stu-id="64ed5-132">ICorDebugAssembly</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)|<span data-ttu-id="64ed5-133">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-133">1.0</span></span>|  
|`ver_ICorDebugProcess`|[<span data-ttu-id="64ed5-134">Icordebugprocess</span><span class="sxs-lookup"><span data-stu-id="64ed5-134">ICorDebugProcess</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)|<span data-ttu-id="64ed5-135">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-135">1.0</span></span>|  
|`ver_ICorDebugBreakpoint`|[<span data-ttu-id="64ed5-136">Icordebugbreakpoint</span><span class="sxs-lookup"><span data-stu-id="64ed5-136">ICorDebugBreakpoint</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)|<span data-ttu-id="64ed5-137">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-137">1.0</span></span>|  
|`ver_ICorDebugFunctionBreakpoint`|[<span data-ttu-id="64ed5-138">ICorDebugFunctionBreakpoint</span><span class="sxs-lookup"><span data-stu-id="64ed5-138">ICorDebugFunctionBreakpoint</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)|<span data-ttu-id="64ed5-139">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-139">1.0</span></span>|  
|`ver_ICorDebugModuleBreakpoint`|[<span data-ttu-id="64ed5-140">Icordebugmodulebreakpoint</span><span class="sxs-lookup"><span data-stu-id="64ed5-140">ICorDebugModuleBreakpoint</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)|<span data-ttu-id="64ed5-141">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-141">1.0</span></span>|  
|`ver_ICorDebugValueBreakpoint`|[<span data-ttu-id="64ed5-142">Icordebugvaluebreakpoint</span><span class="sxs-lookup"><span data-stu-id="64ed5-142">ICorDebugValueBreakpoint</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-interface.md)|<span data-ttu-id="64ed5-143">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-143">1.0</span></span>|  
|`ver_ICorDebugStepper`|[<span data-ttu-id="64ed5-144">ICorDebugStepper</span><span class="sxs-lookup"><span data-stu-id="64ed5-144">ICorDebugStepper</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)|<span data-ttu-id="64ed5-145">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-145">1.0</span></span>|  
|`ver_ICorDebugRegisterSet`|[<span data-ttu-id="64ed5-146">Icordebugregisterset</span><span class="sxs-lookup"><span data-stu-id="64ed5-146">ICorDebugRegisterSet</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)|<span data-ttu-id="64ed5-147">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-147">1.0</span></span>|  
|`ver_ICorDebugThread`|[<span data-ttu-id="64ed5-148">Icordebugthread</span><span class="sxs-lookup"><span data-stu-id="64ed5-148">ICorDebugThread</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)|<span data-ttu-id="64ed5-149">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-149">1.0</span></span>|  
|`ver_ICorDebugChain`|[<span data-ttu-id="64ed5-150">Icordebugchain</span><span class="sxs-lookup"><span data-stu-id="64ed5-150">ICorDebugChain</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)|<span data-ttu-id="64ed5-151">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-151">1.0</span></span>|  
|`ver_ICorDebugFrame`|[<span data-ttu-id="64ed5-152">Icordebugframe</span><span class="sxs-lookup"><span data-stu-id="64ed5-152">ICorDebugFrame</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)|<span data-ttu-id="64ed5-153">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-153">1.0</span></span>|  
|`ver_ICorDebugILFrame`|[<span data-ttu-id="64ed5-154">Icordebugılframe</span><span class="sxs-lookup"><span data-stu-id="64ed5-154">ICorDebugILFrame</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)|<span data-ttu-id="64ed5-155">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-155">1.0</span></span>|  
|`ver_ICorDebugNativeFrame`|[<span data-ttu-id="64ed5-156">Icordebugnativeframe</span><span class="sxs-lookup"><span data-stu-id="64ed5-156">ICorDebugNativeFrame</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)|<span data-ttu-id="64ed5-157">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-157">1.0</span></span>|  
|`ver_ICorDebugModule`|[<span data-ttu-id="64ed5-158">Icordebugmodule</span><span class="sxs-lookup"><span data-stu-id="64ed5-158">ICorDebugModule</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)|<span data-ttu-id="64ed5-159">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-159">1.0</span></span>|  
|`ver_ICorDebugFunction`|[<span data-ttu-id="64ed5-160">ICorDebugFunction</span><span class="sxs-lookup"><span data-stu-id="64ed5-160">ICorDebugFunction</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)|<span data-ttu-id="64ed5-161">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-161">1.0</span></span>|  
|`ver_ICorDebugCode`|[<span data-ttu-id="64ed5-162">Icordebugcode</span><span class="sxs-lookup"><span data-stu-id="64ed5-162">ICorDebugCode</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)|<span data-ttu-id="64ed5-163">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-163">1.0</span></span>|  
|`ver_ICorDebugClass`|[<span data-ttu-id="64ed5-164">Icordebugclass</span><span class="sxs-lookup"><span data-stu-id="64ed5-164">ICorDebugClass</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)|<span data-ttu-id="64ed5-165">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-165">1.0</span></span>|  
|`ver_ICorDebugEval`|[<span data-ttu-id="64ed5-166">Icordebugeval</span><span class="sxs-lookup"><span data-stu-id="64ed5-166">ICorDebugEval</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)|<span data-ttu-id="64ed5-167">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-167">1.0</span></span>|  
|`ver_ICorDebugValue`|[<span data-ttu-id="64ed5-168">Icordebugvalue</span><span class="sxs-lookup"><span data-stu-id="64ed5-168">ICorDebugValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md)|<span data-ttu-id="64ed5-169">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-169">1.0</span></span>|  
|`ver_ICorDebugGenericValue`|[<span data-ttu-id="64ed5-170">Icordebuggenericvalue</span><span class="sxs-lookup"><span data-stu-id="64ed5-170">ICorDebugGenericValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)|<span data-ttu-id="64ed5-171">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-171">1.0</span></span>|  
|`ver_ICorDebugReferenceValue`|[<span data-ttu-id="64ed5-172">Icordebugreferencevalue</span><span class="sxs-lookup"><span data-stu-id="64ed5-172">ICorDebugReferenceValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)|<span data-ttu-id="64ed5-173">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-173">1.0</span></span>|  
|`ver_ICorDebugHeapValue`|[<span data-ttu-id="64ed5-174">Icordebugheapvalue</span><span class="sxs-lookup"><span data-stu-id="64ed5-174">ICorDebugHeapValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)|<span data-ttu-id="64ed5-175">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-175">1.0</span></span>|  
|`ver_ICorDebugObjectValue`|[<span data-ttu-id="64ed5-176">Icordebugobjectvalue</span><span class="sxs-lookup"><span data-stu-id="64ed5-176">ICorDebugObjectValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)|<span data-ttu-id="64ed5-177">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-177">1.0</span></span>|  
|`ver_ICorDebugBoxValue`|[<span data-ttu-id="64ed5-178">Icordebugboxvalue</span><span class="sxs-lookup"><span data-stu-id="64ed5-178">ICorDebugBoxValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)|<span data-ttu-id="64ed5-179">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-179">1.0</span></span>|  
|`ver_ICorDebugStringValue`|[<span data-ttu-id="64ed5-180">Icordebugstringvalue</span><span class="sxs-lookup"><span data-stu-id="64ed5-180">ICorDebugStringValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)|<span data-ttu-id="64ed5-181">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-181">1.0</span></span>|  
|`ver_ICorDebugArrayValue`|[<span data-ttu-id="64ed5-182">Icordebugarrayvalue</span><span class="sxs-lookup"><span data-stu-id="64ed5-182">ICorDebugArrayValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)|<span data-ttu-id="64ed5-183">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-183">1.0</span></span>|  
|`ver_ICorDebugContext`|[<span data-ttu-id="64ed5-184">Icordebugcontext</span><span class="sxs-lookup"><span data-stu-id="64ed5-184">ICorDebugContext</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)|<span data-ttu-id="64ed5-185">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-185">1.0</span></span>|  
|`ver_ICorDebugEnum`|[<span data-ttu-id="64ed5-186">Icordebugenum</span><span class="sxs-lookup"><span data-stu-id="64ed5-186">ICorDebugEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)|<span data-ttu-id="64ed5-187">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-187">1.0</span></span>|  
|`ver_ICorDebugObjectEnum`|[<span data-ttu-id="64ed5-188">Icordebugobjectenum</span><span class="sxs-lookup"><span data-stu-id="64ed5-188">ICorDebugObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)|<span data-ttu-id="64ed5-189">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-189">1.0</span></span>|  
|`ver_ICorDebugBreakpointEnum`|[<span data-ttu-id="64ed5-190">Icordebugbreakpointenum</span><span class="sxs-lookup"><span data-stu-id="64ed5-190">ICorDebugBreakpointEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)|<span data-ttu-id="64ed5-191">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-191">1.0</span></span>|  
|`ver_ICorDebugStepperEnum`|[<span data-ttu-id="64ed5-192">Icordebugstepperenum</span><span class="sxs-lookup"><span data-stu-id="64ed5-192">ICorDebugStepperEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)|<span data-ttu-id="64ed5-193">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-193">1.0</span></span>|  
|`ver_ICorDebugProcessEnum`|[<span data-ttu-id="64ed5-194">Icordebugprocessenum</span><span class="sxs-lookup"><span data-stu-id="64ed5-194">ICorDebugProcessEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)|<span data-ttu-id="64ed5-195">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-195">1.0</span></span>|  
|`ver_ICorDebugThreadEnum`|[<span data-ttu-id="64ed5-196">Icordebugthreadenum</span><span class="sxs-lookup"><span data-stu-id="64ed5-196">ICorDebugThreadEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)|<span data-ttu-id="64ed5-197">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-197">1.0</span></span>|  
|`ver_ICorDebugFrameEnum`|[<span data-ttu-id="64ed5-198">Icordebugframeenum</span><span class="sxs-lookup"><span data-stu-id="64ed5-198">ICorDebugFrameEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)|<span data-ttu-id="64ed5-199">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-199">1.0</span></span>|  
|`ver_ICorDebugChainEnum`|[<span data-ttu-id="64ed5-200">Icordebugchainenum</span><span class="sxs-lookup"><span data-stu-id="64ed5-200">ICorDebugChainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)|<span data-ttu-id="64ed5-201">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-201">1.0</span></span>|  
|`ver_ICorDebugModuleEnum`|[<span data-ttu-id="64ed5-202">Icordebugmoduleenum</span><span class="sxs-lookup"><span data-stu-id="64ed5-202">ICorDebugModuleEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)|<span data-ttu-id="64ed5-203">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-203">1.0</span></span>|  
|`ver_ICorDebugValueEnum`|[<span data-ttu-id="64ed5-204">Icordebugvalueenum</span><span class="sxs-lookup"><span data-stu-id="64ed5-204">ICorDebugValueEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalueenum-interface.md)|<span data-ttu-id="64ed5-205">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-205">1.0</span></span>|  
|`ver_ICorDebugCodeEnum`|[<span data-ttu-id="64ed5-206">Icordebugcodeenum</span><span class="sxs-lookup"><span data-stu-id="64ed5-206">ICorDebugCodeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)|<span data-ttu-id="64ed5-207">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-207">1.0</span></span>|  
|`ver_ICorDebugTypeEnum`|[<span data-ttu-id="64ed5-208">Icordebugtypeenum</span><span class="sxs-lookup"><span data-stu-id="64ed5-208">ICorDebugTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)|<span data-ttu-id="64ed5-209">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-209">1.0</span></span>|  
|`ver_ICorDebugErrorInfoEnum`|[<span data-ttu-id="64ed5-210">Icordebugerrorınfoenum</span><span class="sxs-lookup"><span data-stu-id="64ed5-210">ICorDebugErrorInfoEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)|<span data-ttu-id="64ed5-211">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-211">1.0</span></span>|  
|`ver_ICorDebugAppDomainEnum`|[<span data-ttu-id="64ed5-212">Icordebugappdomainenum</span><span class="sxs-lookup"><span data-stu-id="64ed5-212">ICorDebugAppDomainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)|<span data-ttu-id="64ed5-213">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-213">1.0</span></span>|  
|`ver_ICorDebugAssemblyEnum`|[<span data-ttu-id="64ed5-214">Icordebugassemblyenum</span><span class="sxs-lookup"><span data-stu-id="64ed5-214">ICorDebugAssemblyEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)|<span data-ttu-id="64ed5-215">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-215">1.0</span></span>|  
|`ver_ICorDebugEditAndContinueErrorInfo`|[<span data-ttu-id="64ed5-216">Icordebugeditandcontinueerrorınfo</span><span class="sxs-lookup"><span data-stu-id="64ed5-216">ICorDebugEditAndContinueErrorInfo</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)|<span data-ttu-id="64ed5-217">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-217">1.0</span></span>|  
|`ver_ICorDebugEditAndContinueSnapshot`|[<span data-ttu-id="64ed5-218">ICorDebugEditAndContinueSnapshot</span><span class="sxs-lookup"><span data-stu-id="64ed5-218">ICorDebugEditAndContinueSnapshot</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)|<span data-ttu-id="64ed5-219">1.0</span><span class="sxs-lookup"><span data-stu-id="64ed5-219">1.0</span></span>|  
|`ver_ICorDebugManagedCallback2`|[<span data-ttu-id="64ed5-220">Icordebugmanagedcallback2</span><span class="sxs-lookup"><span data-stu-id="64ed5-220">ICorDebugManagedCallback2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)|<span data-ttu-id="64ed5-221">2,0</span><span class="sxs-lookup"><span data-stu-id="64ed5-221">2.0</span></span>|  
|`ver_ICorDebugAppDomain2`|[<span data-ttu-id="64ed5-222">Icordebugappdomain2</span><span class="sxs-lookup"><span data-stu-id="64ed5-222">ICorDebugAppDomain2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)|<span data-ttu-id="64ed5-223">2,0</span><span class="sxs-lookup"><span data-stu-id="64ed5-223">2.0</span></span>|  
|`ver_ICorDebugProcess2`|[<span data-ttu-id="64ed5-224">Icordebugprocess2</span><span class="sxs-lookup"><span data-stu-id="64ed5-224">ICorDebugProcess2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)|<span data-ttu-id="64ed5-225">2,0</span><span class="sxs-lookup"><span data-stu-id="64ed5-225">2.0</span></span>|  
|`ver_ICorDebugStepper2`|[<span data-ttu-id="64ed5-226">Icordebugstepper2</span><span class="sxs-lookup"><span data-stu-id="64ed5-226">ICorDebugStepper2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)|<span data-ttu-id="64ed5-227">2,0</span><span class="sxs-lookup"><span data-stu-id="64ed5-227">2.0</span></span>|  
|`ver_ICorDebugRegisterSet2`|[<span data-ttu-id="64ed5-228">Icordebugregisterset2</span><span class="sxs-lookup"><span data-stu-id="64ed5-228">ICorDebugRegisterSet2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)|<span data-ttu-id="64ed5-229">2,0</span><span class="sxs-lookup"><span data-stu-id="64ed5-229">2.0</span></span>|  
|`ver_ICorDebugThread2`|[<span data-ttu-id="64ed5-230">Icordebugthread2</span><span class="sxs-lookup"><span data-stu-id="64ed5-230">ICorDebugThread2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)|<span data-ttu-id="64ed5-231">2,0</span><span class="sxs-lookup"><span data-stu-id="64ed5-231">2.0</span></span>|  
|`ver_ICorDebugILFrame2`|[<span data-ttu-id="64ed5-232">Icordebugılframe2</span><span class="sxs-lookup"><span data-stu-id="64ed5-232">ICorDebugILFrame2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)|<span data-ttu-id="64ed5-233">2,0</span><span class="sxs-lookup"><span data-stu-id="64ed5-233">2.0</span></span>|  
|`ver_ICorDebugModule2`|[<span data-ttu-id="64ed5-234">Icordebugmodule2</span><span class="sxs-lookup"><span data-stu-id="64ed5-234">ICorDebugModule2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)|<span data-ttu-id="64ed5-235">2,0</span><span class="sxs-lookup"><span data-stu-id="64ed5-235">2.0</span></span>|  
|`ver_ICorDebugFunction2`|[<span data-ttu-id="64ed5-236">Icordebugfunction2</span><span class="sxs-lookup"><span data-stu-id="64ed5-236">ICorDebugFunction2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)|<span data-ttu-id="64ed5-237">2,0</span><span class="sxs-lookup"><span data-stu-id="64ed5-237">2.0</span></span>|  
|`ver_ICorDebugCode2`|[<span data-ttu-id="64ed5-238">Icordebugcode2</span><span class="sxs-lookup"><span data-stu-id="64ed5-238">ICorDebugCode2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)|<span data-ttu-id="64ed5-239">2,0</span><span class="sxs-lookup"><span data-stu-id="64ed5-239">2.0</span></span>|  
|`ver_ICorDebugClass2`|<span data-ttu-id="64ed5-240">"ICorDebugClass2"</span><span class="sxs-lookup"><span data-stu-id="64ed5-240">"ICorDebugClass2"</span></span>|<span data-ttu-id="64ed5-241">2,0</span><span class="sxs-lookup"><span data-stu-id="64ed5-241">2.0</span></span>|  
|`ver_ICorDebugValue2`|<span data-ttu-id="64ed5-242">"ICorDebugValue2"</span><span class="sxs-lookup"><span data-stu-id="64ed5-242">"ICorDebugValue2"</span></span>|<span data-ttu-id="64ed5-243">2,0</span><span class="sxs-lookup"><span data-stu-id="64ed5-243">2.0</span></span>|  
|`ver_ICorDebugEval2`|<span data-ttu-id="64ed5-244">"Icordebugeval2".</span><span class="sxs-lookup"><span data-stu-id="64ed5-244">The "ICorDebugEval2".</span></span>|<span data-ttu-id="64ed5-245">2,0</span><span class="sxs-lookup"><span data-stu-id="64ed5-245">2.0</span></span>|  
|`ver_ICorDebugObjectValue2`|<span data-ttu-id="64ed5-246">"ICorDebugObjectValue2"</span><span class="sxs-lookup"><span data-stu-id="64ed5-246">"ICorDebugObjectValue2"</span></span>|<span data-ttu-id="64ed5-247">2,0</span><span class="sxs-lookup"><span data-stu-id="64ed5-247">2.0</span></span>|  
|`ver_ICorDebugThread3`|[<span data-ttu-id="64ed5-248">Icordebugthread3</span><span class="sxs-lookup"><span data-stu-id="64ed5-248">ICorDebugThread3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)|<span data-ttu-id="64ed5-249">4</span><span class="sxs-lookup"><span data-stu-id="64ed5-249">4</span></span>|  
|`ver_ICorDebugThread4`|[<span data-ttu-id="64ed5-250">Icordebugthread4</span><span class="sxs-lookup"><span data-stu-id="64ed5-250">ICorDebugThread4</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)|<span data-ttu-id="64ed5-251">4</span><span class="sxs-lookup"><span data-stu-id="64ed5-251">4</span></span>|  
|`ver_ICorDebugStackWalk`|[<span data-ttu-id="64ed5-252">Icordebugstackwalk</span><span class="sxs-lookup"><span data-stu-id="64ed5-252">ICorDebugStackWalk</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)|<span data-ttu-id="64ed5-253">4</span><span class="sxs-lookup"><span data-stu-id="64ed5-253">4</span></span>|  
|`ver_ICorDebugNativeFrame2`|[<span data-ttu-id="64ed5-254">Icordebugnativeframe2</span><span class="sxs-lookup"><span data-stu-id="64ed5-254">ICorDebugNativeFrame2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)|<span data-ttu-id="64ed5-255">4</span><span class="sxs-lookup"><span data-stu-id="64ed5-255">4</span></span>|  
|`ver_ICorDebugInternalFrame2`|[<span data-ttu-id="64ed5-256">Icordebugınternalframe2</span><span class="sxs-lookup"><span data-stu-id="64ed5-256">ICorDebugInternalFrame2</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)|<span data-ttu-id="64ed5-257">4</span><span class="sxs-lookup"><span data-stu-id="64ed5-257">4</span></span>|  
|`ver_ICorDebugRuntimeUnwindableFrame`|[<span data-ttu-id="64ed5-258">Icordebugruntimeunwindableframe</span><span class="sxs-lookup"><span data-stu-id="64ed5-258">ICorDebugRuntimeUnwindableFrame</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)|<span data-ttu-id="64ed5-259">4</span><span class="sxs-lookup"><span data-stu-id="64ed5-259">4</span></span>|  
|`ver_ICorDebugHeapValue3`|[<span data-ttu-id="64ed5-260">ICorDebugHeapValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64ed5-260">ICorDebugHeapValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)|<span data-ttu-id="64ed5-261">4</span><span class="sxs-lookup"><span data-stu-id="64ed5-261">4</span></span>|  
|`ver_ICorDebugBlockingObjectEnum`|[<span data-ttu-id="64ed5-262">ICorDebugBlockingObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64ed5-262">ICorDebugBlockingObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)|<span data-ttu-id="64ed5-263">4</span><span class="sxs-lookup"><span data-stu-id="64ed5-263">4</span></span>|  
|`ver_ICorDebugValue3`|[<span data-ttu-id="64ed5-264">Icordebugvalue3</span><span class="sxs-lookup"><span data-stu-id="64ed5-264">ICorDebugValue3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)|<span data-ttu-id="64ed5-265">4</span><span class="sxs-lookup"><span data-stu-id="64ed5-265">4</span></span>|  
|`ver_ICorDebugComObjectValue`|[<span data-ttu-id="64ed5-266">Icordebugcomobjectvalue</span><span class="sxs-lookup"><span data-stu-id="64ed5-266">ICorDebugComObjectValue</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)|<span data-ttu-id="64ed5-267">4,5</span><span class="sxs-lookup"><span data-stu-id="64ed5-267">4.5</span></span>|  
|`ver_ICorDebugAppDomain3`|[<span data-ttu-id="64ed5-268">Icordebugappdomain3</span><span class="sxs-lookup"><span data-stu-id="64ed5-268">ICorDebugAppDomain3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)|<span data-ttu-id="64ed5-269">4,5</span><span class="sxs-lookup"><span data-stu-id="64ed5-269">4.5</span></span>|  
|`ver_ICorDebugCode3`|[<span data-ttu-id="64ed5-270">Icordebugcode3</span><span class="sxs-lookup"><span data-stu-id="64ed5-270">ICorDebugCode3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)|<span data-ttu-id="64ed5-271">4,5</span><span class="sxs-lookup"><span data-stu-id="64ed5-271">4.5</span></span>|  
|`ver_ICorDebugILFrame3`|[<span data-ttu-id="64ed5-272">Icordebugılframe3</span><span class="sxs-lookup"><span data-stu-id="64ed5-272">ICorDebugILFrame3</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)|<span data-ttu-id="64ed5-273">4,5</span><span class="sxs-lookup"><span data-stu-id="64ed5-273">4.5</span></span>|  
|`CorDebugLatestVersion`|<span data-ttu-id="64ed5-274">Tüm hizmet paketleri de dahil olmak üzere .NET Framework'ün en son sürümü sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="64ed5-274">The version of the .NET Framework, including all of its service packs, is the latest version.</span></span>|-|  
  
## <a name="remarks"></a><span data-ttu-id="64ed5-275">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="64ed5-275">Remarks</span></span>  
 <span data-ttu-id="64ed5-276">Bir hata ayıklayıcı kullanabilirsiniz `CorDebugInterfaceVersion` numaralandırmada [Createdebuggingınterfacefromversion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) hata ayıklayıcısının desteklediği .NET Framework'ün en yüksek sürümü belirtmek için işlev.</span><span class="sxs-lookup"><span data-stu-id="64ed5-276">A debugger can use the `CorDebugInterfaceVersion` enumeration in the [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) function to specify the highest version of the .NET Framework that the debugger supports.</span></span>  
  
## <a name="interface-names"></a><span data-ttu-id="64ed5-277">Arabirim adı</span><span class="sxs-lookup"><span data-stu-id="64ed5-277">Interface Names</span></span>  
 <span data-ttu-id="64ed5-278">Hata ayıklama API Arabirimi adların sonuna sayı (örneğin, "3" `ICorDebugThread3`) arabirimi, .NET Framework'ün sürümü olmayan sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="64ed5-278">The number that appears at the end of the interface names in the debugging API (for example, the "3" in `ICorDebugThread3`) specifies the version of the interface, not the version of the .NET Framework.</span></span> <span data-ttu-id="64ed5-279">Hata ayıklama API'sindeki tüm arabirimi adları, .NET Framework sürüm 1 sunulan arabirimler dışında sürüm numaralarını içerir.</span><span class="sxs-lookup"><span data-stu-id="64ed5-279">All interface names in the debugging API include version numbers except for interfaces that were introduced in the .NET Framework version 1.</span></span> <span data-ttu-id="64ed5-280">Arabirimi sürüm numaralarını and.NET Framework sürüm numaraları arasındaki bir ilişkiyi içerik olarak farklı.</span><span class="sxs-lookup"><span data-stu-id="64ed5-280">Any correspondence between interface version numbers and.NET Framework version numbers are coincidental.</span></span>  
  
-   <span data-ttu-id="64ed5-281">Tüm örtük olarak sürüm 1 olduğundan, .NET Framework sürüm 1.0 sunulan arabirimler numaralarını dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="64ed5-281">Interfaces that were introduced in the .NET Framework version 1.0 do not include numbers, because they are all implicitly version 1.</span></span>  
  
-   <span data-ttu-id="64ed5-282">.NET Framework sürüm 1.1, 1.0 sürümü arabirimleri kullanır ve herhangi bir yeni hata ayıklama arabirimleri sunmaz.</span><span class="sxs-lookup"><span data-stu-id="64ed5-282">The .NET Framework version 1.1 uses version 1.0 interfaces, and does not introduce any new debugging interfaces.</span></span>  
  
-   <span data-ttu-id="64ed5-283">.NET Framework 2.0 sürümünde sunulan 14 hata ayıklama arabirimleri mantıksal uzantıları kendi sürüm 1 ortaklarınıza ve "2" sayısı adlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="64ed5-283">The 14 debugging interfaces introduced in the .NET Framework version 2.0 are logical extensions of their version 1 counterparts and include the number "2" in their names.</span></span>  
  
-   <span data-ttu-id="64ed5-284">.NET Framework 3.0 ve 3.5 sürümlerini mevcut .NET Framework 2.0 arabirimleri kullanır ve hiçbir yeni arabirim ekleme.</span><span class="sxs-lookup"><span data-stu-id="64ed5-284">The .NET Framework versions 3.0 and 3.5 use the existing .NET Framework 2.0 interfaces, and do not introduce any new interfaces.</span></span>  
  
-   <span data-ttu-id="64ed5-285">[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] Arabirimi sürümleri bir karışımını sunar.</span><span class="sxs-lookup"><span data-stu-id="64ed5-285">The [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] introduces a mix of interface versions.</span></span> <span data-ttu-id="64ed5-286">Örneğin, her ikisi de `ICorDebugThread3` ve `ICorDebugThread4` üçüncü ve dördüncü sürümlerini görünen `ICorDebugThread` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="64ed5-286">For example, both `ICorDebugThread3` and `ICorDebugThread4` appear as the third and fourth versions of the `ICorDebugThread` interface.</span></span> <span data-ttu-id="64ed5-287">[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] İlk sürümü de tanıtır `ICorDebugStackWalk` arabirimi ve ikinci sürümü `ICorDebugNativeFrame` arabirimi (`ICorDebugNativeFrame2`).</span><span class="sxs-lookup"><span data-stu-id="64ed5-287">The [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] also introduces the first version of the `ICorDebugStackWalk` interface and the second version of the `ICorDebugNativeFrame` interface (`ICorDebugNativeFrame2`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64ed5-288">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64ed5-288">Requirements</span></span>  
 <span data-ttu-id="64ed5-289">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64ed5-289">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64ed5-290">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="64ed5-290">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64ed5-291">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64ed5-291">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64ed5-292">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64ed5-292">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64ed5-293">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64ed5-293">See also</span></span>

- [<span data-ttu-id="64ed5-294">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="64ed5-294">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
