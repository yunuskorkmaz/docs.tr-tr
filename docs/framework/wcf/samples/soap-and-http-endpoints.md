---
title: "SOAP ve HTTP Uç Noktaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9404d304302360b2be590c814d1f94cb46bd5f84
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="soap-and-http-endpoints"></a><span data-ttu-id="79ba7-102">SOAP ve HTTP Uç Noktaları</span><span class="sxs-lookup"><span data-stu-id="79ba7-102">SOAP and HTTP Endpoints</span></span>
<span data-ttu-id="79ba7-103">Bu örnek, RPC tabanlı bir hizmete uygulamak ve SOAP biçiminde kullanıma sunmak gösterilmiştir ve "düz eski XML" (POX) biçimlendirme kullanarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web programlama modeli.</span><span class="sxs-lookup"><span data-stu-id="79ba7-103">This sample demonstrates how to implement an RPC-based service and expose it in the SOAP format and the "Plain Old XML" (POX) format using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web Programming model.</span></span> <span data-ttu-id="79ba7-104">Bkz: [temel HTTP hizmeti](../../../../docs/framework/wcf/samples/basic-http-service.md) hizmeti için HTTP bağlama hakkında daha fazla ayrıntı için örnek.</span><span class="sxs-lookup"><span data-stu-id="79ba7-104">See the [Basic HTTP Service](../../../../docs/framework/wcf/samples/basic-http-service.md) sample for more details about the HTTP binding for the service.</span></span> <span data-ttu-id="79ba7-105">Bu örnek SOAP ve farklı bağlamalar kullanılarak HTTP üzerinden aynı hizmeti gösterme ilgilidir ayrıntıları odaklanır.</span><span class="sxs-lookup"><span data-stu-id="79ba7-105">This sample focuses on the details that pertain to exposing the same service over SOAP and HTTP using different bindings.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="79ba7-106">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="79ba7-106">Demonstrates</span></span>  
 <span data-ttu-id="79ba7-107">SOAP ve HTTP üzerinden RPC hizmeti gösterme kullanarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="79ba7-107">Exposing an RPC service over SOAP and HTTP using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="79ba7-108">Tartışma</span><span class="sxs-lookup"><span data-stu-id="79ba7-108">Discussion</span></span>  
 <span data-ttu-id="79ba7-109">Bu örnek iki bileşenden oluşur: içeren bir Web uygulaması projesi (hizmeti) bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti ve SOAP ve HTTP bağlantılarını kullanarak hizmet işlemlerini çağıran bir konsol uygulaması (istemci).</span><span class="sxs-lookup"><span data-stu-id="79ba7-109">This sample consists of two components: a Web Application project (Service) that contains a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service and a console application (Client) that invokes service operations using SOAP and HTTP bindings.</span></span>  
  
 <span data-ttu-id="79ba7-110">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Hizmet sunan 2 operations –`GetData` ve `PutData` – giriş olarak geçirilen dize echo.</span><span class="sxs-lookup"><span data-stu-id="79ba7-110">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service exposes 2 operations –`GetData` and `PutData` – that echo the string that was passed as input.</span></span> <span data-ttu-id="79ba7-111">Hizmet işlemleri ile Açıklama <xref:System.ServiceModel.Web.WebGetAttribute> ve <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="79ba7-111">The service operations are annotated with <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="79ba7-112">Bu öznitelikler, bu işlemlerin HTTP projeksiyon denetler.</span><span class="sxs-lookup"><span data-stu-id="79ba7-112">These attributes control the HTTP projection of these operations.</span></span> <span data-ttu-id="79ba7-113">İle ek olarak, açıklama <xref:System.ServiceModel.OperationContractAttribute>, bunları SOAP bağlamaları açığa çıkarılması sağlar.</span><span class="sxs-lookup"><span data-stu-id="79ba7-113">In addition, they are annotated with <xref:System.ServiceModel.OperationContractAttribute>, which enables them to be exposed over SOAP bindings.</span></span> <span data-ttu-id="79ba7-114">Hizmetin `PutData` yöntemi atar bir <xref:System.ServiceModel.Web.WebFaultException>, geri HTTP durum kodu kullanarak HTTP üzerinden gönderilir ve bir SOAP hatası olarak SOAP üzerinden geri gönderilir.</span><span class="sxs-lookup"><span data-stu-id="79ba7-114">The service’s `PutData` method throws a <xref:System.ServiceModel.Web.WebFaultException>, which gets sent back over HTTP using the HTTP status code and gets sent back over SOAP as a SOAP fault.</span></span>  
  
 <span data-ttu-id="79ba7-115">Web.config dosyasını yapılandırır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti 3 uç noktaları ile:</span><span class="sxs-lookup"><span data-stu-id="79ba7-115">The Web.config file configures the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service with 3 endpoints:</span></span>  
  
-   <span data-ttu-id="79ba7-116">SOAP tabanlı istemcilerine erişmek için hizmet meta verilerini kullanıma sunan ~/service.svc/mex uç noktası.</span><span class="sxs-lookup"><span data-stu-id="79ba7-116">The ~/service.svc/mex endpoint that exposes the service metadata for access by SOAP-based clients.</span></span>  
  
-   <span data-ttu-id="79ba7-117">İstemcilerin HTTP bağlama kullanarak hizmet erişmesine olanak sağlayan ~/service.svc/http uç noktası.</span><span class="sxs-lookup"><span data-stu-id="79ba7-117">The ~/service.svc/http endpoint that enables clients to access the service using the HTTP binding.</span></span>  
  
-   <span data-ttu-id="79ba7-118">SOAP üzerinden HTTP bağlama kullanarak hizmete erişmek istemcilerin ~/service.svc/soap uç noktası.</span><span class="sxs-lookup"><span data-stu-id="79ba7-118">The ~/service.svc/soap endpoint that allows the clients to access the service using the SOAP over HTTP binding.</span></span>  
  
 <span data-ttu-id="79ba7-119">HTTP uç noktası ile yapılandırılmış bir <`webHttp`> olan standart endpoint `helpEnabled` kümesine `true`.</span><span class="sxs-lookup"><span data-stu-id="79ba7-119">The HTTP endpoint is configured with a <`webHttp`> standard endpoint which has `helpEnabled` set to `true`.</span></span> <span data-ttu-id="79ba7-120">Sonuç olarak, hizmet istemcilerin HTTP tabanlı hizmete erişmek için kullanabileceği ~/service.svc/http/help bir temel XHTML yardım sayfasına kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="79ba7-120">As a result, the service exposes an XHTML based help page at ~/service.svc/http/help that HTTP-based clients can use to access the service.</span></span>  
  
 <span data-ttu-id="79ba7-121">Hizmeti bir SOAP proxy kullanarak erişen istemci projesi gösterir (aracılığıyla oluşturulan **hizmet Başvurusu Ekle**) ve hizmet kullanarak erişme <xref:System.Net.WebClient>.</span><span class="sxs-lookup"><span data-stu-id="79ba7-121">The client project demonstrates accessing the service using a SOAP proxy (generated through **Add Service Reference**) and accessing the service using <xref:System.Net.WebClient>.</span></span>  
  
 <span data-ttu-id="79ba7-122">Örnek bir Web barındırılan hizmeti ve bir konsol uygulaması oluşur.</span><span class="sxs-lookup"><span data-stu-id="79ba7-122">The sample consists of a Web-hosted service and a console application.</span></span> <span data-ttu-id="79ba7-123">Konsol uygulaması çalışırken, istemci hizmete istek yaptığında ve konsol penceresine yanıtlardan bilgileri yazar.</span><span class="sxs-lookup"><span data-stu-id="79ba7-123">As the console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="79ba7-124">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="79ba7-124">To run the sample</span></span>  
  
1.  <span data-ttu-id="79ba7-125">Çözüm SOAP ve HTTP uç noktaları örnek için açın.</span><span class="sxs-lookup"><span data-stu-id="79ba7-125">Open the solution for the SOAP and HTTP Endpoints Sample.</span></span>  
  
2.  <span data-ttu-id="79ba7-126">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="79ba7-126">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="79ba7-127">Zaten açık değilse, CTRL + W, açmak için S tuşlarına basın **Çözüm Gezgini** penceresi.</span><span class="sxs-lookup"><span data-stu-id="79ba7-127">If it is not already open, press CTRL+W, S to open the **Solution Explorer** window.</span></span>  
  
4.  <span data-ttu-id="79ba7-128">Gelen **Çözüm Gezgini** penceresinde sağ **hizmet** proje ve imleci üzerine getirin **hata ayıklama** bağlam menüsü seçeneğini böylece **Başlat yeni Örnek** bağlam menüsü görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="79ba7-128">From the **Solution Explorer** window, right-click the **Service** project and place the cursor over the **Debug** context menu option so that the **Start New Instance** context menu appears.</span></span> <span data-ttu-id="79ba7-129">Tıklatın **Başlat yeni örnek**.</span><span class="sxs-lookup"><span data-stu-id="79ba7-129">Click **Start New Instance**.</span></span> <span data-ttu-id="79ba7-130">Bu hizmeti barındıran ASP.NET geliştirme sunucusu başlatır.</span><span class="sxs-lookup"><span data-stu-id="79ba7-130">This launches the ASP.NET development server, which hosts the service.</span></span>  
  
5.  <span data-ttu-id="79ba7-131">Çözüm Gezgini Windows istemci projesine sağ tıklayın ve imleci üzerine getirin **hata ayıklama** bağlam menüsü seçeneğini böylece **Başlat yeni örnek** bağlam menüsü görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="79ba7-131">From the Solution Explorer windows, right-click the Client project and place the cursor over the **Debug** context menu option so that the **Start New Instance** context menu appears.</span></span> <span data-ttu-id="79ba7-132">Tıklatın **Başlat yeni örnek**.</span><span class="sxs-lookup"><span data-stu-id="79ba7-132">Click **Start New Instance**.</span></span>  
  
6.  <span data-ttu-id="79ba7-133">İstemci konsol penceresi görüntülenir ve çalışan hizmetin URI sağlar ve URI HTML sayfası çalışan hizmetin için yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="79ba7-133">The client console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span> <span data-ttu-id="79ba7-134">Herhangi bir noktada, HTML Yardım sayfasına bir tarayıcıda yardım sayfasına URI'sini yazarak görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="79ba7-134">At any point in time you can view the HTML help page by typing the URI of the help page in a browser.</span></span>  
  
7.  <span data-ttu-id="79ba7-135">Örnek çalışırken, istemcinin geçerli etkinlik durumunu yazar.</span><span class="sxs-lookup"><span data-stu-id="79ba7-135">As the sample runs, the client writes the status of the current activity.</span></span>  
  
8.  <span data-ttu-id="79ba7-136">İstemci konsol uygulaması sonlandırmak için herhangi bir tuşa basın.</span><span class="sxs-lookup"><span data-stu-id="79ba7-136">Press any key to terminate the client console application.</span></span>  
  
9. <span data-ttu-id="79ba7-137">Hata ayıklama hizmetini durdurmak için SHIFT + F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="79ba7-137">Press SHIFT+F5 to stop debugging the service.</span></span>  
  
10. <span data-ttu-id="79ba7-138">Windows bildirim alanında ASP.NET Geliştirme Sunucusu simgesini sağ tıklatın ve seçin **durdurmak** ve bağlam menüsünden.</span><span class="sxs-lookup"><span data-stu-id="79ba7-138">In the Windows Notification Area, right-click the ASP.NET development server icon and select **Stop** from the context menu.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="79ba7-139">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="79ba7-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="79ba7-140">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="79ba7-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="79ba7-141">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="79ba7-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="79ba7-142">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="79ba7-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
