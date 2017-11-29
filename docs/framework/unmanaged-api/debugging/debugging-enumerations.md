---
title: "Hata Ayıklama Numaralandırmaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
caps.latest.revision: "27"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c24882f2bd9819043bbc786bd2e5f35129a92744
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="debugging-enumerations"></a><span data-ttu-id="c9e2f-102">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="c9e2f-102">Debugging Enumerations</span></span>
<span data-ttu-id="c9e2f-103">Bu bölümde, hata ayıklama API'si kullanan yönetilmeyen numaralandırmalar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-103">This section describes the unmanaged enumerations that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c9e2f-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c9e2f-104">In This Section</span></span>  
 [<span data-ttu-id="c9e2f-105">Clr_debuggıng_process_flags numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c9e2f-105">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)  
 <span data-ttu-id="c9e2f-106">Tarafından kullanılan değerleri sağlayan [Iclrdebugging::openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-106">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="c9e2f-107">CLRDataEnumMemoryFlags numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c9e2f-107">CLRDataEnumMemoryFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)  
 <span data-ttu-id="c9e2f-108">Hangi bellek bölümlerinin yapılan bir çağrı gösterir [Iclrdataenummemoryregions::enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) yöntemi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-108">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
 [<span data-ttu-id="c9e2f-109">COR_PUB_ENUMPROCESS numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c9e2f-109">COR_PUB_ENUMPROCESS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)  
 <span data-ttu-id="c9e2f-110">Numaralandırılacak işlem türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-110">Identifies the type of process to be enumerated.</span></span>  
  
 [<span data-ttu-id="c9e2f-111">CorDebugBlockingReason numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c9e2f-111">CorDebugBlockingReason Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingreason-enumeration.md)  
 <span data-ttu-id="c9e2f-112">Bir iş parçacığı neden engellenmiş duruma nedeniyle belirli bir nesne üzerinde belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-112">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
 <span data-ttu-id="c9e2f-113">CorDebugChainReason</span><span class="sxs-lookup"><span data-stu-id="c9e2f-113">CorDebugChainReason</span></span>  
 <span data-ttu-id="c9e2f-114">Neden veya çağrı zincirine başlatma nedenlerle gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-114">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
 [<span data-ttu-id="c9e2f-115">Cordebugcodeınvokekind numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c9e2f-115">CorDebugCodeInvokeKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)  
 <span data-ttu-id="c9e2f-116">Yönetilen kod nasıl verilen işlevi çağırır açıklar.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-116">Describes how an exported function invokes managed code.</span></span>  
  
 [<span data-ttu-id="c9e2f-117">Cordebugcodeınvokepurpose numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c9e2f-117">CorDebugCodeInvokePurpose Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)  
 <span data-ttu-id="c9e2f-118">Yönetilen kod neden verilen işlevi çağırır açıklar.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-118">Describes why an exported function calls managed code.</span></span>  
  
 <span data-ttu-id="c9e2f-119">CorDebugCreateProcessFlags</span><span class="sxs-lookup"><span data-stu-id="c9e2f-119">CorDebugCreateProcessFlags</span></span>  
 <span data-ttu-id="c9e2f-120">Çağrıda kullanılan ek hata ayıklama seçenekleri sunar [Icordebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-120">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="c9e2f-121">CorDebugDebugEventKind numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c9e2f-121">CorDebugDebugEventKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)  
 <span data-ttu-id="c9e2f-122">, Bilgileri kodunu çözdü olay türünü gösterir [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-122">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
 [<span data-ttu-id="c9e2f-123">CorDebugDecodeEventFlagsWindows numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c9e2f-123">CorDebugDecodeEventFlagsWindows Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)  
 <span data-ttu-id="c9e2f-124">Hata ayıklama olaylar hakkında ek bilgi Windows platformunda sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-124">Provides additional information about debug events on the Windows platform.</span></span>  
  
 <span data-ttu-id="c9e2f-125">CorDebugExceptionCallbackType</span><span class="sxs-lookup"><span data-stu-id="c9e2f-125">CorDebugExceptionCallbackType</span></span>  
 <span data-ttu-id="c9e2f-126">Gelen yaptığınız geri çağırma türünü gösteren bir [Icordebugmanagedcallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) olay.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-126">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
 [<span data-ttu-id="c9e2f-127">CorDebugExceptionFlags numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c9e2f-127">CorDebugExceptionFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)  
 <span data-ttu-id="c9e2f-128">Bir özel durum hakkında ek bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-128">Provides additional information about an exception.</span></span>  
  
 <span data-ttu-id="c9e2f-129">CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="c9e2f-129">CorDebugExceptionUnwindCallbackType</span></span>  
 <span data-ttu-id="c9e2f-130">Geri çağırma göre geriye doğru izleme aşamasında işaret olay gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-130">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 [<span data-ttu-id="c9e2f-131">Cordebuggctype sabit listesi</span><span class="sxs-lookup"><span data-stu-id="c9e2f-131">CorDebugGCType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)  
 <span data-ttu-id="c9e2f-132">Çöp toplayıcı bir iş istasyonunda veya sunucuda çalışıp çalışmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-132">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
 [<span data-ttu-id="c9e2f-133">Cordebuggenerationtypes sabit listesi</span><span class="sxs-lookup"><span data-stu-id="c9e2f-133">CorDebugGenerationTypes Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)  
 <span data-ttu-id="c9e2f-134">Bellek bölgesi nesil yönetilen yığında belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-134">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
 <span data-ttu-id="c9e2f-135">CorDebugHandleType</span><span class="sxs-lookup"><span data-stu-id="c9e2f-135">CorDebugHandleType</span></span>  
 <span data-ttu-id="c9e2f-136">Tanıtıcı türü gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-136">Indicates the handle type.</span></span>  
  
 [<span data-ttu-id="c9e2f-137">Cordebugıltonativemappingtypes numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c9e2f-137">CorDebugIlToNativeMappingTypes Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)  
 <span data-ttu-id="c9e2f-138">Yerel yönergeleri belirli bir dizi özel kod bölgesine karşılık gelen olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-138">Indicates whether a particular range of native instructions corresponds to a special code region.</span></span>  
  
 <span data-ttu-id="c9e2f-139">Cordebugıntercept</span><span class="sxs-lookup"><span data-stu-id="c9e2f-139">CorDebugIntercept</span></span>  
 <span data-ttu-id="c9e2f-140">İçine adım adım kod türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-140">Indicates the types of code that can be stepped into.</span></span>  
  
 [<span data-ttu-id="c9e2f-141">Cordebugınterfaceversion numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c9e2f-141">CorDebugInterfaceVersion Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)  
 <span data-ttu-id="c9e2f-142">.NET Framework sürümü ya da bir arabirim kullanılmaya başlanan .NET Framework sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-142">Specifies either a version of the .NET Framework, or the version of the .NET Framework in which an interface was introduced.</span></span>  
  
 <span data-ttu-id="c9e2f-143">Cordebugınternalframetype</span><span class="sxs-lookup"><span data-stu-id="c9e2f-143">CorDebugInternalFrameType</span></span>  
 <span data-ttu-id="c9e2f-144">Yığın çerçevesi türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-144">Identifies the type of stack frame.</span></span>  
  
 [<span data-ttu-id="c9e2f-145">Cordebugjıtcompilerflags numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c9e2f-145">CorDebugJITCompilerFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)  
 <span data-ttu-id="c9e2f-146">Yönetilen tam zamanında (JIT) derleyici davranışını etkilemek değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-146">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
 [<span data-ttu-id="c9e2f-147">Cordebugjıtcompilerflagsdeprecated numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c9e2f-147">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflagsdeprecated-enumeration.md)  
 <span data-ttu-id="c9e2f-148">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-148">Obsolete.</span></span> <span data-ttu-id="c9e2f-149">Kullanım `CORDEBUG_JIT_DEFAULT` üyesi [Cordebugjıtcompilerflags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) numaralandırma yerine.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-149">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
 <span data-ttu-id="c9e2f-150">CorDebugMappingResult</span><span class="sxs-lookup"><span data-stu-id="c9e2f-150">CorDebugMappingResult</span></span>  
 <span data-ttu-id="c9e2f-151">Yönerge işaretçisi (IP) değerini nasıl edinilen ayrıntılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-151">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
 [<span data-ttu-id="c9e2f-152">CorDebugMDAFlags numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c9e2f-152">CorDebugMDAFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)  
 <span data-ttu-id="c9e2f-153">İş parçacığı üzerinde yönetilen hata ayıklama Yardımcısı (MDA) tetiklenir durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-153">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
 [<span data-ttu-id="c9e2f-154">Cordebugngenpolicy sabit listesi</span><span class="sxs-lookup"><span data-stu-id="c9e2f-154">CorDebugNGenPolicy Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)  
 <span data-ttu-id="c9e2f-155">Bir hata ayıklayıcısı yerel görüntü önbellekten yerel (NGen) görüntüler yükler olup olmadığını belirleyen bir değer sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-155">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
 [<span data-ttu-id="c9e2f-156">CorDebugPlatform numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c9e2f-156">CorDebugPlatform Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)  
 <span data-ttu-id="c9e2f-157">Tarafından kullanılan hedef platform değerleri sağlayan [Icordebugdatatarget::getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-157">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
 [<span data-ttu-id="c9e2f-158">CorDebugRecordFormat numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c9e2f-158">CorDebugRecordFormat Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
 <span data-ttu-id="c9e2f-159">Yerel özel durum hata ayıklama olay hakkında bilgi içeren bir bayt dizisi verilerin biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-159">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
 <span data-ttu-id="c9e2f-160">CorDebugRegister</span><span class="sxs-lookup"><span data-stu-id="c9e2f-160">CorDebugRegister</span></span>  
 <span data-ttu-id="c9e2f-161">Verilen işlemci mimarisi ile ilişkili olan kayıtları belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-161">Specifies the registers associated with a given processor architecture.</span></span>  
  
 [<span data-ttu-id="c9e2f-162">CorDebugSetContextFlag numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c9e2f-162">CorDebugSetContextFlag Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)  
 <span data-ttu-id="c9e2f-163">Bağlam etkin olup olmadığını gösterir (veya yaprak) çerçeve yığında veya başka bir çerçevesinden geriye doğru izleme tarafından hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-163">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
 [<span data-ttu-id="c9e2f-164">CorDebugStateChange numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c9e2f-164">CorDebugStateChange Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugstatechange-enumeration.md)  
 <span data-ttu-id="c9e2f-165">Değişiklikleri işleme dayalı atılan gerekir önbelleğe alınan veri miktarı açıklar.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-165">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
 <span data-ttu-id="c9e2f-166">CorDebugStepReason</span><span class="sxs-lookup"><span data-stu-id="c9e2f-166">CorDebugStepReason</span></span>  
 <span data-ttu-id="c9e2f-167">Tek bir adımı sonucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-167">Indicates the outcome of an individual step.</span></span>  
  
 <span data-ttu-id="c9e2f-168">CorDebugThreadState</span><span class="sxs-lookup"><span data-stu-id="c9e2f-168">CorDebugThreadState</span></span>  
 <span data-ttu-id="c9e2f-169">Hata ayıklama için bir iş parçacığı durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-169">Specifies the state of a thread for debugging.</span></span>  
  
 <span data-ttu-id="c9e2f-170">\>CorDebugUnmappedStop</span><span class="sxs-lookup"><span data-stu-id="c9e2f-170">\>CorDebugUnmappedStop</span></span>  
 <span data-ttu-id="c9e2f-171">Kod yürütülmesine durdurmak tarafından Adımlayıcı tetikleyebilir eşlenmemiş kod türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-171">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
 <span data-ttu-id="c9e2f-172">CorDebugUserState</span><span class="sxs-lookup"><span data-stu-id="c9e2f-172">CorDebugUserState</span></span>  
 <span data-ttu-id="c9e2f-173">Bir iş parçacığı kullanıcı durumunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-173">Indicates the user state of a thread.</span></span>  
  
 [<span data-ttu-id="c9e2f-174">CorGCReferenceType sabit listesi</span><span class="sxs-lookup"><span data-stu-id="c9e2f-174">CorGCReferenceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)  
 <span data-ttu-id="c9e2f-175">Çöp toplanan olması için bir nesne kaynak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-175">Identifies the source of an object to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="c9e2f-176">Ilcodekind numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c9e2f-176">ILCodeKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)  
 <span data-ttu-id="c9e2f-177">Hata ayıklayıcı yerel değişkenler veya profiler ReJIT araçları eklenen kod erişmek yapılıp yapılamayacağını belirten değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-177">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="c9e2f-178">LoggingLevelEnum numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c9e2f-178">LoggingLevelEnum Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)  
 <span data-ttu-id="c9e2f-179">Yönetilen iş parçacığı bir olayı günlüğe kaydettiğinde, olay günlüğüne yazılır açıklayıcı bir ileti önem düzeyini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-179">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
 [<span data-ttu-id="c9e2f-180">LogSwitchCallReason numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c9e2f-180">LogSwitchCallReason Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)  
 <span data-ttu-id="c9e2f-181">Hata ayıklama izleme anahtarı üzerinde gerçekleştirilen işlemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-181">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
 [<span data-ttu-id="c9e2f-182">VariableLocationType numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c9e2f-182">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 <span data-ttu-id="c9e2f-183">Bir değişken yerel konum türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-183">Indicates the native location type of a variable.</span></span>  
  
 [<span data-ttu-id="c9e2f-184">WriteableMetadataUpdateMode numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c9e2f-184">WriteableMetadataUpdateMode Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)  
 <span data-ttu-id="c9e2f-185">Bellek içi güncelleştirmeleri meta verilerinin bir hata ayıklayıcısı görünür olup olmadığını belirten değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9e2f-185">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c9e2f-186">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="c9e2f-186">Related Sections</span></span>  
 [<span data-ttu-id="c9e2f-187">Hata ayıklama coclass'ları</span><span class="sxs-lookup"><span data-stu-id="c9e2f-187">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="c9e2f-188">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c9e2f-188">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="c9e2f-189">Hata ayıklama genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="c9e2f-189">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="c9e2f-190">Hata ayıklama yapıları</span><span class="sxs-lookup"><span data-stu-id="c9e2f-190">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
