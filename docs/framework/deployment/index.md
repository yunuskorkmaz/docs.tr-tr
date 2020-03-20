---
title: .NET Framework ve Uygulamaları Dağıtma
ms.date: 03/30/2017
helpviewer_keywords:
- deploying applications [.NET Framework], packaging
- deploying applications [.NET Framework]
- deploying applications [.NET Framework], features
- deploying applications [.NET Framework], distribution
- .NET Framework, deploying
- .NET Framework application deployment
ms.assetid: 238d8284-6042-4a38-a7f6-1ee8efd719da
ms.openlocfilehash: b1ba9810b4b0d5a1688318db1093a9ce9bdf8fda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75716472"
---
# <a name="deploying-the-net-framework-and-applications"></a><span data-ttu-id="57207-102">.NET Framework ve Uygulamaları Dağıtma</span><span class="sxs-lookup"><span data-stu-id="57207-102">Deploying the .NET Framework and Applications</span></span>

<span data-ttu-id="57207-103">Bu makale, .NET Framework'u uygulamanızla birlikte dağıtmaya başlamanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="57207-103">This article helps you get started deploying the .NET Framework with your application.</span></span> <span data-ttu-id="57207-104">Bilgilerin çoğu geliştiriciler, OEM'ler ve kurumsal yöneticiler için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="57207-104">Most of the information is intended for developers, OEMs, and enterprise administrators.</span></span> <span data-ttu-id="57207-105">.NET Framework'u bilgisayarlarına yüklemek isteyen kullanıcılar [.NET Framework'ün yüklenmesini](../install/index.md)okumalıdır.</span><span class="sxs-lookup"><span data-stu-id="57207-105">Users who want to install the .NET Framework on their computers should read [Installing the .NET Framework](../install/index.md).</span></span>

## <a name="key-deployment-resources"></a><span data-ttu-id="57207-106">Anahtar Dağıtım Kaynakları</span><span class="sxs-lookup"><span data-stu-id="57207-106">Key Deployment Resources</span></span>

<span data-ttu-id="57207-107">.NET Framework'ün dağıtımı ve servisi hakkında belirli bilgiler için diğer MSDN konularına aşağıdaki bağlantıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="57207-107">Use the following links to other MSDN topics for specific information about deploying and servicing the .NET Framework.</span></span>

<span data-ttu-id="57207-108">**Kurulum ve dağıtım**</span><span class="sxs-lookup"><span data-stu-id="57207-108">**Setup and deployment**</span></span>

- <span data-ttu-id="57207-109">Genel yükleyici ve dağıtım bilgileri:</span><span class="sxs-lookup"><span data-stu-id="57207-109">General installer and deployment information:</span></span>

  - <span data-ttu-id="57207-110">Yükleyici seçenekleri:</span><span class="sxs-lookup"><span data-stu-id="57207-110">Installer options:</span></span>

    - [<span data-ttu-id="57207-111">Web yükleyici</span><span class="sxs-lookup"><span data-stu-id="57207-111">Web installer</span></span>](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

    - [<span data-ttu-id="57207-112">Çevrimdışı yükleyici</span><span class="sxs-lookup"><span data-stu-id="57207-112">Offline installer</span></span>](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

  - <span data-ttu-id="57207-113">Yükleme modları:</span><span class="sxs-lookup"><span data-stu-id="57207-113">Installation modes:</span></span>

    - [<span data-ttu-id="57207-114">Sessiz yükleme</span><span class="sxs-lookup"><span data-stu-id="57207-114">Silent installation</span></span>](deployment-guide-for-developers.md#chaining_custom)

    - [<span data-ttu-id="57207-115">UI görüntüleme</span><span class="sxs-lookup"><span data-stu-id="57207-115">Displaying a UI</span></span>](deployment-guide-for-developers.md#chaining_default)

  - [<span data-ttu-id="57207-116">.NET Framework 4.5 kurulumları sırasında sistem yeniden başlatmayı azaltma</span><span class="sxs-lookup"><span data-stu-id="57207-116">Reducing system restarts during .NET Framework 4.5 installations</span></span>](reducing-system-restarts.md)

  - [<span data-ttu-id="57207-117">Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="57207-117">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](../install/troubleshoot-blocked-installations-and-uninstallations.md)

- <span data-ttu-id="57207-118">.NET Framework'ü istemci uygulamasıyla dağıtma (geliştiriciler için):</span><span class="sxs-lookup"><span data-stu-id="57207-118">Deploying the .NET Framework with a client application (for developers):</span></span>

  - <span data-ttu-id="57207-119">Kurulum ve dağıtım projesinde [InstallShield'i kullanma](deployment-guide-for-developers.md#installshield-deployment)</span><span class="sxs-lookup"><span data-stu-id="57207-119">[Using InstallShield](deployment-guide-for-developers.md#installshield-deployment) in a setup and deployment project</span></span>

  - [<span data-ttu-id="57207-120">Visual Studio ClickOnce uygulamasını kullanma</span><span class="sxs-lookup"><span data-stu-id="57207-120">Using a Visual Studio ClickOnce application</span></span>](deployment-guide-for-developers.md#clickonce-deployment)

  - [<span data-ttu-id="57207-121">WiX yükleme paketi oluşturma</span><span class="sxs-lookup"><span data-stu-id="57207-121">Creating a WiX installation package</span></span>](deployment-guide-for-developers.md#wix)

  - [<span data-ttu-id="57207-122">Özel yükleyici kullanma</span><span class="sxs-lookup"><span data-stu-id="57207-122">Using a custom installer</span></span>](deployment-guide-for-developers.md#chaining)

  - <span data-ttu-id="57207-123">Geliştiriciler için [ek bilgiler](deployment-guide-for-developers.md)</span><span class="sxs-lookup"><span data-stu-id="57207-123">[Additional information](deployment-guide-for-developers.md) for developers</span></span>

- <span data-ttu-id="57207-124">.NET Framework'ün dağıtılması (OEM'ler ve yöneticiler için):</span><span class="sxs-lookup"><span data-stu-id="57207-124">Deploying the .NET Framework (for OEMs and administrators):</span></span>

  - [<span data-ttu-id="57207-125">Windows Değerlendirme ve Dağıtım Seti (ADK)</span><span class="sxs-lookup"><span data-stu-id="57207-125">Windows Assessment and Deployment Kit (ADK)</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=254976)

  - [<span data-ttu-id="57207-126">Yönetici kılavuzu</span><span class="sxs-lookup"><span data-stu-id="57207-126">Administrator's guide</span></span>](guide-for-administrators.md)

<span data-ttu-id="57207-127">**Bakım**</span><span class="sxs-lookup"><span data-stu-id="57207-127">**Servicing**</span></span>

- <span data-ttu-id="57207-128">Genel bilgi için [.NET Framework bloguna](https://devblogs.microsoft.com/dotnet/)bakın.</span><span class="sxs-lookup"><span data-stu-id="57207-128">For general information, see the [.NET Framework blog](https://devblogs.microsoft.com/dotnet/).</span></span>

- [<span data-ttu-id="57207-129">Sürümleri algılama</span><span class="sxs-lookup"><span data-stu-id="57207-129">Detecting versions</span></span>](../migration-guide/how-to-determine-which-versions-are-installed.md)

- [<span data-ttu-id="57207-130">Servis paketlerini ve güncelleştirmelerini algılama</span><span class="sxs-lookup"><span data-stu-id="57207-130">Detecting service packs and updates</span></span>](../migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)

## <a name="features-that-simplify-deployment"></a><span data-ttu-id="57207-131">Dağıtımı Basitleştiren Özellikler</span><span class="sxs-lookup"><span data-stu-id="57207-131">Features That Simplify Deployment</span></span>

<span data-ttu-id="57207-132">.NET Framework, uygulamalarınızı dağıtmayı kolaylaştıran bir dizi temel özellik sağlar:</span><span class="sxs-lookup"><span data-stu-id="57207-132">The .NET Framework provides a number of basic features that make it easier to deploy your applications:</span></span>

- <span data-ttu-id="57207-133">Etkilenmez uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="57207-133">No-impact applications.</span></span>

     <span data-ttu-id="57207-134">Bu özellik uygulama yalıtımı sağlar ve DLL çakışmalarını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="57207-134">This feature provides application isolation and eliminates DLL conflicts.</span></span> <span data-ttu-id="57207-135">Varsayılan olarak, bileşenler diğer uygulamaları etkilemez.</span><span class="sxs-lookup"><span data-stu-id="57207-135">By default, components do not affect other applications.</span></span>

- <span data-ttu-id="57207-136">Varsayılan olarak özel bileşenler.</span><span class="sxs-lookup"><span data-stu-id="57207-136">Private components by default.</span></span>

     <span data-ttu-id="57207-137">Varsayılan olarak, bileşenler uygulama dizinine dağıtılır ve yalnızca içeren uygulama tarafından görülebilir.</span><span class="sxs-lookup"><span data-stu-id="57207-137">By default, components are deployed to the application directory and are visible only to the containing application.</span></span>

- <span data-ttu-id="57207-138">Kontrollü kod paylaşımı.</span><span class="sxs-lookup"><span data-stu-id="57207-138">Controlled code sharing.</span></span>

     <span data-ttu-id="57207-139">Kod paylaşımı, varsayılan davranış olmak yerine kodu paylaşım için açıkça kullanılabilir hale getirmenizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="57207-139">Code sharing requires you to explicitly make code available for sharing instead of being the default behavior.</span></span>

- <span data-ttu-id="57207-140">Yan yana sürüm.</span><span class="sxs-lookup"><span data-stu-id="57207-140">Side-by-side versioning.</span></span>

     <span data-ttu-id="57207-141">Bir bileşenin veya uygulamanın birden çok sürümü bir arada bulunabilir, hangi sürümleri kullanacağınızı seçebilirsiniz ve ortak dil çalışma zamanı sürüm ilkesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="57207-141">Multiple versions of a component or application can coexist, you can choose which versions to use, and the common language runtime enforces versioning policy.</span></span>

- <span data-ttu-id="57207-142">XCOPY dağıtımı ve çoğaltma.</span><span class="sxs-lookup"><span data-stu-id="57207-142">XCOPY deployment and replication.</span></span>

     <span data-ttu-id="57207-143">Kendi kendine tanımlanmış ve bağımsız bileşenler ve uygulamalar kayıt defteri girişleri veya bağımlılıkları olmadan dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="57207-143">Self-described and self-contained components and applications can be deployed without registry entries or dependencies.</span></span>

- <span data-ttu-id="57207-144">Anında güncellemeler.</span><span class="sxs-lookup"><span data-stu-id="57207-144">On-the-fly updates.</span></span>

     <span data-ttu-id="57207-145">Yöneticiler, uzak bilgisayarlarda bile program DL'lerini güncelleştirmek için ASP.NET gibi ana bilgisayarları kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="57207-145">Administrators can use hosts, such as ASP.NET, to update program DLLs, even on remote computers.</span></span>

- <span data-ttu-id="57207-146">Windows Yükleyici ile tümleştirme.</span><span class="sxs-lookup"><span data-stu-id="57207-146">Integration with the Windows Installer.</span></span>

     <span data-ttu-id="57207-147">Uygulamanızı dağıtırken reklam, yayımlama, onarım ve isteğe bağlı yükleme mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="57207-147">Advertisement, publishing, repair, and install-on-demand are all available when deploying your application.</span></span>

- <span data-ttu-id="57207-148">Kurumsal dağıtım.</span><span class="sxs-lookup"><span data-stu-id="57207-148">Enterprise deployment.</span></span>

     <span data-ttu-id="57207-149">Bu özellik, Active Directory'yi kullanmak da dahil olmak üzere kolay yazılım dağıtımı sağlar.</span><span class="sxs-lookup"><span data-stu-id="57207-149">This feature provides easy software distribution, including using Active Directory.</span></span>

- <span data-ttu-id="57207-150">İndirme ve önbelleğe alma.</span><span class="sxs-lookup"><span data-stu-id="57207-150">Downloading and caching.</span></span>

     <span data-ttu-id="57207-151">Artımlı indirmeler indirmeleri daha küçük tutar ve bileşenler yalnızca düşük etkili dağıtım uygulaması tarafından kullanılmak üzere yalıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="57207-151">Incremental downloads keep downloads smaller, and components can be isolated for use only by the application for low-impact deployment.</span></span>

- <span data-ttu-id="57207-152">Kısmen güvenilen kod.</span><span class="sxs-lookup"><span data-stu-id="57207-152">Partially trusted code.</span></span>

     <span data-ttu-id="57207-153">Kimlik, kullanıcı yerine koda dayanır ve sertifika iletişim kutusu görünmez.</span><span class="sxs-lookup"><span data-stu-id="57207-153">Identity is based on the code instead of the user, and no certificate dialog boxes appear.</span></span>

## <a name="packaging-and-distributing-net-framework-applications"></a><span data-ttu-id="57207-154">.NET Çerçeve Uygulamalarının Paketlenmesi ve Dağıtılması</span><span class="sxs-lookup"><span data-stu-id="57207-154">Packaging and Distributing .NET Framework Applications</span></span>

<span data-ttu-id="57207-155">.NET Framework'ün bazı paketleme ve dağıtım bilgileri belgelerin diğer bölümlerinde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="57207-155">Some of the packaging and deployment information for the .NET Framework is described in other sections of the documentation.</span></span> <span data-ttu-id="57207-156">Bu [bölümler,](../../standard/assembly/index.md)hiçbir kayıt defteri girişi, [güçlü adlandırılmış derlemeler](../../standard/assembly/strong-named.md), ad tekliği sağlamak ve ad sızdırma önlemek ve [derleme sürümü](../../standard/assembly/versioning.md), DLL çakışmaları ile ilişkili sorunların çoğunu giderir, derleme ler, derlemeler olarak adlandırılan kendi kendini açıklayan birimler hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="57207-156">Those sections provide information about the self-describing units called [assemblies](../../standard/assembly/index.md), which require no registry entries, [strong-named assemblies](../../standard/assembly/strong-named.md), which ensure name uniqueness and prevent name spoofing, and [assembly versioning](../../standard/assembly/versioning.md), which addresses many of the problems associated with DLL conflicts.</span></span> <span data-ttu-id="57207-157">Aşağıdaki bölümlerde .NET Framework uygulamalarının paketlenmesi ve dağıtılması hakkında bilgi verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="57207-157">The following sections provide information about packaging and distributing .NET Framework applications.</span></span>

### <a name="packaging"></a><span data-ttu-id="57207-158">Paketleme</span><span class="sxs-lookup"><span data-stu-id="57207-158">Packaging</span></span>

<span data-ttu-id="57207-159">.NET Framework, ambalaj uygulamaları için aşağıdaki seçenekleri sunar:</span><span class="sxs-lookup"><span data-stu-id="57207-159">The .NET Framework provides the following options for packaging applications:</span></span>

- <span data-ttu-id="57207-160">Tek bir derleme olarak veya derlemeler topluluğu olarak.</span><span class="sxs-lookup"><span data-stu-id="57207-160">As a single assembly or as a collection of assemblies.</span></span>

     <span data-ttu-id="57207-161">Bu seçenekle,..dll veya .exe dosyalarını oluşturulurken kullanmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="57207-161">With this option, you simply use the .dll or .exe files as they were built.</span></span>

- <span data-ttu-id="57207-162">Dolap (CAB) dosyaları olarak.</span><span class="sxs-lookup"><span data-stu-id="57207-162">As cabinet (CAB) files.</span></span>

     <span data-ttu-id="57207-163">Bu seçenekle, dağıtım yapmak veya daha az zaman alan bir şekilde indirmek için dosyaları .cab dosyalarına sıkıştırırsınız.</span><span class="sxs-lookup"><span data-stu-id="57207-163">With this option, you compress files into .cab files to make distribution or download less time consuming.</span></span>

- <span data-ttu-id="57207-164">Windows Installer paketi olarak veya diğer yükleyici biçimlerinde.</span><span class="sxs-lookup"><span data-stu-id="57207-164">As a Windows Installer package or in other installer formats.</span></span>

     <span data-ttu-id="57207-165">Bu seçenekle, Windows Yükleyiciile kullanılmak üzere .msi dosyaları oluşturursunuz veya uygulamanızı başka bir yükleyiciyle kullanmak üzere paketlersiniz.</span><span class="sxs-lookup"><span data-stu-id="57207-165">With this option, you create .msi files for use with the Windows Installer, or you package your application for use with some other installer.</span></span>

### <a name="distribution"></a><span data-ttu-id="57207-166">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="57207-166">Distribution</span></span>

<span data-ttu-id="57207-167">.NET Framework, uygulamaları dağıtmak için aşağıdaki seçenekleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="57207-167">The .NET Framework provides the following options for distributing applications:</span></span>

- <span data-ttu-id="57207-168">XCOPY veya FTP kullanın.</span><span class="sxs-lookup"><span data-stu-id="57207-168">Use XCOPY or FTP.</span></span>

     <span data-ttu-id="57207-169">Ortak dil çalışma zamanı uygulamaları kendi kendini tanımladığından ve kayıt defteri girişi gerektirmediği için, uygulamayı yalnızca uygun bir dizine kopyalamak için XCOPY veya FTP'yi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57207-169">Because common language runtime applications are self-describing and require no registry entries, you can use XCOPY or FTP to simply copy the application to an appropriate directory.</span></span> <span data-ttu-id="57207-170">Uygulama daha sonra bu dizinden çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="57207-170">The application can then be run from that directory.</span></span>

- <span data-ttu-id="57207-171">Kod karşıdan yüklemeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="57207-171">Use code download.</span></span>

     <span data-ttu-id="57207-172">Uygulamanızı Internet üzerinden veya kurumsal bir intranet üzerinden dağıtıyorsanız, kodu bir bilgisayara indirebilir ve uygulamayı orada çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57207-172">If you are distributing your application over the Internet or through a corporate intranet, you can simply download the code to a computer and run the application there.</span></span>

- <span data-ttu-id="57207-173">Windows Installer 2.0 gibi bir yükleyici programı kullanın.</span><span class="sxs-lookup"><span data-stu-id="57207-173">Use an installer program such as Windows Installer 2.0.</span></span>

     <span data-ttu-id="57207-174">Windows Installer 2.0, genel derleme önbelleğinde ve özel dizinlerde .NET Framework derlemelerini yükleyebilir, onarabilir veya kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="57207-174">Windows Installer 2.0 can install, repair, or remove .NET Framework assemblies in the global assembly cache and in private directories.</span></span>

### <a name="installation-location"></a><span data-ttu-id="57207-175">Yükleme Konumu</span><span class="sxs-lookup"><span data-stu-id="57207-175">Installation Location</span></span>

<span data-ttu-id="57207-176">Çalışma süresine kadar bulunabilmeleri için uygulamanızın derlemelerini nereye dağıtacağınızı belirlemek için [Çalışma Zamanı Derlemeleri'ni nasıl bulur'a](how-the-runtime-locates-assemblies.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="57207-176">To determine where to deploy your application's assemblies so they can be found by the runtime, see [How the Runtime Locates Assemblies](how-the-runtime-locates-assemblies.md).</span></span>

<span data-ttu-id="57207-177">Güvenlik hususları, uygulamanızı nasıl dağıtdığınızı da etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="57207-177">Security considerations can also affect how you deploy your application.</span></span> <span data-ttu-id="57207-178">Güvenlik izinleri, kodun bulunduğu yere göre yönetilen koda verilir.</span><span class="sxs-lookup"><span data-stu-id="57207-178">Security permissions are granted to managed code according to where the code is located.</span></span> <span data-ttu-id="57207-179">Bir uygulamayı veya bileşeni Internet gibi çok az güven aldığı bir konuma dağıtmak, uygulamanın veya bileşenin yapabileceklerini sınırlar.</span><span class="sxs-lookup"><span data-stu-id="57207-179">Deploying an application or component to a location where it receives little trust, such as the Internet, limits what the application or component can do.</span></span> <span data-ttu-id="57207-180">Dağıtım ve güvenlik konuları hakkında daha fazla bilgi için [Kod Erişim Güvenlik Temelleri'ne](../misc/code-access-security-basics.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="57207-180">For more information about deployment and security considerations, see [Code Access Security Basics](../misc/code-access-security-basics.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="57207-181">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="57207-181">Related Topics</span></span>

|<span data-ttu-id="57207-182">Başlık</span><span class="sxs-lookup"><span data-stu-id="57207-182">Title</span></span>|<span data-ttu-id="57207-183">Açıklama</span><span class="sxs-lookup"><span data-stu-id="57207-183">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="57207-184">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="57207-184">How the Runtime Locates Assemblies</span></span>](how-the-runtime-locates-assemblies.md)|<span data-ttu-id="57207-185">Ortak dil çalışma zamanının bağlayıcı bir isteği yerine getirmek için hangi derlemenin kullanılacağını nasıl belirlediğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="57207-185">Describes how the common language runtime determines which assembly to use to fulfill a binding request.</span></span>|
|[<span data-ttu-id="57207-186">Derleme Yükleme için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="57207-186">Best Practices for Assembly Loading</span></span>](best-practices-for-assembly-loading.md)|<span data-ttu-id="57207-187">Tür kimliği, "ve <xref:System.InvalidCastException> <xref:System.MissingMethodException>diğer hatalara" yol açabilecek sorunlardan kaçınmanın yollarını tartışır.</span><span class="sxs-lookup"><span data-stu-id="57207-187">Discusses ways to avoid problems of type identity that can lead to <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, and other errors.</span></span>|
|[<span data-ttu-id="57207-188">.NET Framework 4.5 Yüklemeleri Sırasında Sistem Yeniden Başlatmalarını Azaltma</span><span class="sxs-lookup"><span data-stu-id="57207-188">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](reducing-system-restarts.md)|<span data-ttu-id="57207-189">Mümkün olduğunda yeniden başlatmayı önleyen yeniden başlatma yöneticisini açıklar ve .NET Framework'ü yükleyen uygulamaların bundan nasıl yararlanabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="57207-189">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>|
|[<span data-ttu-id="57207-190">Yöneticiler için Dağıtım Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="57207-190">Deployment Guide for Administrators</span></span>](guide-for-administrators.md)|<span data-ttu-id="57207-191">Bir sistem yöneticisinin Microsoft Endpoint Configuration Manager'ı kullanarak .NET Framework'ünü ve sistem bağımlılıklarını ağ da nasıl dağıtabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="57207-191">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using Microsoft Endpoint Configuration Manager.</span></span>|
|[<span data-ttu-id="57207-192">Geliştiriciler için Dağıtım Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="57207-192">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)|<span data-ttu-id="57207-193">Geliştiricilerin .NET Framework'u uygulamalarıyla birlikte kullanıcılarının bilgisayarlarına nasıl yükleyebileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="57207-193">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>|
|[<span data-ttu-id="57207-194">Uygulamaları, Hizmetleri ve Bileşenleri Dağıtma</span><span class="sxs-lookup"><span data-stu-id="57207-194">Deploying Applications, Services, and Components</span></span>](/visualstudio/deployment/deploying-applications-services-and-components)|<span data-ttu-id="57207-195">Visual Studio'da ClickOnce ve Windows Installer teknolojilerini kullanarak bir uygulamayı yayımlama yönergeleri de dahil olmak üzere dağıtım seçeneklerini tartışır.</span><span class="sxs-lookup"><span data-stu-id="57207-195">Discusses deployment options in Visual Studio, including instructions for publishing an application using the ClickOnce and Windows Installer technologies.</span></span>|
|[<span data-ttu-id="57207-196">ClickOnce Uygulamalarını Yayımlama</span><span class="sxs-lookup"><span data-stu-id="57207-196">Publishing ClickOnce Applications</span></span>](/visualstudio/deployment/publishing-clickonce-applications)|<span data-ttu-id="57207-197">Windows Forms uygulamasını nasıl paketleyip ClickOnce ile ağdaki istemci bilgisayarlara nasıl dağıtılanın açıklar.</span><span class="sxs-lookup"><span data-stu-id="57207-197">Describes how to package a Windows Forms application and deploy it with ClickOnce to client computers on a network.</span></span>|
|[<span data-ttu-id="57207-198">Kaynakları Paketleme ve Dağıtma</span><span class="sxs-lookup"><span data-stu-id="57207-198">Packaging and Deploying Resources</span></span>](../resources/packaging-and-deploying-resources-in-desktop-apps.md)|<span data-ttu-id="57207-199">.NET Framework'ün kaynakları paketlemek ve dağıtmak için kullandığı hub ve spoke modelini açıklar; kaynak adlandırma kuralları, geri dönüş süreci ve paketleme alternatiflerini kapsar.</span><span class="sxs-lookup"><span data-stu-id="57207-199">Describes the hub and spoke model that the .NET Framework uses to package and deploy resources; covers resource naming conventions, fallback process, and packaging alternatives.</span></span>|
|[<span data-ttu-id="57207-200">Birlikte Çalışma Uygulamasını Dağıtma</span><span class="sxs-lookup"><span data-stu-id="57207-200">Deploying an Interop Application</span></span>](../interop/deploying-an-interop-application.md)|<span data-ttu-id="57207-201">Genellikle bir .NET Framework istemci derlemesi, farklı COM türü kitaplıklarını temsil eden bir veya daha fazla interop derlemesi ve bir veya daha fazla kayıtlı COM bileşeni içeren interop uygulamalarının nasıl gönderililip yüklenirolduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="57207-201">Explains how to ship and install interop applications, which typically include a .NET Framework client assembly, one or more interop assemblies representing distinct COM type libraries, and one or more registered COM components.</span></span>|
|[<span data-ttu-id="57207-202">Nasıl Yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma</span><span class="sxs-lookup"><span data-stu-id="57207-202">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](how-to-get-progress-from-the-dotnet-installer.md)|<span data-ttu-id="57207-203">Kurulum ilerlemesini kendi görünümünüz gösterirken .NET Framework kurulum işlemini sessizce nasıl başlatıp izleyeceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="57207-203">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>|

## <a name="see-also"></a><span data-ttu-id="57207-204">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57207-204">See also</span></span>

- [<span data-ttu-id="57207-205">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="57207-205">Development Guide</span></span>](../development-guide.md)
