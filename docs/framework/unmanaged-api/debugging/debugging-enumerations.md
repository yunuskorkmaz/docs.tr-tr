---
title: Hata Ayıklama Numaralandırmaları
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: a83b1aa0b2cc068ed2f73dca04083b1085d45201
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789168"
---
# <a name="debugging-enumerations"></a><span data-ttu-id="a94a8-102">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="a94a8-102">Debugging Enumerations</span></span>
<span data-ttu-id="a94a8-103">Bu bölümde hata ayıklama API 'sinin kullandığı yönetilmeyen numaralandırmalar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a94a8-103">This section describes the unmanaged enumerations that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a94a8-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a94a8-104">In This Section</span></span>  
 [<span data-ttu-id="a94a8-105">CLR_DEBUGGING_PROCESS_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-105">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>](clr-debugging-process-flags-enumeration.md)  
 <span data-ttu-id="a94a8-106">[ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) yöntemi tarafından kullanılan değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="a94a8-106">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="a94a8-107">CLRDataEnumMemoryFlags Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-107">CLRDataEnumMemoryFlags Enumeration</span></span>](clrdataenummemoryflags-enumeration.md)  
 <span data-ttu-id="a94a8-108">Hangi bellek bölgelerinin [ıclrdataenummemoryregion:: EnumMemoryRegion](iclrdataenummemoryregions-enummemoryregions-method.md) yöntemine yönelik bir çağrı içermesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a94a8-108">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
 [<span data-ttu-id="a94a8-109">COR_PUB_ENUMPROCESS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-109">COR_PUB_ENUMPROCESS Enumeration</span></span>](cor-pub-enumprocess-enumeration.md)  
 <span data-ttu-id="a94a8-110">Numaralandırılacak işlemin türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a94a8-110">Identifies the type of process to be enumerated.</span></span>  
  
 [<span data-ttu-id="a94a8-111">CorDebugBlockingReason Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-111">CorDebugBlockingReason Enumeration</span></span>](cordebugblockingreason-enumeration.md)  
 <span data-ttu-id="a94a8-112">Bir iş parçacığının belirli bir nesne üzerinde engellenip engellenme nedenlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a94a8-112">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
 <span data-ttu-id="a94a8-113">CorDebugChainReason</span><span class="sxs-lookup"><span data-stu-id="a94a8-113">CorDebugChainReason</span></span>  
 <span data-ttu-id="a94a8-114">Bir çağrı zincirinin başlatılması için neden veya nedenleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="a94a8-114">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
 [<span data-ttu-id="a94a8-115">CorDebugCodeInvokeKind Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-115">CorDebugCodeInvokeKind Enumeration</span></span>](cordebugcodeinvokekind-enumeration.md)  
 <span data-ttu-id="a94a8-116">Bir içe aktarılmış işlevin yönetilen kodu nasıl çağırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a94a8-116">Describes how an exported function invokes managed code.</span></span>  
  
 [<span data-ttu-id="a94a8-117">CorDebugCodeInvokePurpose Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-117">CorDebugCodeInvokePurpose Enumeration</span></span>](cordebugcodeinvokepurpose-enumeration.md)  
 <span data-ttu-id="a94a8-118">Bir içe aktarılmış işlevin neden yönetilen kodu çağırıyor olduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="a94a8-118">Describes why an exported function calls managed code.</span></span>  
  
 <span data-ttu-id="a94a8-119">CorDebugCreateProcessFlags</span><span class="sxs-lookup"><span data-stu-id="a94a8-119">CorDebugCreateProcessFlags</span></span>  
 <span data-ttu-id="a94a8-120">[ICorDebug:: CreateProcess](icordebug-createprocess-method.md) metoduna yapılan bir çağrıda kullanılabilecek ek hata ayıklama seçenekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="a94a8-120">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](icordebug-createprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="a94a8-121">CorDebugDebugEventKind Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-121">CorDebugDebugEventKind Enumeration</span></span>](cordebugdebugeventkind-enumeration.md)  
 <span data-ttu-id="a94a8-122">Bilgileri [DecodeEvent](icordebugprocess6-decodeevent-method.md) yöntemi tarafından kodu çözülen olay türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="a94a8-122">Indicates the type of event whose information is decoded by the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
 [<span data-ttu-id="a94a8-123">CorDebugDecodeEventFlagsWindows Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-123">CorDebugDecodeEventFlagsWindows Enumeration</span></span>](cordebugdecodeeventflagswindows-enumeration.md)  
 <span data-ttu-id="a94a8-124">Windows platformunda hata ayıklama olayları hakkında ek bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a94a8-124">Provides additional information about debug events on the Windows platform.</span></span>  
  
 <span data-ttu-id="a94a8-125">CorDebugExceptionCallbackType</span><span class="sxs-lookup"><span data-stu-id="a94a8-125">CorDebugExceptionCallbackType</span></span>  
 <span data-ttu-id="a94a8-126">Bir [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md) olayından yapılan geri aramanın türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="a94a8-126">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
 [<span data-ttu-id="a94a8-127">CorDebugExceptionFlags Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-127">CorDebugExceptionFlags Enumeration</span></span>](cordebugexceptionflags-enumeration.md)  
 <span data-ttu-id="a94a8-128">Bir özel durum hakkında ek bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a94a8-128">Provides additional information about an exception.</span></span>  
  
 <span data-ttu-id="a94a8-129">CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="a94a8-129">CorDebugExceptionUnwindCallbackType</span></span>  
 <span data-ttu-id="a94a8-130">Geriye doğru izleme aşamasında geri çağırma tarafından sinyal edilen olayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a94a8-130">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 [<span data-ttu-id="a94a8-131">CorDebugGCType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-131">CorDebugGCType Enumeration</span></span>](cordebuggctype-enumeration.md)  
 <span data-ttu-id="a94a8-132">Çöp toplayıcının bir iş istasyonunda veya sunucuda çalışıp çalışmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a94a8-132">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
 [<span data-ttu-id="a94a8-133">CorDebugGenerationTypes Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-133">CorDebugGenerationTypes Enumeration</span></span>](cordebuggenerationtypes-enumeration.md)  
 <span data-ttu-id="a94a8-134">Yönetilen yığında bir bellek bölgesinin üretilmesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a94a8-134">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
 <span data-ttu-id="a94a8-135">CorDebugHandleType</span><span class="sxs-lookup"><span data-stu-id="a94a8-135">CorDebugHandleType</span></span>  
 <span data-ttu-id="a94a8-136">Tanıtıcı türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="a94a8-136">Indicates the handle type.</span></span>  
  
 [<span data-ttu-id="a94a8-137">CorDebugIlToNativeMappingTypes Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-137">CorDebugIlToNativeMappingTypes Enumeration</span></span>](cordebugiltonativemappingtypes-enumeration.md)  
 <span data-ttu-id="a94a8-138">Belirli bir yerel yönerge aralığının özel bir kod bölgesine karşılık geldiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a94a8-138">Indicates whether a particular range of native instructions corresponds to a special code region.</span></span>  
  
 <span data-ttu-id="a94a8-139">CorDebugIntercept</span><span class="sxs-lookup"><span data-stu-id="a94a8-139">CorDebugIntercept</span></span>  
 <span data-ttu-id="a94a8-140">İçine bulanan kod türlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a94a8-140">Indicates the types of code that can be stepped into.</span></span>  
  
 [<span data-ttu-id="a94a8-141">CorDebugInterfaceVersion Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-141">CorDebugInterfaceVersion Enumeration</span></span>](cordebuginterfaceversion-enumeration.md)  
 <span data-ttu-id="a94a8-142">.NET Framework sürümünü veya bir arabirimin tanıtılmasıyla .NET Framework sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a94a8-142">Specifies either a version of the .NET Framework, or the version of the .NET Framework in which an interface was introduced.</span></span>  
  
 <span data-ttu-id="a94a8-143">CorDebugInternalFrameType</span><span class="sxs-lookup"><span data-stu-id="a94a8-143">CorDebugInternalFrameType</span></span>  
 <span data-ttu-id="a94a8-144">Yığın çerçevesinin türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a94a8-144">Identifies the type of stack frame.</span></span>  
  
 [<span data-ttu-id="a94a8-145">CorDebugJITCompilerFlags Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-145">CorDebugJITCompilerFlags Enumeration</span></span>](cordebugjitcompilerflags-enumeration.md)  
 <span data-ttu-id="a94a8-146">Yönetilen Just-In-Time (JıT) derleyicisinin davranışını etkileyen değerler içerir.</span><span class="sxs-lookup"><span data-stu-id="a94a8-146">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
 [<span data-ttu-id="a94a8-147">CorDebugJITCompilerFlagsDeprecated Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-147">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>](cordebugjitcompilerflagsdeprecated-enumeration.md)  
 <span data-ttu-id="a94a8-148">{1&gt;Artık kullanılmıyor.&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a94a8-148">Obsolete.</span></span> <span data-ttu-id="a94a8-149">Bunun yerine [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) numaralandırmasının `CORDEBUG_JIT_DEFAULT` üyesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a94a8-149">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
 <span data-ttu-id="a94a8-150">CorDebugMappingResult</span><span class="sxs-lookup"><span data-stu-id="a94a8-150">CorDebugMappingResult</span></span>  
 <span data-ttu-id="a94a8-151">Yönerge işaretçisinin (IP) değerinin nasıl alındıklarına ilişkin ayrıntıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="a94a8-151">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
 [<span data-ttu-id="a94a8-152">CorDebugMDAFlags Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-152">CorDebugMDAFlags Enumeration</span></span>](cordebugmdaflags-enumeration.md)  
 <span data-ttu-id="a94a8-153">Yönetilen hata ayıklama Yardımcısı 'nın (MDA) harekete geçirildiği iş parçacığının durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a94a8-153">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
 [<span data-ttu-id="a94a8-154">CorDebugNGenPolicy Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-154">CorDebugNGenPolicy Enumeration</span></span>](cordebugngenpolicy-enumeration.md)  
 <span data-ttu-id="a94a8-155">Bir hata ayıklayıcının yerel görüntü önbelleğinden yerel (NGen) görüntüler yükleyip yüklemeyeceğini belirleyen bir değer sağlar.</span><span class="sxs-lookup"><span data-stu-id="a94a8-155">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
 [<span data-ttu-id="a94a8-156">CorDebugPlatform Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-156">CorDebugPlatform Enumeration</span></span>](cordebugplatform-enumeration.md)  
 <span data-ttu-id="a94a8-157">[ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) yöntemi tarafından kullanılan hedef platform değerlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a94a8-157">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
 [<span data-ttu-id="a94a8-158">CorDebugRecordFormat Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-158">CorDebugRecordFormat Enumeration</span></span>](cordebugrecordformat-enumeration.md)  
 <span data-ttu-id="a94a8-159">Bir yerel özel durum ayıklama olayı hakkında bilgi içeren bir bayt dizisindeki verilerin biçimini açıklar.</span><span class="sxs-lookup"><span data-stu-id="a94a8-159">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
 <span data-ttu-id="a94a8-160">CorDebugRegister</span><span class="sxs-lookup"><span data-stu-id="a94a8-160">CorDebugRegister</span></span>  
 <span data-ttu-id="a94a8-161">Belirli bir işlemci mimarisiyle ilişkili kayıtları belirtir.</span><span class="sxs-lookup"><span data-stu-id="a94a8-161">Specifies the registers associated with a given processor architecture.</span></span>  
  
 [<span data-ttu-id="a94a8-162">CorDebugSetContextFlag Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-162">CorDebugSetContextFlag Enumeration</span></span>](cordebugsetcontextflag-enumeration.md)  
 <span data-ttu-id="a94a8-163">Bağlamın yığındaki etkin (veya yaprak) kareden mi olduğunu yoksa başka bir çerçeveden geriye doğru bir şekilde mi hesaplandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a94a8-163">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
 [<span data-ttu-id="a94a8-164">CorDebugStateChange Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-164">CorDebugStateChange Enumeration</span></span>](cordebugstatechange-enumeration.md)  
 <span data-ttu-id="a94a8-165">İşlemdeki değişikliklere göre atılması gereken önbelleğe alınmış verilerin miktarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a94a8-165">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
 <span data-ttu-id="a94a8-166">CorDebugStepReason</span><span class="sxs-lookup"><span data-stu-id="a94a8-166">CorDebugStepReason</span></span>  
 <span data-ttu-id="a94a8-167">Tek bir adımın sonucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a94a8-167">Indicates the outcome of an individual step.</span></span>  
  
 <span data-ttu-id="a94a8-168">CorDebugThreadState</span><span class="sxs-lookup"><span data-stu-id="a94a8-168">CorDebugThreadState</span></span>  
 <span data-ttu-id="a94a8-169">Hata ayıklama için bir iş parçacığının durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a94a8-169">Specifies the state of a thread for debugging.</span></span>  
  
 <span data-ttu-id="a94a8-170">\>CorDebugUnmappedStop</span><span class="sxs-lookup"><span data-stu-id="a94a8-170">\>CorDebugUnmappedStop</span></span>  
 <span data-ttu-id="a94a8-171">Stepper tarafından kod yürütmede bir durdurmak tetikleyemeyecek eşlenmemiş kod türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="a94a8-171">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
 <span data-ttu-id="a94a8-172">CorDebugUserState</span><span class="sxs-lookup"><span data-stu-id="a94a8-172">CorDebugUserState</span></span>  
 <span data-ttu-id="a94a8-173">Bir iş parçacığının kullanıcı durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="a94a8-173">Indicates the user state of a thread.</span></span>  
  
 [<span data-ttu-id="a94a8-174">CorGCReferenceType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-174">CorGCReferenceType Enumeration</span></span>](corgcreferencetype-enumeration.md)  
 <span data-ttu-id="a94a8-175">Atık olarak toplanmış bir nesnenin kaynağını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a94a8-175">Identifies the source of an object to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="a94a8-176">ILCodeKind Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-176">ILCodeKind Enumeration</span></span>](ilcodekind-enumeration.md)  
 <span data-ttu-id="a94a8-177">Hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen yerel değişkenlere veya koda erişip erişemeyeceğini belirten değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a94a8-177">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="a94a8-178">LoggingLevelEnum Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-178">LoggingLevelEnum Enumeration</span></span>](logginglevelenum-enumeration.md)  
 <span data-ttu-id="a94a8-179">Yönetilen bir iş parçacığı bir olay günlüğe kaydederken olay günlüğüne yazılan açıklayıcı bir iletinin önem derecesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a94a8-179">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
 [<span data-ttu-id="a94a8-180">LogSwitchCallReason Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-180">LogSwitchCallReason Enumeration</span></span>](logswitchcallreason-enumeration.md)  
 <span data-ttu-id="a94a8-181">Hata ayıklama/izleme anahtarı üzerinde gerçekleştirilen işlemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="a94a8-181">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
 [<span data-ttu-id="a94a8-182">VariableLocationType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-182">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)  
 <span data-ttu-id="a94a8-183">Bir değişkenin yerel konum türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="a94a8-183">Indicates the native location type of a variable.</span></span>  
  
 [<span data-ttu-id="a94a8-184">WriteableMetadataUpdateMode Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a94a8-184">WriteableMetadataUpdateMode Enumeration</span></span>](writeablemetadataupdatemode-enumeration.md)  
 <span data-ttu-id="a94a8-185">Meta verilerde bellek içi güncelleştirmelerin hata ayıklayıcıya görünür olup olmadığını belirten değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a94a8-185">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span> 

 <span data-ttu-id="a94a8-186">[ClrDataSourceType numaralandırması](clrdatasourcetype-enumeration.md) CLRDATA_IL_ADDRESS_MAP yapısı tarafından kullanılan değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="a94a8-186">[ClrDataSourceType Enumeration](clrdatasourcetype-enumeration.md) Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="a94a8-187">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="a94a8-187">Related Sections</span></span>  
 [<span data-ttu-id="a94a8-188">Hata Ayıklama Coclass’ları</span><span class="sxs-lookup"><span data-stu-id="a94a8-188">Debugging Coclasses</span></span>](debugging-coclasses.md)  
  
 [<span data-ttu-id="a94a8-189">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a94a8-189">Debugging Interfaces</span></span>](debugging-interfaces.md)  
  
 [<span data-ttu-id="a94a8-190">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="a94a8-190">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)  
  
 [<span data-ttu-id="a94a8-191">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="a94a8-191">Debugging Structures</span></span>](debugging-structures.md)
