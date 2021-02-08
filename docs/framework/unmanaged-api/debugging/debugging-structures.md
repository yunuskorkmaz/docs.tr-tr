---
description: 'Daha fazla bilgi edinin: hata ayıklama yapıları'
title: Hata Ayıklama Yapıları
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
ms.openlocfilehash: 2b3b9e3678b34a25f9bfa58fcf6913cfe95aa729
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791562"
---
# <a name="debugging-structures"></a><span data-ttu-id="609a5-103">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="609a5-103">Debugging Structures</span></span>

<span data-ttu-id="609a5-104">Bu bölümde hata ayıklama API 'sinin kullandığı yönetilmeyen yapılar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="609a5-104">This section describes the unmanaged structures that the debugging API uses.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="609a5-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="609a5-105">In This Section</span></span>

 <span data-ttu-id="609a5-106">[CLRDATA_ADDRESS_RANGE yapısı](clrdata-address-range-structure.md) Bir adres aralığı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="609a5-106">[CLRDATA_ADDRESS_RANGE Structure](clrdata-address-range-structure.md) Defines an address range.</span></span>

 <span data-ttu-id="609a5-107">[CLRDATA_IL_ADDRESS_MAP yapısı](clrdata-il-address-map-structure.md) Adres eşleme için bir Il tanımlar</span><span class="sxs-lookup"><span data-stu-id="609a5-107">[CLRDATA_IL_ADDRESS_MAP Structure](clrdata-il-address-map-structure.md) Defines an IL to address mapping</span></span>

 <span data-ttu-id="609a5-108">[CLR_DEBUGGING_VERSION yapısı](clr-debugging-version-structure.md) Hata ayıklama amacıyla ortak dil çalışma zamanının (CLR) ürün sürümünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="609a5-108">[CLR_DEBUGGING_VERSION Structure](clr-debugging-version-structure.md) Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>

 <span data-ttu-id="609a5-109">[CodeChunkInfo yapısı](codechunkinfo-structure.md) Bellekte tek bir kod öbeğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="609a5-109">[CodeChunkInfo Structure](codechunkinfo-structure.md) Represents a single chunk of code in memory.</span></span>

 <span data-ttu-id="609a5-110">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Şu anda bir iş parçacığının çerçevelerinde etkin olan işlevlerle ilgili bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="609a5-110">[COR_ACTIVE_FUNCTION](cor-active-function-structure.md) Contains information about the functions that are currently active in a thread's frames.</span></span>

 <span data-ttu-id="609a5-111">[COR_ARRAY_LAYOUT yapısı](cor-array-layout-structure.md) Bellekte bir dizi nesnesinin yerleşimi hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="609a5-111">[COR_ARRAY_LAYOUT Structure](cor-array-layout-structure.md) Provides information about the layout of an array object in memory.</span></span>

 <span data-ttu-id="609a5-112">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Microsoft ara dili (MSIL) kodunu yerel kodla eşlemek için kullanılan uzaklıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="609a5-112">[COR_DEBUG_IL_TO_NATIVE_MAP](cor-debug-il-to-native-map-structure.md) Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>

 <span data-ttu-id="609a5-113">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Bir kod aralığı için konum bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="609a5-113">[COR_DEBUG_STEP_RANGE](cor-debug-step-range-structure.md) Contains the offset information for a range of code.</span></span>

 <span data-ttu-id="609a5-114">[COR_FIELD yapısı](cor-field-structure.md) Bir nesne içindeki bir alan hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="609a5-114">[COR_FIELD Structure](cor-field-structure.md) Provides information about a field in an object.</span></span>

 <span data-ttu-id="609a5-115">[Cor_gc_reference yapısı](cor-gc-reference-structure.md) Atık olarak toplanmış bir nesne hakkındaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="609a5-115">[COR_GC_REFERENCE Structure](cor-gc-reference-structure.md) Contains information about an object that is to be garbage-collected.</span></span>

 <span data-ttu-id="609a5-116">[COR_HEAPINFO yapısı](cor-heapinfo-structure.md) Çöp toplama yığını hakkında, numaralandırılabilir olup olmadığı dahil genel bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="609a5-116">[COR_HEAPINFO Structure](cor-heapinfo-structure.md) Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>

 <span data-ttu-id="609a5-117">[COR_HEAPOBJECT Yapısı](cor-heapobject-structure.md) Yönetilen yığında bir nesne hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="609a5-117">[COR_HEAPOBJECT Structure](cor-heapobject-structure.md) Provides information about an object on the managed heap.</span></span>

 <span data-ttu-id="609a5-118">[COR_IL_MAP](cor-il-map-structure.md) Bir işlevin göreli uzaklığının değişikliklerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="609a5-118">[COR_IL_MAP](cor-il-map-structure.md) Specifies changes in the relative offset of a function.</span></span>

 <span data-ttu-id="609a5-119">[COR_SEGMENT Yapısı](cor-segment-structure.md) Yönetilen yığında bir bellek bölgesi hakkındaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="609a5-119">[COR_SEGMENT Structure](cor-segment-structure.md) Contains information about a region of memory in the managed heap.</span></span>

 <span data-ttu-id="609a5-120">[COR_TYPEID yapısı](cor-typeid-structure.md) Bir tür tanımlayıcısı içerir.</span><span class="sxs-lookup"><span data-stu-id="609a5-120">[COR_TYPEID Structure](cor-typeid-structure.md) Contains a type identifier.</span></span>

 <span data-ttu-id="609a5-121">[Cor_type_layout yapısı](cor-type-layout-structure.md) Bellekteki bir nesnenin düzeni hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="609a5-121">[COR_TYPE_LAYOUT Structure](cor-type-layout-structure.md) Provides information about the layout of an object in memory.</span></span>

 <span data-ttu-id="609a5-122">[COR_VERSION](cor-version-structure.md) Ortak dil çalışma zamanının Standart Dört parçalı sürüm numarasını depolar.</span><span class="sxs-lookup"><span data-stu-id="609a5-122">[COR_VERSION](cor-version-structure.md) Stores the standard four-part version number of the common language runtime.</span></span>

 <span data-ttu-id="609a5-123">[CorDebugBlockingObject yapısı](cordebugblockingobject-structure.md) Bir iş parçacığını engelleyen bir nesne ve iş parçacığının engellenme nedenini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="609a5-123">[CorDebugBlockingObject Structure](cordebugblockingobject-structure.md) Defines an object that is blocking a thread and the reason why the thread is blocked.</span></span>

 <span data-ttu-id="609a5-124">[Corhata ayıklama Gehclause yapısı](cordebugehclause-structure.md) Belirli bir ara dil (IL) parçası için bir özel durum işleme (EH) yan tümcesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="609a5-124">[CorDebugEHClause Structure](cordebugehclause-structure.md) Represents an exception handling (EH) clause for a given piece of intermediate language (IL).</span></span>

 <span data-ttu-id="609a5-125">[CorDebugExceptionObjectStackFrame yapısı](cordebugexceptionobjectstackframe-structure.md) Bir özel durum nesnesinden yığın çerçeve bilgilerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="609a5-125">[CorDebugExceptionObjectStackFrame Structure](cordebugexceptionobjectstackframe-structure.md) Represents stack frame information from an exception object.</span></span>

 <span data-ttu-id="609a5-126">[CorDebugGuidToTypeMapping yapısı](cordebugguidtotypemapping-structure.md) Windows Çalışma Zamanı GUID 'sini karşılık gelen [ICorDebugType](icordebugtype-interface.md) nesnesine eşler.</span><span class="sxs-lookup"><span data-stu-id="609a5-126">[CorDebugGuidToTypeMapping Structure](cordebugguidtotypemapping-structure.md) Maps a Windows Runtime GUID to its corresponding [ICorDebugType](icordebugtype-interface.md) object.</span></span>

 <span data-ttu-id="609a5-127">[DacpGetModuleAddress yapısı](dacpgetmoduleaddress-structure.md) Modül adresi isteği için kapsayıcıyı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="609a5-127">[DacpGetModuleAddress Structure](dacpgetmoduleaddress-structure.md) Defines the container for a module address request.</span></span>

 <span data-ttu-id="609a5-128">[Dadcpmethoddescdata yapısı](dacpmethoddescdata-structure.md) Metodun çalışma zamanı bilgileri için bir aktarım arabelleği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="609a5-128">[DacpMethodDescData Structure](dacpmethoddescdata-structure.md) Defines a transport buffer for a method's runtime information.</span></span>

 <span data-ttu-id="609a5-129">[Dadcpmoduledata yapısı](dacpmoduledata-structure.md) Modülün çalışma zamanı bilgileri için bir aktarım arabelleği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="609a5-129">[DacpModuleData Structure](dacpmoduledata-structure.md) Defines a transport buffer for a module's runtime information.</span></span>

 <span data-ttu-id="609a5-130">[Dacprejdata yapısı](dacprejitdata-structure.md) Belirli bir profil oluşturucu tarafından işaretlenmiş yöntem hakkında temel bilgileri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="609a5-130">[DacpReJitData Structure](dacprejitdata-structure.md) Defines the basic information about a given profiler-instrumented method.</span></span>

 <span data-ttu-id="609a5-131">[StackTrace_SimpleContext yapısı](stacktrace-simplecontext-structure.md) Tam bir yapının yerine kullanılabilecek basit bir bağlam sağlar `CONTEXT` .</span><span class="sxs-lookup"><span data-stu-id="609a5-131">[StackTrace_SimpleContext Structure](stacktrace-simplecontext-structure.md) Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="609a5-132">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="609a5-132">Related Sections</span></span>

 [<span data-ttu-id="609a5-133">Hata Ayıklama Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="609a5-133">Debugging Coclasses</span></span>](debugging-coclasses.md)

 [<span data-ttu-id="609a5-134">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="609a5-134">Debugging Interfaces</span></span>](debugging-interfaces.md)

 [<span data-ttu-id="609a5-135">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="609a5-135">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)

 [<span data-ttu-id="609a5-136">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="609a5-136">Debugging Enumerations</span></span>](debugging-enumerations.md)

 [<span data-ttu-id="609a5-137">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="609a5-137">Debugging</span></span>](index.md)
