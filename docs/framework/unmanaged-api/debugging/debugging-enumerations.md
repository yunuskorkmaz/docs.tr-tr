---
title: Hata Ayıklama Numaralandırmaları
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: 7948b78da1db5267ce53364af1e4a26ff73801e0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124327"
---
# <a name="debugging-enumerations"></a><span data-ttu-id="62483-102">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="62483-102">Debugging Enumerations</span></span>
<span data-ttu-id="62483-103">Bu bölümde hata ayıklama API 'sinin kullandığı yönetilmeyen numaralandırmalar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="62483-103">This section describes the unmanaged enumerations that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="62483-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="62483-104">In This Section</span></span>  
 [<span data-ttu-id="62483-105">CLR_DEBUGGING_PROCESS_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-105">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)  
 <span data-ttu-id="62483-106">[ICLRDebugging:: OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) yöntemi tarafından kullanılan değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="62483-106">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="62483-107">CLRDataEnumMemoryFlags Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-107">CLRDataEnumMemoryFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)  
 <span data-ttu-id="62483-108">Hangi bellek bölgelerinin [ıclrdataenummemoryregion:: EnumMemoryRegion](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) yöntemine yönelik bir çağrı içermesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="62483-108">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
 [<span data-ttu-id="62483-109">COR_PUB_ENUMPROCESS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-109">COR_PUB_ENUMPROCESS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)  
 <span data-ttu-id="62483-110">Numaralandırılacak işlemin türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="62483-110">Identifies the type of process to be enumerated.</span></span>  
  
 [<span data-ttu-id="62483-111">CorDebugBlockingReason Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-111">CorDebugBlockingReason Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingreason-enumeration.md)  
 <span data-ttu-id="62483-112">Bir iş parçacığının belirli bir nesne üzerinde engellenip engellenme nedenlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="62483-112">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
 <span data-ttu-id="62483-113">CorDebugChainReason</span><span class="sxs-lookup"><span data-stu-id="62483-113">CorDebugChainReason</span></span>  
 <span data-ttu-id="62483-114">Bir çağrı zincirinin başlatılması için neden veya nedenleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="62483-114">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
 [<span data-ttu-id="62483-115">CorDebugCodeInvokeKind Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-115">CorDebugCodeInvokeKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)  
 <span data-ttu-id="62483-116">Bir içe aktarılmış işlevin yönetilen kodu nasıl çağırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="62483-116">Describes how an exported function invokes managed code.</span></span>  
  
 [<span data-ttu-id="62483-117">CorDebugCodeInvokePurpose Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-117">CorDebugCodeInvokePurpose Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)  
 <span data-ttu-id="62483-118">Bir içe aktarılmış işlevin neden yönetilen kodu çağırıyor olduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="62483-118">Describes why an exported function calls managed code.</span></span>  
  
 <span data-ttu-id="62483-119">CorDebugCreateProcessFlags</span><span class="sxs-lookup"><span data-stu-id="62483-119">CorDebugCreateProcessFlags</span></span>  
 <span data-ttu-id="62483-120">[ICorDebug:: CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) metoduna yapılan bir çağrıda kullanılabilecek ek hata ayıklama seçenekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="62483-120">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="62483-121">CorDebugDebugEventKind Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-121">CorDebugDebugEventKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)  
 <span data-ttu-id="62483-122">Bilgileri [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) yöntemi tarafından kodu çözülen olay türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="62483-122">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
 [<span data-ttu-id="62483-123">CorDebugDecodeEventFlagsWindows Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-123">CorDebugDecodeEventFlagsWindows Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)  
 <span data-ttu-id="62483-124">Windows platformunda hata ayıklama olayları hakkında ek bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="62483-124">Provides additional information about debug events on the Windows platform.</span></span>  
  
 <span data-ttu-id="62483-125">CorDebugExceptionCallbackType</span><span class="sxs-lookup"><span data-stu-id="62483-125">CorDebugExceptionCallbackType</span></span>  
 <span data-ttu-id="62483-126">Bir [ICorDebugManagedCallback2:: Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) olayından yapılan geri aramanın türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="62483-126">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
 [<span data-ttu-id="62483-127">CorDebugExceptionFlags Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-127">CorDebugExceptionFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)  
 <span data-ttu-id="62483-128">Bir özel durum hakkında ek bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="62483-128">Provides additional information about an exception.</span></span>  
  
 <span data-ttu-id="62483-129">CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="62483-129">CorDebugExceptionUnwindCallbackType</span></span>  
 <span data-ttu-id="62483-130">Geriye doğru izleme aşamasında geri çağırma tarafından sinyal edilen olayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="62483-130">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 [<span data-ttu-id="62483-131">CorDebugGCType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-131">CorDebugGCType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)  
 <span data-ttu-id="62483-132">Çöp toplayıcının bir iş istasyonunda veya sunucuda çalışıp çalışmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="62483-132">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
 [<span data-ttu-id="62483-133">CorDebugGenerationTypes Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-133">CorDebugGenerationTypes Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)  
 <span data-ttu-id="62483-134">Yönetilen yığında bir bellek bölgesinin üretilmesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="62483-134">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
 <span data-ttu-id="62483-135">CorDebugHandleType</span><span class="sxs-lookup"><span data-stu-id="62483-135">CorDebugHandleType</span></span>  
 <span data-ttu-id="62483-136">Tanıtıcı türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="62483-136">Indicates the handle type.</span></span>  
  
 [<span data-ttu-id="62483-137">CorDebugIlToNativeMappingTypes Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-137">CorDebugIlToNativeMappingTypes Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)  
 <span data-ttu-id="62483-138">Belirli bir yerel yönerge aralığının özel bir kod bölgesine karşılık geldiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="62483-138">Indicates whether a particular range of native instructions corresponds to a special code region.</span></span>  
  
 <span data-ttu-id="62483-139">CorDebugIntercept</span><span class="sxs-lookup"><span data-stu-id="62483-139">CorDebugIntercept</span></span>  
 <span data-ttu-id="62483-140">İçine bulanan kod türlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="62483-140">Indicates the types of code that can be stepped into.</span></span>  
  
 [<span data-ttu-id="62483-141">CorDebugInterfaceVersion Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-141">CorDebugInterfaceVersion Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)  
 <span data-ttu-id="62483-142">.NET Framework sürümünü veya bir arabirimin tanıtılmasıyla .NET Framework sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="62483-142">Specifies either a version of the .NET Framework, or the version of the .NET Framework in which an interface was introduced.</span></span>  
  
 <span data-ttu-id="62483-143">CorDebugInternalFrameType</span><span class="sxs-lookup"><span data-stu-id="62483-143">CorDebugInternalFrameType</span></span>  
 <span data-ttu-id="62483-144">Yığın çerçevesinin türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="62483-144">Identifies the type of stack frame.</span></span>  
  
 [<span data-ttu-id="62483-145">CorDebugJITCompilerFlags Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-145">CorDebugJITCompilerFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)  
 <span data-ttu-id="62483-146">Yönetilen Just-In-Time (JıT) derleyicisinin davranışını etkileyen değerler içerir.</span><span class="sxs-lookup"><span data-stu-id="62483-146">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
 [<span data-ttu-id="62483-147">CorDebugJITCompilerFlagsDeprecated Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-147">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflagsdeprecated-enumeration.md)  
 <span data-ttu-id="62483-148">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="62483-148">Obsolete.</span></span> <span data-ttu-id="62483-149">Bunun yerine [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) numaralandırmasının `CORDEBUG_JIT_DEFAULT` üyesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="62483-149">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
 <span data-ttu-id="62483-150">CorDebugMappingResult</span><span class="sxs-lookup"><span data-stu-id="62483-150">CorDebugMappingResult</span></span>  
 <span data-ttu-id="62483-151">Yönerge işaretçisinin (IP) değerinin nasıl alındıklarına ilişkin ayrıntıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="62483-151">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
 [<span data-ttu-id="62483-152">CorDebugMDAFlags Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-152">CorDebugMDAFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)  
 <span data-ttu-id="62483-153">Yönetilen hata ayıklama Yardımcısı 'nın (MDA) harekete geçirildiği iş parçacığının durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="62483-153">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
 [<span data-ttu-id="62483-154">CorDebugNGenPolicy Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-154">CorDebugNGenPolicy Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)  
 <span data-ttu-id="62483-155">Bir hata ayıklayıcının yerel görüntü önbelleğinden yerel (NGen) görüntüler yükleyip yüklemeyeceğini belirleyen bir değer sağlar.</span><span class="sxs-lookup"><span data-stu-id="62483-155">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
 [<span data-ttu-id="62483-156">CorDebugPlatform Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-156">CorDebugPlatform Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)  
 <span data-ttu-id="62483-157">[ICorDebugDataTarget:: GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) yöntemi tarafından kullanılan hedef platform değerlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="62483-157">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
 [<span data-ttu-id="62483-158">CorDebugRecordFormat Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-158">CorDebugRecordFormat Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
 <span data-ttu-id="62483-159">Bir yerel özel durum ayıklama olayı hakkında bilgi içeren bir bayt dizisindeki verilerin biçimini açıklar.</span><span class="sxs-lookup"><span data-stu-id="62483-159">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
 <span data-ttu-id="62483-160">CorDebugRegister</span><span class="sxs-lookup"><span data-stu-id="62483-160">CorDebugRegister</span></span>  
 <span data-ttu-id="62483-161">Belirli bir işlemci mimarisiyle ilişkili kayıtları belirtir.</span><span class="sxs-lookup"><span data-stu-id="62483-161">Specifies the registers associated with a given processor architecture.</span></span>  
  
 [<span data-ttu-id="62483-162">CorDebugSetContextFlag Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-162">CorDebugSetContextFlag Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)  
 <span data-ttu-id="62483-163">Bağlamın yığındaki etkin (veya yaprak) kareden mi olduğunu yoksa başka bir çerçeveden geriye doğru bir şekilde mi hesaplandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="62483-163">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
 [<span data-ttu-id="62483-164">CorDebugStateChange Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-164">CorDebugStateChange Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugstatechange-enumeration.md)  
 <span data-ttu-id="62483-165">İşlemdeki değişikliklere göre atılması gereken önbelleğe alınmış verilerin miktarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="62483-165">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
 <span data-ttu-id="62483-166">CorDebugStepReason</span><span class="sxs-lookup"><span data-stu-id="62483-166">CorDebugStepReason</span></span>  
 <span data-ttu-id="62483-167">Tek bir adımın sonucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="62483-167">Indicates the outcome of an individual step.</span></span>  
  
 <span data-ttu-id="62483-168">CorDebugThreadState</span><span class="sxs-lookup"><span data-stu-id="62483-168">CorDebugThreadState</span></span>  
 <span data-ttu-id="62483-169">Hata ayıklama için bir iş parçacığının durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="62483-169">Specifies the state of a thread for debugging.</span></span>  
  
 <span data-ttu-id="62483-170">\>CorDebugUnmappedStop</span><span class="sxs-lookup"><span data-stu-id="62483-170">\>CorDebugUnmappedStop</span></span>  
 <span data-ttu-id="62483-171">Stepper tarafından kod yürütmede bir durdurmak tetikleyemeyecek eşlenmemiş kod türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="62483-171">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
 <span data-ttu-id="62483-172">CorDebugUserState</span><span class="sxs-lookup"><span data-stu-id="62483-172">CorDebugUserState</span></span>  
 <span data-ttu-id="62483-173">Bir iş parçacığının kullanıcı durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="62483-173">Indicates the user state of a thread.</span></span>  
  
 [<span data-ttu-id="62483-174">CorGCReferenceType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-174">CorGCReferenceType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)  
 <span data-ttu-id="62483-175">Atık olarak toplanmış bir nesnenin kaynağını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="62483-175">Identifies the source of an object to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="62483-176">ILCodeKind Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-176">ILCodeKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)  
 <span data-ttu-id="62483-177">Hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen yerel değişkenlere veya koda erişip erişemeyeceğini belirten değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="62483-177">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="62483-178">LoggingLevelEnum Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-178">LoggingLevelEnum Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)  
 <span data-ttu-id="62483-179">Yönetilen bir iş parçacığı bir olay günlüğe kaydederken olay günlüğüne yazılan açıklayıcı bir iletinin önem derecesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="62483-179">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
 [<span data-ttu-id="62483-180">LogSwitchCallReason Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-180">LogSwitchCallReason Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)  
 <span data-ttu-id="62483-181">Hata ayıklama/izleme anahtarı üzerinde gerçekleştirilen işlemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="62483-181">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
 [<span data-ttu-id="62483-182">VariableLocationType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-182">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 <span data-ttu-id="62483-183">Bir değişkenin yerel konum türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="62483-183">Indicates the native location type of a variable.</span></span>  
  
 [<span data-ttu-id="62483-184">WriteableMetadataUpdateMode Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="62483-184">WriteableMetadataUpdateMode Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)  
 <span data-ttu-id="62483-185">Meta verilerde bellek içi güncelleştirmelerin hata ayıklayıcıya görünür olup olmadığını belirten değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="62483-185">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span> 

 <span data-ttu-id="62483-186">[ClrDataSourceType numaralandırması](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md) CLRDATA_IL_ADDRESS_MAP yapısı tarafından kullanılan değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="62483-186">[ClrDataSourceType Enumeration](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md) Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="62483-187">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="62483-187">Related Sections</span></span>  
 [<span data-ttu-id="62483-188">Hata Ayıklama Coclass’ları</span><span class="sxs-lookup"><span data-stu-id="62483-188">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="62483-189">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="62483-189">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="62483-190">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="62483-190">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="62483-191">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="62483-191">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
