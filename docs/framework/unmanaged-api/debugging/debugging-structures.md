---
title: Hata Ayıklama Yapıları
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18bf03fee1a95c898e8273fa839e41a86b2d1c32
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828377"
---
# <a name="debugging-structures"></a><span data-ttu-id="470f8-102">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="470f8-102">Debugging Structures</span></span>
<span data-ttu-id="470f8-103">Bu bölümde, hata ayıklama API'SİNİN kullandığı yönetilmeyen yapıları açıklar.</span><span class="sxs-lookup"><span data-stu-id="470f8-103">This section describes the unmanaged structures that the debugging API uses.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="470f8-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="470f8-104">In This Section</span></span>
 <span data-ttu-id="470f8-105">[CLRDATA_ADDRESS_RANGE yapısı](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) bir adres aralığı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="470f8-105">[CLRDATA_ADDRESS_RANGE Structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-address-range-structure.md) Defines an address range.</span></span>

 <span data-ttu-id="470f8-106">[CLRDATA_IL_ADDRESS_MAP yapısı](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) bir IL adresi eşleme tanımlar.</span><span class="sxs-lookup"><span data-stu-id="470f8-106">[CLRDATA_IL_ADDRESS_MAP Structure](../../../../docs/framework/unmanaged-api/debugging/clrdata-il-address-map-structure.md) Defines an IL to address mapping</span></span>

 <span data-ttu-id="470f8-107">[Clr_debuggıng_versıon yapısı](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) hata ayıklama amacıyla ortak dil çalışma zamanı (CLR) ürün sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="470f8-107">[CLR_DEBUGGING_VERSION Structure](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md) Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>

 <span data-ttu-id="470f8-108">[Codechunkınfo yapısı1](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md) kod bellekte tek bir öbek temsil eder.</span><span class="sxs-lookup"><span data-stu-id="470f8-108">[CodeChunkInfo Structure1](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md) Represents a single chunk of code in memory.</span></span>

 <span data-ttu-id="470f8-109">[Cor_actıve_functıon](cor-active-function-structure.md) bir iş parçacığının çerçevelerde şu an etkin olan işlevler hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="470f8-109">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Contains information about the functions that are currently active in a thread's frames.</span></span>

 <span data-ttu-id="470f8-110">[COR_ARRAY_LAYOUT yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) bir dizi nesnesinin bellek düzeni hakkında bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="470f8-110">[COR_ARRAY_LAYOUT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) Provides information about the layout of an array object in memory.</span></span>

 <span data-ttu-id="470f8-111">[Cor_debug_ıl_to_natıve_map](cor-debug-il-to-native-map-structure.md) Microsoft Ara dilini (MSIL) eşlemek için kullanılan uzaklıkları yerel kod için kod içerir.</span><span class="sxs-lookup"><span data-stu-id="470f8-111">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>

 <span data-ttu-id="470f8-112">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) kod aralığı uzaklık bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="470f8-112">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Contains the offset information for a range of code.</span></span>

 <span data-ttu-id="470f8-113">[Cor_fıeld yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) bir alanda bir nesne hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="470f8-113">[COR_FIELD Structure](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) Provides information about a field in an object.</span></span>

 <span data-ttu-id="470f8-114">[COR_GC_REFERENCE yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) atık olarak toplanmış olacak bir nesneyle ilgili bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="470f8-114">[COR_GC_REFERENCE Structure](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) Contains information about an object that is to be garbage-collected.</span></span>

 <span data-ttu-id="470f8-115">[Cor_heapınfo yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) numaralandırılabilir olup olmadığı dahil çöp toplama yığınındaki hakkında genel bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="470f8-115">[COR_HEAPINFO Structure](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>

 <span data-ttu-id="470f8-116">[COR_HEAPOBJECT yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) yönetilen yığındaki bir nesne hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="470f8-116">[COR_HEAPOBJECT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) Provides information about an object on the managed heap.</span></span>

 <span data-ttu-id="470f8-117">[Cor_ıl_map](cor-il-map-structure.md) değişiklikleri bir işlevin göreli uzaklığı belirtir.</span><span class="sxs-lookup"><span data-stu-id="470f8-117">[COR_IL_MAP](cor-il-map-structure.md) Specifies changes in the relative offset of a function.</span></span>

 <span data-ttu-id="470f8-118">[COR_SEGMENT yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) bellek yönetilen yığında bir bölge hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="470f8-118">[COR_SEGMENT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md) Contains information about a region of memory in the managed heap.</span></span>

 <span data-ttu-id="470f8-119">[Cor_typeıd yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) bir tür tanımlayıcısı içeriyor.</span><span class="sxs-lookup"><span data-stu-id="470f8-119">[COR_TYPEID Structure](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) Contains a type identifier.</span></span>

 <span data-ttu-id="470f8-120">[COR_TYPE_LAYOUT yapısı](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) bellekte bir nesne düzeni hakkında bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="470f8-120">[COR_TYPE_LAYOUT Structure](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) Provides information about the layout of an object in memory.</span></span>

 <span data-ttu-id="470f8-121">[Cor_versıon](cor-version-structure.md) ortak dil çalışma zamanı standart Dört bölümlü sürüm numarasını depolar.</span><span class="sxs-lookup"><span data-stu-id="470f8-121">[COR_VERSION](cor-version-structure.md) Stores the standard four-part version number of the common language runtime.</span></span>

 <span data-ttu-id="470f8-122">[CorDebugBlockingObject yapısı](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) bir iş parçacığı ve iş parçacığı engellendi neden neden engelleyen bir nesneyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="470f8-122">[CorDebugBlockingObject Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>

 <span data-ttu-id="470f8-123">[CorDebugEHClause yapısı](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) bir özel durum işleme (EH) yan tümcesi için Ara dil (IL) belirli bir parçasını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="470f8-123">[CorDebugEHClause Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md) Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>

 <span data-ttu-id="470f8-124">[CorDebugExceptionObjectStackFrame yapısı](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) yığın çerçeve bilgileri bir özel durum nesnesinden temsil eder.</span><span class="sxs-lookup"><span data-stu-id="470f8-124">[CorDebugExceptionObjectStackFrame Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) Represents stack frame information from an exception object.</span></span>

 <span data-ttu-id="470f8-125">[CorDebugGuidToTypeMapping yapısı](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) eşlemeleri bir [!INCLUDE[wrt](../../../../includes/wrt-md.md)] , karşılık gelen GUID [Icordebugtype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="470f8-125">[CorDebugGuidToTypeMapping Structure](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) object.</span></span>

 <span data-ttu-id="470f8-126">[DacpGetModuleAddress yapısı](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) modülü adresi isteği için bir kapsayıcı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="470f8-126">[DacpGetModuleAddress Structure](../../../../docs/framework/unmanaged-api/debugging/dacpgetmoduleaddress-structure.md) Defines the container for a module address request.</span></span>

 <span data-ttu-id="470f8-127">[DacpMethodDescData yapısı](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md) bir yöntemin çalışma zamanı bilgileri için transport arabellek tanımlar.</span><span class="sxs-lookup"><span data-stu-id="470f8-127">[DacpMethodDescData Structure](../../../../docs/framework/unmanaged-api/debugging/dacpmethoddescdata-structure.md) Defines a transport buffer for a method's runtime information.</span></span>

 <span data-ttu-id="470f8-128">[DacpModuleData yapısı](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md) aktarım arabelleği için bir modülün çalışma zamanı bilgileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="470f8-128">[DacpModuleData Structure](../../../../docs/framework/unmanaged-api/debugging/dacpmoduledata-structure.md) Defines a transport buffer for a module's runtime information.</span></span>

 <span data-ttu-id="470f8-129">[DacpReJitData yapısı](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md) belirli bir profil oluşturucu izleme eklenmiş yöntemi ile ilgili temel bilgileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="470f8-129">[DacpReJitData Structure](../../../../docs/framework/unmanaged-api/debugging/dacprejitdata-structure.md) Defines the basic information about a given profiler-instrumented method.</span></span>

 <span data-ttu-id="470f8-130">[StackTrace_SimpleContext yapısı](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) tam yerine kullanılabilecek basit bir bağlam sağlar `CONTEXT` yapısı.</span><span class="sxs-lookup"><span data-stu-id="470f8-130">[StackTrace_SimpleContext Structure](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>



## <a name="related-sections"></a><span data-ttu-id="470f8-131">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="470f8-131">Related Sections</span></span>
 [<span data-ttu-id="470f8-132">Hata Ayıklama Coclass’ları</span><span class="sxs-lookup"><span data-stu-id="470f8-132">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)

 [<span data-ttu-id="470f8-133">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="470f8-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

 [<span data-ttu-id="470f8-134">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="470f8-134">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

 [<span data-ttu-id="470f8-135">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="470f8-135">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

 [<span data-ttu-id="470f8-136">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="470f8-136">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
