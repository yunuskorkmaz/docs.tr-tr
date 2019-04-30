---
title: Hata Ayıklama Numaralandırmaları
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5edd6dfb3dac05ce4614c43949f2ec4c19b5f742
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698518"
---
# <a name="debugging-enumerations"></a><span data-ttu-id="66909-102">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="66909-102">Debugging Enumerations</span></span>
<span data-ttu-id="66909-103">Bu bölümde, hata ayıklama API'SİNİN kullandığı yönetilmeyen numaralandırmaları açıklar.</span><span class="sxs-lookup"><span data-stu-id="66909-103">This section describes the unmanaged enumerations that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="66909-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="66909-104">In This Section</span></span>  
 [<span data-ttu-id="66909-105">CLR_DEBUGGING_PROCESS_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-105">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)  
 <span data-ttu-id="66909-106">Tarafından kullanılan değerleri sağlar [Iclrdebugging::openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="66909-106">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="66909-107">CLRDataEnumMemoryFlags Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-107">CLRDataEnumMemoryFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)  
 <span data-ttu-id="66909-108">Hangi bellek bölgeleri için bir çağrı gösterir [Iclrdataenummemoryregions::enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) yöntemini içerir.</span><span class="sxs-lookup"><span data-stu-id="66909-108">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
 [<span data-ttu-id="66909-109">COR_PUB_ENUMPROCESS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-109">COR_PUB_ENUMPROCESS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)  
 <span data-ttu-id="66909-110">Numaralandırılacak işlem türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="66909-110">Identifies the type of process to be enumerated.</span></span>  
  
 [<span data-ttu-id="66909-111">CorDebugBlockingReason Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-111">CorDebugBlockingReason Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingreason-enumeration.md)  
 <span data-ttu-id="66909-112">Belirli bir nesne üzerinde bir iş parçacığı neden engellenmiş duruma nedenlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="66909-112">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
 <span data-ttu-id="66909-113">CorDebugChainReason</span><span class="sxs-lookup"><span data-stu-id="66909-113">CorDebugChainReason</span></span>  
 <span data-ttu-id="66909-114">Neden veya çağrı zincirinin başlatma nedenlerle gösterir.</span><span class="sxs-lookup"><span data-stu-id="66909-114">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
 [<span data-ttu-id="66909-115">CorDebugCodeInvokeKind Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-115">CorDebugCodeInvokeKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)  
 <span data-ttu-id="66909-116">Dışarı aktarılan bir işlevin yönetilen kod nasıl çağırır açıklar.</span><span class="sxs-lookup"><span data-stu-id="66909-116">Describes how an exported function invokes managed code.</span></span>  
  
 [<span data-ttu-id="66909-117">CorDebugCodeInvokePurpose Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-117">CorDebugCodeInvokePurpose Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)  
 <span data-ttu-id="66909-118">Neden yönetilen kod dışa aktarılan bir işlevin çağrıları açıklar.</span><span class="sxs-lookup"><span data-stu-id="66909-118">Describes why an exported function calls managed code.</span></span>  
  
 <span data-ttu-id="66909-119">CorDebugCreateProcessFlags</span><span class="sxs-lookup"><span data-stu-id="66909-119">CorDebugCreateProcessFlags</span></span>  
 <span data-ttu-id="66909-120">Bir çağrıda kullanılan ek hata ayıklama seçenekleri sağlar [Icordebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="66909-120">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="66909-121">CorDebugDebugEventKind Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-121">CorDebugDebugEventKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)  
 <span data-ttu-id="66909-122">, Bilgileri kodu çözülen olay türünü gösteren [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="66909-122">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
 [<span data-ttu-id="66909-123">CorDebugDecodeEventFlagsWindows Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-123">CorDebugDecodeEventFlagsWindows Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)  
 <span data-ttu-id="66909-124">Hata ayıklama olaylar hakkında ek bilgi için Windows platformunda sağlar.</span><span class="sxs-lookup"><span data-stu-id="66909-124">Provides additional information about debug events on the Windows platform.</span></span>  
  
 <span data-ttu-id="66909-125">CorDebugExceptionCallbackType</span><span class="sxs-lookup"><span data-stu-id="66909-125">CorDebugExceptionCallbackType</span></span>  
 <span data-ttu-id="66909-126">Gelen yapılan bir geri çağırma türünü gösteren bir [Icordebugmanagedcallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) olay.</span><span class="sxs-lookup"><span data-stu-id="66909-126">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
 [<span data-ttu-id="66909-127">CorDebugExceptionFlags Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-127">CorDebugExceptionFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)  
 <span data-ttu-id="66909-128">Bir özel durum hakkında ek bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="66909-128">Provides additional information about an exception.</span></span>  
  
 <span data-ttu-id="66909-129">CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="66909-129">CorDebugExceptionUnwindCallbackType</span></span>  
 <span data-ttu-id="66909-130">Geri çağırma tarafından geriye doğru izleme aşamasında sinyal olay gösterir.</span><span class="sxs-lookup"><span data-stu-id="66909-130">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 [<span data-ttu-id="66909-131">CorDebugGCType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-131">CorDebugGCType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)  
 <span data-ttu-id="66909-132">Atık toplayıcı bir iş istasyonunda veya sunucuda çalışıp çalışmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="66909-132">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
 [<span data-ttu-id="66909-133">CorDebugGenerationTypes Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-133">CorDebugGenerationTypes Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)  
 <span data-ttu-id="66909-134">Yönetilen yığında bir bellek bölgesini oluşturulmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="66909-134">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
 <span data-ttu-id="66909-135">CorDebugHandleType</span><span class="sxs-lookup"><span data-stu-id="66909-135">CorDebugHandleType</span></span>  
 <span data-ttu-id="66909-136">Tanıtıcı türü gösterir.</span><span class="sxs-lookup"><span data-stu-id="66909-136">Indicates the handle type.</span></span>  
  
 [<span data-ttu-id="66909-137">CorDebugIlToNativeMappingTypes Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-137">CorDebugIlToNativeMappingTypes Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)  
 <span data-ttu-id="66909-138">Yerel yönergeleri belirli bir dizi özel kod bölgesine karşılık gelen olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="66909-138">Indicates whether a particular range of native instructions corresponds to a special code region.</span></span>  
  
 <span data-ttu-id="66909-139">Cordebugıntercept</span><span class="sxs-lookup"><span data-stu-id="66909-139">CorDebugIntercept</span></span>  
 <span data-ttu-id="66909-140">İçine girdiğiniz kod türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="66909-140">Indicates the types of code that can be stepped into.</span></span>  
  
 [<span data-ttu-id="66909-141">CorDebugInterfaceVersion Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-141">CorDebugInterfaceVersion Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)  
 <span data-ttu-id="66909-142">.NET Framework sürümünü veya içinde bir arabirimi kullanıma sunulmuştur .NET Framework sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="66909-142">Specifies either a version of the .NET Framework, or the version of the .NET Framework in which an interface was introduced.</span></span>  
  
 <span data-ttu-id="66909-143">Cordebugınternalframetype</span><span class="sxs-lookup"><span data-stu-id="66909-143">CorDebugInternalFrameType</span></span>  
 <span data-ttu-id="66909-144">Yığın çerçevesinin türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="66909-144">Identifies the type of stack frame.</span></span>  
  
 [<span data-ttu-id="66909-145">CorDebugJITCompilerFlags Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-145">CorDebugJITCompilerFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)  
 <span data-ttu-id="66909-146">Yönetilen just-ın-time (JIT) derleyici davranışını etkileyen değerlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="66909-146">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
 [<span data-ttu-id="66909-147">CorDebugJITCompilerFlagsDeprecated Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-147">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflagsdeprecated-enumeration.md)  
 <span data-ttu-id="66909-148">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="66909-148">Obsolete.</span></span> <span data-ttu-id="66909-149">Kullanım `CORDEBUG_JIT_DEFAULT` üyesi [Cordebugjıtcompilerflags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) numaralandırma yerine.</span><span class="sxs-lookup"><span data-stu-id="66909-149">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
 <span data-ttu-id="66909-150">CorDebugMappingResult</span><span class="sxs-lookup"><span data-stu-id="66909-150">CorDebugMappingResult</span></span>  
 <span data-ttu-id="66909-151">Yönerge işaretçisi (IP) değerini nasıl edinilen ayrıntılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="66909-151">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
 [<span data-ttu-id="66909-152">CorDebugMDAFlags Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-152">CorDebugMDAFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)  
 <span data-ttu-id="66909-153">Yönetilen hata ayıklama Yardımcısı (MDA) harekete geçirilen iş parçacığı durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="66909-153">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
 [<span data-ttu-id="66909-154">CorDebugNGenPolicy Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-154">CorDebugNGenPolicy Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)  
 <span data-ttu-id="66909-155">Bir hata ayıklayıcı yerel görüntü önbelleğinden kaldırırız (NGen) yerel görüntüleri yükleyip yüklemediğini belirleyen bir değer sağlar.</span><span class="sxs-lookup"><span data-stu-id="66909-155">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
 [<span data-ttu-id="66909-156">CorDebugPlatform Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-156">CorDebugPlatform Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)  
 <span data-ttu-id="66909-157">Tarafından kullanılan hedef platform değerleri sağlayan [Icordebugdatatarget::getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="66909-157">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
 [<span data-ttu-id="66909-158">CorDebugRecordFormat Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-158">CorDebugRecordFormat Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
 <span data-ttu-id="66909-159">Yerel özel durum hata ayıklama olayla ilgili bilgileri içeren bir bayt dizisi verilerinin biçimini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="66909-159">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
 <span data-ttu-id="66909-160">CorDebugRegister</span><span class="sxs-lookup"><span data-stu-id="66909-160">CorDebugRegister</span></span>  
 <span data-ttu-id="66909-161">Bir verilen işlemci mimarisi ile ilişkili olan kayıtları belirtir.</span><span class="sxs-lookup"><span data-stu-id="66909-161">Specifies the registers associated with a given processor architecture.</span></span>  
  
 [<span data-ttu-id="66909-162">CorDebugSetContextFlag Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-162">CorDebugSetContextFlag Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)  
 <span data-ttu-id="66909-163">Bağlam etkin olup olmadığını belirtir (veya yaprak) çerçevesi yığın üzerinde veya başka bir çerçeveden geriye doğru izleme tarafından hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="66909-163">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
 [<span data-ttu-id="66909-164">CorDebugStateChange Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-164">CorDebugStateChange Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugstatechange-enumeration.md)  
 <span data-ttu-id="66909-165">Değişiklikler iş akışına dayalı atılması gerekir önbelleğe alınan veri miktarı açıklar.</span><span class="sxs-lookup"><span data-stu-id="66909-165">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
 <span data-ttu-id="66909-166">CorDebugStepReason</span><span class="sxs-lookup"><span data-stu-id="66909-166">CorDebugStepReason</span></span>  
 <span data-ttu-id="66909-167">Bir adımın sonucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="66909-167">Indicates the outcome of an individual step.</span></span>  
  
 <span data-ttu-id="66909-168">CorDebugThreadState</span><span class="sxs-lookup"><span data-stu-id="66909-168">CorDebugThreadState</span></span>  
 <span data-ttu-id="66909-169">Hata ayıklama için bir iş parçacığı durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="66909-169">Specifies the state of a thread for debugging.</span></span>  
  
 <span data-ttu-id="66909-170">\>CorDebugUnmappedStop</span><span class="sxs-lookup"><span data-stu-id="66909-170">\>CorDebugUnmappedStop</span></span>  
 <span data-ttu-id="66909-171">Kod yürütülmesine bir durdurmak tarafından adımlayıcıdaki tetikleyebilirsiniz eşlenmemiş kodun türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="66909-171">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
 <span data-ttu-id="66909-172">CorDebugUserState</span><span class="sxs-lookup"><span data-stu-id="66909-172">CorDebugUserState</span></span>  
 <span data-ttu-id="66909-173">Kullanıcı durumunu bir iş parçacığının gösterir.</span><span class="sxs-lookup"><span data-stu-id="66909-173">Indicates the user state of a thread.</span></span>  
  
 [<span data-ttu-id="66909-174">CorGCReferenceType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-174">CorGCReferenceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)  
 <span data-ttu-id="66909-175">Kaynağı olarak atık olarak toplanmış bir nesneyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="66909-175">Identifies the source of an object to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="66909-176">ILCodeKind Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-176">ILCodeKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)  
 <span data-ttu-id="66909-177">Hata ayıklayıcı yerel değişkenler veya ReJIT izleme profil oluşturucu, eklenen kod erişmek mümkün olup olmadığını belirten değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="66909-177">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="66909-178">LoggingLevelEnum Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-178">LoggingLevelEnum Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)  
 <span data-ttu-id="66909-179">Yönetilen iş parçacığı bir olayı günlüğe kaydettiğinde, olay günlüğüne yazılan açıklayıcı bir iletisi önem derecesi düzeyini gösterir.</span><span class="sxs-lookup"><span data-stu-id="66909-179">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
 [<span data-ttu-id="66909-180">LogSwitchCallReason Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-180">LogSwitchCallReason Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)  
 <span data-ttu-id="66909-181">Hata ayıklama izlemeyi anahtarda gerçekleştirilen bir işlemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="66909-181">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
 [<span data-ttu-id="66909-182">VariableLocationType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-182">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 <span data-ttu-id="66909-183">Bir değişken yerel konum türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="66909-183">Indicates the native location type of a variable.</span></span>  
  
 [<span data-ttu-id="66909-184">WriteableMetadataUpdateMode Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="66909-184">WriteableMetadataUpdateMode Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)  
 <span data-ttu-id="66909-185">Meta veriler için bellek içi güncelleştirmeler için bir hata ayıklayıcı görünür olup olmadığını belirten değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="66909-185">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span> 

 <span data-ttu-id="66909-186">[ClrDataSourceType numaralandırma](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md) CLRDATA_IL_ADDRESS_MAP yapısı tarafından kullanılan değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="66909-186">[ClrDataSourceType Enumeration](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md) Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="66909-187">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="66909-187">Related Sections</span></span>  
 [<span data-ttu-id="66909-188">Hata Ayıklama Coclass’ları</span><span class="sxs-lookup"><span data-stu-id="66909-188">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="66909-189">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="66909-189">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="66909-190">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="66909-190">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="66909-191">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="66909-191">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
