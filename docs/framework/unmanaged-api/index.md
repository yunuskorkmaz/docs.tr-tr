---
title: "Yönetilmeyen API Başvurusu"
ms.custom: 
ms.date: 11/06/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- runtime, unmanaged APIs
- common language runtime, unmanaged APIs
- native API reference [.NET Framework]
- unmanaged API reference [.NET Framework]
ms.assetid: 9aa000ee-c04c-492c-ae4f-83ecdf4fdbbe
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a7069762dd95636399c53c98e8bdef6f00be62c1
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2017
---
# <a name="unmanaged-api-reference"></a><span data-ttu-id="aa021-102">Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="aa021-102">Unmanaged API Reference</span></span>
<span data-ttu-id="aa021-103">Bu bölüm, çalışma zamanı ana bilgisayarlar, derleyicileri, çözücüler, obfuscators, hata ayıklayıcıları ve profil oluşturucular gibi yönetilen-kod ile ilgili uygulamaları tarafından kullanılan yönetilmeyen API'ler hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="aa021-103">This section includes information on unmanaged APIs that can be used by managed-code-related applications, such as runtime hosts, compilers, disassemblers, obfuscators, debuggers, and profilers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aa021-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="aa021-104">In This Section</span></span>  
 [<span data-ttu-id="aa021-105">Ortak veri türleri</span><span class="sxs-lookup"><span data-stu-id="aa021-105">Common Data Types</span></span>](../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)  
 <span data-ttu-id="aa021-106">Özellikle yönetilmeyen profil oluşturma ve API hata ayıklama içinde kullanılan ortak veri türleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="aa021-106">Lists the common data types that are used, particularly in the unmanaged profiling and debugging APIs.</span></span>  
  
 [<span data-ttu-id="aa021-107">ALink</span><span class="sxs-lookup"><span data-stu-id="aa021-107">ALink</span></span>](../../../docs/framework/unmanaged-api/alink/index.md)  
 <span data-ttu-id="aa021-108">.NET Framework derlemeler ve ilişkisiz modülleri oluşturmayı destekler ALink API açıklar.</span><span class="sxs-lookup"><span data-stu-id="aa021-108">Describes the ALink API, which supports the creation of .NET Framework assemblies and unbound modules.</span></span>  
  
 [<span data-ttu-id="aa021-109">Authenticode</span><span class="sxs-lookup"><span data-stu-id="aa021-109">Authenticode</span></span>](../../../docs/framework/unmanaged-api/authenticode/index.md)  
 <span data-ttu-id="aa021-110">Authenticode XrML lisans oluşturma ve doğrulama modülü destekler.</span><span class="sxs-lookup"><span data-stu-id="aa021-110">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
 [<span data-ttu-id="aa021-111">Sabitleri</span><span class="sxs-lookup"><span data-stu-id="aa021-111">Constants</span></span>](../../../docs/framework/unmanaged-api/constants-unmanaged-api-reference.md)  
 <span data-ttu-id="aa021-112">CorSym.idl içinde tanımlanan sabitleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="aa021-112">Describes the constants that are defined in CorSym.idl.</span></span>  
  
 [<span data-ttu-id="aa021-113">Özel arabirim öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="aa021-113">Custom Interface Attributes</span></span>](http://msdn.microsoft.com/en-us/940952f9-46ad-4a1a-920f-118dc0bdcd9f)  
 <span data-ttu-id="aa021-114">Bileşen Nesne Modeli (COM) özel arabirim öznitelikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aa021-114">Describes component object model (COM) custom interface attributes.</span></span>  
  
 [<span data-ttu-id="aa021-115">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="aa021-115">Debugging</span></span>](../../../docs/framework/unmanaged-api/debugging/index.md)  
 <span data-ttu-id="aa021-116">Ortak dil çalışma zamanı (CLR) ortamında çalışan kod hatalarını ayıklamak bir hata ayıklayıcı sağlar hata ayıklama API'si açıklar.</span><span class="sxs-lookup"><span data-stu-id="aa021-116">Describes the debugging API, which enables a debugger to debug code that runs in the common language runtime (CLR) environment.</span></span>  
  
 [<span data-ttu-id="aa021-117">Tanılama sembol deposu</span><span class="sxs-lookup"><span data-stu-id="aa021-117">Diagnostics Symbol Store</span></span>](../../../docs/framework/unmanaged-api/diagnostics/index.md)  
 <span data-ttu-id="aa021-118">Bir hata ayıklayıcısı tarafından kullanılmak üzere sembol bilgileri oluşturmak bir derleyici sağlayan tanılama sembol deposu API, açıklar.</span><span class="sxs-lookup"><span data-stu-id="aa021-118">Describes the diagnostics symbol store API, which enables a compiler to generate symbol information for use by a debugger.</span></span>  
  
 [<span data-ttu-id="aa021-119">Fusion</span><span class="sxs-lookup"><span data-stu-id="aa021-119">Fusion</span></span>](../../../docs/framework/unmanaged-api/fusion/index.md)  
 <span data-ttu-id="aa021-120">Uygulama için bu kaynakların doğru sürümlerini bulmak için uygulamanın kaynak özelliklerine erişmek bir çalışma zamanı ana bilgisayarı sağlar fusion API açıklar.</span><span class="sxs-lookup"><span data-stu-id="aa021-120">Describes the fusion API, which enables a runtime host to access the properties of an application's resources in order to locate the correct versions of those resources for the application.</span></span>  
  
 [<span data-ttu-id="aa021-121">Barındırma</span><span class="sxs-lookup"><span data-stu-id="aa021-121">Hosting</span></span>](../../../docs/framework/unmanaged-api/hosting/index.md)  
 <span data-ttu-id="aa021-122">CLR uygulamalarına tümleştirmeleri için yönetilmeyen ana bilgisayarları sağlar barındırma API açıklar.</span><span class="sxs-lookup"><span data-stu-id="aa021-122">Describes the hosting API, which enables unmanaged hosts to integrate the CLR into their applications.</span></span>  
  
 [<span data-ttu-id="aa021-123">Meta veriler</span><span class="sxs-lookup"><span data-stu-id="aa021-123">Metadata</span></span>](../../../docs/framework/unmanaged-api/metadata/index.md)  
 <span data-ttu-id="aa021-124">CLR tarafından yüklenen türleri olmadan bir bileşenin meta verilerine erişmek veya oluşturmak bir istemci bir derleyici gibi sağlayan API meta verileri açıklar.</span><span class="sxs-lookup"><span data-stu-id="aa021-124">Describes the metadata API, which enables a client such as a compiler to generate or access a component's metadata without the types being loaded by the CLR.</span></span>  
  
 [<span data-ttu-id="aa021-125">Profil oluşturma</span><span class="sxs-lookup"><span data-stu-id="aa021-125">Profiling</span></span>](../../../docs/framework/unmanaged-api/profiling/index.md)  
 <span data-ttu-id="aa021-126">Bir programın yürütme CLR tarafından izlemek bir profil oluşturucu sağlar profil oluşturma API açıklar.</span><span class="sxs-lookup"><span data-stu-id="aa021-126">Describes the profiling API, which enables a profiler to monitor a program's execution by the CLR.</span></span>  
  
 [<span data-ttu-id="aa021-127">Tanımlayıcı ad oluşturma</span><span class="sxs-lookup"><span data-stu-id="aa021-127">Strong Naming</span></span>](../../../docs/framework/unmanaged-api/strong-naming/index.md)  
 <span data-ttu-id="aa021-128">Tanımlayıcı adlı derlemeler için imzalama yönetmek bir istemci sağlayan güçlü adlandırma API açıklar.</span><span class="sxs-lookup"><span data-stu-id="aa021-128">Describes the strong naming API, which enables a client to administer strong name signing for assemblies.</span></span>  

 [<span data-ttu-id="aa021-129">WMI ve performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="aa021-129">WMI and Performance Counters</span></span>](wmi/index.md)  
 <span data-ttu-id="aa021-130">Windows Yönetim Araçları (WMI) kitaplıklarına sarmalamak API'ları açıklar.</span><span class="sxs-lookup"><span data-stu-id="aa021-130">Describes the APIs that wrap calls to Windows Management Instrumentation (WMI) libraries.</span></span>
  
 [<span data-ttu-id="aa021-131">Tlbexp yardımcı işlevleri</span><span class="sxs-lookup"><span data-stu-id="aa021-131">Tlbexp Helper Functions</span></span>](../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 <span data-ttu-id="aa021-132">Tür kitaplığı dışarı Aktarıcı tarafından (Tlbexp.exe) derleme için tür kitaplığı dönüştürme işlemi sırasında kullanılan arabirimi ve iki yardımcı işlevleri açıklanır.</span><span class="sxs-lookup"><span data-stu-id="aa021-132">Describes the two helper functions and interface used by the Type Library Exporter (Tlbexp.exe) during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="aa021-133">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="aa021-133">Related Sections</span></span>  
 [<span data-ttu-id="aa021-134">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="aa021-134">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
  
 [<span data-ttu-id="aa021-135">.NET Framework için Gelişmiş okuma</span><span class="sxs-lookup"><span data-stu-id="aa021-135">Advanced Reading for the .NET Framework</span></span>](http://msdn.microsoft.com/en-us/faae8083-fecb-4514-b133-b0a5a32a7c3c)
