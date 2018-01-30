---
title: ".NET Framework ve Bant Dışı Yayınlar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 721f10fa-3189-4124-a00d-56ddabd889b3
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 83c3688afb3fe509d9a57eba8765cbd13bf581c8
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2018
---
# <a name="the-net-framework-and-out-of-band-releases"></a><span data-ttu-id="5c4f6-102">.NET Framework ve Bant Dışı Yayınlar</span><span class="sxs-lookup"><span data-stu-id="5c4f6-102">The .NET Framework and Out-of-Band Releases</span></span>
<span data-ttu-id="5c4f6-103">.NET Framework, Windows Phone ve Windows Mağazası uygulamaları yanı sıra geleneksel masaüstü ve web uygulamaları ve kod tekrar kullanımını en üst düzeye çıkarmak üzere farklı platformlara uyum sağlamak için gelişiyor.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-103">The .NET Framework is evolving to accommodate different platforms such as Windows Phone and Windows Store apps as well as traditional desktop and web apps, and to maximize code reuse.</span></span> <span data-ttu-id="5c4f6-104">Normal .NET Framework yayınlarımızın yanı sıra, platformlar arası geliştirmeyi geliştirmek veya yeni işlevsellikler eklemek için yeni özellikleri bant dışı (OOB) yayınlarız.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-104">In addition to our regular .NET Framework releases, we release new features out of band (OOB) to improve cross-platform development or to introduce new functionality.</span></span> <span data-ttu-id="5c4f6-105">Bu konu, .NET Framework ve OOB sürümlerinin gelecekteki yönelimlerini tartışır.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-105">This topic discusses the future direction of the .NET Framework and its OOB releases.</span></span>  
  
## <a name="advantages-of-oob-releases"></a><span data-ttu-id="5c4f6-106">OOB sürümlerinin avantajları</span><span class="sxs-lookup"><span data-stu-id="5c4f6-106">Advantages of OOB releases</span></span>  
 <span data-ttu-id="5c4f6-107">Yeni bileşenleri veya bant dışı bileşenlerin güncellemeleri, Microsoft'un .NET Framework'e daha sık güncelleme sağlamasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-107">Shipping new components or updates to components out of band enables Microsoft to provide more frequent updates to the .NET Framework.</span></span> <span data-ttu-id="5c4f6-108">Buna ek olarak, müşteri geri bildirimlerini toplayıp olabildiğince hızlı yanıtlayabiliyoruz.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-108">In addition, we can gather and respond to customer feedback more quickly.</span></span>  
  
 <span data-ttu-id="5c4f6-109">Uygulamanızda bir OOB özelliğini kullanırsanız, OOB derlemeleri uygulama paketinizle birlikte dağıtıldığından, kullanıcılarınızın uygulamanızı çalıştırmak için .NET Framework'ün son sürümünü yüklemeleri gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-109">When you use an OOB feature in your app, your users do not have to install the latest version of the .NET Framework to run your app, because the OOB assemblies deploy with your app package.</span></span>  
  
## <a name="how-oob-packages-are-distributed"></a><span data-ttu-id="5c4f6-110">OOB paketleri nasıl dağıtılır?</span><span class="sxs-lookup"><span data-stu-id="5c4f6-110">How OOB packages are distributed</span></span>  
<span data-ttu-id="5c4f6-111">Çekirdek ortak dil çalışma zamanı (CLR) bileşenlerini OOB sürümleri aracılığıyla teslim edilir [NuGet](https://www.nuget.org/), .NET için bir paket Yöneticisi olduğu.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-111">OOB releases for core common language runtime (CLR) components are delivered through the [NuGet](https://www.nuget.org/), which is a package manager for .NET.</span></span> <span data-ttu-id="5c4f6-112">NuGet, Visual Studio'daki Çözüm Gezgini'nden .NET Framework projelerinize kolaylıkla göz atmanıza ve kitaplıklar eklemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-112">NuGet enables you to browse and add libraries to your .NET Framework projects easily from the Solution Explorer in Visual Studio.</span></span> <span data-ttu-id="5c4f6-113">NuGet, Visual Studio 2012'den itibaren tüm Visual Studio sürümleriyle birlikte gelir.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-113">NuGet is included with all editions of Visual Studio starting with Visual Studio 2012.</span></span> <span data-ttu-id="5c4f6-114">NuGet'ın yüklü olup olmadığını görmek için Ara **kitaplık Paket Yöneticisi** Visual Studio üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-114">To see if NuGet is installed, look for **Library Package Manager** on the Visual Studio **Tools** menu.</span></span> <span data-ttu-id="5c4f6-115">Yüklü değilse:</span><span class="sxs-lookup"><span data-stu-id="5c4f6-115">If it’s not installed:</span></span>  
  
1.  <span data-ttu-id="5c4f6-116">Visual Studio menü çubuğunda seçin **Araçları**, **Uzantılar ve güncelleştirmeler** (Visual Studio 2010'da seçin **Uzantı Yöneticisi**).</span><span class="sxs-lookup"><span data-stu-id="5c4f6-116">On the Visual Studio menu bar, choose **Tools**, **Extensions and Updates** (in Visual Studio 2010, choose **Extension Manager**).</span></span>  
  
     <span data-ttu-id="5c4f6-117">**Uzantılar ve güncelleştirmeler** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-117">The **Extensions and Updates** dialog box opens.</span></span>  
  
2.  <span data-ttu-id="5c4f6-118">Seçin **çevrimiçi**, **NuGet Paket Yöneticisi**ve ardından **karşıdan**.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-118">Choose **Online**, **NuGet Package Manager**, and then choose **Download**.</span></span>  
  
3.  <span data-ttu-id="5c4f6-119">Karşıdan yükleme tamamlandıktan sonra Visual Studio'yu yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-119">After the download completes, restart Visual Studio.</span></span>  
  
 <span data-ttu-id="5c4f6-120">Ayrıntılı yükleme yönergeleri için bkz: [yükleme NuGet](http://docs.nuget.org/docs/start-here/installing-nuget) NuGet belgeleri Web üzerinde.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-120">For detailed installation instructions, see [Installing NuGet](http://docs.nuget.org/docs/start-here/installing-nuget) on the NuGet Docs website.</span></span> <span data-ttu-id="5c4f6-121">NuGet hakkında daha fazla bilgi için bkz: [NuGet belgelerine](http://docs.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="5c4f6-121">For more information about NuGet, see the [NuGet documentation](http://docs.nuget.org/).</span></span>  
  
## <a name="using-a-nuget-oob-package"></a><span data-ttu-id="5c4f6-122">NuGet OOB paketini kullanma</span><span class="sxs-lookup"><span data-stu-id="5c4f6-122">Using a NuGet OOB package</span></span>  
 <span data-ttu-id="5c4f6-123">NuGet yükledikten sonra, Visual Studio'da Çözüm Gezgini'ni kullanarak NuGet paketlerine göz atabilir ve başvurular ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5c4f6-123">After you install NuGet, you can browse and add references to NuGet packages by using Solution Explorer in Visual Studio:</span></span>  
  
1.  <span data-ttu-id="5c4f6-124">Visual Studio'da projeniz için kısayol menüsünü açın ve ardından **NuGet paketlerini Yönet**.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-124">Open the shortcut menu for your project in Visual Studio, and then choose **Manage NuGet Packages**.</span></span> <span data-ttu-id="5c4f6-125">(Bu seçenek ayrıca kullanılabilir **proje** menü.)</span><span class="sxs-lookup"><span data-stu-id="5c4f6-125">(This option is also available from the **Project** menu.)</span></span>  
  
2.  <span data-ttu-id="5c4f6-126">Sol bölmede seçin **çevrimiçi**.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-126">In the left pane, choose **Online**.</span></span>  
  
3.  <span data-ttu-id="5c4f6-127">Orta bölmede aşağı açılan liste kutusunda ön sürüm paketlerini kullanmak istiyorsanız, seçin **dahil ön** yerine **yalnızca kararlı**.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-127">If you want to use prerelease packages, in the drop-down list box in the middle pane, choose **Include Prerelease** instead of **Stable Only**.</span></span>  
  
4.  <span data-ttu-id="5c4f6-128">Sağ bölmede, kullanmak **arama** kutusunu kullanmak istediğiniz paketi bulun.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-128">In the right pane, use the **Search** box to locate the package you would like to use.</span></span> <span data-ttu-id="5c4f6-129">Bazı Microsoft paketleri, Microsoft .NET Framework logosu ile tanımlanır ve tümü Microsoft'u yayımcı olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-129">Some Microsoft packages are identified by the Microsoft .NET Framework logo, and all identify Microsoft as the publisher.</span></span>  
  
 <span data-ttu-id="5c4f6-130">![NuGet Paket Yöneticisi](../../../docs/framework/get-started/media/clrnugetdialog.png "clrNugetDialog")</span><span class="sxs-lookup"><span data-stu-id="5c4f6-130">![NuGet Package Manager](../../../docs/framework/get-started/media/clrnugetdialog.png "clrNugetDialog")</span></span>  
  
 <span data-ttu-id="5c4f6-131">Daha önce belirtildiği gibi, OOB paketi kullanan bir uygulamayı dağıttığınızda OOB derlemeleri, uygulama paketinizle birlikte sevk edilir.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-131">As mentioned previously, when you deploy an app that uses an OOB package, the OOB assemblies will ship with your app package.</span></span>  
  
## <a name="types-of-oob-releases"></a><span data-ttu-id="5c4f6-132">OOB sürümlerinin türleri</span><span class="sxs-lookup"><span data-stu-id="5c4f6-132">Types of OOB releases</span></span>  
 <span data-ttu-id="5c4f6-133">Genellikle, bir OOB paketi bir veya daha fazla yayın öncesi sürüm ve kararlı bir sürüm içerir.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-133">Typically, an OOB package has one or more prerelease versions and a stable version.</span></span> <span data-ttu-id="5c4f6-134">Bir yayın öncesi eşlik lisans yeniden dağıtımı genellikle izin vermez ancak bu bir paket deneyin ve geri bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-134">The license that accompanies a prerelease doesn't typically allow redistribution, but enables you to try out a package and provide feedback.</span></span> <span data-ttu-id="5c4f6-135">Geribildirim, pakete yapılan tüm güncelleştirmelere eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-135">Feedback is incorporated in any updates made to the package.</span></span> <span data-ttu-id="5c4f6-136">Son sürüm NuGet ile bir kararlı paket olarak dağıtılır ve NuGet paketini uygulamanızla yeniden dağıtmanıza olanak sağlayan bir lisans içerir.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-136">A final release is distributed as a stable package with NuGet and includes a license that lets you redistribute the NuGet package with your app.</span></span> <span data-ttu-id="5c4f6-137">Kalıcı paketler, Microsoft tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-137">Stable packages are supported by Microsoft.</span></span> <span data-ttu-id="5c4f6-138">Microsoft diğer türleri blog gönderileri gibi belgelerin yanı sıra IntelliSense desteği sağlar ve forum tüm paketler için yanıtlar.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-138">Microsoft provides IntelliSense support as well as other types of documentation such as blog posts and forum answers for all packages.</span></span> <span data-ttu-id="5c4f6-139">Ayrıca, kaynak kodu, ancak bazı değil tüm paketleri ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-139">In addition, source code may be available with some, but not all, packages.</span></span> <span data-ttu-id="5c4f6-140">Yeni ve güncelleştirilmiş paketleri ile ilgili daha fazla duyuruları için için abone olabilirsiniz [.NET Framework Blog](http://blogs.msdn.com/b/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="5c4f6-140">For announcements regarding new and updated packages, you can subscribe to [the .NET Framework Blog](http://blogs.msdn.com/b/dotnet/).</span></span>  
  
 <span data-ttu-id="5c4f6-141">Yayın öncesi ve kararlı paketleri bulmak için tercih **dahil ön** NuGet Paket Yöneticisi'nde.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-141">To find both prerelease and stable packages, choose **Include Prerelease** in the NuGet Package Manager.</span></span>  
  
 <span data-ttu-id="5c4f6-142">Kararlı paketi sürümleri bildirim almak istiyorsanız, abone [akış .NET Framework](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/).</span><span class="sxs-lookup"><span data-stu-id="5c4f6-142">If you want to be notified of stable package releases, subscribe to [the .NET Framework feed](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c4f6-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5c4f6-143">See Also</span></span>  
 [<span data-ttu-id="5c4f6-144">Başlarken</span><span class="sxs-lookup"><span data-stu-id="5c4f6-144">Getting Started</span></span>](../../../docs/framework/get-started/index.md)
