---
title: Hata Ayıklama Numaralandırmaları
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: c37b6ff42b428184d301d63b6dbbd9d80a72bf3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179137"
---
# <a name="debugging-enumerations"></a><span data-ttu-id="9438a-102">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="9438a-102">Debugging Enumerations</span></span>
<span data-ttu-id="9438a-103">Bu bölümde, hata ayıklama API'sinin kullandığı yönetilmeyen sayısallaştırmalar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9438a-103">This section describes the unmanaged enumerations that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9438a-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9438a-104">In This Section</span></span>  
 [<span data-ttu-id="9438a-105">CLR_DEBUGGING_PROCESS_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9438a-105">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>](clr-debugging-process-flags-enumeration.md)  
 <span data-ttu-id="9438a-106">[ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) yöntemi tarafından kullanılan değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="9438a-106">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="9438a-107">CLRDataEnumMemoryFlags Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="9438a-107">CLRDataEnumMemoryFlags Enumeration</span></span>](clrdataenummemoryflags-enumeration.md)  
 <span data-ttu-id="9438a-108">[ICLRDataEnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) için bir çağrı hangi bellek bölgeleri gösterir::EnumMemoryRegions yöntemi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="9438a-108">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
 [<span data-ttu-id="9438a-109">COR_PUB_ENUMPROCESS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9438a-109">COR_PUB_ENUMPROCESS Enumeration</span></span>](cor-pub-enumprocess-enumeration.md)  
 <span data-ttu-id="9438a-110">Numaralandırılacak işlem türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9438a-110">Identifies the type of process to be enumerated.</span></span>  
  
 [<span data-ttu-id="9438a-111">CorDebugBlockingReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9438a-111">CorDebugBlockingReason Enumeration</span></span>](cordebugblockingreason-enumeration.md)  
 <span data-ttu-id="9438a-112">Bir iş parçacığının belirli bir nesne üzerinde engellenme nedenlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9438a-112">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
 <span data-ttu-id="9438a-113">CorDebugChainReason</span><span class="sxs-lookup"><span data-stu-id="9438a-113">CorDebugChainReason</span></span>  
 <span data-ttu-id="9438a-114">Çağrı zincirinin başlatılmasının nedenini veya nedenlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9438a-114">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
 [<span data-ttu-id="9438a-115">CorDebugCodeInvokeKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9438a-115">CorDebugCodeInvokeKind Enumeration</span></span>](cordebugcodeinvokekind-enumeration.md)  
 <span data-ttu-id="9438a-116">Dışa aktarılan bir işlevin yönetilen kodu nasıl çağırdığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9438a-116">Describes how an exported function invokes managed code.</span></span>  
  
 [<span data-ttu-id="9438a-117">CorDebugCodeInvokePurpose Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9438a-117">CorDebugCodeInvokePurpose Enumeration</span></span>](cordebugcodeinvokepurpose-enumeration.md)  
 <span data-ttu-id="9438a-118">Dışa aktarılan bir işlevin yönetilen kodu neden aradığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9438a-118">Describes why an exported function calls managed code.</span></span>  
  
 <span data-ttu-id="9438a-119">CorDebugCreateProcessFlags</span><span class="sxs-lookup"><span data-stu-id="9438a-119">CorDebugCreateProcessFlags</span></span>  
 <span data-ttu-id="9438a-120">[ICorDebug::CreateProcess](icordebug-createprocess-method.md) yöntemine yapılan bir çağrıda kullanılabilecek ek hata ayıklama seçenekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="9438a-120">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](icordebug-createprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="9438a-121">CorDebugDebugEventKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9438a-121">CorDebugDebugEventKind Enumeration</span></span>](cordebugdebugeventkind-enumeration.md)  
 <span data-ttu-id="9438a-122">[DecodeEvent](icordebugprocess6-decodeevent-method.md) yöntemiyle bilgileri deşifre edilen olayın türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="9438a-122">Indicates the type of event whose information is decoded by the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
 [<span data-ttu-id="9438a-123">CorDebugDecodeEventFlagsWindows Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="9438a-123">CorDebugDecodeEventFlagsWindows Enumeration</span></span>](cordebugdecodeeventflagswindows-enumeration.md)  
 <span data-ttu-id="9438a-124">Windows platformundaki hata ayıklama olayları hakkında ek bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9438a-124">Provides additional information about debug events on the Windows platform.</span></span>  
  
 <span data-ttu-id="9438a-125">CorDebugExceptionCallbackType</span><span class="sxs-lookup"><span data-stu-id="9438a-125">CorDebugExceptionCallbackType</span></span>  
 <span data-ttu-id="9438a-126">[ICorDebugManagedCallback2::Özel durum](icordebugmanagedcallback2-exception-method.md) olayından yapılan geri arama türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="9438a-126">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
 [<span data-ttu-id="9438a-127">CorDebugExceptionFlags Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="9438a-127">CorDebugExceptionFlags Enumeration</span></span>](cordebugexceptionflags-enumeration.md)  
 <span data-ttu-id="9438a-128">Özel durum hakkında ek bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9438a-128">Provides additional information about an exception.</span></span>  
  
 <span data-ttu-id="9438a-129">CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="9438a-129">CorDebugExceptionUnwindCallbackType</span></span>  
 <span data-ttu-id="9438a-130">Gevşeme aşamasında geri arama tarafından sinyal verilen olayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="9438a-130">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 [<span data-ttu-id="9438a-131">CorDebugGCType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="9438a-131">CorDebugGCType Enumeration</span></span>](cordebuggctype-enumeration.md)  
 <span data-ttu-id="9438a-132">Çöp toplayıcısının iş istasyonunda mı yoksa sunucuda mı çalıştığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9438a-132">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
 [<span data-ttu-id="9438a-133">CorDebugGenerationTypes Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="9438a-133">CorDebugGenerationTypes Enumeration</span></span>](cordebuggenerationtypes-enumeration.md)  
 <span data-ttu-id="9438a-134">Yönetilen yığında bellek bir bölgenin nesil belirtir.</span><span class="sxs-lookup"><span data-stu-id="9438a-134">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
 <span data-ttu-id="9438a-135">CorDebugHandleType</span><span class="sxs-lookup"><span data-stu-id="9438a-135">CorDebugHandleType</span></span>  
 <span data-ttu-id="9438a-136">Tutamaç türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="9438a-136">Indicates the handle type.</span></span>  
  
 [<span data-ttu-id="9438a-137">CorDebugIlToNativeMappingTypes Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9438a-137">CorDebugIlToNativeMappingTypes Enumeration</span></span>](cordebugiltonativemappingtypes-enumeration.md)  
 <span data-ttu-id="9438a-138">Belirli bir yerel yönerge aralığının özel bir kod bölgesine karşılık gelip gelmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9438a-138">Indicates whether a particular range of native instructions corresponds to a special code region.</span></span>  
  
 <span data-ttu-id="9438a-139">CorDebugIntercept</span><span class="sxs-lookup"><span data-stu-id="9438a-139">CorDebugIntercept</span></span>  
 <span data-ttu-id="9438a-140">Adım atılabilir kod türlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9438a-140">Indicates the types of code that can be stepped into.</span></span>  
  
 [<span data-ttu-id="9438a-141">CorDebugInterfaceVersion Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9438a-141">CorDebugInterfaceVersion Enumeration</span></span>](cordebuginterfaceversion-enumeration.md)  
 <span data-ttu-id="9438a-142">.NET Framework'ün bir sürümünü veya arabirimin tanıtıldığı .NET Framework sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="9438a-142">Specifies either a version of the .NET Framework, or the version of the .NET Framework in which an interface was introduced.</span></span>  
  
 <span data-ttu-id="9438a-143">CorDebugInternalFrameType</span><span class="sxs-lookup"><span data-stu-id="9438a-143">CorDebugInternalFrameType</span></span>  
 <span data-ttu-id="9438a-144">Yığın çerçevesinin türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9438a-144">Identifies the type of stack frame.</span></span>  
  
 [<span data-ttu-id="9438a-145">CorDebugJITCompilerFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9438a-145">CorDebugJITCompilerFlags Enumeration</span></span>](cordebugjitcompilerflags-enumeration.md)  
 <span data-ttu-id="9438a-146">Yönetilen tam zamanında (JIT) derleyicisinin davranışını etkileyen değerler içerir.</span><span class="sxs-lookup"><span data-stu-id="9438a-146">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
 [<span data-ttu-id="9438a-147">CorDebugJITCompilerFlagsDeprecated Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9438a-147">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>](cordebugjitcompilerflagsdeprecated-enumeration.md)  
 <span data-ttu-id="9438a-148">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="9438a-148">Obsolete.</span></span> <span data-ttu-id="9438a-149">Bunun `CORDEBUG_JIT_DEFAULT` yerine [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) numaralandırma üyesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9438a-149">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
 <span data-ttu-id="9438a-150">CorDebugMappingResult</span><span class="sxs-lookup"><span data-stu-id="9438a-150">CorDebugMappingResult</span></span>  
 <span data-ttu-id="9438a-151">Yönerge işaretçisinin (IP) değerinin nasıl elde edildiğine ilişkin ayrıntıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="9438a-151">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
 [<span data-ttu-id="9438a-152">CorDebugMDAFlags Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="9438a-152">CorDebugMDAFlags Enumeration</span></span>](cordebugmdaflags-enumeration.md)  
 <span data-ttu-id="9438a-153">Yönetilen hata ayıklama yardımcısının (MDA) kovulduğunuiş iş parçacığının durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="9438a-153">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
 [<span data-ttu-id="9438a-154">CorDebugNGenPolicy Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="9438a-154">CorDebugNGenPolicy Enumeration</span></span>](cordebugngenpolicy-enumeration.md)  
 <span data-ttu-id="9438a-155">Hata ayıkıcının yerel görüntü önbelleğinden yerel (NGen) görüntüler yükleyip yüklemediğini belirleyen bir değer sağlar.</span><span class="sxs-lookup"><span data-stu-id="9438a-155">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
 [<span data-ttu-id="9438a-156">CorDebugPlatform Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9438a-156">CorDebugPlatform Enumeration</span></span>](cordebugplatform-enumeration.md)  
 <span data-ttu-id="9438a-157">[ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) yöntemi tarafından kullanılan hedef platform değerlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="9438a-157">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
 [<span data-ttu-id="9438a-158">CorDebugRecordFormat Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="9438a-158">CorDebugRecordFormat Enumeration</span></span>](cordebugrecordformat-enumeration.md)  
 <span data-ttu-id="9438a-159">Yerel bir özel durum hata ayıklama olayı hakkında bilgi içeren bir bayt dizisinde verilerin biçimini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9438a-159">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
 <span data-ttu-id="9438a-160">CorDebugRegister</span><span class="sxs-lookup"><span data-stu-id="9438a-160">CorDebugRegister</span></span>  
 <span data-ttu-id="9438a-161">Belirli bir işlemci mimarisiyle ilişkili kayıtları belirtir.</span><span class="sxs-lookup"><span data-stu-id="9438a-161">Specifies the registers associated with a given processor architecture.</span></span>  
  
 [<span data-ttu-id="9438a-162">CorDebugSetContextFlag Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9438a-162">CorDebugSetContextFlag Enumeration</span></span>](cordebugsetcontextflag-enumeration.md)  
 <span data-ttu-id="9438a-163">Bağlamın yığındaki etkin (veya yaprak) çerçeveden mi yoksa başka bir çerçeveden gevşemeyle hesaplanıp hesaplanmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9438a-163">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
 [<span data-ttu-id="9438a-164">CorDebugStateChange Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="9438a-164">CorDebugStateChange Enumeration</span></span>](cordebugstatechange-enumeration.md)  
 <span data-ttu-id="9438a-165">İşlemdeki değişikliklere bağlı olarak atılması gereken önbelleğe alınmış veri miktarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9438a-165">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
 <span data-ttu-id="9438a-166">CorDebugStepReason</span><span class="sxs-lookup"><span data-stu-id="9438a-166">CorDebugStepReason</span></span>  
 <span data-ttu-id="9438a-167">Tek bir adımın sonucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9438a-167">Indicates the outcome of an individual step.</span></span>  
  
 <span data-ttu-id="9438a-168">CorDebugThreadState</span><span class="sxs-lookup"><span data-stu-id="9438a-168">CorDebugThreadState</span></span>  
 <span data-ttu-id="9438a-169">Hata ayıklama için bir iş parçacığının durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="9438a-169">Specifies the state of a thread for debugging.</span></span>  
  
 <span data-ttu-id="9438a-170">\>CorDebugUnmappedStop</span><span class="sxs-lookup"><span data-stu-id="9438a-170">\>CorDebugUnmappedStop</span></span>  
 <span data-ttu-id="9438a-171">Adım layıcı tarafından kod yürütülmesinde durmayı tetiklenebilen eşlenmemiş kod türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="9438a-171">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
 <span data-ttu-id="9438a-172">CorDebugUserState</span><span class="sxs-lookup"><span data-stu-id="9438a-172">CorDebugUserState</span></span>  
 <span data-ttu-id="9438a-173">İş parçacığının kullanıcı durumunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9438a-173">Indicates the user state of a thread.</span></span>  
  
 [<span data-ttu-id="9438a-174">CorGCReferenceType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="9438a-174">CorGCReferenceType Enumeration</span></span>](corgcreferencetype-enumeration.md)  
 <span data-ttu-id="9438a-175">Çöp toplanacak bir nesnenin kaynağını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9438a-175">Identifies the source of an object to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="9438a-176">ILCodeKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9438a-176">ILCodeKind Enumeration</span></span>](ilcodekind-enumeration.md)  
 <span data-ttu-id="9438a-177">Hata ayıklayıcının yerel değişkenlere veya profil oluşturucu ReJIT enstrümantasyonuna eklenen koda erişip erişemeyeceğini belirten değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9438a-177">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="9438a-178">LoggingLevelEnum Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="9438a-178">LoggingLevelEnum Enumeration</span></span>](logginglevelenum-enumeration.md)  
 <span data-ttu-id="9438a-179">Yönetilen bir iş parçacığı bir olay günlüğe kaydettiğinde olay günlüğüne yazılan açıklayıcı iletinin önem düzeyini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9438a-179">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
 [<span data-ttu-id="9438a-180">LogSwitchCallReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9438a-180">LogSwitchCallReason Enumeration</span></span>](logswitchcallreason-enumeration.md)  
 <span data-ttu-id="9438a-181">Hata ayıklama/izleme anahtarında gerçekleştirilen işlemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="9438a-181">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
 [<span data-ttu-id="9438a-182">VariableLocationType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="9438a-182">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)  
 <span data-ttu-id="9438a-183">Bir değişkenin yerel konum türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="9438a-183">Indicates the native location type of a variable.</span></span>  
  
 [<span data-ttu-id="9438a-184">WriteableMetadataUpdateMode Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="9438a-184">WriteableMetadataUpdateMode Enumeration</span></span>](writeablemetadataupdatemode-enumeration.md)  
 <span data-ttu-id="9438a-185">Meta verilerdeki bellek güncelleştirmelerinin hata ayıklayan tarafından görülüp görülemeyeceğini belirten değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9438a-185">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>

 <span data-ttu-id="9438a-186">[ClrDataSourceType Numaralandırma](clrdatasourcetype-enumeration.md) CLRDATA_IL_ADDRESS_MAP yapısı tarafından kullanılan değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="9438a-186">[ClrDataSourceType Enumeration](clrdatasourcetype-enumeration.md) Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="9438a-187">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="9438a-187">Related Sections</span></span>  
 [<span data-ttu-id="9438a-188">Hata Ayıklama Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="9438a-188">Debugging Coclasses</span></span>](debugging-coclasses.md)  
  
 [<span data-ttu-id="9438a-189">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9438a-189">Debugging Interfaces</span></span>](debugging-interfaces.md)  
  
 [<span data-ttu-id="9438a-190">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="9438a-190">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)  
  
 [<span data-ttu-id="9438a-191">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="9438a-191">Debugging Structures</span></span>](debugging-structures.md)
