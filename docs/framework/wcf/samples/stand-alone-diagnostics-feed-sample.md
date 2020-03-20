---
title: Bağımsız Tanılama Akış Örneği
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: 29d8caee48925040db9f1812f015870e3a1272bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144012"
---
# <a name="stand-alone-diagnostics-feed-sample"></a><span data-ttu-id="e8437-102">Bağımsız Tanılama Akış Örneği</span><span class="sxs-lookup"><span data-stu-id="e8437-102">Stand-Alone Diagnostics Feed Sample</span></span>
<span data-ttu-id="e8437-103">Bu örnek, Windows Communication Foundation (WCF) ile sendikasyon için bir RSS/Atom beslemesi oluşturmanın nasıl olduğunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="e8437-103">This sample demonstrates how to create an RSS/Atom feed for syndication with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="e8437-104">Nesne modelinin temellerini ve windows communication foundation (WCF) hizmetinde nasıl kurulabildiğini gösteren temel bir "Hello World" programıdır.</span><span class="sxs-lookup"><span data-stu-id="e8437-104">It is a basic "Hello World" program that shows the basics of the object model and how to set it up on a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="e8437-105">WCF modelleri sendikasyon akışları özel bir veri türünü <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>döndüren hizmet işlemleri olarak, .</span><span class="sxs-lookup"><span data-stu-id="e8437-105">WCF models syndication feeds as service operations that return a special data type, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="e8437-106">RsS <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> 2.0 ve Atom 1.0 biçimlerine bir akışı serihale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8437-106">Instances of <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> can serialize a feed into both the RSS 2.0 and Atom 1.0 formats.</span></span> <span data-ttu-id="e8437-107">Aşağıdaki örnek kod, kullanılan sözleşmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8437-107">The following sample code shows the contract used.</span></span>  
  
```csharp  
[ServiceContract(Namespace = "")]  
    interface IDiagnosticsService  
    {  
        [OperationContract]  
        //The [WebGet] attribute controls how WCF dispatches  
        //HTTP requests to service operations based on a URI suffix  
        //(the part of the request URI after the endpoint address)  
        //using the HTTP GET method. The UriTemplate specifies a relative  
        //path of 'feed', and specifies that the format is  
        //supplied using a query string.
        [WebGet(UriTemplate="feed?format={format}")]  
        [ServiceKnownType(typeof(Atom10FeedFormatter))]  
        [ServiceKnownType(typeof(Rss20FeedFormatter))]  
        SyndicationFeedFormatter GetProcesses(string format);  
    }  
```  
  
 <span data-ttu-id="e8437-108">İşlem, `GetProcesses` WCF'nin http <xref:System.ServiceModel.Web.WebGetAttribute> GET isteklerini hizmet işlemlerine nasıl gönderdiğini denetlemenize ve gönderilen iletilerin biçimini belirtmenize olanak tanıyan öznitelikle açıklamalı olarak açıklanır.</span><span class="sxs-lookup"><span data-stu-id="e8437-108">The `GetProcesses` operation is annotated with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute that enables you to control how WCF dispatches HTTP GET requests to service operations and specify the format of the messages sent.</span></span>  
  
 <span data-ttu-id="e8437-109">Herhangi bir WCF hizmeti gibi, sendikasyon akışları da yönetilen herhangi bir uygulamada kendi kendine barındırılabilir.</span><span class="sxs-lookup"><span data-stu-id="e8437-109">Like any WCF service, syndication feeds can be self hosted in any managed application.</span></span> <span data-ttu-id="e8437-110">Sendikasyon hizmetleri, düzgün çalışması <xref:System.ServiceModel.WebHttpBinding>için belirli bir bağlama (the) ve belirli bir bitiş noktası davranışı (the) <xref:System.ServiceModel.Description.WebHttpBehavior>gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e8437-110">Syndication services require a specific binding (the <xref:System.ServiceModel.WebHttpBinding>) and a specific endpoint behavior (the <xref:System.ServiceModel.Description.WebHttpBehavior>) to function correctly.</span></span> <span data-ttu-id="e8437-111">Yeni <xref:System.ServiceModel.Web.WebServiceHost> sınıf, belirli yapılandırma olmadan bu tür uç noktaları oluşturmak için kullanışlı bir API sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8437-111">The new <xref:System.ServiceModel.Web.WebServiceHost> class provides a convenient API for creating such endpoints without specific configuration.</span></span>  
  
```csharp  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 <span data-ttu-id="e8437-112">Alternatif olarak, eşdeğer <xref:System.ServiceModel.Activation.WebServiceHostFactory> işlevsellik sağlamak için IIS tarafından barındırılan .svc dosyasının içinden kullanabilirsiniz (bu teknik bu örnek kodda gösterilmez).</span><span class="sxs-lookup"><span data-stu-id="e8437-112">Alternatively, you can use <xref:System.ServiceModel.Activation.WebServiceHostFactory> from within an IIS-hosted .svc file to provide equivalent functionality (this technique is not demonstrated in this sample code).</span></span>  
  
```xml
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>
```
  
 <span data-ttu-id="e8437-113">Bu hizmet, HTTP GET standardını kullanarak istek aldığından, hizmete erişmek için herhangi bir RSS veya ATOM'a duyarlı istemcik kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8437-113">Because this service receives requests using the standard HTTP GET, you can use any RSS or ATOM-aware client to access the service.</span></span> <span data-ttu-id="e8437-114">Örneğin, RSS'ye duyarlı bir tarayıcıda `http://localhost:8000/diagnostics/feed/?format=atom` veya `http://localhost:8000/diagnostics/feed/?format=rss` bu hizmetin çıktısını görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8437-114">For example, you can view the output of this service by navigating to `http://localhost:8000/diagnostics/feed/?format=atom` or `http://localhost:8000/diagnostics/feed/?format=rss` in an RSS-aware browser.</span></span>
  
 <span data-ttu-id="e8437-115">Ayrıca, sendikasyon verilerini okumak ve zorunlu kodu kullanarak işlemek [için WCF Sendikasyon Nesnesi Model Eşlerini Atom ve RSS'ye nasıl](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e8437-115">You can also use the [How the WCF Syndication Object Model Maps to Atom and RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) to read syndicated data and process it using imperative code.</span></span>  
  
```csharp
XmlReader reader = XmlReader.Create( "http://localhost:8000/diagnostics/feed/?format=rss",
    new XmlReaderSettings()
    {
        //MaxCharactersInDocument can be used to control the maximum amount of data
        //read from the reader and helps prevent OutOfMemoryException
        MaxCharactersInDocument = 1024 * 64
    } );

SyndicationFeed feed = SyndicationFeed.Load(reader);

foreach (SyndicationItem i in feed.Items)
{
    XmlSyndicationContent content = i.Content as XmlSyndicationContent;
    ProcessData pd = content.ReadContent<ProcessData>();

    Console.WriteLine(i.Title.Text);
    Console.WriteLine(pd.ToString());
}
```
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="e8437-116">Örneği ayarlama, oluşturma ve çalıştırma</span><span class="sxs-lookup"><span data-stu-id="e8437-116">Set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="e8437-117">Windows Communication Foundation Samples için [Tek Seferlik Kurulum Prosedürü'nde](one-time-setup-procedure-for-the-wcf-samples.md)belirtilen şekilde bilgisayarda HTTP ve HTTPS için doğru adres kayıt iznine sahip olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e8437-117">Ensure that you have the right address registration permission for HTTP and HTTPS on the computer as explained in the set up instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="e8437-118">Çözümü derleyin.</span><span class="sxs-lookup"><span data-stu-id="e8437-118">Build the solution.</span></span>

3. <span data-ttu-id="e8437-119">Konsol uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e8437-119">Run the console application.</span></span>

4. <span data-ttu-id="e8437-120">Konsol uygulaması çalışırken, RSS'ye duyarlı bir tarayıcıya `http://localhost:8000/diagnostics/feed/?format=atom` gidin veya `http://localhost:8000/diagnostics/feed/?format=rss` bu tarayıcıyı kullanarak gidin.</span><span class="sxs-lookup"><span data-stu-id="e8437-120">While the console application is running, navigate to `http://localhost:8000/diagnostics/feed/?format=atom` or `http://localhost:8000/diagnostics/feed/?format=rss` using an RSS-aware browser.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e8437-121">Örnekler bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="e8437-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e8437-122">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="e8437-122">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="e8437-123">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="e8437-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e8437-124">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="e8437-124">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`

## <a name="see-also"></a><span data-ttu-id="e8437-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8437-125">See also</span></span>

- [<span data-ttu-id="e8437-126">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="e8437-126">WCF Web HTTP Programming Model</span></span>](../feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="e8437-127">WCF Dağıtımı</span><span class="sxs-lookup"><span data-stu-id="e8437-127">WCF Syndication</span></span>](../feature-details/wcf-syndication.md)
