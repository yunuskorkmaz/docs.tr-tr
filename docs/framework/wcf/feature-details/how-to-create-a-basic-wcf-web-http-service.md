---
title: "Nasıl yapılır: Temel Bir WCF Web HTTP Hizmeti Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 877662d3-d372-4e08-b417-51f66a0095cd
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4dc60bbb51bc573840d0d45356f0cd84fd32db2a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-basic-wcf-web-http-service"></a><span data-ttu-id="42365-102">Nasıl yapılır: Temel Bir WCF Web HTTP Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="42365-102">How to: Create a Basic WCF Web HTTP Service</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="42365-103">bir Web uç noktası kullanıma sunan bir hizmet oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="42365-103"> allows you to create a service that exposes a Web endpoint.</span></span> <span data-ttu-id="42365-104">Web uç noktaları XML veya JSON veri gönderme, SOAP Zarfı.</span><span class="sxs-lookup"><span data-stu-id="42365-104">Web endpoints send data by XML or JSON, there is no SOAP envelope.</span></span> <span data-ttu-id="42365-105">Bu konu, bu tür bir uç nokta kullanıma gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="42365-105">This topic demonstrates how to expose such an endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42365-106">Taşıma güvenliği kullanarak, HTTPS kullanıma sunmak için yalnızca bir Web uç noktası güvenli şekilde denetleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42365-106">The only way to secure a Web endpoint is to expose it through HTTPS, using transport security.</span></span> <span data-ttu-id="42365-107">İleti tabanlı güvenlik kullanırken, güvenlik bilgileri genellikle SOAP üstbilgileri yerleştirilir ve gönderilen iletiler için hiç SOAP Zarfı olmayan SOAP uç noktaları içeren, saklanıyorsa güvenlik bilgilerini yerleştirmek için yoktur ve aktarım güvenliğe güvenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="42365-107">When using message-based security, security information is usually placed in SOAP headers and because the messages sent to non-SOAP endpoints contain no SOAP envelope, there is nowhere to place the security information and you must rely on transport security.</span></span>  
  
### <a name="to-create-a-web-endpoint"></a><span data-ttu-id="42365-108">Bir Web uç noktası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="42365-108">To create a Web endpoint</span></span>  
  
1.  <span data-ttu-id="42365-109">İle işaretlenen arabirimini kullanarak bir hizmet sözleşmesini tanımlayan <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> ve <xref:System.ServiceModel.Web.WebGetAttribute> öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="42365-109">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> and the <xref:System.ServiceModel.Web.WebGetAttribute> attributes.</span></span>  
  
     [!code-csharp[htBasicService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#0)]
     [!code-vb[htBasicService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="42365-110">Varsayılan olarak, <xref:System.ServiceModel.Web.WebInvokeAttribute> işlemi POST çağrıları eşler.</span><span class="sxs-lookup"><span data-stu-id="42365-110">By default, <xref:System.ServiceModel.Web.WebInvokeAttribute> maps POST calls to the operation.</span></span> <span data-ttu-id="42365-111">Bununla birlikte, çalışması için belirterek eşleştirmek için HTTP yöntemini (örneğin, HEAD, PUT veya Sil) belirleyebilirsiniz bir "yöntemi =" parametresi.</span><span class="sxs-lookup"><span data-stu-id="42365-111">You can, however, specify the HTTP method (for example, HEAD, PUT, or DELETE) to map to the operation by specifying a "method=" parameter.</span></span> <span data-ttu-id="42365-112"><xref:System.ServiceModel.Web.WebGetAttribute>sahip olmayan bir "yöntemi =" GET parametre ve yalnızca eşlemeleri hizmet işlemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="42365-112"><xref:System.ServiceModel.Web.WebGetAttribute> does not have a "method=" parameter and only maps GET calls to the service operation.</span></span>  
  
2.  <span data-ttu-id="42365-113">Hizmet sözleşmesini uygulama.</span><span class="sxs-lookup"><span data-stu-id="42365-113">Implement the service contract.</span></span>  
  
     [!code-csharp[htBasicService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#1)]
     [!code-vb[htBasicService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#1)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="42365-114">Ana bilgisayar hizmeti</span><span class="sxs-lookup"><span data-stu-id="42365-114">To host the service</span></span>  
  
1.  <span data-ttu-id="42365-115">Oluşturma bir <xref:System.ServiceModel.Web.WebServiceHost> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="42365-115">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>  
  
     [!code-csharp[htBasicService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#2)]
     [!code-vb[htBasicService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#2)]  
  
2.  <span data-ttu-id="42365-116">Ekleme bir <xref:System.ServiceModel.Description.ServiceEndpoint> ile <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="42365-116">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
     [!code-csharp[htBasicService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#3)]
     [!code-vb[htBasicService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#3)]  
  
    > [!NOTE]
    >  <span data-ttu-id="42365-117">Bir uç nokta eklemezseniz <xref:System.ServiceModel.Web.WebServiceHost> otomatik olarak varsayılan uç noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="42365-117">If you do not add an endpoint, <xref:System.ServiceModel.Web.WebServiceHost> automatically creates a default endpoint.</span></span> <span data-ttu-id="42365-118"><xref:System.ServiceModel.Web.WebServiceHost>Ayrıca ekler <xref:System.ServiceModel.Description.WebHttpBehavior> ve meta veri uç noktasının varsayılan HTTP uç noktası ile etkilemediğinden için HTTP yardım sayfasına ve Web Hizmetleri Açıklama Dili (WSDL) alma işlevini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="42365-118"><xref:System.ServiceModel.Web.WebServiceHost> also adds <xref:System.ServiceModel.Description.WebHttpBehavior> and disables the HTTP Help page and the Web Services Description Language (WSDL) GET functionality so the metadata endpoint does not interfere with the default HTTP endpoint.</span></span>  
    >   
    >  <span data-ttu-id="42365-119">SOAP olmayan uç nokta URL'si ile ekleme "" uç nokta üzerinde bir işlemi çağırmak için bir girişimde beklenmeyen davranışlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="42365-119">Adding a non-SOAP endpoint with a URL of "" causes unexpected behavior when an attempt is made to call an operation on the endpoint.</span></span> <span data-ttu-id="42365-120">Bu uç nokta URI'sini dinleme aynıdır yardım sayfasına URI'sini nedeni (temel adresine göz atarken görüntülenen sayfa bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti).</span><span class="sxs-lookup"><span data-stu-id="42365-120">The reason for this is the listen URI of the endpoint is the same as the URI for the help page (the page that is displayed when you browse to the base address of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service).</span></span>  
  
     <span data-ttu-id="42365-121">Bunun olmaması için aşağıdaki işlemlerden birini yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="42365-121">You can do one of the following actions to prevent this from happening:</span></span>  
  
    -   <span data-ttu-id="42365-122">Her zaman bir SOAP olmayan uç noktası için boş olmayan URI belirtin.</span><span class="sxs-lookup"><span data-stu-id="42365-122">Always specify a non-blank URI for a non-SOAP endpoint.</span></span>  
  
    -   <span data-ttu-id="42365-123">Yardım sayfasını kapat.</span><span class="sxs-lookup"><span data-stu-id="42365-123">Turn off the help page.</span></span> <span data-ttu-id="42365-124">Bu, aşağıdaki kod ile yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="42365-124">This can be done with the following code.</span></span>  
  
     [!code-csharp[htBasicService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#4)]
     [!code-vb[htBasicService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#4)]  
  
3.  <span data-ttu-id="42365-125">Hizmet ana bilgisayarı'nı açın ve kullanıcı ENTER tuşuna bastığında kadar bekleyin.</span><span class="sxs-lookup"><span data-stu-id="42365-125">Open the service host and wait until the user presses ENTER.</span></span>  
  
     [!code-csharp[htBasicService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#5)]
     [!code-vb[htBasicService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#5)]  
  
     <span data-ttu-id="42365-126">Bu örnek, bir konsol uygulaması ile Web stili hizmeti barındırma gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="42365-126">This sample demonstrates how to host a Web-Style service with a console application.</span></span> <span data-ttu-id="42365-127">Ayrıca, bu tür bir hizmet IIS içinde barındırabilir.</span><span class="sxs-lookup"><span data-stu-id="42365-127">You can also host such a service within IIS.</span></span> <span data-ttu-id="42365-128">Bunu yapmak için belirtmek <xref:System.ServiceModel.Activation.WebServiceHostFactory> aşağıdaki kodda gibi .svc dosyasında sınıfı.</span><span class="sxs-lookup"><span data-stu-id="42365-128">To do this, specify the <xref:System.ServiceModel.Activation.WebServiceHostFactory> class in a .svc file as the following code demonstrates.</span></span>  
  
    ```  
          <%ServiceHost   
    language=c#  
    Debug="true"  
    Service="Microsoft.Samples.Service"  
    Factory=System.ServiceModel.Activation.WebServiceHostFactory%>  
    ```  
  
### <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a><span data-ttu-id="42365-129">Internet Explorer'da GET eşlenen hizmet işlemleri çağırmak için</span><span class="sxs-lookup"><span data-stu-id="42365-129">To call service operations mapped to GET in Internet Explorer</span></span>  
  
1.  <span data-ttu-id="42365-130">Açık Internet Explorer ve türü "`http://localhost:8000/EchoWithGet?s=Hello, world!`" ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="42365-130">Open Internet Explorer and type "`http://localhost:8000/EchoWithGet?s=Hello, world!`" and press ENTER.</span></span> <span data-ttu-id="42365-131">Hizmetin taban adresi URL içerir ("8000 /"), bitiş noktasının göreli adresi (""), hizmet işlemi çağrı ("EchoWithGet") ve bir soru işareti adlandırılmış parametreleri ampersan tarafından ayrılmış bir listesi ve ardından (&).</span><span class="sxs-lookup"><span data-stu-id="42365-131">The URL contains the base address of the service ("http://localhost:8000/"), the relative address of the endpoint (""), the service operation to call ("EchoWithGet"), and a question mark followed by a list of named parameters separated by an ampersand (&).</span></span>  
  
### <a name="to-call-service-operations-in-code"></a><span data-ttu-id="42365-132">Kod içinde hizmet işlemleri çağırmak için</span><span class="sxs-lookup"><span data-stu-id="42365-132">To call service operations in code</span></span>  
  
1.  <span data-ttu-id="42365-133">Bir örneğini oluşturmak <!--zz <xref:System.ServiceModel.Web.WebChannelFactory>--> `System.ServiceModel.Web.WebChannelFactory` içinde bir `using` bloğu.</span><span class="sxs-lookup"><span data-stu-id="42365-133">Create an instance of <!--zz <xref:System.ServiceModel.Web.WebChannelFactory>--> `System.ServiceModel.Web.WebChannelFactory` within a `using` block.</span></span>  
  
     [!code-csharp[htBasicService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#6)]
     [!code-vb[htBasicService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#6)]  
  
2.  <span data-ttu-id="42365-134">Ekleme <xref:System.ServiceModel.Description.WebHttpBehavior> uç <xref:System.ServiceModel.ChannelFactory> çağrıları.</span><span class="sxs-lookup"><span data-stu-id="42365-134">Add <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint the <xref:System.ServiceModel.ChannelFactory> calls.</span></span>  
  
     [!code-csharp[htBasicService#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#7)]
     [!code-vb[htBasicService#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#7)]  
  
3.  <span data-ttu-id="42365-135">Kanal oluşturmak ve hizmet çağırın.</span><span class="sxs-lookup"><span data-stu-id="42365-135">Create the channel and call the service.</span></span>  
  
     [!code-csharp[htBasicService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#8)]
     [!code-vb[htBasicService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#8)]  
  
4.  <span data-ttu-id="42365-136">Kapat <xref:System.ServiceModel.Web.WebServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="42365-136">Close the <xref:System.ServiceModel.Web.WebServiceHost>.</span></span>  
  
     [!code-csharp[htBasicService#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#9)]
     [!code-vb[htBasicService#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="42365-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="42365-137">Example</span></span>  
 <span data-ttu-id="42365-138">Bu örnek için listeleme tam kod aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="42365-138">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htBasicService#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#10)]
 [!code-vb[htBasicService#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="42365-139">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="42365-139">Compiling the Code</span></span>  
 <span data-ttu-id="42365-140">Adını da başvuru System.ServiceModel.dll ve System.ServiceModel.Web.dll derlerken.</span><span class="sxs-lookup"><span data-stu-id="42365-140">When compiling Service.cs reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42365-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="42365-141">See Also</span></span>  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Web.WebServiceHost>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [<span data-ttu-id="42365-142">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="42365-142">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
