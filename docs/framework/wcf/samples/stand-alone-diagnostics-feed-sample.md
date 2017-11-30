---
title: "Bağımsız Tanılama Akış Örneği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c95a2e1e1790633df77e7c4ecd6603e68321e478
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="stand-alone-diagnostics-feed-sample"></a><span data-ttu-id="99dd5-102">Bağımsız Tanılama Akış Örneği</span><span class="sxs-lookup"><span data-stu-id="99dd5-102">Stand-Alone Diagnostics Feed Sample</span></span>
<span data-ttu-id="99dd5-103">Bu örnek nasıl ile dağıtım için akış RSS/Atom oluşturulduğunu gösteren [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="99dd5-103">This sample demonstrates how to create an RSS/Atom feed for syndication with [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="99dd5-104">Nesne modeli ve üzerinde ayarlamak nasıl temelleri gösterilmektedir temel bir "Hello World" programı olan bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="99dd5-104">It is a basic "Hello World" program that shows the basics of the object model and how to set it up on a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="99dd5-105">bir özel veri türü döndüren hizmet işlemleri dağıtım akışlarını modeller <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span><span class="sxs-lookup"><span data-stu-id="99dd5-105"> models syndication feeds as service operations that return a special data type, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="99dd5-106">Örneklerini <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> RSS 2.0 ve Atom 1.0 biçimleri akışa seri hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="99dd5-106">Instances of <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> can serialize a feed into both the RSS 2.0 and Atom 1.0 formats.</span></span> <span data-ttu-id="99dd5-107">Aşağıdaki örnek kod kullanılan sözleşme gösterir.</span><span class="sxs-lookup"><span data-stu-id="99dd5-107">The following sample code shows the contract used.</span></span>  
  
```  
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
  
 <span data-ttu-id="99dd5-108">`GetProcesses` İşlemi açıklama ile <xref:System.ServiceModel.Web.WebGetAttribute> denetimine nasıl sağlayan öznitelik [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] işlemleri hizmet ve gönderilen iletileri biçimini belirtmek için HTTP GET istekleri gönderir.</span><span class="sxs-lookup"><span data-stu-id="99dd5-108">The `GetProcesses` operation is annotated with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute that enables you to control how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dispatches HTTP GET requests to service operations and specify the format of the messages sent.</span></span>  
  
 <span data-ttu-id="99dd5-109">Gibi herhangi bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti, dağıtım akışlarını olabilir kendi kendine yönetilen bir uygulamada barındırılan.</span><span class="sxs-lookup"><span data-stu-id="99dd5-109">Like any [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, syndication feeds can be self hosted in any managed application.</span></span> <span data-ttu-id="99dd5-110">Dağıtım Hizmetleri gerektiren belirli bir bağlama ( <xref:System.ServiceModel.WebHttpBinding>) ve belirli uç noktası davranışı ( <xref:System.ServiceModel.Description.WebHttpBehavior>) düzgün çalışabilmesi için.</span><span class="sxs-lookup"><span data-stu-id="99dd5-110">Syndication services require a specific binding (the <xref:System.ServiceModel.WebHttpBinding>) and a specific endpoint behavior (the <xref:System.ServiceModel.Description.WebHttpBehavior>) to function correctly.</span></span> <span data-ttu-id="99dd5-111">Yeni <xref:System.ServiceModel.Web.WebServiceHost> sınıfı, belirli bir yapılandırma olmadan böyle uç noktaları oluşturmak için uygun bir API sağlar.</span><span class="sxs-lookup"><span data-stu-id="99dd5-111">The new <xref:System.ServiceModel.Web.WebServiceHost> class provides a convenient API for creating such endpoints without specific configuration.</span></span>  
  
```  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 <span data-ttu-id="99dd5-112">Alternatif olarak, kullanabileceğiniz <xref:System.ServiceModel.Activation.WebServiceHostFactory> gelen (Bu teknik Bu örnek kodda değil de gösterilmiştir) eşdeğer işlevselliği sağlamak için IIS tarafından barındırılan .svc dosyası içinde.</span><span class="sxs-lookup"><span data-stu-id="99dd5-112">Alternatively, you can use <xref:System.ServiceModel.Activation.WebServiceHostFactory> from within an IIS-hosted .svc file to provide equivalent functionality (this technique is not demonstrated in this sample code).</span></span>  
  
```  
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>  
```  
  
 <span data-ttu-id="99dd5-113">Bu hizmeti kullanan standart HTTP GET istekleri aldığından, hizmete erişmek için herhangi bir RSS veya ATOM algılayan İstemcisi'ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99dd5-113">Because this service receives requests using the standard HTTP GET, you can use any RSS or ATOM-aware client to access the service.</span></span> <span data-ttu-id="99dd5-114">Örneğin, bu hizmet çıktısını tanılama/8000/akışı giderek görüntüleyebileceğiniz /? biçimi atom veya tanılama/8000/akışı = /? biçimi = Internet Explorer 7 gibi RSS uyumlu bir tarayıcıda rss.</span><span class="sxs-lookup"><span data-stu-id="99dd5-114">For example, you can view the output of this service by navigating to http://localhost:8000/diagnostics/feed/?format=atom or http://localhost:8000/diagnostics/feed/?format=rss in an RSS-aware browser such as Internet Explorer 7.</span></span>  
  
 <span data-ttu-id="99dd5-115">Aynı zamanda [nasıl WCF dağıtım nesnesi modeli eşlemeleri Atom ve RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) Dağıtılmış veri okumak ve kesinlik temelli kodu kullanarak işlemek için.</span><span class="sxs-lookup"><span data-stu-id="99dd5-115">You can also use the [How the WCF Syndication Object Model Maps to Atom and RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) to read syndicated data and process it using imperative code.</span></span>  
  
```  
XmlReader reader = XmlReader.Create( "http://localhost:8000/diagnostics/feed/?format=rss",  
new XmlReaderSettings()  
{  
//MaxCharactersInDocument can be used to control the maximum amount of data   
//read from the reader and helps prevent OutOfMemoryException  
MaxCharactersInDocument = 1024 * 64  
} );  
  
SyndicationFeed feed = SyndicationFeed.Load( reader );  
  
foreach (SyndicationItem i in feed.Items)  
{  
        XmlSyndicationContent content = i.Content as XmlSyndicationContent;  
        ProcessData pd = content.ReadContent<ProcessData>();  
  
        Console.WriteLine(i.Title.Text);  
        Console.WriteLine(pd.ToString());  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="99dd5-116">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="99dd5-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="99dd5-117">' Ndaki yönergeleri ayarlama açıklandığı gibi bilgisayarı HTTP ve HTTPS için doğru adres kayıt izni olduğundan emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="99dd5-117">Ensure that you have the right address registration permission for HTTP and HTTPS on the computer as explained in the set up instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="99dd5-118">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="99dd5-118">Build the solution.</span></span>  
  
3.  <span data-ttu-id="99dd5-119">Konsol uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="99dd5-119">Run the console application.</span></span>  
  
4.  <span data-ttu-id="99dd5-120">Konsol uygulaması çalışırken, tanılama/8000/akışı gidin /? biçimi atom veya tanılama/8000/akışı = /? format = RSS uyumlu bir tarayıcı kullanarak rss.</span><span class="sxs-lookup"><span data-stu-id="99dd5-120">While the console application is running, navigate to http://localhost:8000/diagnostics/feed/?format=atom or http://localhost:8000/diagnostics/feed/?format=rss using an RSS-aware browser.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="99dd5-121">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="99dd5-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="99dd5-122">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="99dd5-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="99dd5-123">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="99dd5-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="99dd5-124">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="99dd5-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`  
  
## <a name="see-also"></a><span data-ttu-id="99dd5-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="99dd5-125">See Also</span></span>  
 [<span data-ttu-id="99dd5-126">WCF Web HTTP programlama modeli</span><span class="sxs-lookup"><span data-stu-id="99dd5-126">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="99dd5-127">WCF dağıtımı</span><span class="sxs-lookup"><span data-stu-id="99dd5-127">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
