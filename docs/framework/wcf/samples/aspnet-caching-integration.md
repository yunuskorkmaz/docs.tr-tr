---
title: ASP.NET Önbelleğe Alma Tümleştirmesi
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: 8ed546459479e9986d6bbecf6eaca350d2d73c98
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59770028"
---
# <a name="aspnet-caching-integration"></a><span data-ttu-id="66801-102">ASP.NET Önbelleğe Alma Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="66801-102">ASP.NET Caching Integration</span></span>
<span data-ttu-id="66801-103">Bu örnek, WCF WEB HTTP programlama modeli ile ASP.NET çıktı önbelleği nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="66801-103">This sample demonstrates how to utilize the ASP.NET output cache with the WCF WEB HTTP programming model.</span></span> <span data-ttu-id="66801-104">Bu konu, ASP.NET çıktı önbelleği tümleştirme özelliği üzerinde odaklanır.</span><span class="sxs-lookup"><span data-stu-id="66801-104">This topic focuses on the ASP.NET output cache integration feature.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="66801-105">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="66801-105">Demonstrates</span></span>  
 <span data-ttu-id="66801-106">ASP.NET çıktı önbelleği ile tümleştirme</span><span class="sxs-lookup"><span data-stu-id="66801-106">Integration with the ASP.NET Output Cache</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="66801-107">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="66801-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="66801-108">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="66801-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="66801-109">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="66801-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="66801-110">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="66801-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`  
  
## <a name="discussion"></a><span data-ttu-id="66801-111">Tartışma</span><span class="sxs-lookup"><span data-stu-id="66801-111">Discussion</span></span>  
 <span data-ttu-id="66801-112">Örnek kullanır <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> ASP.NET kullanmaya çıktı Windows Communication Foundation (WCF) hizmetiyle önbelleği.</span><span class="sxs-lookup"><span data-stu-id="66801-112">The sample uses the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> to utilize ASP.NET output caching with the Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="66801-113"><xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> Hizmet işlemleri için uygulanır ve yanıtlarını belirtilen işlemi uygulanması gereken yapılandırma dosyasında bir önbellek profili adını sağlar.</span><span class="sxs-lookup"><span data-stu-id="66801-113">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is applied to service operations, and provides the name of a cache profile in a configuration file that should be applied to responses from the given operation.</span></span>  
  
 <span data-ttu-id="66801-114">Örnek hizmet projesinin adını da dosyasında hem `GetCustomer` ve `GetCustomers` işlemleri ile işaretlenir <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, önbellek profili adı "CacheFor60Seconds" sağlar.</span><span class="sxs-lookup"><span data-stu-id="66801-114">In the Service.cs file of the sample Service project, both the `GetCustomer` and `GetCustomers` operations are marked with the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, which provides the cache profile name "CacheFor60Seconds".</span></span> <span data-ttu-id="66801-115">Hizmet projesinin Web.config dosyasının önbellek profili "CacheFor60Seconds" kapsamında sağlanır <`caching`> öğesi <`system.web`>.</span><span class="sxs-lookup"><span data-stu-id="66801-115">In the Web.config file of the Service project, the cache profile "CacheFor60Seconds" is provided under the <`caching`> element of <`system.web`>.</span></span> <span data-ttu-id="66801-116">Bu önbellek profili değeri için `duration` özniteliktir "60" şekilde bu profil ile ilişkili yanıtları ASP.NET çıktı önbelleğinde 60 saniye için önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="66801-116">For this cache profile, the value of the `duration` attribute is "60", so responses associated with this profile are cached in the ASP.NET output cache for 60 seconds.</span></span> <span data-ttu-id="66801-117">Ayrıca, bu önbellek profili için `varmByParam` "için farklı değerlerle bunu isteklerini biçimlendirmek için" özniteliği ayarlanmış `format` sorgu dizesi parametresi yanıtlarını ayrı olarak önbelleğe sahip.</span><span class="sxs-lookup"><span data-stu-id="66801-117">Also, for this cache profile, the `varmByParam` attribute is set to "format" so requests with different values for the `format` query string parameter have their responses cached separately.</span></span> <span data-ttu-id="66801-118">Son olarak, önbellek profilin `varyByHeader` özniteliği "Kabul et" olarak ayarlanmışsa, farklı bir Accept üstbilgi değerlerini isteklerle yanıtlarını ayrı olarak önbelleğe alacak şekilde.</span><span class="sxs-lookup"><span data-stu-id="66801-118">Lastly, the cache profile’s `varyByHeader` attribute is set to "Accept", so requests with different Accept header values have their responses cached separately.</span></span>  
  
 <span data-ttu-id="66801-119">İstemci projesindeki program.cs gösterir böyle bir istemci nasıl olabileceğini kullanılarak yazılan <xref:System.Net.HttpWebRequest>.</span><span class="sxs-lookup"><span data-stu-id="66801-119">Program.cs in the Client project demonstrates how such a client can be authored using <xref:System.Net.HttpWebRequest>.</span></span> <span data-ttu-id="66801-120">Bir WCF Hizmeti erişmek için yalnızca bir yol olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="66801-120">Note that this is just one way to access a WCF service.</span></span> <span data-ttu-id="66801-121">WCF kanal fabrikası gibi diğer .NET Framework sınıflarını kullanarak hizmete erişmek mümkündür ve <xref:System.Net.WebClient>.</span><span class="sxs-lookup"><span data-stu-id="66801-121">It is also possible to access the service using other .NET Framework classes like the WCF channel factory and <xref:System.Net.WebClient>.</span></span> <span data-ttu-id="66801-122">SDK diğer örnekleri (gibi [temel HTTP hizmeti](../../../../docs/framework/wcf/samples/basic-http-service.md) örnek) bu sınıfların bir WCF Hizmeti ile iletişim için nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="66801-122">Other samples in the SDK (such as the [Basic HTTP Service](../../../../docs/framework/wcf/samples/basic-http-service.md) sample) illustrate how to use these classes to communicate with a WCF service.</span></span>  
  
## <a name="to-run-the-sample"></a><span data-ttu-id="66801-123">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="66801-123">To run the sample</span></span>  
 <span data-ttu-id="66801-124">Örnek üç projelerin oluşur:</span><span class="sxs-lookup"><span data-stu-id="66801-124">The sample consists of three projects:</span></span>  
  
-   <span data-ttu-id="66801-125">**Hizmet**: ASP.NET'te barındırılan bir WCF HTTP hizmeti içeren bir Web uygulaması projesi.</span><span class="sxs-lookup"><span data-stu-id="66801-125">**Service**: A Web Application project that includes a WCF HTTP service hosted in ASP.NET.</span></span>  
  
-   <span data-ttu-id="66801-126">**İstemci**: Hizmet çağrıları yapan bir konsol uygulama projesi.</span><span class="sxs-lookup"><span data-stu-id="66801-126">**Client**: A console application project that makes calls to the service.</span></span>  
  
-   <span data-ttu-id="66801-127">**Ortak**: İstemci ve hizmet tarafından kullanılan müşteri türü içeren paylaşılan bir kitaplık.</span><span class="sxs-lookup"><span data-stu-id="66801-127">**Common**: A shared library that contains the Customer type used by the client and service.</span></span>  
  
 <span data-ttu-id="66801-128">İstemci konsol uygulaması çalışırken istemci hizmete isteği yapan ve konsol penceresine yanıtlardan bilgileri yazar.</span><span class="sxs-lookup"><span data-stu-id="66801-128">As the Client console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="66801-129">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="66801-129">To run the sample</span></span>  
  
1. <span data-ttu-id="66801-130">ASP.NET önbelleğe alma tümleştirmesi için örnek çözümü açın.</span><span class="sxs-lookup"><span data-stu-id="66801-130">Open the solution for the ASP.NET Caching Integration Sample.</span></span>  
  
2. <span data-ttu-id="66801-131">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="66801-131">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3. <span data-ttu-id="66801-132">Varsa **Çözüm Gezgini** pencere zaten açık değilse, CTRL + W + S tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="66801-132">If the **Solution Explorer** window is not already open, press CTRL+W+S.</span></span>  
  
4. <span data-ttu-id="66801-133">Gelen **Çözüm Gezgini** penceresinde, sağ tıklama **hizmet** seçin ve proje **yeni örnek Başlat**.</span><span class="sxs-lookup"><span data-stu-id="66801-133">From the **Solution Explorer** window, right click the **Service** project and select **Start New Instance**.</span></span> <span data-ttu-id="66801-134">Bu, hizmeti barındıran ASP.NET geliştirme sunucusu başlatır.</span><span class="sxs-lookup"><span data-stu-id="66801-134">This launches the ASP.NET development server, which hosts the service.</span></span>  
  
5. <span data-ttu-id="66801-135">Gelen **Çözüm Gezgini** penceresinde, sağ tıklama **istemci** seçin ve proje **yeni örnek Başlat**.</span><span class="sxs-lookup"><span data-stu-id="66801-135">From the **Solution Explorer** window, right click the **Client** project and select **Start New Instance**.</span></span>  
  
6. <span data-ttu-id="66801-136">İstemci konsol penceresi görünür ve çalışan hizmetin URI sağlar ve URI HTML Yardım sayfası çalışan hizmeti.</span><span class="sxs-lookup"><span data-stu-id="66801-136">The client console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span> <span data-ttu-id="66801-137">Herhangi bir noktada HTML Yardım sayfası URI Yardım sayfasının bir tarayıcıda yazarak görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="66801-137">At any point in time you can view the HTML help page by typing the URI of the help page in a browser.</span></span>  
  
7. <span data-ttu-id="66801-138">Örnek çalışırken, istemcinin geçerli etkinlik durumunu yazar.</span><span class="sxs-lookup"><span data-stu-id="66801-138">As the sample runs, the client writes the status of the current activity.</span></span>  
  
8. <span data-ttu-id="66801-139">İstemci Konsolu uygulamayı sonlandırmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="66801-139">Press any key to terminate the client console application.</span></span>  
  
9. <span data-ttu-id="66801-140">Hizmet hata ayıklamayı durdurmak için SHIFT + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="66801-140">Press SHIFT+F5 to stop debugging the service.</span></span>  
  
10. <span data-ttu-id="66801-141">Windows bildirim alanındaki ASP.NET Geliştirme Sunucusu simgesine sağ tıklayın ve seçin **Durdur**.</span><span class="sxs-lookup"><span data-stu-id="66801-141">In the Windows Notification Area, right click the ASP.NET development server icon and select **Stop**.</span></span>
