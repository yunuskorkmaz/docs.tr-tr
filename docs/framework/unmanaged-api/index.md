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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73092020"
---
# <a name="unmanaged-api-reference"></a><span data-ttu-id="eb252-102">Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="eb252-102">Unmanaged API Reference</span></span>
<span data-ttu-id="eb252-103">Bu bölümde, runtime ana bilgisayarları, derleyiciler, sökücüler, obfuscators, hata ayıklayıcılar ve profilciler gibi yönetilen kodla ilgili uygulamalar tarafından kullanılabilecek yönetilmeyen API'ler hakkında bilgiler bulunur.</span><span class="sxs-lookup"><span data-stu-id="eb252-103">This section includes information on unmanaged APIs that can be used by managed-code-related applications, such as runtime hosts, compilers, disassemblers, obfuscators, debuggers, and profilers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eb252-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="eb252-104">In This Section</span></span>  
 [<span data-ttu-id="eb252-105">Ortak Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="eb252-105">Common Data Types</span></span>](common-data-types-unmanaged-api-reference.md)  
 <span data-ttu-id="eb252-106">Özellikle yönetilmeyen profil oluşturma ve hata ayıklama API'lerinde olmak üzere kullanılan yaygın veri türlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="eb252-106">Lists the common data types that are used, particularly in the unmanaged profiling and debugging APIs.</span></span>  
  
 [<span data-ttu-id="eb252-107">Alink</span><span class="sxs-lookup"><span data-stu-id="eb252-107">ALink</span></span>](./alink/index.md)  
 <span data-ttu-id="eb252-108">.NET Framework derlemeleri ve bağlantısız modüllerin oluşturulmasını destekleyen ALink API'sini açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb252-108">Describes the ALink API, which supports the creation of .NET Framework assemblies and unbound modules.</span></span>  
  
 [<span data-ttu-id="eb252-109">Authenticode</span><span class="sxs-lookup"><span data-stu-id="eb252-109">Authenticode</span></span>](./authenticode/index.md)  
 <span data-ttu-id="eb252-110">Authenticode XrML lisans oluşturma ve doğrulama modüllerini destekler.</span><span class="sxs-lookup"><span data-stu-id="eb252-110">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
 [<span data-ttu-id="eb252-111">Sabitler</span><span class="sxs-lookup"><span data-stu-id="eb252-111">Constants</span></span>](constants-unmanaged-api-reference.md)  
 <span data-ttu-id="eb252-112">CorSym.idl'de tanımlanan sabitleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb252-112">Describes the constants that are defined in CorSym.idl.</span></span>  
  
 <span data-ttu-id="eb252-113">[Özel Arayüz Öznitelikleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms231946(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="eb252-113">[Custom Interface Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms231946(v=vs.100))</span></span>  
 <span data-ttu-id="eb252-114">Bileşen nesne modeli (COM) özel arabirim özniteliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb252-114">Describes component object model (COM) custom interface attributes.</span></span>  
  
 [<span data-ttu-id="eb252-115">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="eb252-115">Debugging</span></span>](./debugging/index.md)  
 <span data-ttu-id="eb252-116">Hata ayıklayıcının ortak dil çalışma zamanı (CLR) ortamında çalışan hata ayıklayıcı kodunu ayıklamasını sağlayan hata ayıklama API'sini açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb252-116">Describes the debugging API, which enables a debugger to debug code that runs in the common language runtime (CLR) environment.</span></span>  
  
 [<span data-ttu-id="eb252-117">Tanılama Simge Deposu</span><span class="sxs-lookup"><span data-stu-id="eb252-117">Diagnostics Symbol Store</span></span>](./diagnostics/index.md)  
 <span data-ttu-id="eb252-118">Bir derleyicinin hata ayıklayıcı tarafından kullanılmak üzere sembol bilgileri oluşturmasını sağlayan tanılama sembolü deposu API'yi açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb252-118">Describes the diagnostics symbol store API, which enables a compiler to generate symbol information for use by a debugger.</span></span>  
  
 [<span data-ttu-id="eb252-119">Fusion</span><span class="sxs-lookup"><span data-stu-id="eb252-119">Fusion</span></span>](./fusion/index.md)  
 <span data-ttu-id="eb252-120">Uygulama için bu kaynakların doğru sürümlerini bulmak için bir çalışma zamanı ana bilgisayar bir uygulamakaynaklarının özelliklerine erişmek için izin füzyon API açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb252-120">Describes the fusion API, which enables a runtime host to access the properties of an application's resources in order to locate the correct versions of those resources for the application.</span></span>  
  
 [<span data-ttu-id="eb252-121">Barındırma</span><span class="sxs-lookup"><span data-stu-id="eb252-121">Hosting</span></span>](./hosting/index.md)  
 <span data-ttu-id="eb252-122">Yönetilmeyen ana bilgisayarların CLR'yi uygulamalarına entegre etmesini sağlayan barındırma API'sini açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb252-122">Describes the hosting API, which enables unmanaged hosts to integrate the CLR into their applications.</span></span>  
  
 [<span data-ttu-id="eb252-123">Meta veriler</span><span class="sxs-lookup"><span data-stu-id="eb252-123">Metadata</span></span>](./metadata/index.md)  
 <span data-ttu-id="eb252-124">Derleyici gibi bir istemcinin CLR tarafından yüklenen türler olmadan bir bileşenin meta verilerini oluşturmasına veya bunlara erişmesini sağlayan meta veri API'sını açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb252-124">Describes the metadata API, which enables a client such as a compiler to generate or access a component's metadata without the types being loaded by the CLR.</span></span>  
  
 [<span data-ttu-id="eb252-125">Profil oluşturma</span><span class="sxs-lookup"><span data-stu-id="eb252-125">Profiling</span></span>](./profiling/index.md)  
 <span data-ttu-id="eb252-126">Profil oluşturma API'sini açıklar ve bir profil oluşturucunun bir programın CLR tarafından yürütülmesini izlemesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="eb252-126">Describes the profiling API, which enables a profiler to monitor a program's execution by the CLR.</span></span>  
  
 [<span data-ttu-id="eb252-127">Güçlü Adlandırma</span><span class="sxs-lookup"><span data-stu-id="eb252-127">Strong Naming</span></span>](./strong-naming/index.md)  
 <span data-ttu-id="eb252-128">İstemci derlemeler için güçlü ad imzalama yönetmek sağlayan güçlü adlandırma API açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb252-128">Describes the strong naming API, which enables a client to administer strong name signing for assemblies.</span></span>  

 [<span data-ttu-id="eb252-129">WMI ve Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="eb252-129">WMI and Performance Counters</span></span>](wmi/index.md)  
 <span data-ttu-id="eb252-130">Windows Yönetim Araçları (WMI) kitaplıklarına çağrıları kaydıran API'leri açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb252-130">Describes the APIs that wrap calls to Windows Management Instrumentation (WMI) libraries.</span></span>
  
 [<span data-ttu-id="eb252-131">Tlbexp Yardımcı İşlevleri</span><span class="sxs-lookup"><span data-stu-id="eb252-131">Tlbexp Helper Functions</span></span>](./tlbexp/index.md)  
 <span data-ttu-id="eb252-132">Montaj-to-type-kitaplık dönüştürme işlemi sırasında Tip Kitaplığı İhracatçısı (Tlbexp.exe) tarafından kullanılan iki yardımcı işlevi ve arabirimi açıklar.</span><span class="sxs-lookup"><span data-stu-id="eb252-132">Describes the two helper functions and interface used by the Type Library Exporter (Tlbexp.exe) during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="eb252-133">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="eb252-133">Related Sections</span></span>  
 [<span data-ttu-id="eb252-134">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="eb252-134">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
