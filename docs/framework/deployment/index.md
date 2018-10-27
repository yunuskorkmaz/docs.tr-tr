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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a650fa0340ce63a573074746eef60994e2254c86
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49453235"
---
# <a name="deploying-the-net-framework-and-applications"></a><span data-ttu-id="c7012-102">.NET Framework ve Uygulamaları Dağıtma</span><span class="sxs-lookup"><span data-stu-id="c7012-102">Deploying the .NET Framework and Applications</span></span>
<span data-ttu-id="c7012-103">Bu makalede, uygulamanızla birlikte .NET Framework'ü dağıtma başlamanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="c7012-103">This article helps you get started deploying the .NET Framework with your application.</span></span> <span data-ttu-id="c7012-104">İlgili bilgilerin çoğunu geliştiriciler, OEM'ler ve kuruluş yöneticileri için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c7012-104">Most of the information is intended for developers, OEMs, and enterprise administrators.</span></span> <span data-ttu-id="c7012-105">Kendi bilgisayarlarına .NET Framework'ü yüklemek isteyen kullanıcıların kimler [.NET Framework yükleme](~/docs/framework/install/index.md).</span><span class="sxs-lookup"><span data-stu-id="c7012-105">Users who want to install the .NET Framework on their computers should read [Installing the .NET Framework](~/docs/framework/install/index.md).</span></span>  
  
## <a name="key-deployment-resources"></a><span data-ttu-id="c7012-106">Anahtar Dağıtım Kaynakları</span><span class="sxs-lookup"><span data-stu-id="c7012-106">Key Deployment Resources</span></span>  
 <span data-ttu-id="c7012-107">Dağıtma ve .NET Framework bakım hakkında ayrıntılı bilgi için MSDN diğer konular için aşağıdaki bağlantıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7012-107">Use the following links to other MSDN topics for specific information about deploying and servicing the .NET Framework.</span></span>  
  
 <span data-ttu-id="c7012-108">**Kurulum ve dağıtım**</span><span class="sxs-lookup"><span data-stu-id="c7012-108">**Setup and deployment**</span></span>  
  
-   <span data-ttu-id="c7012-109">Genel yükleyici ve dağıtım bilgileri:</span><span class="sxs-lookup"><span data-stu-id="c7012-109">General installer and deployment information:</span></span>  
  
    -   <span data-ttu-id="c7012-110">Yükleyici seçenekleri:</span><span class="sxs-lookup"><span data-stu-id="c7012-110">Installer options:</span></span>  
  
        -   [<span data-ttu-id="c7012-111">Web yükleyicisi</span><span class="sxs-lookup"><span data-stu-id="c7012-111">Web installer</span></span>](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)  
  
        -   [<span data-ttu-id="c7012-112">Çevrimdışı yükleyici</span><span class="sxs-lookup"><span data-stu-id="c7012-112">Offline installer</span></span>](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)  
  
    -   <span data-ttu-id="c7012-113">Yükleme modu:</span><span class="sxs-lookup"><span data-stu-id="c7012-113">Installation modes:</span></span>  
  
        -   [<span data-ttu-id="c7012-114">Sessiz yükleme</span><span class="sxs-lookup"><span data-stu-id="c7012-114">Silent installation</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_custom)  
  
        -   [<span data-ttu-id="c7012-115">Bir kullanıcı Arabirimi görüntüleme</span><span class="sxs-lookup"><span data-stu-id="c7012-115">Displaying a UI</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_default)  
  
    -   [<span data-ttu-id="c7012-116">Sistem .NET Framework 4.5 yüklemeleri sırasında yeniden başlatmalarını azaltma</span><span class="sxs-lookup"><span data-stu-id="c7012-116">Reducing system restarts during .NET Framework 4.5 installations</span></span>](../../../docs/framework/deployment/reducing-system-restarts.md)  
  
    -   [<span data-ttu-id="c7012-117">Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="c7012-117">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](~/docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)  
  
-   <span data-ttu-id="c7012-118">.NET Framework istemci uygulaması ile (geliştiriciler için) dağıtma:</span><span class="sxs-lookup"><span data-stu-id="c7012-118">Deploying the .NET Framework with a client application (for developers):</span></span>  
  
    -   <span data-ttu-id="c7012-119">[InstallShield kullanarak](../../../docs/framework/deployment/deployment-guide-for-developers.md#installshield-deployment) Kurulum ve dağıtım projesindeki</span><span class="sxs-lookup"><span data-stu-id="c7012-119">[Using InstallShield](../../../docs/framework/deployment/deployment-guide-for-developers.md#installshield-deployment) in a setup and deployment project</span></span>  
  
    -   [<span data-ttu-id="c7012-120">Visual Studio ClickOnce uygulaması kullanma</span><span class="sxs-lookup"><span data-stu-id="c7012-120">Using a Visual Studio ClickOnce application</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#clickonce-deployment)  
  
    -   [<span data-ttu-id="c7012-121">WiX kurulum paketi oluşturuluyor</span><span class="sxs-lookup"><span data-stu-id="c7012-121">Creating a WiX installation package</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#wix)  
  
    -   [<span data-ttu-id="c7012-122">Özel bir yükleyici kullanarak</span><span class="sxs-lookup"><span data-stu-id="c7012-122">Using a custom installer</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining)  
  
    -   <span data-ttu-id="c7012-123">[Ek bilgi](../../../docs/framework/deployment/deployment-guide-for-developers.md) geliştiricileri için</span><span class="sxs-lookup"><span data-stu-id="c7012-123">[Additional information](../../../docs/framework/deployment/deployment-guide-for-developers.md) for developers</span></span>  
  
-   <span data-ttu-id="c7012-124">.NET Framework'ü (OEM'ler ve Yöneticiler) dağıtma:</span><span class="sxs-lookup"><span data-stu-id="c7012-124">Deploying the .NET Framework (for OEMs and administrators):</span></span>  
  
    -   [<span data-ttu-id="c7012-125">Windows değerlendirme ve dağıtım Seti'nin (ADK)</span><span class="sxs-lookup"><span data-stu-id="c7012-125">Windows Assessment and Deployment Kit (ADK)</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=254976)  
  
    -   [<span data-ttu-id="c7012-126">Yönetici Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c7012-126">Administrator's guide</span></span>](../../../docs/framework/deployment/guide-for-administrators.md)  
  
 <span data-ttu-id="c7012-127">**Bakım**</span><span class="sxs-lookup"><span data-stu-id="c7012-127">**Servicing**</span></span>  
  
-   <span data-ttu-id="c7012-128">Genel bilgi için bkz. [.NET Framework blogu](https://go.microsoft.com/fwlink/p/?LinkId=254977)</span><span class="sxs-lookup"><span data-stu-id="c7012-128">For general information, see the [.NET Framework blog](https://go.microsoft.com/fwlink/p/?LinkId=254977)</span></span>  
  
-   [<span data-ttu-id="c7012-129">Sürümlerini algılamaya</span><span class="sxs-lookup"><span data-stu-id="c7012-129">Detecting versions</span></span>](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)  
  
-   [<span data-ttu-id="c7012-130">Hizmet paketleri ve güncelleştirmeler algılanıyor</span><span class="sxs-lookup"><span data-stu-id="c7012-130">Detecting service packs and updates</span></span>](../../../docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
  
## <a name="features-that-simplify-deployment"></a><span data-ttu-id="c7012-131">Dağıtım basitleştiren özellikleri</span><span class="sxs-lookup"><span data-stu-id="c7012-131">Features That Simplify Deployment</span></span>  
 <span data-ttu-id="c7012-132">.NET Framework ve uygulamalarınızı daha kolay hale getirmek temel özellikleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="c7012-132">The .NET Framework provides a number of basic features that make it easier to deploy your applications:</span></span>  
  
-   <span data-ttu-id="c7012-133">Etkisiz uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="c7012-133">No-impact applications.</span></span>  
  
     <span data-ttu-id="c7012-134">Bu özellik, uygulama yalıtımı sağlar ve DLL çakışmalarını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c7012-134">This feature provides application isolation and eliminates DLL conflicts.</span></span> <span data-ttu-id="c7012-135">Varsayılan olarak, bileşenleri, diğer uygulamaları etkilemez.</span><span class="sxs-lookup"><span data-stu-id="c7012-135">By default, components do not affect other applications.</span></span>  
  
-   <span data-ttu-id="c7012-136">Özel bileşenler varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="c7012-136">Private components by default.</span></span>  
  
     <span data-ttu-id="c7012-137">Varsayılan olarak, bileşenleri uygulama dizinine dağıtılır ve yalnızca içeren uygulamaya görülebilir.</span><span class="sxs-lookup"><span data-stu-id="c7012-137">By default, components are deployed to the application directory and are visible only to the containing application.</span></span>  
  
-   <span data-ttu-id="c7012-138">Kod paylaşımını denetlenir.</span><span class="sxs-lookup"><span data-stu-id="c7012-138">Controlled code sharing.</span></span>  
  
     <span data-ttu-id="c7012-139">Kod paylaşımını açıkça kod varsayılan davranışı olan yerine paylaşmak için kullanılabilir olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c7012-139">Code sharing requires you to explicitly make code available for sharing instead of being the default behavior.</span></span>  
  
-   <span data-ttu-id="c7012-140">Yan yana sürüm oluşturma.</span><span class="sxs-lookup"><span data-stu-id="c7012-140">Side-by-side versioning.</span></span>  
  
     <span data-ttu-id="c7012-141">Bir bileşen ya da uygulama birden çok sürümünü bir arada var olabilen kullanmak için hangi sürümlerin seçebilirsiniz ve ortak dil çalışma zamanı sürüm ilkesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="c7012-141">Multiple versions of a component or application can coexist, you can choose which versions to use, and the common language runtime enforces versioning policy.</span></span>  
  
-   <span data-ttu-id="c7012-142">XCOPY dağıtım ve çoğaltma.</span><span class="sxs-lookup"><span data-stu-id="c7012-142">XCOPY deployment and replication.</span></span>  
  
     <span data-ttu-id="c7012-143">Şirket içinde açıklanan ve kendi başına bileşenler ve uygulamalar, kayıt defteri girdileri veya bağımlılıkları dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="c7012-143">Self-described and self-contained components and applications can be deployed without registry entries or dependencies.</span></span>  
  
-   <span data-ttu-id="c7012-144">Üzerinde halindeyken güncelleştirmeler.</span><span class="sxs-lookup"><span data-stu-id="c7012-144">On-the-fly updates.</span></span>  
  
     <span data-ttu-id="c7012-145">Yöneticiler, ASP.NET gibi bir ana bilgisayar programı DLL'leri, uzak bilgisayarlarda bile güncelleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7012-145">Administrators can use hosts, such as ASP.NET, to update program DLLs, even on remote computers.</span></span>  
  
-   <span data-ttu-id="c7012-146">Windows Installer ile tümleştirme.</span><span class="sxs-lookup"><span data-stu-id="c7012-146">Integration with the Windows Installer.</span></span>  
  
     <span data-ttu-id="c7012-147">Reklam, yayımlama, onarım ve isteğe bağlı yükleme uygulamanızı dağıtırken tüm kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c7012-147">Advertisement, publishing, repair, and install-on-demand are all available when deploying your application.</span></span>  
  
-   <span data-ttu-id="c7012-148">Kurumsal Dağıtım.</span><span class="sxs-lookup"><span data-stu-id="c7012-148">Enterprise deployment.</span></span>  
  
     <span data-ttu-id="c7012-149">Bu özellik, kolay yazılım dağıtımı, Active Directory kullanma dahil olmak üzere sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7012-149">This feature provides easy software distribution, including using Active Directory.</span></span>  
  
-   <span data-ttu-id="c7012-150">İndirme ve önbelleğe alma.</span><span class="sxs-lookup"><span data-stu-id="c7012-150">Downloading and caching.</span></span>  
  
     <span data-ttu-id="c7012-151">Artımlı indirme daha küçük indirmeler tutun ve bileşenleri yalnızca low Impact dağıtım için uygulama tarafından kullanılmak üzere ayrılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="c7012-151">Incremental downloads keep downloads smaller, and components can be isolated for use only by the application for low-impact deployment.</span></span>  
  
-   <span data-ttu-id="c7012-152">Kısmen güvenilen kod.</span><span class="sxs-lookup"><span data-stu-id="c7012-152">Partially trusted code.</span></span>  
  
     <span data-ttu-id="c7012-153">Kimlik kodu kullanıcı yerine temel alır ve hiçbir sertifika iletişim kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="c7012-153">Identity is based on the code instead of the user, and no certificate dialog boxes appear.</span></span>  
  
## <a name="packaging-and-distributing-net-framework-applications"></a><span data-ttu-id="c7012-154">Paketleme ve .NET Framework uygulamalarını dağıtma</span><span class="sxs-lookup"><span data-stu-id="c7012-154">Packaging and Distributing .NET Framework Applications</span></span>  
 <span data-ttu-id="c7012-155">Bazı paketleme ve dağıtım bilgileri için .NET Framework belgelerinin diğer bölümlerinde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c7012-155">Some of the packaging and deployment information for the .NET Framework is described in other sections of the documentation.</span></span> <span data-ttu-id="c7012-156">Bu bölümler adlı kendiliğinden açıklayıcı birimleri hakkında bilgi sağlamak [derlemeleri](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md), hiçbir kayıt defteri girdilerini gerektir [tanımlayıcı adlı derlemeler](../../../docs/framework/app-domains/strong-named-assemblies.md), adının benzersiz olmasını sağlamak ve ad engelleme yanıltma, ve [derleme sürümlendirme](../../../docs/framework/app-domains/assembly-versioning.md), hangi adresleri birçok DLL çakışmaları ile ilgili sorunlar.</span><span class="sxs-lookup"><span data-stu-id="c7012-156">Those sections provide information about the self-describing units called [assemblies](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md), which require no registry entries, [strong-named assemblies](../../../docs/framework/app-domains/strong-named-assemblies.md), which ensure name uniqueness and prevent name spoofing, and [assembly versioning](../../../docs/framework/app-domains/assembly-versioning.md), which addresses many of the problems associated with DLL conflicts.</span></span> <span data-ttu-id="c7012-157">Aşağıdaki bölümlerde, paketleme ve .NET Framework uygulamalarını dağıtmak hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c7012-157">The following sections provide information about packaging and distributing .NET Framework applications.</span></span>  
  
### <a name="packaging"></a><span data-ttu-id="c7012-158">Paketleme</span><span class="sxs-lookup"><span data-stu-id="c7012-158">Packaging</span></span>  
 <span data-ttu-id="c7012-159">.NET Framework uygulama paketleme için aşağıdaki seçenekleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="c7012-159">The .NET Framework provides the following options for packaging applications:</span></span>  
  
-   <span data-ttu-id="c7012-160">Tek bir derleme veya derlemeler koleksiyonu olarak.</span><span class="sxs-lookup"><span data-stu-id="c7012-160">As a single assembly or as a collection of assemblies.</span></span>  
  
     <span data-ttu-id="c7012-161">Oluşturuldukları gibi bu seçenek, sadece .dll veya .exe dosyaları kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7012-161">With this option, you simply use the .dll or .exe files as they were built.</span></span>  
  
-   <span data-ttu-id="c7012-162">Dolap (CAB) dosyaları olarak.</span><span class="sxs-lookup"><span data-stu-id="c7012-162">As cabinet (CAB) files.</span></span>  
  
     <span data-ttu-id="c7012-163">Bu seçenek belirtilmişse, dağıtım yapmak veya daha az zaman alan indirmek için bir .cab dosyasına dosyaları sıkıştırın.</span><span class="sxs-lookup"><span data-stu-id="c7012-163">With this option, you compress files into .cab files to make distribution or download less time consuming.</span></span>  
  
-   <span data-ttu-id="c7012-164">Bir Windows Installer paketi olarak veya diğer yükleyici biçimleri.</span><span class="sxs-lookup"><span data-stu-id="c7012-164">As a Windows Installer package or in other installer formats.</span></span>  
  
     <span data-ttu-id="c7012-165">Bu seçenek, .msi dosyaları kullanmak için Windows Installer ile oluşturabilir veya diğer bir yükleyici ile kullanmak için uygulama paketi.</span><span class="sxs-lookup"><span data-stu-id="c7012-165">With this option, you create .msi files for use with the Windows Installer, or you package your application for use with some other installer.</span></span>  
  
### <a name="distribution"></a><span data-ttu-id="c7012-166">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="c7012-166">Distribution</span></span>  
 <span data-ttu-id="c7012-167">.NET Framework uygulamalarını dağıtmak için aşağıdaki seçenekleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="c7012-167">The .NET Framework provides the following options for distributing applications:</span></span>  
  
-   <span data-ttu-id="c7012-168">XCOPY veya FTP kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7012-168">Use XCOPY or FTP.</span></span>  
  
     <span data-ttu-id="c7012-169">Ortak dil çalışma zamanı uygulamaları kendiliğinden açıklayıcı ve kayıt defteri girdisi gerekli olduğundan uygulamaya uygun bir dizine kopyalamak XCOPY veya FTP kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7012-169">Because common language runtime applications are self-describing and require no registry entries, you can use XCOPY or FTP to simply copy the application to an appropriate directory.</span></span> <span data-ttu-id="c7012-170">Uygulama bu dizinden çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7012-170">The application can then be run from that directory.</span></span>  
  
-   <span data-ttu-id="c7012-171">Kod indirmeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7012-171">Use code download.</span></span>  
  
     <span data-ttu-id="c7012-172">Uygulamanız Internet üzerinden veya kurumsal bir intranet üzerinden dağıtıyorsanız, yalnızca kod bir bilgisayara indirebilir ve var. uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c7012-172">If you are distributing your application over the Internet or through a corporate intranet, you can simply download the code to a computer and run the application there.</span></span>  
  
-   <span data-ttu-id="c7012-173">Windows Installer 2.0 gibi bir yükleyici programı kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7012-173">Use an installer program such as Windows Installer 2.0.</span></span>  
  
     <span data-ttu-id="c7012-174">Windows Installer 2.0 yükleyin, onarın veya .NET Framework derlemeleri genel derleme önbelleğini ve özel dizinleri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="c7012-174">Windows Installer 2.0 can install, repair, or remove .NET Framework assemblies in the global assembly cache and in private directories.</span></span>  
  
### <a name="installation-location"></a><span data-ttu-id="c7012-175">Yükleme Konumu</span><span class="sxs-lookup"><span data-stu-id="c7012-175">Installation Location</span></span>  
 <span data-ttu-id="c7012-176">Çalışma zamanı tarafından bulunabilir bu nedenle, uygulamanızın derlemeleri dağıtılacağı yeri belirlemek için bkz: [çalışma zamanı derlemeleri nasıl konumlandırır](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="c7012-176">To determine where to deploy your application's assemblies so they can be found by the runtime, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="c7012-177">Uygulama dağıtımı güvenlik konuları da etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="c7012-177">Security considerations can also affect how you deploy your application.</span></span> <span data-ttu-id="c7012-178">Kodun bulunduğu yere göre yönetilen kod için güvenlik izinleri verilir.</span><span class="sxs-lookup"><span data-stu-id="c7012-178">Security permissions are granted to managed code according to where the code is located.</span></span> <span data-ttu-id="c7012-179">Bir uygulama veya bileşenin nereden sınırları Internet gibi çok az güven aldığı bir konuma dağıtma ne uygulamanın veya bileşenin yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7012-179">Deploying an application or component to a location where it receives little trust, such as the Internet, limits what the application or component can do.</span></span> <span data-ttu-id="c7012-180">Dağıtım ve güvenlik konuları hakkında daha fazla bilgi için bkz. [kod erişimi güvenliği Temelleri](../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="c7012-180">For more information about deployment and security considerations, see [Code Access Security Basics](../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="c7012-181">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="c7012-181">Related Topics</span></span>  
  
|<span data-ttu-id="c7012-182">Başlık</span><span class="sxs-lookup"><span data-stu-id="c7012-182">Title</span></span>|<span data-ttu-id="c7012-183">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7012-183">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="c7012-184">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="c7012-184">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|<span data-ttu-id="c7012-185">Ortak dil çalışma zamanının hangi derleme bağlama isteğini yerine getirmek için kullanılacak etiketleneceğini nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="c7012-185">Describes how the common language runtime determines which assembly to use to fulfill a binding request.</span></span>|  
|[<span data-ttu-id="c7012-186">Bütünleştirilmiş Kod Yükleme için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c7012-186">Best Practices for Assembly Loading</span></span>](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)|<span data-ttu-id="c7012-187">Yol açabilir türü kimliği sorunları önlemek için yollar ele alınmaktadır <xref:System.InvalidCastException>, <xref:System.MissingMethodException>ve diğer hataları.</span><span class="sxs-lookup"><span data-stu-id="c7012-187">Discusses ways to avoid problems of type identity that can lead to <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, and other errors.</span></span>|  
|[<span data-ttu-id="c7012-188">.NET Framework 4.5 Yüklemeleri Sırasında Sistem Yeniden Başlatmalarını Azaltma</span><span class="sxs-lookup"><span data-stu-id="c7012-188">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](../../../docs/framework/deployment/reducing-system-restarts.md)|<span data-ttu-id="c7012-189">Yeniden başlatma Yöneticisi önleyen mümkün olduğunda yeniden başlatır ve .NET Framework yükleme uygulamaları bu Avantajdan nasıl alabilir açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c7012-189">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>|  
|[<span data-ttu-id="c7012-190">Yöneticiler için Dağıtım Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c7012-190">Deployment Guide for Administrators</span></span>](../../../docs/framework/deployment/guide-for-administrators.md)|<span data-ttu-id="c7012-191">Nasıl bir Sistem Yöneticisi .NET Framework ve sistem bağımlılıklarını bir ağ üzerinden System Center Configuration Manager (SCCM) kullanarak dağıtılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c7012-191">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using System Center Configuration Manager (SCCM).</span></span>|  
|[<span data-ttu-id="c7012-192">Geliştiriciler için Dağıtım Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c7012-192">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)|<span data-ttu-id="c7012-193">Geliştiriciler uygulamalarını ile kullanıcıların bilgisayarlarına .NET Framework nasıl yükleyebilirsiniz açıklar.</span><span class="sxs-lookup"><span data-stu-id="c7012-193">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>|  
|[<span data-ttu-id="c7012-194">Uygulamaları, Hizmetleri ve Bileşenleri Dağıtma</span><span class="sxs-lookup"><span data-stu-id="c7012-194">Deploying Applications, Services, and Components</span></span>](/visualstudio/deployment/deploying-applications-services-and-components)|<span data-ttu-id="c7012-195">ClickOnce ve Windows Installer teknolojilerini kullanarak uygulama yayımlama yönergeleri de dahil olmak üzere Visual Studio dağıtım seçenekleri ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c7012-195">Discusses deployment options in Visual Studio, including instructions for publishing an application using the ClickOnce and Windows Installer technologies.</span></span>| 
|[<span data-ttu-id="c7012-196">ClickOnce Uygulamalarını Yayımlama</span><span class="sxs-lookup"><span data-stu-id="c7012-196">Publishing ClickOnce Applications</span></span>](/visualstudio/deployment/publishing-clickonce-applications)|<span data-ttu-id="c7012-197">Bir Windows Forms uygulaması'nı paketlemek ve ağdaki istemci bilgisayarları ile ClickOnce dağıtma işlemini açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="c7012-197">Describes how to package a Windows Forms application and deploy it with ClickOnce to client computers on a network.</span></span>|  
|[<span data-ttu-id="c7012-198">Kaynakları Paketleme ve Dağıtma</span><span class="sxs-lookup"><span data-stu-id="c7012-198">Packaging and Deploying Resources</span></span>](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)|<span data-ttu-id="c7012-199">Paketleme ve dağıtma kaynakları için kullandığı .NET Framework merkez ve ışınsal modelini açıklar; Kaynak adlandırma kuralları, geri dönüş işlemi ve paketleme seçenekleri ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c7012-199">Describes the hub and spoke model that the .NET Framework uses to package and deploy resources; covers resource naming conventions, fallback process, and packaging alternatives.</span></span>|  
|[<span data-ttu-id="c7012-200">Birlikte Çalışma Uygulamasını Dağıtma</span><span class="sxs-lookup"><span data-stu-id="c7012-200">Deploying an Interop Application</span></span>](../../../docs/framework/interop/deploying-an-interop-application.md)|<span data-ttu-id="c7012-201">Gönderin ve genellikle bir .NET Framework istemci bütünleştirilmiş kodu ayrı bir COM tür kitaplıkları temsil eden bir veya daha fazla birlikte çalışma derlemelerini içeren, birlikte çalışma uygulamaları ve bir veya daha fazla kayıtlı COM bileşenlerini yüklemek açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c7012-201">Explains how to ship and install interop applications, which typically include a .NET Framework client assembly, one or more interop assemblies representing distinct COM type libraries, and one or more registered COM components.</span></span>|  
|[<span data-ttu-id="c7012-202">Nasıl Yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma</span><span class="sxs-lookup"><span data-stu-id="c7012-202">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)|<span data-ttu-id="c7012-203">Sessizce başlatmak ve kendi görünüm Kurulum sürecinizin gösterirken .NET Framework Kurulum sürecini izlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="c7012-203">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c7012-204">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c7012-204">See Also</span></span>  
- [<span data-ttu-id="c7012-205">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c7012-205">Development Guide</span></span>](../../../docs/framework/development-guide.md)
