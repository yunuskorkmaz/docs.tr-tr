---
description: 'Daha fazla bilgi edinin: yönetilmeyen API başvurusu'
title: Yönetilmeyen API Başvurusu
ms.date: 11/06/2017
helpviewer_keywords:
- runtime, unmanaged APIs
- common language runtime, unmanaged APIs
- native API reference [.NET Framework]
- unmanaged API reference [.NET Framework]
ms.assetid: 9aa000ee-c04c-492c-ae4f-83ecdf4fdbbe
ms.openlocfilehash: 3c9c485d8dced9641d0d1af850de190318902aa9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678997"
---
# <a name="unmanaged-api-reference"></a><span data-ttu-id="b5c1e-103">Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="b5c1e-103">Unmanaged API Reference</span></span>

<span data-ttu-id="b5c1e-104">Bu bölüm, çalışma zamanı Konakları, derleyiciler, kod çözücüler, gizleme, hata ayıklayıcılar ve profil oluşturucular gibi yönetilen kodla ilgili uygulamalar tarafından kullanılabilecek yönetilmeyen API 'Ler hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="b5c1e-104">This section includes information on unmanaged APIs that can be used by managed-code-related applications, such as runtime hosts, compilers, disassemblers, obfuscators, debuggers, and profilers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b5c1e-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b5c1e-105">In This Section</span></span>  

 [<span data-ttu-id="b5c1e-106">Ortak Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="b5c1e-106">Common Data Types</span></span>](common-data-types-unmanaged-api-reference.md)  
 <span data-ttu-id="b5c1e-107">Özellikle yönetilmeyen profil oluşturma ve hata ayıklama API 'Lerinde kullanılan ortak veri türlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="b5c1e-107">Lists the common data types that are used, particularly in the unmanaged profiling and debugging APIs.</span></span>  
  
 [<span data-ttu-id="b5c1e-108">ALINK</span><span class="sxs-lookup"><span data-stu-id="b5c1e-108">ALink</span></span>](./alink/index.md)  
 <span data-ttu-id="b5c1e-109">.NET Framework derlemeleri ve ilişkisiz modülleri oluşturmayı destekleyen ALink API 'sini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b5c1e-109">Describes the ALink API, which supports the creation of .NET Framework assemblies and unbound modules.</span></span>  
  
 [<span data-ttu-id="b5c1e-110">Authenticode</span><span class="sxs-lookup"><span data-stu-id="b5c1e-110">Authenticode</span></span>](./authenticode/index.md)  
 <span data-ttu-id="b5c1e-111">Authenticode XrML lisans oluşturma ve doğrulama modülünü destekler.</span><span class="sxs-lookup"><span data-stu-id="b5c1e-111">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
 [<span data-ttu-id="b5c1e-112">Sabitler</span><span class="sxs-lookup"><span data-stu-id="b5c1e-112">Constants</span></span>](constants-unmanaged-api-reference.md)  
 <span data-ttu-id="b5c1e-113">Corsyd. IDL içinde tanımlanan sabitleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="b5c1e-113">Describes the constants that are defined in CorSym.idl.</span></span>  
  
 <span data-ttu-id="b5c1e-114">[Özel arabirim öznitelikleri](/previous-versions/dotnet/netframework-4.0/ms231946(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b5c1e-114">[Custom Interface Attributes](/previous-versions/dotnet/netframework-4.0/ms231946(v=vs.100))</span></span>  
 <span data-ttu-id="b5c1e-115">Bileşen nesne modeli (COM) özel arabirim özniteliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b5c1e-115">Describes component object model (COM) custom interface attributes.</span></span>  
  
 [<span data-ttu-id="b5c1e-116">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="b5c1e-116">Debugging</span></span>](./debugging/index.md)  
 <span data-ttu-id="b5c1e-117">Bir hata ayıklayıcının ortak dil çalışma zamanı (CLR) ortamında çalışan kodun hatalarını ayıklamasını sağlayan hata ayıklama API 'sini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b5c1e-117">Describes the debugging API, which enables a debugger to debug code that runs in the common language runtime (CLR) environment.</span></span>  
  
 [<span data-ttu-id="b5c1e-118">Tanılama Sembol Deposu</span><span class="sxs-lookup"><span data-stu-id="b5c1e-118">Diagnostics Symbol Store</span></span>](./diagnostics/index.md)  
 <span data-ttu-id="b5c1e-119">Bir derleyicinin hata ayıklayıcı tarafından kullanılmak üzere sembol bilgisi oluşturmasını sağlayan tanılama sembol deposu API 'sini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b5c1e-119">Describes the diagnostics symbol store API, which enables a compiler to generate symbol information for use by a debugger.</span></span>  
  
 [<span data-ttu-id="b5c1e-120">Fusion</span><span class="sxs-lookup"><span data-stu-id="b5c1e-120">Fusion</span></span>](./fusion/index.md)  
 <span data-ttu-id="b5c1e-121">Uygulama için bu kaynakların doğru sürümlerini bulmak üzere bir çalışma zamanı konağının bir uygulama kaynaklarının özelliklerine erişmesini sağlayan Fusion API 'sini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b5c1e-121">Describes the fusion API, which enables a runtime host to access the properties of an application's resources in order to locate the correct versions of those resources for the application.</span></span>  
  
 [<span data-ttu-id="b5c1e-122">Hosting</span><span class="sxs-lookup"><span data-stu-id="b5c1e-122">Hosting</span></span>](./hosting/index.md)  
 <span data-ttu-id="b5c1e-123">Yönetilmeyen ana bilgisayarların CLR 'yi uygulamalarıyla tümleştirmesini sağlayan barındırma API 'sini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b5c1e-123">Describes the hosting API, which enables unmanaged hosts to integrate the CLR into their applications.</span></span>  
  
 [<span data-ttu-id="b5c1e-124">Meta veri</span><span class="sxs-lookup"><span data-stu-id="b5c1e-124">Metadata</span></span>](./metadata/index.md)  
 <span data-ttu-id="b5c1e-125">Bir derleyicinin, CLR tarafından yüklenen türler olmadan bir bileşenin meta verilerini oluşturmasına veya erişmesine olanak tanıyan meta veri API 'sini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b5c1e-125">Describes the metadata API, which enables a client such as a compiler to generate or access a component's metadata without the types being loaded by the CLR.</span></span>  
  
 [<span data-ttu-id="b5c1e-126">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="b5c1e-126">Profiling</span></span>](./profiling/index.md)  
 <span data-ttu-id="b5c1e-127">Profil oluşturucunun bir programın CLR tarafından yürütülmesini izlemesini sağlayan profil oluşturma API 'sini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b5c1e-127">Describes the profiling API, which enables a profiler to monitor a program's execution by the CLR.</span></span>  
  
 [<span data-ttu-id="b5c1e-128">Tanımlayıcı adlandırma</span><span class="sxs-lookup"><span data-stu-id="b5c1e-128">Strong Naming</span></span>](./strong-naming/index.md)  
 <span data-ttu-id="b5c1e-129">Bir istemcinin derlemeler için tanımlayıcı ad imzalamayı yönetmesine olanak tanıyan güçlü adlandırma API 'sini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b5c1e-129">Describes the strong naming API, which enables a client to administer strong name signing for assemblies.</span></span>  

 [<span data-ttu-id="b5c1e-130">WMI ve Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="b5c1e-130">WMI and Performance Counters</span></span>](wmi/index.md)  
 <span data-ttu-id="b5c1e-131">Windows Yönetim Araçları (WMI) kitaplıklarına çağrıları kaymakta olan API 'Leri açıklar.</span><span class="sxs-lookup"><span data-stu-id="b5c1e-131">Describes the APIs that wrap calls to Windows Management Instrumentation (WMI) libraries.</span></span>
  
 [<span data-ttu-id="b5c1e-132">Tlbexp Yardımcı İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b5c1e-132">Tlbexp Helper Functions</span></span>](./tlbexp/index.md)  
 <span data-ttu-id="b5c1e-133">Derleme-tür kitaplığı dönüştürme işlemi sırasında tür kitaplığı verme programı (Tlbexp.exe) tarafından kullanılan iki yardımcı işlevi ve arabirimi açıklar.</span><span class="sxs-lookup"><span data-stu-id="b5c1e-133">Describes the two helper functions and interface used by the Type Library Exporter (Tlbexp.exe) during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b5c1e-134">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="b5c1e-134">Related Sections</span></span>  

 [<span data-ttu-id="b5c1e-135">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b5c1e-135">Development Guide</span></span>](../development-guide.md)
