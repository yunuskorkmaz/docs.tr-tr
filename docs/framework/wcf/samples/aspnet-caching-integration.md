---
title: "ASP.NET Önbelleğe Alma Tümleştirmesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a8830f1c19b7a91d6c22d3b5955624c7d8a86f5f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="aspnet-caching-integration"></a><span data-ttu-id="a7afe-102">ASP.NET Önbelleğe Alma Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="a7afe-102">ASP.NET Caching Integration</span></span>
<span data-ttu-id="a7afe-103">Bu örnek, ASP.NET çıktı önbelleğine WCF WEB HTTP programlama modeli kullanan gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a7afe-103">This sample demonstrates how to utilize the ASP.NET output cache with the WCF WEB HTTP programming model.</span></span> <span data-ttu-id="a7afe-104">Lütfen bakın [temel kaynak hizmeti](../../../../docs/framework/wcf/samples/basic-resource-service.md) kendini barındıran sürümü derinliği hizmet uygulamasında ele bu senaryo için örnek.</span><span class="sxs-lookup"><span data-stu-id="a7afe-104">Please see the [Basic Resource Service](../../../../docs/framework/wcf/samples/basic-resource-service.md) sample for a self-hosted version of this scenario that discusses the service implementation in depth.</span></span> <span data-ttu-id="a7afe-105">Bu konu ASP.NET çıktı önbelleği tümleştirme özelliğini odaklanır.</span><span class="sxs-lookup"><span data-stu-id="a7afe-105">This topic focuses on the ASP.NET output cache integration feature.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="a7afe-106">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="a7afe-106">Demonstrates</span></span>  
 <span data-ttu-id="a7afe-107">ASP.NET çıktı önbelleği ile tümleştirme</span><span class="sxs-lookup"><span data-stu-id="a7afe-107">Integration with the ASP.NET Output Cache</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a7afe-108">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a7afe-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a7afe-109">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a7afe-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a7afe-110">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="a7afe-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a7afe-111">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a7afe-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`  
  
## <a name="discussion"></a><span data-ttu-id="a7afe-112">Tartışma</span><span class="sxs-lookup"><span data-stu-id="a7afe-112">Discussion</span></span>  
 <span data-ttu-id="a7afe-113">Örnek kullanır <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> ASP.NET faydalanmak için çıkış önbelleğe almayı [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="a7afe-113">The sample uses the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> to utilize ASP.NET output caching with the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span></span> <span data-ttu-id="a7afe-114"><xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> Hizmet işlemleri için uygulanır ve yanıtlarını verilen işlemi uygulanması gereken yapılandırma dosyasında bir önbellek profili adı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7afe-114">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is applied to service operations, and provides the name of a cache profile in a configuration file that should be applied to responses from the given operation.</span></span>  
  
 <span data-ttu-id="a7afe-115">Örnek hizmet projesinin adını da dosyasındaki hem `GetCustomer` ve `GetCustomers` işlemleri ile işaretlenmiş <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, önbellek profili adı "CacheFor60Seconds" sağlar.</span><span class="sxs-lookup"><span data-stu-id="a7afe-115">In the Service.cs file of the sample Service project, both the `GetCustomer` and `GetCustomers` operations are marked with the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, which provides the cache profile name "CacheFor60Seconds".</span></span> <span data-ttu-id="a7afe-116">Hizmet projesinin Web.config dosyasında önbellek profili "CacheFor60Seconds" altında sağlanır <`caching`> öğesi <`system.web`>.</span><span class="sxs-lookup"><span data-stu-id="a7afe-116">In the Web.config file of the Service project, the cache profile "CacheFor60Seconds" is provided under the <`caching`> element of <`system.web`>.</span></span> <span data-ttu-id="a7afe-117">Bu önbellek profili değeri için `duration` özniteliktir "60", bu profil ile ilişkili ASP.NET çıktı önbelleği 60 saniye boyunca önbelleğe alınan yanıtları şekilde.</span><span class="sxs-lookup"><span data-stu-id="a7afe-117">For this cache profile, the value of the `duration` attribute is "60", so responses associated with this profile are cached in the ASP.NET output cache for 60 seconds.</span></span> <span data-ttu-id="a7afe-118">Ayrıca, bu önbellek profili için `varmByParam` özniteliği ayarlanmış "için farklı değerler bunu istekleriyle biçim" `format` sorgu dizesi parametresi ayrı olarak önbelleğe yanıtlarını sahip.</span><span class="sxs-lookup"><span data-stu-id="a7afe-118">Also, for this cache profile, the `varmByParam` attribute is set to "format" so requests with different values for the `format` query string parameter have their responses cached separately.</span></span> <span data-ttu-id="a7afe-119">Son olarak, önbellek profilinin `varyByHeader` özniteliği, "Kabul et" ayarlanmışsa, farklı Accept üstbilgi değerlerini istekleriyle yanıtlarını ayrı olarak önbelleğe alacak şekilde.</span><span class="sxs-lookup"><span data-stu-id="a7afe-119">Lastly, the cache profile’s `varyByHeader` attribute is set to "Accept", so requests with different Accept header values have their responses cached separately.</span></span>  
  
 <span data-ttu-id="a7afe-120">İstemci projesindeki program.cs gösteren böyle bir istemci nasıl olabilir kullanılarak yazılan <xref:System.Net.HttpWebRequest>.</span><span class="sxs-lookup"><span data-stu-id="a7afe-120">Program.cs in the Client project demonstrates how such a client can be authored using <xref:System.Net.HttpWebRequest>.</span></span> <span data-ttu-id="a7afe-121">Bu bir WCF Hizmeti erişmenin tek yolu olduğuna dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="a7afe-121">Note that this is just one way to access a WCF service.</span></span> <span data-ttu-id="a7afe-122">Diğer .NET Framework sınıfları gibi kullanarak hizmete erişmek mümkündür [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanal fabrikası ve <xref:System.Net.WebClient>.</span><span class="sxs-lookup"><span data-stu-id="a7afe-122">It is also possible to access the service using other .NET Framework classes like the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] channel factory and <xref:System.Net.WebClient>.</span></span> <span data-ttu-id="a7afe-123">SDK'sındaki diğer örnekleri (gibi [temel HTTP hizmeti](../../../../docs/framework/wcf/samples/basic-http-service.md) örnek ve [Otomatik Biçim Seçimi](../../../../docs/framework/wcf/samples/automatic-format-selection.md) örnek) bu sınıfların ile iletişim kurmak için nasıl kullanılacağını gösteren bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="a7afe-123">Other samples in the SDK (such as the [Basic HTTP Service](../../../../docs/framework/wcf/samples/basic-http-service.md) sample and the [Automatic Format Selection](../../../../docs/framework/wcf/samples/automatic-format-selection.md) sample) illustrate how to use these classes to communicate with a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
## <a name="to-run-the-sample"></a><span data-ttu-id="a7afe-124">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a7afe-124">To run the sample</span></span>  
 <span data-ttu-id="a7afe-125">Örnek üç projelerin oluşur:</span><span class="sxs-lookup"><span data-stu-id="a7afe-125">The sample consists of three projects:</span></span>  
  
-   <span data-ttu-id="a7afe-126">**Hizmet**: ASP.NET barındırılan bir WCF HTTP hizmeti içeren bir Web uygulaması projesi.</span><span class="sxs-lookup"><span data-stu-id="a7afe-126">**Service**: A Web Application project that includes a WCF HTTP service hosted in ASP.NET.</span></span>  
  
-   <span data-ttu-id="a7afe-127">**İstemci**: hizmet çağrılar bir konsol uygulama projesi.</span><span class="sxs-lookup"><span data-stu-id="a7afe-127">**Client**: A console application project that makes calls to the service.</span></span>  
  
-   <span data-ttu-id="a7afe-128">**Ortak**: istemci ve hizmet tarafından kullanılan müşteri türünü içeren paylaşılan bir kitaplık.</span><span class="sxs-lookup"><span data-stu-id="a7afe-128">**Common**: A shared library that contains the Customer type used by the client and service.</span></span>  
  
 <span data-ttu-id="a7afe-129">İstemci konsol uygulaması çalışırken, istemci hizmete istek yaptığında ve konsol penceresine yanıtlardan bilgileri yazar.</span><span class="sxs-lookup"><span data-stu-id="a7afe-129">As the Client console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="a7afe-130">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a7afe-130">To run the sample</span></span>  
  
1.  <span data-ttu-id="a7afe-131">ASP.NET önbelleğe alma tümleştirmesi için örnek çözümü açın.</span><span class="sxs-lookup"><span data-stu-id="a7afe-131">Open the solution for the ASP.NET Caching Integration Sample.</span></span>  
  
2.  <span data-ttu-id="a7afe-132">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a7afe-132">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="a7afe-133">Varsa **Çözüm Gezgini** penceresi zaten açık, CTRL + W + S tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="a7afe-133">If the **Solution Explorer** window is not already open, press CTRL+W+S.</span></span>  
  
4.  <span data-ttu-id="a7afe-134">Gelen **Çözüm Gezgini** penceresinde, sağ tıklatma **hizmet** proje ve seçin **Başlat yeni örnek**.</span><span class="sxs-lookup"><span data-stu-id="a7afe-134">From the **Solution Explorer** window, right click the **Service** project and select **Start New Instance**.</span></span> <span data-ttu-id="a7afe-135">Bu hizmeti barındıran ASP.NET geliştirme sunucusu başlatır.</span><span class="sxs-lookup"><span data-stu-id="a7afe-135">This launches the ASP.NET development server, which hosts the service.</span></span>  
  
5.  <span data-ttu-id="a7afe-136">Gelen **Çözüm Gezgini** penceresinde, sağ tıklatma **istemci** proje ve seçin **Başlat yeni örnek**.</span><span class="sxs-lookup"><span data-stu-id="a7afe-136">From the **Solution Explorer** window, right click the **Client** project and select **Start New Instance**.</span></span>  
  
6.  <span data-ttu-id="a7afe-137">İstemci konsol penceresi görüntülenir ve çalışan hizmetin URI sağlar ve URI HTML sayfası çalışan hizmetin için yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="a7afe-137">The client console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span> <span data-ttu-id="a7afe-138">Herhangi bir noktada, HTML Yardım sayfasına bir tarayıcıda yardım sayfasına URI'sini yazarak görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a7afe-138">At any point in time you can view the HTML help page by typing the URI of the help page in a browser.</span></span>  
  
7.  <span data-ttu-id="a7afe-139">Örnek çalışırken, istemcinin geçerli etkinlik durumunu yazar.</span><span class="sxs-lookup"><span data-stu-id="a7afe-139">As the sample runs, the client writes the status of the current activity.</span></span>  
  
8.  <span data-ttu-id="a7afe-140">İstemci konsol uygulaması sonlandırmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="a7afe-140">Press any key to terminate the client console application.</span></span>  
  
9. <span data-ttu-id="a7afe-141">Hata ayıklama hizmetini durdurmak için SHIFT + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a7afe-141">Press SHIFT+F5 to stop debugging the service.</span></span>  
  
10. <span data-ttu-id="a7afe-142">Windows bildirim alanında ASP.NET Geliştirme Sunucusu simgesini sağ tıklatın ve seçin **durdurmak**.</span><span class="sxs-lookup"><span data-stu-id="a7afe-142">In the Windows Notification Area, right click the ASP.NET development server icon and select **Stop**.</span></span>
