---
title: ASP.NET Önbelleğe Alma Tümleştirmesi
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: 56f686b83deb576f1245a9d4b9df2df433ea1e2f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045785"
---
# <a name="aspnet-caching-integration"></a><span data-ttu-id="31243-102">ASP.NET Önbelleğe Alma Tümleştirmesi</span><span class="sxs-lookup"><span data-stu-id="31243-102">ASP.NET Caching Integration</span></span>

<span data-ttu-id="31243-103">Bu örnek, WCF WEB HTTP programlama modeliyle ASP.NET çıktı önbelleğinin nasıl kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="31243-103">This sample demonstrates how to utilize the ASP.NET output cache with the WCF WEB HTTP programming model.</span></span> <span data-ttu-id="31243-104">Bu konu, ASP.NET çıktı önbelleği tümleştirme özelliğine odaklanır.</span><span class="sxs-lookup"><span data-stu-id="31243-104">This topic focuses on the ASP.NET output cache integration feature.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="31243-105">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="31243-105">Demonstrates</span></span>

<span data-ttu-id="31243-106">ASP.NET çıktı önbelleğiyle tümleştirme</span><span class="sxs-lookup"><span data-stu-id="31243-106">Integration with the ASP.NET Output Cache</span></span>

> [!IMPORTANT]
> <span data-ttu-id="31243-107">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="31243-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="31243-108">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="31243-108">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="31243-109">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin.</span><span class="sxs-lookup"><span data-stu-id="31243-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="31243-110">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="31243-110">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`

## <a name="discussion"></a><span data-ttu-id="31243-111">Tartışma</span><span class="sxs-lookup"><span data-stu-id="31243-111">Discussion</span></span>

<span data-ttu-id="31243-112">Örnek, <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> Windows Communication Foundation (WCF) hizmetiyle ASP.net çıktı önbelleği kullanmak için öğesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="31243-112">The sample uses the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> to utilize ASP.NET output caching with the Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="31243-113">, <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> Hizmet işlemlerine uygulanır ve belirli bir işlemden alınan yanıtlara uygulanması gereken bir yapılandırma dosyasında Önbellek profilinin adını sağlar.</span><span class="sxs-lookup"><span data-stu-id="31243-113">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is applied to service operations, and provides the name of a cache profile in a configuration file that should be applied to responses from the given operation.</span></span>

<span data-ttu-id="31243-114">Örnek hizmet projesinin `GetCustomer` Service.cs dosyasında, ve `GetCustomers` <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>işlemleri "CacheFor60Seconds" önbellek profili adını sağlayan ile işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="31243-114">In the Service.cs file of the sample Service project, both the `GetCustomer` and `GetCustomers` operations are marked with the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, which provides the cache profile name "CacheFor60Seconds".</span></span> <span data-ttu-id="31243-115">Hizmet projesinin Web. config dosyasında, "CacheFor60Seconds" önbellek profili <`caching``system.web`> < > öğesi altında sağlanır.</span><span class="sxs-lookup"><span data-stu-id="31243-115">In the Web.config file of the Service project, the cache profile "CacheFor60Seconds" is provided under the <`caching`> element of <`system.web`>.</span></span> <span data-ttu-id="31243-116">Bu önbellek profili için, `duration` öznitelik değeri "60" olur, bu nedenle bu profille ilişkili yanıtlar 60 saniye için ASP.net çıktı önbelleğinde önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="31243-116">For this cache profile, the value of the `duration` attribute is "60", so responses associated with this profile are cached in the ASP.NET output cache for 60 seconds.</span></span> <span data-ttu-id="31243-117">Ayrıca, bu önbellek profili `varmByParam` için öznitelik "biçim" olarak ayarlanır, böylece `format` sorgu dizesi parametresi için farklı değerlere sahip isteklerin yanıtları ayrı olarak önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="31243-117">Also, for this cache profile, the `varmByParam` attribute is set to "format" so requests with different values for the `format` query string parameter have their responses cached separately.</span></span> <span data-ttu-id="31243-118">Son olarak, Önbellek profilinin `varyByHeader` özniteliği "kabul et" olarak ayarlanır; bu nedenle, farklı Accept üst bilgisi değerlerine sahip isteklerin yanıtları ayrı olarak önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="31243-118">Lastly, the cache profile’s `varyByHeader` attribute is set to "Accept", so requests with different Accept header values have their responses cached separately.</span></span>

<span data-ttu-id="31243-119">Istemci projesindeki Program.cs, bu tür bir istemcinin kullanılarak <xref:System.Net.HttpWebRequest>nasıl yazılabilir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="31243-119">Program.cs in the Client project demonstrates how such a client can be authored using <xref:System.Net.HttpWebRequest>.</span></span> <span data-ttu-id="31243-120">Bu, bir WCF hizmetine erişmenin yalnızca bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="31243-120">Note that this is just one way to access a WCF service.</span></span> <span data-ttu-id="31243-121">WCF kanal fabrikası ve <xref:System.Net.WebClient>gibi diğer .NET Framework sınıfları kullanılarak hizmete de erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31243-121">It is also possible to access the service using other .NET Framework classes like the WCF channel factory and <xref:System.Net.WebClient>.</span></span> <span data-ttu-id="31243-122">SDK 'daki diğer örnekler ( [temel http hizmet](../../../../docs/framework/wcf/samples/basic-http-service.md) örneği gibi), bu SıNıFLARıN bir WCF hizmeti ile iletişim kurmak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="31243-122">Other samples in the SDK (such as the [Basic HTTP Service](../../../../docs/framework/wcf/samples/basic-http-service.md) sample) illustrate how to use these classes to communicate with a WCF service.</span></span>

## <a name="to-run-the-sample"></a><span data-ttu-id="31243-123">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="31243-123">To run the sample</span></span>

<span data-ttu-id="31243-124">Örnek üç projeden oluşur:</span><span class="sxs-lookup"><span data-stu-id="31243-124">The sample consists of three projects:</span></span>

- <span data-ttu-id="31243-125">**Hizmet**: ASP.NET içinde barındırılan bir WCF HTTP hizmetini içeren bir Web uygulaması projesi.</span><span class="sxs-lookup"><span data-stu-id="31243-125">**Service**: A Web Application project that includes a WCF HTTP service hosted in ASP.NET.</span></span>

- <span data-ttu-id="31243-126">**İstemci**: Hizmete çağrı yapan bir konsol uygulaması projesi.</span><span class="sxs-lookup"><span data-stu-id="31243-126">**Client**: A console application project that makes calls to the service.</span></span>

- <span data-ttu-id="31243-127">**Ortak**: İstemci ve hizmet tarafından kullanılan müşteri türünü içeren paylaşılan bir kitaplık.</span><span class="sxs-lookup"><span data-stu-id="31243-127">**Common**: A shared library that contains the Customer type used by the client and service.</span></span>

<span data-ttu-id="31243-128">Istemci konsol uygulaması çalışırken, istemci hizmete istekler yapar ve ilgili bilgileri, yanıtlardan konsol penceresine yazar.</span><span class="sxs-lookup"><span data-stu-id="31243-128">As the Client console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>

#### <a name="to-run-the-sample"></a><span data-ttu-id="31243-129">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="31243-129">To run the sample</span></span>

1. <span data-ttu-id="31243-130">ASP.NET önbelleğe alma tümleştirme örneği için çözümü açın.</span><span class="sxs-lookup"><span data-stu-id="31243-130">Open the solution for the ASP.NET Caching Integration Sample.</span></span>

2. <span data-ttu-id="31243-131">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="31243-131">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="31243-132">**Çözüm Gezgini** pencere zaten açık DEĞILSE, CTRL + W + S tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="31243-132">If the **Solution Explorer** window is not already open, press CTRL+W+S.</span></span>

4. <span data-ttu-id="31243-133">**Çözüm Gezgini** penceresinden, **hizmet** projesine sağ tıklayın ve **Yeni örnek Başlat**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="31243-133">From the **Solution Explorer** window, right click the **Service** project and select **Start New Instance**.</span></span> <span data-ttu-id="31243-134">Bu, hizmeti barındıran ASP.NET geliştirme sunucusunu başlatır.</span><span class="sxs-lookup"><span data-stu-id="31243-134">This launches the ASP.NET development server, which hosts the service.</span></span>

5. <span data-ttu-id="31243-135">**Çözüm Gezgini** penceresinden, **istemci** projesine sağ tıklayın ve **Yeni örnek Başlat**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="31243-135">From the **Solution Explorer** window, right click the **Client** project and select **Start New Instance**.</span></span>

6. <span data-ttu-id="31243-136">İstemci Konsolu penceresi görünür ve çalışan hizmetin URI 'sini ve çalışan hizmet için HTML yardım sayfasının URI 'sini sağlar.</span><span class="sxs-lookup"><span data-stu-id="31243-136">The client console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span> <span data-ttu-id="31243-137">Herhangi bir noktada, yardım sayfasının URI 'sini bir tarayıcıda yazarak HTML yardım sayfasını görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="31243-137">At any point in time you can view the HTML help page by typing the URI of the help page in a browser.</span></span>

7. <span data-ttu-id="31243-138">Örnek çalışırken, istemci geçerli etkinliğin durumunu yazar.</span><span class="sxs-lookup"><span data-stu-id="31243-138">As the sample runs, the client writes the status of the current activity.</span></span>

8. <span data-ttu-id="31243-139">İstemci konsol uygulamasını sonlandırmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="31243-139">Press any key to terminate the client console application.</span></span>

9. <span data-ttu-id="31243-140">Hizmetin hata ayıklamasını durdurmak için SHIFT + F5 tuşlarına basın.</span><span class="sxs-lookup"><span data-stu-id="31243-140">Press SHIFT+F5 to stop debugging the service.</span></span>

10. <span data-ttu-id="31243-141">Windows bildirim alanında, ASP.NET Development Server simgesine sağ tıklayın ve **Durdur**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="31243-141">In the Windows Notification Area, right click the ASP.NET development server icon and select **Stop**.</span></span>
