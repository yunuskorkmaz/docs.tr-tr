---
title: Hata Ayıklama Yapıları
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
ms.openlocfilehash: a18094fb2621478dbdb4bbf672df436234112ed0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793751"
---
# <a name="debugging-structures"></a><span data-ttu-id="1dc92-102">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="1dc92-102">Debugging Structures</span></span>

<span data-ttu-id="1dc92-103">Bu bölümde hata ayıklama API 'sinin kullandığı yönetilmeyen yapılar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1dc92-103">This section describes the unmanaged structures that the debugging API uses.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="1dc92-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1dc92-104">In This Section</span></span>
 <span data-ttu-id="1dc92-105">[CLRDATA_ADDRESS_RANGE yapısı](clrdata-address-range-structure.md) Bir adres aralığı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1dc92-105">[CLRDATA_ADDRESS_RANGE Structure](clrdata-address-range-structure.md) Defines an address range.</span></span>

 <span data-ttu-id="1dc92-106">[CLRDATA_IL_ADDRESS_MAP yapısı](clrdata-il-address-map-structure.md) Adres eşleme için bir Il tanımlar</span><span class="sxs-lookup"><span data-stu-id="1dc92-106">[CLRDATA_IL_ADDRESS_MAP Structure](clrdata-il-address-map-structure.md) Defines an IL to address mapping</span></span>

 <span data-ttu-id="1dc92-107">[CLR_DEBUGGING_VERSION yapısı](clr-debugging-version-structure.md) Hata ayıklama amacıyla ortak dil çalışma zamanının (CLR) ürün sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1dc92-107">[CLR_DEBUGGING_VERSION Structure](clr-debugging-version-structure.md) Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>

 <span data-ttu-id="1dc92-108">[CodeChunkInfo yapısı](codechunkinfo-structure.md) Bellekte tek bir kod öbeğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1dc92-108">[CodeChunkInfo Structure](codechunkinfo-structure.md) Represents a single chunk of code in memory.</span></span>

 <span data-ttu-id="1dc92-109">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Şu anda bir iş parçacığının çerçevelerinde etkin olan işlevlerle ilgili bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="1dc92-109">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Contains information about the functions that are currently active in a thread's frames.</span></span>

 <span data-ttu-id="1dc92-110">[COR_ARRAY_LAYOUT yapısı](cor-array-layout-structure.md) Bellekte bir dizi nesnesinin yerleşimi hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1dc92-110">[COR_ARRAY_LAYOUT Structure](cor-array-layout-structure.md) Provides information about the layout of an array object in memory.</span></span>

 <span data-ttu-id="1dc92-111">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Microsoft ara dili (MSIL) kodunu yerel kodla eşlemek için kullanılan uzaklıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="1dc92-111">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>

 <span data-ttu-id="1dc92-112">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Bir kod aralığı için konum bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="1dc92-112">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Contains the offset information for a range of code.</span></span>

 <span data-ttu-id="1dc92-113">[COR_FIELD yapısı](cor-field-structure.md) Bir nesne içindeki bir alan hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1dc92-113">[COR_FIELD Structure](cor-field-structure.md) Provides information about a field in an object.</span></span>

 <span data-ttu-id="1dc92-114">[Cor_gc_reference yapısı](cor-gc-reference-structure.md) Atık olarak toplanmış bir nesne hakkındaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="1dc92-114">[COR_GC_REFERENCE Structure](cor-gc-reference-structure.md) Contains information about an object that is to be garbage-collected.</span></span>

 <span data-ttu-id="1dc92-115">[COR_HEAPINFO yapısı](cor-heapinfo-structure.md) Çöp toplama yığını hakkında, numaralandırılabilir olup olmadığı dahil genel bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="1dc92-115">[COR_HEAPINFO Structure](cor-heapinfo-structure.md) Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>

 <span data-ttu-id="1dc92-116">[COR_HEAPOBJECT Yapısı](cor-heapobject-structure.md) Yönetilen yığında bir nesne hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1dc92-116">[COR_HEAPOBJECT Structure](cor-heapobject-structure.md) Provides information about an object on the managed heap.</span></span>

 <span data-ttu-id="1dc92-117">[COR_IL_MAP](cor-il-map-structure.md) Bir işlevin göreli uzaklığının değişikliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1dc92-117">[COR_IL_MAP](cor-il-map-structure.md) Specifies changes in the relative offset of a function.</span></span>

 <span data-ttu-id="1dc92-118">[COR_SEGMENT Yapısı](cor-segment-structure.md) Yönetilen yığında bir bellek bölgesi hakkındaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="1dc92-118">[COR_SEGMENT Structure](cor-segment-structure.md) Contains information about a region of memory in the managed heap.</span></span>

 <span data-ttu-id="1dc92-119">[COR_TYPEID yapısı](cor-typeid-structure.md) Bir tür tanımlayıcısı içerir.</span><span class="sxs-lookup"><span data-stu-id="1dc92-119">[COR_TYPEID Structure](cor-typeid-structure.md) Contains a type identifier.</span></span>

 <span data-ttu-id="1dc92-120">[Cor_type_layout yapısı](cor-type-layout-structure.md) Bellekteki bir nesnenin düzeni hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="1dc92-120">[COR_TYPE_LAYOUT Structure](cor-type-layout-structure.md) Provides information about the layout of an object in memory.</span></span>

 <span data-ttu-id="1dc92-121">[COR_VERSION](cor-version-structure.md) Ortak dil çalışma zamanının Standart Dört parçalı sürüm numarasını depolar.</span><span class="sxs-lookup"><span data-stu-id="1dc92-121">[COR_VERSION](cor-version-structure.md) Stores the standard four-part version number of the common language runtime.</span></span>

 <span data-ttu-id="1dc92-122">[CorDebugBlockingObject yapısı](cordebugblockingobject-structure.md) Bir iş parçacığını engelleyen bir nesne ve iş parçacığının engellenme nedenini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1dc92-122">[CorDebugBlockingObject Structure](cordebugblockingobject-structure.md) Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>

 <span data-ttu-id="1dc92-123">[Corhata ayıklama Gehclause yapısı](cordebugehclause-structure.md) Belirli bir ara dil (IL) parçası için bir özel durum işleme (EH) yan tümcesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1dc92-123">[CorDebugEHClause Structure](cordebugehclause-structure.md) Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>

 <span data-ttu-id="1dc92-124">[CorDebugExceptionObjectStackFrame yapısı](cordebugexceptionobjectstackframe-structure.md) Bir özel durum nesnesinden yığın çerçeve bilgilerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1dc92-124">[CorDebugExceptionObjectStackFrame Structure](cordebugexceptionobjectstackframe-structure.md) Represents stack frame information from an exception object.</span></span>

 <span data-ttu-id="1dc92-125">[CorDebugGuidToTypeMapping yapısı](cordebugguidtotypemapping-structure.md) Windows Çalışma Zamanı GUID 'sini karşılık gelen [ICorDebugType](icordebugtype-interface.md) nesnesine eşler.</span><span class="sxs-lookup"><span data-stu-id="1dc92-125">[CorDebugGuidToTypeMapping Structure](cordebugguidtotypemapping-structure.md) Maps a Windows Runtime GUID to its corresponding [ICorDebugType](icordebugtype-interface.md) object.</span></span>

 <span data-ttu-id="1dc92-126">[DacpGetModuleAddress yapısı](dacpgetmoduleaddress-structure.md) Modül adresi isteği için kapsayıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1dc92-126">[DacpGetModuleAddress Structure](dacpgetmoduleaddress-structure.md) Defines the container for a module address request.</span></span>

 <span data-ttu-id="1dc92-127">[Dadcpmethoddescdata yapısı](dacpmethoddescdata-structure.md) Metodun çalışma zamanı bilgileri için bir aktarım arabelleği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1dc92-127">[DacpMethodDescData Structure](dacpmethoddescdata-structure.md) Defines a transport buffer for a method's runtime information.</span></span>

 <span data-ttu-id="1dc92-128">[Dadcpmoduledata yapısı](dacpmoduledata-structure.md) Modülün çalışma zamanı bilgileri için bir aktarım arabelleği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1dc92-128">[DacpModuleData Structure](dacpmoduledata-structure.md) Defines a transport buffer for a module's runtime information.</span></span>

 <span data-ttu-id="1dc92-129">[Dacprejdata yapısı](dacprejitdata-structure.md) Belirli bir profil oluşturucu tarafından işaretlenmiş yöntem hakkında temel bilgileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1dc92-129">[DacpReJitData Structure](dacprejitdata-structure.md) Defines the basic information about a given profiler-instrumented method.</span></span>

 <span data-ttu-id="1dc92-130">[StackTrace_SimpleContext yapısı](stacktrace-simplecontext-structure.md) Tam `CONTEXT` yapısının yerine kullanılabilecek basit bir bağlam sağlar.</span><span class="sxs-lookup"><span data-stu-id="1dc92-130">[StackTrace_SimpleContext Structure](stacktrace-simplecontext-structure.md) Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="1dc92-131">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="1dc92-131">Related Sections</span></span>

 [<span data-ttu-id="1dc92-132">Hata Ayıklama Coclass’ları</span><span class="sxs-lookup"><span data-stu-id="1dc92-132">Debugging Coclasses</span></span>](debugging-coclasses.md)

 [<span data-ttu-id="1dc92-133">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1dc92-133">Debugging Interfaces</span></span>](debugging-interfaces.md)

 [<span data-ttu-id="1dc92-134">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1dc92-134">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)

 [<span data-ttu-id="1dc92-135">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="1dc92-135">Debugging Enumerations</span></span>](debugging-enumerations.md)

 [<span data-ttu-id="1dc92-136">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="1dc92-136">Debugging</span></span>](index.md)
