---
title: Yönetilmeyen API Başvurusu
ms.date: 11/06/2017
helpviewer_keywords:
- runtime, unmanaged APIs
- common language runtime, unmanaged APIs
- native API reference [.NET Framework]
- unmanaged API reference [.NET Framework]
ms.assetid: 9aa000ee-c04c-492c-ae4f-83ecdf4fdbbe
ms.openlocfilehash: f7dd78b889129998dee31a22f5dd23325613b8ea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092020"
---
# <a name="unmanaged-api-reference"></a><span data-ttu-id="9a8b6-102">Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="9a8b6-102">Unmanaged API Reference</span></span>
<span data-ttu-id="9a8b6-103">Bu bölüm, çalışma zamanı Konakları, derleyiciler, kod çözücüler, gizleme, hata ayıklayıcılar ve profil oluşturucular gibi yönetilen kodla ilgili uygulamalar tarafından kullanılabilecek yönetilmeyen API 'Ler hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="9a8b6-103">This section includes information on unmanaged APIs that can be used by managed-code-related applications, such as runtime hosts, compilers, disassemblers, obfuscators, debuggers, and profilers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9a8b6-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9a8b6-104">In This Section</span></span>  
 [<span data-ttu-id="9a8b6-105">Ortak Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="9a8b6-105">Common Data Types</span></span>](common-data-types-unmanaged-api-reference.md)  
 <span data-ttu-id="9a8b6-106">Özellikle yönetilmeyen profil oluşturma ve hata ayıklama API 'Lerinde kullanılan ortak veri türlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="9a8b6-106">Lists the common data types that are used, particularly in the unmanaged profiling and debugging APIs.</span></span>  
  
 [<span data-ttu-id="9a8b6-107">ALINK</span><span class="sxs-lookup"><span data-stu-id="9a8b6-107">ALink</span></span>](./alink/index.md)  
 <span data-ttu-id="9a8b6-108">.NET Framework derlemeleri ve ilişkisiz modülleri oluşturmayı destekleyen ALink API 'sini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9a8b6-108">Describes the ALink API, which supports the creation of .NET Framework assemblies and unbound modules.</span></span>  
  
 [<span data-ttu-id="9a8b6-109">Authenticode</span><span class="sxs-lookup"><span data-stu-id="9a8b6-109">Authenticode</span></span>](./authenticode/index.md)  
 <span data-ttu-id="9a8b6-110">Authenticode XrML lisans oluşturma ve doğrulama modülünü destekler.</span><span class="sxs-lookup"><span data-stu-id="9a8b6-110">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
 [<span data-ttu-id="9a8b6-111">Sabitler</span><span class="sxs-lookup"><span data-stu-id="9a8b6-111">Constants</span></span>](constants-unmanaged-api-reference.md)  
 <span data-ttu-id="9a8b6-112">Corsyd. IDL içinde tanımlanan sabitleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="9a8b6-112">Describes the constants that are defined in CorSym.idl.</span></span>  
  
 <span data-ttu-id="9a8b6-113">[Özel arabirim öznitelikleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms231946(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9a8b6-113">[Custom Interface Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms231946(v=vs.100))</span></span>  
 <span data-ttu-id="9a8b6-114">Bileşen nesne modeli (COM) özel arabirim özniteliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9a8b6-114">Describes component object model (COM) custom interface attributes.</span></span>  
  
 [<span data-ttu-id="9a8b6-115">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9a8b6-115">Debugging</span></span>](./debugging/index.md)  
 <span data-ttu-id="9a8b6-116">Bir hata ayıklayıcının ortak dil çalışma zamanı (CLR) ortamında çalışan kodun hatalarını ayıklamasını sağlayan hata ayıklama API 'sini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9a8b6-116">Describes the debugging API, which enables a debugger to debug code that runs in the common language runtime (CLR) environment.</span></span>  
  
 [<span data-ttu-id="9a8b6-117">Tanılama Simge Deposu</span><span class="sxs-lookup"><span data-stu-id="9a8b6-117">Diagnostics Symbol Store</span></span>](./diagnostics/index.md)  
 <span data-ttu-id="9a8b6-118">Bir derleyicinin hata ayıklayıcı tarafından kullanılmak üzere sembol bilgisi oluşturmasını sağlayan tanılama sembol deposu API 'sini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9a8b6-118">Describes the diagnostics symbol store API, which enables a compiler to generate symbol information for use by a debugger.</span></span>  
  
 [<span data-ttu-id="9a8b6-119">Fusion</span><span class="sxs-lookup"><span data-stu-id="9a8b6-119">Fusion</span></span>](./fusion/index.md)  
 <span data-ttu-id="9a8b6-120">Uygulama için bu kaynakların doğru sürümlerini bulmak üzere bir çalışma zamanı konağının bir uygulama kaynaklarının özelliklerine erişmesini sağlayan Fusion API 'sini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9a8b6-120">Describes the fusion API, which enables a runtime host to access the properties of an application's resources in order to locate the correct versions of those resources for the application.</span></span>  
  
 [<span data-ttu-id="9a8b6-121">Barındırma</span><span class="sxs-lookup"><span data-stu-id="9a8b6-121">Hosting</span></span>](./hosting/index.md)  
 <span data-ttu-id="9a8b6-122">Yönetilmeyen ana bilgisayarların CLR 'yi uygulamalarıyla tümleştirmesini sağlayan barındırma API 'sini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9a8b6-122">Describes the hosting API, which enables unmanaged hosts to integrate the CLR into their applications.</span></span>  
  
 [<span data-ttu-id="9a8b6-123">Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="9a8b6-123">Metadata</span></span>](./metadata/index.md)  
 <span data-ttu-id="9a8b6-124">Bir derleyicinin, CLR tarafından yüklenen türler olmadan bir bileşenin meta verilerini oluşturmasına veya erişmesine olanak tanıyan meta veri API 'sini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9a8b6-124">Describes the metadata API, which enables a client such as a compiler to generate or access a component's metadata without the types being loaded by the CLR.</span></span>  
  
 [<span data-ttu-id="9a8b6-125">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9a8b6-125">Profiling</span></span>](./profiling/index.md)  
 <span data-ttu-id="9a8b6-126">Profil oluşturucunun bir programın CLR tarafından yürütülmesini izlemesini sağlayan profil oluşturma API 'sini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9a8b6-126">Describes the profiling API, which enables a profiler to monitor a program's execution by the CLR.</span></span>  
  
 [<span data-ttu-id="9a8b6-127">Kesin Adlandırma</span><span class="sxs-lookup"><span data-stu-id="9a8b6-127">Strong Naming</span></span>](./strong-naming/index.md)  
 <span data-ttu-id="9a8b6-128">Bir istemcinin derlemeler için tanımlayıcı ad imzalamayı yönetmesine olanak tanıyan güçlü adlandırma API 'sini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9a8b6-128">Describes the strong naming API, which enables a client to administer strong name signing for assemblies.</span></span>  

 [<span data-ttu-id="9a8b6-129">WMI ve Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="9a8b6-129">WMI and Performance Counters</span></span>](wmi/index.md)  
 <span data-ttu-id="9a8b6-130">Windows Yönetim Araçları (WMI) kitaplıklarına çağrıları kaymakta olan API 'Leri açıklar.</span><span class="sxs-lookup"><span data-stu-id="9a8b6-130">Describes the APIs that wrap calls to Windows Management Instrumentation (WMI) libraries.</span></span>
  
 [<span data-ttu-id="9a8b6-131">Tlbexp Yardımcı İşlevleri</span><span class="sxs-lookup"><span data-stu-id="9a8b6-131">Tlbexp Helper Functions</span></span>](./tlbexp/index.md)  
 <span data-ttu-id="9a8b6-132">Tür kitaplığı verme programı (Tlbexp. exe) tarafından derlemeden tür kitaplığı dönüştürme işlemi sırasında kullanılan iki yardımcı işlevi ve arabirimi açıklar.</span><span class="sxs-lookup"><span data-stu-id="9a8b6-132">Describes the two helper functions and interface used by the Type Library Exporter (Tlbexp.exe) during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9a8b6-133">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="9a8b6-133">Related Sections</span></span>  
 [<span data-ttu-id="9a8b6-134">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9a8b6-134">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
