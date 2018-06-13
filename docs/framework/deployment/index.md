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
ms.openlocfilehash: 2686d0db966192606656167d6e505f34ded333f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396535"
---
# <a name="deploying-the-net-framework-and-applications"></a><span data-ttu-id="4ec00-102">.NET Framework ve Uygulamaları Dağıtma</span><span class="sxs-lookup"><span data-stu-id="4ec00-102">Deploying the .NET Framework and Applications</span></span>
<span data-ttu-id="4ec00-103">Bu makale .NET Framework ile uygulamanızı dağıtımına başlamak yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="4ec00-103">This article helps you get started deploying the .NET Framework with your application.</span></span> <span data-ttu-id="4ec00-104">Bilgilerin çoğunu geliştiriciler, OEM'ler ve kuruluş yöneticileri için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4ec00-104">Most of the information is intended for developers, OEMs, and enterprise administrators.</span></span> <span data-ttu-id="4ec00-105">.NET Framework'ü bilgisayarlarında yüklemek istediğiniz kullanıcıları kimler [.NET Framework yükleme](~/docs/framework/install/index.md).</span><span class="sxs-lookup"><span data-stu-id="4ec00-105">Users who want to install the .NET Framework on their computers should read [Installing the .NET Framework](~/docs/framework/install/index.md).</span></span>  
  
## <a name="key-deployment-resources"></a><span data-ttu-id="4ec00-106">Anahtar Dağıtım Kaynakları</span><span class="sxs-lookup"><span data-stu-id="4ec00-106">Key Deployment Resources</span></span>  
 <span data-ttu-id="4ec00-107">Dağıtma ve .NET Framework hizmet hakkında ayrıntılı bilgi için MSDN diğer konular için aşağıdaki bağlantıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ec00-107">Use the following links to other MSDN topics for specific information about deploying and servicing the .NET Framework.</span></span>  
  
 <span data-ttu-id="4ec00-108">**Kurulum ve dağıtım**</span><span class="sxs-lookup"><span data-stu-id="4ec00-108">**Setup and deployment**</span></span>  
  
-   <span data-ttu-id="4ec00-109">Genel yükleyici ve dağıtım bilgileri:</span><span class="sxs-lookup"><span data-stu-id="4ec00-109">General installer and deployment information:</span></span>  
  
    -   <span data-ttu-id="4ec00-110">Yükleyici seçenekleri:</span><span class="sxs-lookup"><span data-stu-id="4ec00-110">Installer options:</span></span>  
  
        -   [<span data-ttu-id="4ec00-111">Web yükleyicisi</span><span class="sxs-lookup"><span data-stu-id="4ec00-111">Web installer</span></span>](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)  
  
        -   [<span data-ttu-id="4ec00-112">Çevrimdışı yükleyici</span><span class="sxs-lookup"><span data-stu-id="4ec00-112">Offline installer</span></span>](~/docs/framework/install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)  
  
    -   <span data-ttu-id="4ec00-113">Yükleme modu:</span><span class="sxs-lookup"><span data-stu-id="4ec00-113">Installation modes:</span></span>  
  
        -   [<span data-ttu-id="4ec00-114">Sessiz yükleme</span><span class="sxs-lookup"><span data-stu-id="4ec00-114">Silent installation</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_custom)  
  
        -   [<span data-ttu-id="4ec00-115">Bir kullanıcı Arabirimi görüntüleme</span><span class="sxs-lookup"><span data-stu-id="4ec00-115">Displaying a UI</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_default)  
  
    -   [<span data-ttu-id="4ec00-116">Sistem .NET Framework 4.5 yüklemeleri sırasında yeniden başlatmalarını azaltma</span><span class="sxs-lookup"><span data-stu-id="4ec00-116">Reducing system restarts during .NET Framework 4.5 installations</span></span>](../../../docs/framework/deployment/reducing-system-restarts.md)  
  
    -   [<span data-ttu-id="4ec00-117">Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="4ec00-117">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](~/docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)  
  
-   <span data-ttu-id="4ec00-118">Bir istemci uygulaması ile .NET Framework (geliştiriciler için) dağıtma:</span><span class="sxs-lookup"><span data-stu-id="4ec00-118">Deploying the .NET Framework with a client application (for developers):</span></span>  
  
    -   <span data-ttu-id="4ec00-119">[InstallShield kullanarak](../../../docs/framework/deployment/deployment-guide-for-developers.md#installshield-deployment) Kurulum ve dağıtım projesindeki</span><span class="sxs-lookup"><span data-stu-id="4ec00-119">[Using InstallShield](../../../docs/framework/deployment/deployment-guide-for-developers.md#installshield-deployment) in a setup and deployment project</span></span>  
  
    -   [<span data-ttu-id="4ec00-120">Visual Studio ClickOnce uygulamasını kullanma</span><span class="sxs-lookup"><span data-stu-id="4ec00-120">Using a Visual Studio ClickOnce application</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#clickonce-deployment)  
  
    -   [<span data-ttu-id="4ec00-121">WiX yükleme paketi oluşturma</span><span class="sxs-lookup"><span data-stu-id="4ec00-121">Creating a WiX installation package</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#wix)  
  
    -   [<span data-ttu-id="4ec00-122">Özel bir yükleyici kullanarak</span><span class="sxs-lookup"><span data-stu-id="4ec00-122">Using a custom installer</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining)  
  
    -   <span data-ttu-id="4ec00-123">[Ek bilgi](../../../docs/framework/deployment/deployment-guide-for-developers.md) geliştiricileri için</span><span class="sxs-lookup"><span data-stu-id="4ec00-123">[Additional information](../../../docs/framework/deployment/deployment-guide-for-developers.md) for developers</span></span>  
  
-   <span data-ttu-id="4ec00-124">.NET Framework (OEM'ler ve Yöneticiler) dağıtma:</span><span class="sxs-lookup"><span data-stu-id="4ec00-124">Deploying the .NET Framework (for OEMs and administrators):</span></span>  
  
    -   [<span data-ttu-id="4ec00-125">Windows değerlendirme ve Dağıtım Seti (ADK)</span><span class="sxs-lookup"><span data-stu-id="4ec00-125">Windows Assessment and Deployment Kit (ADK)</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=254976)  
  
    -   [<span data-ttu-id="4ec00-126">Yönetici Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4ec00-126">Administrator's guide</span></span>](../../../docs/framework/deployment/guide-for-administrators.md)  
  
 <span data-ttu-id="4ec00-127">**Bakım**</span><span class="sxs-lookup"><span data-stu-id="4ec00-127">**Servicing**</span></span>  
  
-   <span data-ttu-id="4ec00-128">Genel bilgi için bkz: [.NET Framework blogu](http://go.microsoft.com/fwlink/p/?LinkId=254977)</span><span class="sxs-lookup"><span data-stu-id="4ec00-128">For general information, see the [.NET Framework blog](http://go.microsoft.com/fwlink/p/?LinkId=254977)</span></span>  
  
-   [<span data-ttu-id="4ec00-129">Sürümleri algılama</span><span class="sxs-lookup"><span data-stu-id="4ec00-129">Detecting versions</span></span>](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)  
  
-   [<span data-ttu-id="4ec00-130">Hizmet paketlerini ve güncelleştirmelerini algılama</span><span class="sxs-lookup"><span data-stu-id="4ec00-130">Detecting service packs and updates</span></span>](../../../docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
  
## <a name="features-that-simplify-deployment"></a><span data-ttu-id="4ec00-131">Dağıtım basitleştiren özellikleri</span><span class="sxs-lookup"><span data-stu-id="4ec00-131">Features That Simplify Deployment</span></span>  
 <span data-ttu-id="4ec00-132">.NET Framework uygulamalarınızı dağıtma kolaylaştırmak temel özelliklerini sağlar:</span><span class="sxs-lookup"><span data-stu-id="4ec00-132">The .NET Framework provides a number of basic features that make it easier to deploy your applications:</span></span>  
  
-   <span data-ttu-id="4ec00-133">Hayır etkisi uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="4ec00-133">No-impact applications.</span></span>  
  
     <span data-ttu-id="4ec00-134">Bu özellik, uygulama yalıtımı sağlar ve DLL çakışmaları ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4ec00-134">This feature provides application isolation and eliminates DLL conflicts.</span></span> <span data-ttu-id="4ec00-135">Varsayılan olarak, diğer uygulamaların bileşenleri etkilemez.</span><span class="sxs-lookup"><span data-stu-id="4ec00-135">By default, components do not affect other applications.</span></span>  
  
-   <span data-ttu-id="4ec00-136">Özel bileşenler varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="4ec00-136">Private components by default.</span></span>  
  
     <span data-ttu-id="4ec00-137">Varsayılan olarak, bileşenleri uygulama dizinine dağıtılır ve yalnızca içeren uygulamaya görülebilir.</span><span class="sxs-lookup"><span data-stu-id="4ec00-137">By default, components are deployed to the application directory and are visible only to the containing application.</span></span>  
  
-   <span data-ttu-id="4ec00-138">Kod paylaşımını denetlenir.</span><span class="sxs-lookup"><span data-stu-id="4ec00-138">Controlled code sharing.</span></span>  
  
     <span data-ttu-id="4ec00-139">Kod paylaşımını açıkça kod varsayılan davranışı yerine paylaşımı için kullanılabilir olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4ec00-139">Code sharing requires you to explicitly make code available for sharing instead of being the default behavior.</span></span>  
  
-   <span data-ttu-id="4ec00-140">Yan yana sürüm oluşturma.</span><span class="sxs-lookup"><span data-stu-id="4ec00-140">Side-by-side versioning.</span></span>  
  
     <span data-ttu-id="4ec00-141">Bir bileşeni ya da uygulama birden fazla sürümünü bir arada var olabilen, kullanmak için hangi sürümlerinin seçebilirsiniz ve ortak dil çalışma zamanı sürüm ilkesini zorlar.</span><span class="sxs-lookup"><span data-stu-id="4ec00-141">Multiple versions of a component or application can coexist, you can choose which versions to use, and the common language runtime enforces versioning policy.</span></span>  
  
-   <span data-ttu-id="4ec00-142">XCOPY dağıtımı ve çoğaltma.</span><span class="sxs-lookup"><span data-stu-id="4ec00-142">XCOPY deployment and replication.</span></span>  
  
     <span data-ttu-id="4ec00-143">Kendi kendine açıklanan ve müstakil bileşenleri ve uygulamaları kayıt defteri girdileri veya bağımlılıkları dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="4ec00-143">Self-described and self-contained components and applications can be deployed without registry entries or dependencies.</span></span>  
  
-   <span data-ttu-id="4ec00-144">Üzerinde-çalışma sırasında güncelleştirmeler.</span><span class="sxs-lookup"><span data-stu-id="4ec00-144">On-the-fly updates.</span></span>  
  
     <span data-ttu-id="4ec00-145">Yöneticiler gibi ASP.NET, ana bilgisayar programı DLL'ler, uzak bilgisayarlarda bile güncelleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ec00-145">Administrators can use hosts, such as ASP.NET, to update program DLLs, even on remote computers.</span></span>  
  
-   <span data-ttu-id="4ec00-146">Windows Installer ile tümleştirme.</span><span class="sxs-lookup"><span data-stu-id="4ec00-146">Integration with the Windows Installer.</span></span>  
  
     <span data-ttu-id="4ec00-147">Reklam, yayımlama, onarma ve isteğe bağlı yükleme uygulamanızı dağıtırken tüm kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4ec00-147">Advertisement, publishing, repair, and install-on-demand are all available when deploying your application.</span></span>  
  
-   <span data-ttu-id="4ec00-148">Kurumsal Dağıtım.</span><span class="sxs-lookup"><span data-stu-id="4ec00-148">Enterprise deployment.</span></span>  
  
     <span data-ttu-id="4ec00-149">Bu özellik, kolay yazılım dağıtımı, Active Directory kullanımı dahil olmak üzere sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ec00-149">This feature provides easy software distribution, including using Active Directory.</span></span>  
  
-   <span data-ttu-id="4ec00-150">İndirme ve önbelleğe alma.</span><span class="sxs-lookup"><span data-stu-id="4ec00-150">Downloading and caching.</span></span>  
  
     <span data-ttu-id="4ec00-151">Artımlı yüklemeleri yüklemeleri daha küçük olmasını ve bileşenleri yalnızca low Impact dağıtımı için uygulama tarafından kullanılmak üzere ayrılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="4ec00-151">Incremental downloads keep downloads smaller, and components can be isolated for use only by the application for low-impact deployment.</span></span>  
  
-   <span data-ttu-id="4ec00-152">Kısmen güvenilen kod.</span><span class="sxs-lookup"><span data-stu-id="4ec00-152">Partially trusted code.</span></span>  
  
     <span data-ttu-id="4ec00-153">Kimlik kullanıcı yerine kodu temel alır ve hiç sertifika iletişim kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="4ec00-153">Identity is based on the code instead of the user, and no certificate dialog boxes appear.</span></span>  
  
## <a name="packaging-and-distributing-net-framework-applications"></a><span data-ttu-id="4ec00-154">Paketleme ve .NET Framework uygulamalarını dağıtma</span><span class="sxs-lookup"><span data-stu-id="4ec00-154">Packaging and Distributing .NET Framework Applications</span></span>  
 <span data-ttu-id="4ec00-155">Bazı paketleme ve dağıtım bilgileri için .NET Framework belgenin diğer bölümlerinde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4ec00-155">Some of the packaging and deployment information for the .NET Framework is described in other sections of the documentation.</span></span> <span data-ttu-id="4ec00-156">Bu bölümler olarak adlandırılan kendiliğinden açıklayıcı birimler hakkında bilgi sağlar [derlemeleri](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md), hiçbir kayıt defteri girdileri gerektiren [tanımlayıcı adlı derlemeler](../../../docs/framework/app-domains/strong-named-assemblies.md), hangi adının benzersiz olduğundan emin olup adı önlemek kimlik sahtekarlığı, ve [derleme sürümü oluşturma](../../../docs/framework/app-domains/assembly-versioning.md), hangi adresleri birçok DLL çakışmaları ile ilgili sorunları.</span><span class="sxs-lookup"><span data-stu-id="4ec00-156">Those sections provide information about the self-describing units called [assemblies](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md), which require no registry entries, [strong-named assemblies](../../../docs/framework/app-domains/strong-named-assemblies.md), which ensure name uniqueness and prevent name spoofing, and [assembly versioning](../../../docs/framework/app-domains/assembly-versioning.md), which addresses many of the problems associated with DLL conflicts.</span></span> <span data-ttu-id="4ec00-157">Aşağıdaki bölümlerde paketleme ve .NET Framework uygulamaları dağıtma hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ec00-157">The following sections provide information about packaging and distributing .NET Framework applications.</span></span>  
  
### <a name="packaging"></a><span data-ttu-id="4ec00-158">Paketleme</span><span class="sxs-lookup"><span data-stu-id="4ec00-158">Packaging</span></span>  
 <span data-ttu-id="4ec00-159">.NET Framework uygulama paketleme için aşağıdaki seçenekleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="4ec00-159">The .NET Framework provides the following options for packaging applications:</span></span>  
  
-   <span data-ttu-id="4ec00-160">Tek bir derleme veya derlemelerin bir koleksiyon olarak.</span><span class="sxs-lookup"><span data-stu-id="4ec00-160">As a single assembly or as a collection of assemblies.</span></span>  
  
     <span data-ttu-id="4ec00-161">Bunlar oluşturulan gibi bu seçenekle, yalnızca .dll veya .exe dosyaları kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ec00-161">With this option, you simply use the .dll or .exe files as they were built.</span></span>  
  
-   <span data-ttu-id="4ec00-162">Dolap (CAB) dosyası.</span><span class="sxs-lookup"><span data-stu-id="4ec00-162">As cabinet (CAB) files.</span></span>  
  
     <span data-ttu-id="4ec00-163">Bu seçenek ile .cab dosyalarına dağıtım yapmak veya daha az zaman alan indirmek için dosyaları sıkıştırın.</span><span class="sxs-lookup"><span data-stu-id="4ec00-163">With this option, you compress files into .cab files to make distribution or download less time consuming.</span></span>  
  
-   <span data-ttu-id="4ec00-164">Bir Windows Installer paketi olarak veya diğer yükleyici biçimleri.</span><span class="sxs-lookup"><span data-stu-id="4ec00-164">As a Windows Installer package or in other installer formats.</span></span>  
  
     <span data-ttu-id="4ec00-165">Bu seçeneği, Windows Installer ile kullanmak için .msi dosyaları oluşturun veya başka bir yükleyici ile kullanmak için uygulama paketini.</span><span class="sxs-lookup"><span data-stu-id="4ec00-165">With this option, you create .msi files for use with the Windows Installer, or you package your application for use with some other installer.</span></span>  
  
### <a name="distribution"></a><span data-ttu-id="4ec00-166">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="4ec00-166">Distribution</span></span>  
 <span data-ttu-id="4ec00-167">.NET Framework uygulamalarını dağıtmak için aşağıdaki seçenekleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="4ec00-167">The .NET Framework provides the following options for distributing applications:</span></span>  
  
-   <span data-ttu-id="4ec00-168">XCOPY veya FTP kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ec00-168">Use XCOPY or FTP.</span></span>  
  
     <span data-ttu-id="4ec00-169">Ortak dil çalışma zamanı uygulamaları kendiliğinden açıklayıcı ve kayıt defteri girdisi iste olduğundan yalnızca uygun bir dizini uygulamaya kopyalamak için XCOPY veya FTP kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ec00-169">Because common language runtime applications are self-describing and require no registry entries, you can use XCOPY or FTP to simply copy the application to an appropriate directory.</span></span> <span data-ttu-id="4ec00-170">Uygulama, diğer dizinden çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ec00-170">The application can then be run from that directory.</span></span>  
  
-   <span data-ttu-id="4ec00-171">Kodu indirme kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ec00-171">Use code download.</span></span>  
  
     <span data-ttu-id="4ec00-172">Internet üzerinden veya Kurumsal intranet üzerinden uygulamanızı dağıtıyorsanız, yalnızca bir bilgisayara kodu indirin ve uygulama var. çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4ec00-172">If you are distributing your application over the Internet or through a corporate intranet, you can simply download the code to a computer and run the application there.</span></span>  
  
-   <span data-ttu-id="4ec00-173">Windows Installer 2.0 gibi bir yükleyici programı kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ec00-173">Use an installer program such as Windows Installer 2.0.</span></span>  
  
     <span data-ttu-id="4ec00-174">Windows Installer 2.0 yükleyin, onarın veya .NET Framework derlemeleri genel derleme önbelleği ve özel dizinleri kaldırın.</span><span class="sxs-lookup"><span data-stu-id="4ec00-174">Windows Installer 2.0 can install, repair, or remove .NET Framework assemblies in the global assembly cache and in private directories.</span></span>  
  
### <a name="installation-location"></a><span data-ttu-id="4ec00-175">Yükleme Konumu</span><span class="sxs-lookup"><span data-stu-id="4ec00-175">Installation Location</span></span>  
 <span data-ttu-id="4ec00-176">Çalışma zamanı tarafından bulunan şekilde uygulamanızın derlemeleri dağıtma nereye belirlemek için bkz: [nasıl çalışma zamanı bulur derlemeleri](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="4ec00-176">To determine where to deploy your application's assemblies so they can be found by the runtime, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="4ec00-177">Güvenlik konuları da uygulamanızı dağıtmak nasıl etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="4ec00-177">Security considerations can also affect how you deploy your application.</span></span> <span data-ttu-id="4ec00-178">Kod bulunduğu göre yönetilen kod için güvenlik izinleri verilir.</span><span class="sxs-lookup"><span data-stu-id="4ec00-178">Security permissions are granted to managed code according to where the code is located.</span></span> <span data-ttu-id="4ec00-179">Bir uygulama veya bileşenin burada sınırları Internet gibi az güven aldığı bir konuma dağıtma hangi uygulamanın veya bileşenin yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ec00-179">Deploying an application or component to a location where it receives little trust, such as the Internet, limits what the application or component can do.</span></span> <span data-ttu-id="4ec00-180">Dağıtım ve güvenlik konuları hakkında daha fazla bilgi için bkz: [kod erişim güvenliği Temelleri](../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="4ec00-180">For more information about deployment and security considerations, see [Code Access Security Basics](../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="4ec00-181">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="4ec00-181">Related Topics</span></span>  
  
|<span data-ttu-id="4ec00-182">Başlık</span><span class="sxs-lookup"><span data-stu-id="4ec00-182">Title</span></span>|<span data-ttu-id="4ec00-183">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ec00-183">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="4ec00-184">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="4ec00-184">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|<span data-ttu-id="4ec00-185">Hangi derleme bağlama isteği yerine getirmek için kullanılacak ortak dil çalışma zamanı nasıl belirlediğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="4ec00-185">Describes how the common language runtime determines which assembly to use to fulfill a binding request.</span></span>|  
|[<span data-ttu-id="4ec00-186">Bütünleştirilmiş Kod Yükleme için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4ec00-186">Best Practices for Assembly Loading</span></span>](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)|<span data-ttu-id="4ec00-187">Yol açabilir türü kimliğinin sorunları önlemek için yollarını tartışmaktadır <xref:System.InvalidCastException>, <xref:System.MissingMethodException>ve diğer hataları.</span><span class="sxs-lookup"><span data-stu-id="4ec00-187">Discusses ways to avoid problems of type identity that can lead to <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, and other errors.</span></span>|  
|[<span data-ttu-id="4ec00-188">.NET Framework 4.5 Yüklemeleri Sırasında Sistem Yeniden Başlatmalarını Azaltma</span><span class="sxs-lookup"><span data-stu-id="4ec00-188">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](../../../docs/framework/deployment/reducing-system-restarts.md)|<span data-ttu-id="4ec00-189">Yeniden başlatma Yöneticisi önleyen mümkün olduğunca yeniden başlatır ve nasıl .NET Framework'ü yüklemek uygulamalar, bu yararlanabilir açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4ec00-189">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>|  
|[<span data-ttu-id="4ec00-190">Yöneticiler için Dağıtım Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4ec00-190">Deployment Guide for Administrators</span></span>](../../../docs/framework/deployment/guide-for-administrators.md)|<span data-ttu-id="4ec00-191">Nasıl bir Sistem Yöneticisi .NET Framework ve sistem bağımlılıklarını bir ağ üzerinden System Center Configuration Manager (SCCM) kullanarak dağıtabilirsiniz açıklar.</span><span class="sxs-lookup"><span data-stu-id="4ec00-191">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using System Center Configuration Manager (SCCM).</span></span>|  
|[<span data-ttu-id="4ec00-192">Geliştiriciler için Dağıtım Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4ec00-192">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)|<span data-ttu-id="4ec00-193">Geliştiriciler kendi uygulamalarla bunların kullanıcıların bilgisayarlarına .NET Framework nasıl yükleyebileceğinizi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4ec00-193">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>|  
|[<span data-ttu-id="4ec00-194">Uygulamaları, Hizmetleri ve Bileşenleri Dağıtma</span><span class="sxs-lookup"><span data-stu-id="4ec00-194">Deploying Applications, Services, and Components</span></span>](/visualstudio/deployment/deploying-applications-services-and-components)|<span data-ttu-id="4ec00-195">ClickOnce ve Windows Installer teknolojileri kullanarak bir uygulamayı yayımlamak için yönergeler de dahil olmak üzere Visual Studio dağıtım seçenekleri ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4ec00-195">Discusses deployment options in Visual Studio, including instructions for publishing an application using the ClickOnce and Windows Installer technologies.</span></span>| 
|[<span data-ttu-id="4ec00-196">ClickOnce Uygulamalarını Yayımlama</span><span class="sxs-lookup"><span data-stu-id="4ec00-196">Publishing ClickOnce Applications</span></span>](/visualstudio/deployment/publishing-clickonce-applications)|<span data-ttu-id="4ec00-197">Bir Windows Forms uygulaması paketini ve ağdaki istemci bilgisayarlarını ClickOnce ile dağıtmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="4ec00-197">Describes how to package a Windows Forms application and deploy it with ClickOnce to client computers on a network.</span></span>|  
|[<span data-ttu-id="4ec00-198">Kaynakları Paketleme ve Dağıtma</span><span class="sxs-lookup"><span data-stu-id="4ec00-198">Packaging and Deploying Resources</span></span>](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)|<span data-ttu-id="4ec00-199">.NET Framework paketini ve kaynakları dağıtmak için kullandığı hub ve bağlı bileşen modeli açıklar; adlandırma kuralları, geri dönüş işlemi ve paketleme alternatifleri kaynak kapsar.</span><span class="sxs-lookup"><span data-stu-id="4ec00-199">Describes the hub and spoke model that the .NET Framework uses to package and deploy resources; covers resource naming conventions, fallback process, and packaging alternatives.</span></span>|  
|[<span data-ttu-id="4ec00-200">Birlikte Çalışma Uygulamasını Dağıtma</span><span class="sxs-lookup"><span data-stu-id="4ec00-200">Deploying an Interop Application</span></span>](../../../docs/framework/interop/deploying-an-interop-application.md)|<span data-ttu-id="4ec00-201">Sevk ve genellikle bir .NET Framework istemci derleme ayrı COM tür kitaplıklarının temsil eden bir veya daha fazla birlikte çalışma derlemeleri içerir, birlikte çalışma uygulamaları ve bir veya daha fazla kayıtlı COM bileşenleri yüklemek açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4ec00-201">Explains how to ship and install interop applications, which typically include a .NET Framework client assembly, one or more interop assemblies representing distinct COM type libraries, and one or more registered COM components.</span></span>|  
|[<span data-ttu-id="4ec00-202">Nasıl Yapılır: .NET Framework 4.5 Yükleyicisinden İlerleme Durumunu Alma</span><span class="sxs-lookup"><span data-stu-id="4ec00-202">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)|<span data-ttu-id="4ec00-203">Sessiz bir şekilde başlatın ve Kurulum ilerleme kendi görünüm gösterirken .NET Framework Kurulum işlemi izlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="4ec00-203">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4ec00-204">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4ec00-204">See Also</span></span>  
 [<span data-ttu-id="4ec00-205">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4ec00-205">Development Guide</span></span>](../../../docs/framework/development-guide.md)
