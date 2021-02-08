---
description: 'Daha fazla bilgi: Numaralandırmalar hata ayıklaması'
title: Hata Ayıklama Numaralandırmaları
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: 4a1d2fc9061fec7f5384418e4893c357f5d340ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801429"
---
# <a name="debugging-enumerations"></a><span data-ttu-id="b14f5-103">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="b14f5-103">Debugging Enumerations</span></span>

<span data-ttu-id="b14f5-104">Bu bölümde hata ayıklama API 'sinin kullandığı yönetilmeyen numaralandırmalar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b14f5-104">This section describes the unmanaged enumerations that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b14f5-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b14f5-105">In This Section</span></span>  

 [<span data-ttu-id="b14f5-106">CLR_DEBUGGING_PROCESS_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b14f5-106">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>](clr-debugging-process-flags-enumeration.md)  
 <span data-ttu-id="b14f5-107">[ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) yöntemi tarafından kullanılan değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b14f5-107">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="b14f5-108">CLRDataEnumMemoryFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b14f5-108">CLRDataEnumMemoryFlags Enumeration</span></span>](clrdataenummemoryflags-enumeration.md)  
 <span data-ttu-id="b14f5-109">Hangi bellek bölgelerinin [ıclrdataenummemoryregion:: EnumMemoryRegion](iclrdataenummemoryregions-enummemoryregions-method.md) yöntemine yönelik bir çağrı içermesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b14f5-109">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
 [<span data-ttu-id="b14f5-110">COR_PUB_ENUMPROCESS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b14f5-110">COR_PUB_ENUMPROCESS Enumeration</span></span>](cor-pub-enumprocess-enumeration.md)  
 <span data-ttu-id="b14f5-111">Numaralandırılacak işlemin türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b14f5-111">Identifies the type of process to be enumerated.</span></span>  
  
 [<span data-ttu-id="b14f5-112">CorDebugBlockingReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b14f5-112">CorDebugBlockingReason Enumeration</span></span>](cordebugblockingreason-enumeration.md)  
 <span data-ttu-id="b14f5-113">Bir iş parçacığının belirli bir nesne üzerinde engellenip engellenme nedenlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b14f5-113">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
 <span data-ttu-id="b14f5-114">CorDebugChainReason</span><span class="sxs-lookup"><span data-stu-id="b14f5-114">CorDebugChainReason</span></span>  
 <span data-ttu-id="b14f5-115">Bir çağrı zincirinin başlatılması için neden veya nedenleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="b14f5-115">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
 [<span data-ttu-id="b14f5-116">CorDebugCodeInvokeKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b14f5-116">CorDebugCodeInvokeKind Enumeration</span></span>](cordebugcodeinvokekind-enumeration.md)  
 <span data-ttu-id="b14f5-117">Bir içe aktarılmış işlevin yönetilen kodu nasıl çağırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b14f5-117">Describes how an exported function invokes managed code.</span></span>  
  
 [<span data-ttu-id="b14f5-118">CorDebugCodeInvokePurpose Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b14f5-118">CorDebugCodeInvokePurpose Enumeration</span></span>](cordebugcodeinvokepurpose-enumeration.md)  
 <span data-ttu-id="b14f5-119">Bir içe aktarılmış işlevin neden yönetilen kodu çağırıyor olduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="b14f5-119">Describes why an exported function calls managed code.</span></span>  
  
 <span data-ttu-id="b14f5-120">CorDebugCreateProcessFlags</span><span class="sxs-lookup"><span data-stu-id="b14f5-120">CorDebugCreateProcessFlags</span></span>  
 <span data-ttu-id="b14f5-121">[ICorDebug:: CreateProcess](icordebug-createprocess-method.md) metoduna yapılan bir çağrıda kullanılabilecek ek hata ayıklama seçenekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b14f5-121">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](icordebug-createprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="b14f5-122">CorDebugDebugEventKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b14f5-122">CorDebugDebugEventKind Enumeration</span></span>](cordebugdebugeventkind-enumeration.md)  
 <span data-ttu-id="b14f5-123">Bilgileri [DecodeEvent](icordebugprocess6-decodeevent-method.md) yöntemi tarafından kodu çözülen olay türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="b14f5-123">Indicates the type of event whose information is decoded by the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
 [<span data-ttu-id="b14f5-124">CorDebugDecodeEventFlagsWindows Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b14f5-124">CorDebugDecodeEventFlagsWindows Enumeration</span></span>](cordebugdecodeeventflagswindows-enumeration.md)  
 <span data-ttu-id="b14f5-125">Windows platformunda hata ayıklama olayları hakkında ek bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b14f5-125">Provides additional information about debug events on the Windows platform.</span></span>  
  
 <span data-ttu-id="b14f5-126">CorDebugExceptionCallbackType</span><span class="sxs-lookup"><span data-stu-id="b14f5-126">CorDebugExceptionCallbackType</span></span>  
 <span data-ttu-id="b14f5-127">Bir [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md) olayından yapılan geri aramanın türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="b14f5-127">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
 [<span data-ttu-id="b14f5-128">CorDebugExceptionFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b14f5-128">CorDebugExceptionFlags Enumeration</span></span>](cordebugexceptionflags-enumeration.md)  
 <span data-ttu-id="b14f5-129">Bir özel durum hakkında ek bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b14f5-129">Provides additional information about an exception.</span></span>  
  
 <span data-ttu-id="b14f5-130">CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="b14f5-130">CorDebugExceptionUnwindCallbackType</span></span>  
 <span data-ttu-id="b14f5-131">Geriye doğru izleme aşamasında geri çağırma tarafından sinyal edilen olayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b14f5-131">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 [<span data-ttu-id="b14f5-132">CorDebugGCType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="b14f5-132">CorDebugGCType Enumeration</span></span>](cordebuggctype-enumeration.md)  
 <span data-ttu-id="b14f5-133">Çöp toplayıcının bir iş istasyonunda veya sunucuda çalışıp çalışmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b14f5-133">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
 [<span data-ttu-id="b14f5-134">CorDebugGenerationTypes Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="b14f5-134">CorDebugGenerationTypes Enumeration</span></span>](cordebuggenerationtypes-enumeration.md)  
 <span data-ttu-id="b14f5-135">Yönetilen yığında bir bellek bölgesinin üretilmesini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b14f5-135">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
 <span data-ttu-id="b14f5-136">CorDebugHandleType</span><span class="sxs-lookup"><span data-stu-id="b14f5-136">CorDebugHandleType</span></span>  
 <span data-ttu-id="b14f5-137">Tanıtıcı türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="b14f5-137">Indicates the handle type.</span></span>  
  
 [<span data-ttu-id="b14f5-138">CorDebugIlToNativeMappingTypes Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b14f5-138">CorDebugIlToNativeMappingTypes Enumeration</span></span>](cordebugiltonativemappingtypes-enumeration.md)  
 <span data-ttu-id="b14f5-139">Belirli bir yerel yönerge aralığının özel bir kod bölgesine karşılık geldiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b14f5-139">Indicates whether a particular range of native instructions corresponds to a special code region.</span></span>  
  
 <span data-ttu-id="b14f5-140">CorDebugIntercept</span><span class="sxs-lookup"><span data-stu-id="b14f5-140">CorDebugIntercept</span></span>  
 <span data-ttu-id="b14f5-141">İçine bulanan kod türlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b14f5-141">Indicates the types of code that can be stepped into.</span></span>  
  
 [<span data-ttu-id="b14f5-142">CorDebugInterfaceVersion Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b14f5-142">CorDebugInterfaceVersion Enumeration</span></span>](cordebuginterfaceversion-enumeration.md)  
 <span data-ttu-id="b14f5-143">.NET Framework sürümünü veya bir arabirimin tanıtılmasıyla .NET Framework sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b14f5-143">Specifies either a version of the .NET Framework, or the version of the .NET Framework in which an interface was introduced.</span></span>  
  
 <span data-ttu-id="b14f5-144">CorDebugInternalFrameType</span><span class="sxs-lookup"><span data-stu-id="b14f5-144">CorDebugInternalFrameType</span></span>  
 <span data-ttu-id="b14f5-145">Yığın çerçevesinin türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b14f5-145">Identifies the type of stack frame.</span></span>  
  
 [<span data-ttu-id="b14f5-146">CorDebugJITCompilerFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b14f5-146">CorDebugJITCompilerFlags Enumeration</span></span>](cordebugjitcompilerflags-enumeration.md)  
 <span data-ttu-id="b14f5-147">Yönetilen Just-In-Time (JıT) derleyicisinin davranışını etkileyen değerler içerir.</span><span class="sxs-lookup"><span data-stu-id="b14f5-147">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
 [<span data-ttu-id="b14f5-148">CorDebugJITCompilerFlagsDeprecated Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b14f5-148">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>](cordebugjitcompilerflagsdeprecated-enumeration.md)  
 <span data-ttu-id="b14f5-149">Kullanımdan kalktı.</span><span class="sxs-lookup"><span data-stu-id="b14f5-149">Obsolete.</span></span> <span data-ttu-id="b14f5-150">`CORDEBUG_JIT_DEFAULT`Bunun yerine [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) numaralandırmasının üyesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b14f5-150">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
 <span data-ttu-id="b14f5-151">CorDebugMappingResult</span><span class="sxs-lookup"><span data-stu-id="b14f5-151">CorDebugMappingResult</span></span>  
 <span data-ttu-id="b14f5-152">Yönerge işaretçisinin (IP) değerinin nasıl alındıklarına ilişkin ayrıntıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="b14f5-152">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
 [<span data-ttu-id="b14f5-153">CorDebugMDAFlags Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b14f5-153">CorDebugMDAFlags Enumeration</span></span>](cordebugmdaflags-enumeration.md)  
 <span data-ttu-id="b14f5-154">Yönetilen hata ayıklama Yardımcısı 'nın (MDA) harekete geçirildiği iş parçacığının durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b14f5-154">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
 [<span data-ttu-id="b14f5-155">CorDebugNGenPolicy Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="b14f5-155">CorDebugNGenPolicy Enumeration</span></span>](cordebugngenpolicy-enumeration.md)  
 <span data-ttu-id="b14f5-156">Bir hata ayıklayıcının yerel görüntü önbelleğinden yerel (NGen) görüntüler yükleyip yüklemeyeceğini belirleyen bir değer sağlar.</span><span class="sxs-lookup"><span data-stu-id="b14f5-156">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
 [<span data-ttu-id="b14f5-157">CorDebugPlatform Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b14f5-157">CorDebugPlatform Enumeration</span></span>](cordebugplatform-enumeration.md)  
 <span data-ttu-id="b14f5-158">[ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) yöntemi tarafından kullanılan hedef platform değerlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="b14f5-158">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
 [<span data-ttu-id="b14f5-159">CorDebugRecordFormat Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b14f5-159">CorDebugRecordFormat Enumeration</span></span>](cordebugrecordformat-enumeration.md)  
 <span data-ttu-id="b14f5-160">Bir yerel özel durum ayıklama olayı hakkında bilgi içeren bir bayt dizisindeki verilerin biçimini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b14f5-160">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
 <span data-ttu-id="b14f5-161">CorDebugRegister</span><span class="sxs-lookup"><span data-stu-id="b14f5-161">CorDebugRegister</span></span>  
 <span data-ttu-id="b14f5-162">Belirli bir işlemci mimarisiyle ilişkili kayıtları belirtir.</span><span class="sxs-lookup"><span data-stu-id="b14f5-162">Specifies the registers associated with a given processor architecture.</span></span>  
  
 [<span data-ttu-id="b14f5-163">CorDebugSetContextFlag Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b14f5-163">CorDebugSetContextFlag Enumeration</span></span>](cordebugsetcontextflag-enumeration.md)  
 <span data-ttu-id="b14f5-164">Bağlamın yığındaki etkin (veya yaprak) kareden mi olduğunu yoksa başka bir çerçeveden geriye doğru bir şekilde mi hesaplandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b14f5-164">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
 [<span data-ttu-id="b14f5-165">CorDebugStateChange Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b14f5-165">CorDebugStateChange Enumeration</span></span>](cordebugstatechange-enumeration.md)  
 <span data-ttu-id="b14f5-166">İşlemdeki değişikliklere göre atılması gereken önbelleğe alınmış verilerin miktarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b14f5-166">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
 <span data-ttu-id="b14f5-167">CorDebugStepReason</span><span class="sxs-lookup"><span data-stu-id="b14f5-167">CorDebugStepReason</span></span>  
 <span data-ttu-id="b14f5-168">Tek bir adımın sonucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b14f5-168">Indicates the outcome of an individual step.</span></span>  
  
 <span data-ttu-id="b14f5-169">CorDebugThreadState</span><span class="sxs-lookup"><span data-stu-id="b14f5-169">CorDebugThreadState</span></span>  
 <span data-ttu-id="b14f5-170">Hata ayıklama için bir iş parçacığının durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b14f5-170">Specifies the state of a thread for debugging.</span></span>  
  
 <span data-ttu-id="b14f5-171">\>CorDebugUnmappedStop</span><span class="sxs-lookup"><span data-stu-id="b14f5-171">\>CorDebugUnmappedStop</span></span>  
 <span data-ttu-id="b14f5-172">Stepper tarafından kod yürütmede bir durdurmak tetikleyemeyecek eşlenmemiş kod türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="b14f5-172">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
 <span data-ttu-id="b14f5-173">CorDebugUserState</span><span class="sxs-lookup"><span data-stu-id="b14f5-173">CorDebugUserState</span></span>  
 <span data-ttu-id="b14f5-174">Bir iş parçacığının kullanıcı durumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b14f5-174">Indicates the user state of a thread.</span></span>  
  
 [<span data-ttu-id="b14f5-175">CorGCReferenceType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="b14f5-175">CorGCReferenceType Enumeration</span></span>](corgcreferencetype-enumeration.md)  
 <span data-ttu-id="b14f5-176">Atık olarak toplanmış bir nesnenin kaynağını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b14f5-176">Identifies the source of an object to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="b14f5-177">ILCodeKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b14f5-177">ILCodeKind Enumeration</span></span>](ilcodekind-enumeration.md)  
 <span data-ttu-id="b14f5-178">Hata ayıklayıcının profil oluşturucu ReJIT araçları 'nda eklenen yerel değişkenlere veya koda erişip erişemeyeceğini belirten değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b14f5-178">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="b14f5-179">LoggingLevelEnum Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b14f5-179">LoggingLevelEnum Enumeration</span></span>](logginglevelenum-enumeration.md)  
 <span data-ttu-id="b14f5-180">Yönetilen bir iş parçacığı bir olay günlüğe kaydederken olay günlüğüne yazılan açıklayıcı bir iletinin önem derecesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b14f5-180">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
 [<span data-ttu-id="b14f5-181">LogSwitchCallReason Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b14f5-181">LogSwitchCallReason Enumeration</span></span>](logswitchcallreason-enumeration.md)  
 <span data-ttu-id="b14f5-182">Hata ayıklama/izleme anahtarı üzerinde gerçekleştirilen işlemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="b14f5-182">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
 [<span data-ttu-id="b14f5-183">VariableLocationType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="b14f5-183">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)  
 <span data-ttu-id="b14f5-184">Bir değişkenin yerel konum türünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="b14f5-184">Indicates the native location type of a variable.</span></span>  
  
 [<span data-ttu-id="b14f5-185">WriteableMetadataUpdateMode Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b14f5-185">WriteableMetadataUpdateMode Enumeration</span></span>](writeablemetadataupdatemode-enumeration.md)  
 <span data-ttu-id="b14f5-186">Meta verilerde bellek içi güncelleştirmelerin hata ayıklayıcıya görünür olup olmadığını belirten değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b14f5-186">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>

 <span data-ttu-id="b14f5-187">[ClrDataSourceType numaralandırması](clrdatasourcetype-enumeration.md) CLRDATA_IL_ADDRESS_MAP yapısı tarafından kullanılan değerleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b14f5-187">[ClrDataSourceType Enumeration](clrdatasourcetype-enumeration.md) Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="b14f5-188">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="b14f5-188">Related Sections</span></span>  

 [<span data-ttu-id="b14f5-189">Hata Ayıklama Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="b14f5-189">Debugging Coclasses</span></span>](debugging-coclasses.md)  
  
 [<span data-ttu-id="b14f5-190">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b14f5-190">Debugging Interfaces</span></span>](debugging-interfaces.md)  
  
 [<span data-ttu-id="b14f5-191">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b14f5-191">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)  
  
 [<span data-ttu-id="b14f5-192">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="b14f5-192">Debugging Structures</span></span>](debugging-structures.md)
