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
ms.openlocfilehash: 8d9448edab101ef11447b54e12c53abcb578646a
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971599"
---
# <a name="deploying-the-net-framework-and-applications"></a><span data-ttu-id="f379a-102">.NET Framework ve Uygulamaları Dağıtma</span><span class="sxs-lookup"><span data-stu-id="f379a-102">Deploying the .NET Framework and Applications</span></span>

<span data-ttu-id="f379a-103">Bu makale, .NET Framework uygulamanıza dağıtmaya başlamanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="f379a-103">This article helps you get started deploying the .NET Framework with your application.</span></span> <span data-ttu-id="f379a-104">Bilgilerin çoğu geliştiriciler, OEM 'Ler ve kuruluş yöneticileri için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f379a-104">Most of the information is intended for developers, OEMs, and enterprise administrators.</span></span> <span data-ttu-id="f379a-105">.NET Framework bilgisayarlarına yüklemek isteyen kullanıcılar [.NET Framework yüklemeyi](../install/index.md)okumalı.</span><span class="sxs-lookup"><span data-stu-id="f379a-105">Users who want to install the .NET Framework on their computers should read [Installing the .NET Framework](../install/index.md).</span></span>

## <a name="key-deployment-resources"></a><span data-ttu-id="f379a-106">Anahtar dağıtım kaynakları</span><span class="sxs-lookup"><span data-stu-id="f379a-106">Key Deployment Resources</span></span>

<span data-ttu-id="f379a-107">.NET Framework dağıtma ve bakım hakkında belirli bilgiler için diğer MSDN konularına yönelik aşağıdaki bağlantıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="f379a-107">Use the following links to other MSDN topics for specific information about deploying and servicing the .NET Framework.</span></span>

<span data-ttu-id="f379a-108">**Kurulum ve dağıtım**</span><span class="sxs-lookup"><span data-stu-id="f379a-108">**Setup and deployment**</span></span>

- <span data-ttu-id="f379a-109">Genel yükleyici ve dağıtım bilgileri:</span><span class="sxs-lookup"><span data-stu-id="f379a-109">General installer and deployment information:</span></span>

  - <span data-ttu-id="f379a-110">Yükleyici seçenekleri:</span><span class="sxs-lookup"><span data-stu-id="f379a-110">Installer options:</span></span>

    - [<span data-ttu-id="f379a-111">Web Yükleyicisi</span><span class="sxs-lookup"><span data-stu-id="f379a-111">Web installer</span></span>](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

    - [<span data-ttu-id="f379a-112">Çevrimdışı yükleyici</span><span class="sxs-lookup"><span data-stu-id="f379a-112">Offline installer</span></span>](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

  - <span data-ttu-id="f379a-113">Yükleme modları:</span><span class="sxs-lookup"><span data-stu-id="f379a-113">Installation modes:</span></span>

    - [<span data-ttu-id="f379a-114">Sessiz yükleme</span><span class="sxs-lookup"><span data-stu-id="f379a-114">Silent installation</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_custom)

    - [<span data-ttu-id="f379a-115">Kullanıcı arabirimini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="f379a-115">Displaying a UI</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_default)

  - [<span data-ttu-id="f379a-116">.NET Framework 4,5 yüklemeleri sırasında sistem yeniden başlatmaları azaltma</span><span class="sxs-lookup"><span data-stu-id="f379a-116">Reducing system restarts during .NET Framework 4.5 installations</span></span>](../../../docs/framework/deployment/reducing-system-restarts.md)

  - [<span data-ttu-id="f379a-117">Engellenen .NET Framework yükleme ve kaldırma sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="f379a-117">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](../install/troubleshoot-blocked-installations-and-uninstallations.md)

- <span data-ttu-id="f379a-118">.NET Framework bir istemci uygulamasıyla dağıtma (geliştiriciler için):</span><span class="sxs-lookup"><span data-stu-id="f379a-118">Deploying the .NET Framework with a client application (for developers):</span></span>

  - <span data-ttu-id="f379a-119">Kurulum ve dağıtım projesinde [InstallShield kullanma](../../../docs/framework/deployment/deployment-guide-for-developers.md#installshield-deployment)</span><span class="sxs-lookup"><span data-stu-id="f379a-119">[Using InstallShield](../../../docs/framework/deployment/deployment-guide-for-developers.md#installshield-deployment) in a setup and deployment project</span></span>

  - [<span data-ttu-id="f379a-120">Visual Studio ClickOnce uygulaması kullanma</span><span class="sxs-lookup"><span data-stu-id="f379a-120">Using a Visual Studio ClickOnce application</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#clickonce-deployment)

  - [<span data-ttu-id="f379a-121">WiX yükleme paketi oluşturma</span><span class="sxs-lookup"><span data-stu-id="f379a-121">Creating a WiX installation package</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#wix)

  - [<span data-ttu-id="f379a-122">Özel bir yükleyici kullanma</span><span class="sxs-lookup"><span data-stu-id="f379a-122">Using a custom installer</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining)

  - <span data-ttu-id="f379a-123">Geliştiriciler için [ek bilgiler](../../../docs/framework/deployment/deployment-guide-for-developers.md)</span><span class="sxs-lookup"><span data-stu-id="f379a-123">[Additional information](../../../docs/framework/deployment/deployment-guide-for-developers.md) for developers</span></span>

- <span data-ttu-id="f379a-124">.NET Framework dağıtma (OEM 'Ler ve yöneticiler için):</span><span class="sxs-lookup"><span data-stu-id="f379a-124">Deploying the .NET Framework (for OEMs and administrators):</span></span>

  - [<span data-ttu-id="f379a-125">Windows değerlendirme ve Dağıtım Seti (ADK)</span><span class="sxs-lookup"><span data-stu-id="f379a-125">Windows Assessment and Deployment Kit (ADK)</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=254976)

  - [<span data-ttu-id="f379a-126">Yönetici Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f379a-126">Administrator's guide</span></span>](../../../docs/framework/deployment/guide-for-administrators.md)

<span data-ttu-id="f379a-127">**Bakım**</span><span class="sxs-lookup"><span data-stu-id="f379a-127">**Servicing**</span></span>

- <span data-ttu-id="f379a-128">Genel bilgiler için [.NET Framework bloguna](https://go.microsoft.com/fwlink/p/?LinkId=254977) bakın</span><span class="sxs-lookup"><span data-stu-id="f379a-128">For general information, see the [.NET Framework blog](https://go.microsoft.com/fwlink/p/?LinkId=254977)</span></span>

- [<span data-ttu-id="f379a-129">Sürümler algılanıyor</span><span class="sxs-lookup"><span data-stu-id="f379a-129">Detecting versions</span></span>](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)

- [<span data-ttu-id="f379a-130">Hizmet paketleri ve güncelleştirmeler algılanıyor</span><span class="sxs-lookup"><span data-stu-id="f379a-130">Detecting service packs and updates</span></span>](../../../docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)

## <a name="features-that-simplify-deployment"></a><span data-ttu-id="f379a-131">Dağıtımı basitleştiren Özellikler</span><span class="sxs-lookup"><span data-stu-id="f379a-131">Features That Simplify Deployment</span></span>

<span data-ttu-id="f379a-132">.NET Framework, uygulamalarınızı dağıtmayı kolaylaştıran bir dizi temel özellik sağlar:</span><span class="sxs-lookup"><span data-stu-id="f379a-132">The .NET Framework provides a number of basic features that make it easier to deploy your applications:</span></span>

- <span data-ttu-id="f379a-133">Etkili olmayan uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="f379a-133">No-impact applications.</span></span>

     <span data-ttu-id="f379a-134">Bu özellik uygulama yalıtımı sağlar ve DLL çakışmalarını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f379a-134">This feature provides application isolation and eliminates DLL conflicts.</span></span> <span data-ttu-id="f379a-135">Varsayılan olarak, bileşenler diğer uygulamaları etkilemez.</span><span class="sxs-lookup"><span data-stu-id="f379a-135">By default, components do not affect other applications.</span></span>

- <span data-ttu-id="f379a-136">Varsayılan olarak özel bileşenler.</span><span class="sxs-lookup"><span data-stu-id="f379a-136">Private components by default.</span></span>

     <span data-ttu-id="f379a-137">Varsayılan olarak, bileşenler uygulama dizinine dağıtılır ve yalnızca içeren uygulama için görülebilir.</span><span class="sxs-lookup"><span data-stu-id="f379a-137">By default, components are deployed to the application directory and are visible only to the containing application.</span></span>

- <span data-ttu-id="f379a-138">Denetlenen kod paylaşımı.</span><span class="sxs-lookup"><span data-stu-id="f379a-138">Controlled code sharing.</span></span>

     <span data-ttu-id="f379a-139">Kod paylaşımı, varsayılan davranış yerine kodu paylaşıma açık bir şekilde yapmanızı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f379a-139">Code sharing requires you to explicitly make code available for sharing instead of being the default behavior.</span></span>

- <span data-ttu-id="f379a-140">Yan yana sürüm oluşturma.</span><span class="sxs-lookup"><span data-stu-id="f379a-140">Side-by-side versioning.</span></span>

     <span data-ttu-id="f379a-141">Bir bileşenin veya uygulamanın birden çok sürümü birlikte bulunabilir, hangi sürümlerin kullanılacağını seçebilirsiniz ve ortak dil çalışma zamanı sürüm oluşturma ilkesini zorunlu kılar.</span><span class="sxs-lookup"><span data-stu-id="f379a-141">Multiple versions of a component or application can coexist, you can choose which versions to use, and the common language runtime enforces versioning policy.</span></span>

- <span data-ttu-id="f379a-142">XCOPY dağıtımı ve çoğaltma.</span><span class="sxs-lookup"><span data-stu-id="f379a-142">XCOPY deployment and replication.</span></span>

     <span data-ttu-id="f379a-143">Kendi kendine tanımlanmış ve bağımsız bileşenler ve uygulamalar kayıt defteri girişleri veya bağımlılıklar olmadan dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="f379a-143">Self-described and self-contained components and applications can be deployed without registry entries or dependencies.</span></span>

- <span data-ttu-id="f379a-144">Anında güncelleştirmeler.</span><span class="sxs-lookup"><span data-stu-id="f379a-144">On-the-fly updates.</span></span>

     <span data-ttu-id="f379a-145">Yöneticiler, uzak bilgisayarlarda bile program dll 'Lerini güncelleştirmek için ASP.NET gibi Konakları kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="f379a-145">Administrators can use hosts, such as ASP.NET, to update program DLLs, even on remote computers.</span></span>

- <span data-ttu-id="f379a-146">Windows Installer ile tümleştirme.</span><span class="sxs-lookup"><span data-stu-id="f379a-146">Integration with the Windows Installer.</span></span>

     <span data-ttu-id="f379a-147">Uygulamanızı dağıttığınızda tanıtım, yayımlama, onarma ve isteğe bağlı olarak kurma kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f379a-147">Advertisement, publishing, repair, and install-on-demand are all available when deploying your application.</span></span>

- <span data-ttu-id="f379a-148">Kurumsal Dağıtım.</span><span class="sxs-lookup"><span data-stu-id="f379a-148">Enterprise deployment.</span></span>

     <span data-ttu-id="f379a-149">Bu özellik Active Directory kullanımı dahil olmak üzere kolay yazılım dağıtımı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f379a-149">This feature provides easy software distribution, including using Active Directory.</span></span>

- <span data-ttu-id="f379a-150">İndiriliyor ve önbelleğe alınıyor.</span><span class="sxs-lookup"><span data-stu-id="f379a-150">Downloading and caching.</span></span>

     <span data-ttu-id="f379a-151">Artımlı indirmeler İndirmeleri daha küçük tutun ve bileşenler yalnızca uygulama tarafından düşük etkili dağıtım için kullanılmak üzere yalıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="f379a-151">Incremental downloads keep downloads smaller, and components can be isolated for use only by the application for low-impact deployment.</span></span>

- <span data-ttu-id="f379a-152">Kısmen güvenilen kod.</span><span class="sxs-lookup"><span data-stu-id="f379a-152">Partially trusted code.</span></span>

     <span data-ttu-id="f379a-153">Kimlik, Kullanıcı yerine kodu temel alır ve sertifika iletişim kutusu görüntülenmez.</span><span class="sxs-lookup"><span data-stu-id="f379a-153">Identity is based on the code instead of the user, and no certificate dialog boxes appear.</span></span>

## <a name="packaging-and-distributing-net-framework-applications"></a><span data-ttu-id="f379a-154">.NET Framework uygulamalarını paketleme ve dağıtma</span><span class="sxs-lookup"><span data-stu-id="f379a-154">Packaging and Distributing .NET Framework Applications</span></span>

<span data-ttu-id="f379a-155">.NET Framework yönelik paketleme ve dağıtım bilgilerinin bazıları, belgelerinin diğer bölümlerinde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f379a-155">Some of the packaging and deployment information for the .NET Framework is described in other sections of the documentation.</span></span> <span data-ttu-id="f379a-156">Bu bölümler, hiçbir kayıt defteri girişi gerektirmeyen [derleme](../../standard/assembly/index.md)adlı, [tanımlayıcı adlı derlemelerin](../../standard/assembly/strong-named.md)yanı sıra ad yanıltmayı ve [derleme sürümü oluşturmayı](../../standard/assembly/versioning.md) önleyen, kendi kendini açıklayan birimler hakkında bilgi sağlar , DLL çakışmaları ile ilişkili birçok sorunu ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f379a-156">Those sections provide information about the self-describing units called [assemblies](../../standard/assembly/index.md), which require no registry entries, [strong-named assemblies](../../standard/assembly/strong-named.md), which ensure name uniqueness and prevent name spoofing, and [assembly versioning](../../standard/assembly/versioning.md), which addresses many of the problems associated with DLL conflicts.</span></span> <span data-ttu-id="f379a-157">Aşağıdaki bölümlerde .NET Framework uygulamalarını paketleme ve dağıtma hakkında bilgi sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f379a-157">The following sections provide information about packaging and distributing .NET Framework applications.</span></span>

### <a name="packaging"></a><span data-ttu-id="f379a-158">Paketleme</span><span class="sxs-lookup"><span data-stu-id="f379a-158">Packaging</span></span>

<span data-ttu-id="f379a-159">.NET Framework paketleme uygulamaları için aşağıdaki seçenekleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="f379a-159">The .NET Framework provides the following options for packaging applications:</span></span>

- <span data-ttu-id="f379a-160">Tek bir derleme veya derlemelerin koleksiyonu olarak.</span><span class="sxs-lookup"><span data-stu-id="f379a-160">As a single assembly or as a collection of assemblies.</span></span>

     <span data-ttu-id="f379a-161">Bu seçenekle, yalnızca. dll veya. exe dosyalarını oluşturulduğu gibi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="f379a-161">With this option, you simply use the .dll or .exe files as they were built.</span></span>

- <span data-ttu-id="f379a-162">As dolap (CAB) dosyaları.</span><span class="sxs-lookup"><span data-stu-id="f379a-162">As cabinet (CAB) files.</span></span>

     <span data-ttu-id="f379a-163">Bu seçenekle, dağıtım yapmak veya daha az zaman kullanmak için dosyaları. cab dosyalarına sıkıştırursunuz.</span><span class="sxs-lookup"><span data-stu-id="f379a-163">With this option, you compress files into .cab files to make distribution or download less time consuming.</span></span>

- <span data-ttu-id="f379a-164">Windows Installer paketi veya diğer yükleyici biçimlerinde.</span><span class="sxs-lookup"><span data-stu-id="f379a-164">As a Windows Installer package or in other installer formats.</span></span>

     <span data-ttu-id="f379a-165">Bu seçenekle, Windows Installer ile kullanmak üzere. msi dosyaları oluşturur veya uygulamanızı başka bir yükleyiciyle kullanmak üzere paketlemenize yardımcı olursunuz.</span><span class="sxs-lookup"><span data-stu-id="f379a-165">With this option, you create .msi files for use with the Windows Installer, or you package your application for use with some other installer.</span></span>

### <a name="distribution"></a><span data-ttu-id="f379a-166">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="f379a-166">Distribution</span></span>

<span data-ttu-id="f379a-167">.NET Framework, uygulamaları dağıtmak için aşağıdaki seçenekleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="f379a-167">The .NET Framework provides the following options for distributing applications:</span></span>

- <span data-ttu-id="f379a-168">XCOPY veya FTP kullanın.</span><span class="sxs-lookup"><span data-stu-id="f379a-168">Use XCOPY or FTP.</span></span>

     <span data-ttu-id="f379a-169">Ortak dil çalışma zamanı uygulamaları kendi kendini betimleyen ve kayıt defteri girişi gerektirmeyen için, yalnızca uygulamayı uygun bir dizine kopyalamak üzere XCOPY veya FTP kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f379a-169">Because common language runtime applications are self-describing and require no registry entries, you can use XCOPY or FTP to simply copy the application to an appropriate directory.</span></span> <span data-ttu-id="f379a-170">Uygulama daha sonra bu dizinden çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="f379a-170">The application can then be run from that directory.</span></span>

- <span data-ttu-id="f379a-171">Kod indirmeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="f379a-171">Use code download.</span></span>

     <span data-ttu-id="f379a-172">Uygulamanızı Internet üzerinden veya kurumsal bir intranet üzerinden dağıtıyorsanız, kodu bir bilgisayara indirebilir ve uygulamayı orada çalıştırmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="f379a-172">If you are distributing your application over the Internet or through a corporate intranet, you can simply download the code to a computer and run the application there.</span></span>

- <span data-ttu-id="f379a-173">Windows Installer 2,0 gibi bir yükleyici programı kullanın.</span><span class="sxs-lookup"><span data-stu-id="f379a-173">Use an installer program such as Windows Installer 2.0.</span></span>

     <span data-ttu-id="f379a-174">Windows Installer 2,0, genel derleme önbelleğinde ve özel dizinlerde .NET Framework derlemeleri yükleyebilir, onarabilir veya kaldırabilir.</span><span class="sxs-lookup"><span data-stu-id="f379a-174">Windows Installer 2.0 can install, repair, or remove .NET Framework assemblies in the global assembly cache and in private directories.</span></span>

### <a name="installation-location"></a><span data-ttu-id="f379a-175">Yükleme Konumu</span><span class="sxs-lookup"><span data-stu-id="f379a-175">Installation Location</span></span>

<span data-ttu-id="f379a-176">Çalışma zamanı tarafından bulunabilmeleri için uygulamanızın derlemelerinin nereye dağıtılacağını öğrenmek için, bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="f379a-176">To determine where to deploy your application's assemblies so they can be found by the runtime, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>

<span data-ttu-id="f379a-177">Güvenlik konuları, uygulamanızı nasıl dağıtabileceğinizi da etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="f379a-177">Security considerations can also affect how you deploy your application.</span></span> <span data-ttu-id="f379a-178">Güvenlik izinleri, kodun bulunduğu yere göre yönetilen koda verilir.</span><span class="sxs-lookup"><span data-stu-id="f379a-178">Security permissions are granted to managed code according to where the code is located.</span></span> <span data-ttu-id="f379a-179">Bir uygulama veya bileşeni Internet gibi küçük bir güven aldığı bir konuma dağıtmak, uygulamanın veya bileşenin neler yapabileceğini kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="f379a-179">Deploying an application or component to a location where it receives little trust, such as the Internet, limits what the application or component can do.</span></span> <span data-ttu-id="f379a-180">Dağıtım ve güvenlik konuları hakkında daha fazla bilgi için bkz. [kod erişimi güvenlik temelleri](../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="f379a-180">For more information about deployment and security considerations, see [Code Access Security Basics](../../../docs/framework/misc/code-access-security-basics.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="f379a-181">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="f379a-181">Related Topics</span></span>

|<span data-ttu-id="f379a-182">Başlık</span><span class="sxs-lookup"><span data-stu-id="f379a-182">Title</span></span>|<span data-ttu-id="f379a-183">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f379a-183">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="f379a-184">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="f379a-184">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|<span data-ttu-id="f379a-185">Ortak dil çalışma zamanının, bir bağlama isteğini karşılamak için hangi derlemeyi kullanacağınızı nasıl belirlediğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f379a-185">Describes how the common language runtime determines which assembly to use to fulfill a binding request.</span></span>|
|[<span data-ttu-id="f379a-186">Bütünleştirilmiş Kod Yükleme için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f379a-186">Best Practices for Assembly Loading</span></span>](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)|<span data-ttu-id="f379a-187"><xref:System.InvalidCastException> ,<xref:System.MissingMethodException>, Ve diğer hatalara yol açabilecek kimlik tür sorunlarından kaçınmanın yollarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f379a-187">Discusses ways to avoid problems of type identity that can lead to <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, and other errors.</span></span>|
|[<span data-ttu-id="f379a-188">.NET Framework 4.5 Yüklemeleri Sırasında Sistem Yeniden Başlatmalarını Azaltma</span><span class="sxs-lookup"><span data-stu-id="f379a-188">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](../../../docs/framework/deployment/reducing-system-restarts.md)|<span data-ttu-id="f379a-189">Mümkün olan her durumda yeniden başlatma Işlemini önleyen ve .NET Framework yükleyen uygulamaların nasıl yararlanacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f379a-189">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>|
|[<span data-ttu-id="f379a-190">Yöneticiler için Dağıtım Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f379a-190">Deployment Guide for Administrators</span></span>](../../../docs/framework/deployment/guide-for-administrators.md)|<span data-ttu-id="f379a-191">Bir sistem yöneticisinin, System Center Configuration Manager (SCCM) kullanarak bir ağ üzerinde .NET Framework ve sistem bağımlılıklarını nasıl dağıtabilebileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f379a-191">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using System Center Configuration Manager (SCCM).</span></span>|
|[<span data-ttu-id="f379a-192">Geliştiriciler için Dağıtım Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f379a-192">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)|<span data-ttu-id="f379a-193">Geliştiricilerin kullanıcıların bilgisayarlarına uygulamalarına .NET Framework nasıl yükleyebileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f379a-193">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>|
|[<span data-ttu-id="f379a-194">Uygulamaları, Hizmetleri ve Bileşenleri Dağıtma</span><span class="sxs-lookup"><span data-stu-id="f379a-194">Deploying Applications, Services, and Components</span></span>](/visualstudio/deployment/deploying-applications-services-and-components)|<span data-ttu-id="f379a-195">ClickOnce ve Windows Installer teknolojilerini kullanarak uygulama yayımlama yönergeleri de dahil olmak üzere Visual Studio 'da dağıtım seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f379a-195">Discusses deployment options in Visual Studio, including instructions for publishing an application using the ClickOnce and Windows Installer technologies.</span></span>|
|[<span data-ttu-id="f379a-196">ClickOnce Uygulamalarını Yayımlama</span><span class="sxs-lookup"><span data-stu-id="f379a-196">Publishing ClickOnce Applications</span></span>](/visualstudio/deployment/publishing-clickonce-applications)|<span data-ttu-id="f379a-197">Bir Windows Forms uygulamasının nasıl paketleneceğini ve bir ağdaki istemci bilgisayarlara ClickOnce ile nasıl dağıtılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f379a-197">Describes how to package a Windows Forms application and deploy it with ClickOnce to client computers on a network.</span></span>|
|[<span data-ttu-id="f379a-198">Kaynakları Paketleme ve Dağıtma</span><span class="sxs-lookup"><span data-stu-id="f379a-198">Packaging and Deploying Resources</span></span>](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)|<span data-ttu-id="f379a-199">.NET Framework, kaynakları paketlemek ve dağıtmak için kullandığı hub ve bağlı bileşen modelini açıklar; Kaynak adlandırma kurallarını, geri dönüş işlemini ve paketleme alternatiflerini içerir.</span><span class="sxs-lookup"><span data-stu-id="f379a-199">Describes the hub and spoke model that the .NET Framework uses to package and deploy resources; covers resource naming conventions, fallback process, and packaging alternatives.</span></span>|
|[<span data-ttu-id="f379a-200">Birlikte Çalışma Uygulamasını Dağıtma</span><span class="sxs-lookup"><span data-stu-id="f379a-200">Deploying an Interop Application</span></span>](../../../docs/framework/interop/deploying-an-interop-application.md)|<span data-ttu-id="f379a-201">Genellikle bir .NET Framework istemci derlemesi, farklı COM tür kitaplıklarını temsil eden bir veya daha fazla birlikte çalışma derlemesi ve bir veya daha fazla kayıtlı COM bileşeni içeren birlikte çalışma uygulamalarının nasıl teslim edileceğini ve yükleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f379a-201">Explains how to ship and install interop applications, which typically include a .NET Framework client assembly, one or more interop assemblies representing distinct COM type libraries, and one or more registered COM components.</span></span>|
|[<span data-ttu-id="f379a-202">Nasıl yapılır: .NET Framework 4,5 Yükleyicisinden Ilerleme durumunu alın</span><span class="sxs-lookup"><span data-stu-id="f379a-202">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)|<span data-ttu-id="f379a-203">Kurulum ilerleme durumunun kendi görünümünü gösterirken .NET Framework kurulum işleminin sessizce nasıl başlatılmasını ve izleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f379a-203">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>|

## <a name="see-also"></a><span data-ttu-id="f379a-204">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f379a-204">See also</span></span>

- [<span data-ttu-id="f379a-205">Geliştirme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f379a-205">Development Guide</span></span>](../../../docs/framework/development-guide.md)
