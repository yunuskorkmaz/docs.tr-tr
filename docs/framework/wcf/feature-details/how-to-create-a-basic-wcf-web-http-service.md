---
title: 'Nasıl yapılır: Temel Bir WCF Web HTTP Hizmeti Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 877662d3-d372-4e08-b417-51f66a0095cd
ms.openlocfilehash: 1b76d21cb4f416aae76e7597ad16cfd45e5b7cad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779203"
---
# <a name="how-to-create-a-basic-wcf-web-http-service"></a><span data-ttu-id="1f22c-102">Nasıl yapılır: Temel Bir WCF Web HTTP Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1f22c-102">How to: Create a Basic WCF Web HTTP Service</span></span>

<span data-ttu-id="1f22c-103">Windows Communication Foundation (WCF), bir Web uç noktası hizmetidir oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f22c-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a Web endpoint.</span></span> <span data-ttu-id="1f22c-104">Hiç SOAP Zarfı olduğunda, XML veya JSON veri Web uç gönderin.</span><span class="sxs-lookup"><span data-stu-id="1f22c-104">Web endpoints send data by XML or JSON, there is no SOAP envelope.</span></span> <span data-ttu-id="1f22c-105">Bu konuda, bu tür bir uç noktanın kullanıma gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1f22c-105">This topic demonstrates how to expose such an endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="1f22c-106">Yalnızca bir Web uç noktası güvenli şekilde bunu aktarım güvenliği kullanarak HTTPS kullanıma sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="1f22c-106">The only way to secure a Web endpoint is to expose it through HTTPS, using transport security.</span></span> <span data-ttu-id="1f22c-107">İleti tabanlı güvenlik kullanırken, güvenlik bilgileri genellikle SOAP üst bilgilerinde yerleştirilir ve gönderilen iletiler için hiç SOAP Zarfı olmayan SOAP uç noktaları içeren saklanıyorsa güvenlik bilgilerini yerleştirmek için yoktur ve aktarım güvenliği kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1f22c-107">When using message-based security, security information is usually placed in SOAP headers and because the messages sent to non-SOAP endpoints contain no SOAP envelope, there is nowhere to place the security information and you must rely on transport security.</span></span>

## <a name="to-create-a-web-endpoint"></a><span data-ttu-id="1f22c-108">Bir Web uç noktası oluşturma</span><span class="sxs-lookup"><span data-stu-id="1f22c-108">To create a Web endpoint</span></span>

1. <span data-ttu-id="1f22c-109">İle işaretlenmiş bir arabirim kullanarak bir hizmet sözleşmesini tanımlama <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> ve <xref:System.ServiceModel.Web.WebGetAttribute> öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="1f22c-109">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> and the <xref:System.ServiceModel.Web.WebGetAttribute> attributes.</span></span>

     [!code-csharp[htBasicService#0](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#0)]
     [!code-vb[htBasicService#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#0)]

    > [!NOTE]
    > <span data-ttu-id="1f22c-110">Varsayılan olarak, <xref:System.ServiceModel.Web.WebInvokeAttribute> işlemi POST çağrısına eşler.</span><span class="sxs-lookup"><span data-stu-id="1f22c-110">By default, <xref:System.ServiceModel.Web.WebInvokeAttribute> maps POST calls to the operation.</span></span> <span data-ttu-id="1f22c-111">Ancak, işlemi belirterek eşleştirmek için HTTP yöntemini (örneğin, HEAD, PUT veya Sil) belirtebilirsiniz bir "yöntemi =" parametresi.</span><span class="sxs-lookup"><span data-stu-id="1f22c-111">You can, however, specify the HTTP method (for example, HEAD, PUT, or DELETE) to map to the operation by specifying a "method=" parameter.</span></span> <span data-ttu-id="1f22c-112"><xref:System.ServiceModel.Web.WebGetAttribute> olmayan bir "yöntemi =" parametresi ve yalnızca eşlemeler GET hizmet işlemine çağırır.</span><span class="sxs-lookup"><span data-stu-id="1f22c-112"><xref:System.ServiceModel.Web.WebGetAttribute> does not have a "method=" parameter and only maps GET calls to the service operation.</span></span>

2. <span data-ttu-id="1f22c-113">Hizmet sözleşmesini uygulama.</span><span class="sxs-lookup"><span data-stu-id="1f22c-113">Implement the service contract.</span></span>

     [!code-csharp[htBasicService#1](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#1)]
     [!code-vb[htBasicService#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#1)]

## <a name="to-host-the-service"></a><span data-ttu-id="1f22c-114">Ana bilgisayar hizmeti</span><span class="sxs-lookup"><span data-stu-id="1f22c-114">To host the service</span></span>

1. <span data-ttu-id="1f22c-115">Oluşturma bir <xref:System.ServiceModel.Web.WebServiceHost> nesne.</span><span class="sxs-lookup"><span data-stu-id="1f22c-115">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>

     [!code-csharp[htBasicService#2](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#2)]
     [!code-vb[htBasicService#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#2)]

2. <span data-ttu-id="1f22c-116">Ekleme bir <xref:System.ServiceModel.Description.ServiceEndpoint> ile <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="1f22c-116">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>

     [!code-csharp[htBasicService#3](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#3)]
     [!code-vb[htBasicService#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#3)]

    > [!NOTE]
    > <span data-ttu-id="1f22c-117">Bir uç nokta eklemezseniz <xref:System.ServiceModel.Web.WebServiceHost> otomatik olarak bir varsayılan uç noktası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1f22c-117">If you do not add an endpoint, <xref:System.ServiceModel.Web.WebServiceHost> automatically creates a default endpoint.</span></span> <span data-ttu-id="1f22c-118"><xref:System.ServiceModel.Web.WebServiceHost> Ayrıca ekler <xref:System.ServiceModel.Description.WebHttpBehavior> ve meta veri uç noktasının varsayılan HTTP uç noktası ile aksatmaz için HTTP yardım sayfasına ve Web Hizmetleri Açıklama Dili (WSDL) alma işlevselliğini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="1f22c-118"><xref:System.ServiceModel.Web.WebServiceHost> also adds <xref:System.ServiceModel.Description.WebHttpBehavior> and disables the HTTP Help page and the Web Services Description Language (WSDL) GET functionality so the metadata endpoint does not interfere with the default HTTP endpoint.</span></span>
    >
    >  <span data-ttu-id="1f22c-119">Bir URL ile bir olmayan SOAP uç noktası ekleme "" uç noktasında bir işlemi çağırma girişimi yapıldığında beklenmeyen davranışlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="1f22c-119">Adding a non-SOAP endpoint with a URL of "" causes unexpected behavior when an attempt is made to call an operation on the endpoint.</span></span> <span data-ttu-id="1f22c-120">Bunun nedeni, uç nokta URI'si (temel bir WCF Hizmeti adresine göz atarken görüntülenen sayfa) yardım sayfasına URI'sini aynıdır dinleme ' dir.</span><span class="sxs-lookup"><span data-stu-id="1f22c-120">The reason for this is the listen URI of the endpoint is the same as the URI for the help page (the page that is displayed when you browse to the base address of a WCF service).</span></span>

     <span data-ttu-id="1f22c-121">Bunun gerçekleşmesini önlemek için aşağıdaki işlemlerden birini yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1f22c-121">You can do one of the following actions to prevent this from happening:</span></span>

    - <span data-ttu-id="1f22c-122">Her zaman bir olmayan SOAP uç noktası için boş olmayan URI belirtin.</span><span class="sxs-lookup"><span data-stu-id="1f22c-122">Always specify a non-blank URI for a non-SOAP endpoint.</span></span>

    - <span data-ttu-id="1f22c-123">Yardım sayfasını kapat.</span><span class="sxs-lookup"><span data-stu-id="1f22c-123">Turn off the help page.</span></span> <span data-ttu-id="1f22c-124">Bu, aşağıdaki kod ile yapılabilir:</span><span class="sxs-lookup"><span data-stu-id="1f22c-124">This can be done with the following code:</span></span>

     [!code-csharp[htBasicService#4](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#4)]
     [!code-vb[htBasicService#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#4)]

3. <span data-ttu-id="1f22c-125">Hizmet ana bilgisayarı'nı açın ve kullanıcı ENTER tuşuna bastığında kadar bekleyin.</span><span class="sxs-lookup"><span data-stu-id="1f22c-125">Open the service host and wait until the user presses ENTER.</span></span>

     [!code-csharp[htBasicService#5](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#5)]
     [!code-vb[htBasicService#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#5)]

     <span data-ttu-id="1f22c-126">Bu örnek bir konsol uygulaması ile Web stili hizmet barındırmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="1f22c-126">This sample demonstrates how to host a Web-Style service with a console application.</span></span> <span data-ttu-id="1f22c-127">Ayrıca, böyle bir hizmet IIS içinde barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f22c-127">You can also host such a service within IIS.</span></span> <span data-ttu-id="1f22c-128">Bunu yapmak için belirtin <xref:System.ServiceModel.Activation.WebServiceHostFactory> .svc dosyasında aşağıdaki kodun gösterdiği gibi sınıf.</span><span class="sxs-lookup"><span data-stu-id="1f22c-128">To do this, specify the <xref:System.ServiceModel.Activation.WebServiceHostFactory> class in a .svc file as the following code demonstrates.</span></span>

    ```
    <%ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Samples.Service"
        Factory=System.ServiceModel.Activation.WebServiceHostFactory%>
    ```

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a><span data-ttu-id="1f22c-129">Internet Explorer'da GET eşlenen hizmet işlemlerini aramak üzere</span><span class="sxs-lookup"><span data-stu-id="1f22c-129">To call service operations mapped to GET in Internet Explorer</span></span>

1. <span data-ttu-id="1f22c-130">Internet Explorer ve tür açın "`http://localhost:8000/EchoWithGet?s=Hello, world!`" ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="1f22c-130">Open Internet Explorer and type "`http://localhost:8000/EchoWithGet?s=Hello, world!`" and press ENTER.</span></span> <span data-ttu-id="1f22c-131">Hizmetin taban adresi URL içerir (`http://localhost:8000/`), ilgili uç nokta adresi (""), hizmet işlemine çağrı ("EchoWithGet") yanı sıra, bir soru işareti ve işareti tarafından ayrılmış, adlandırılan parametrelerin bir listesi ve ardından (&).</span><span class="sxs-lookup"><span data-stu-id="1f22c-131">The URL contains the base address of the service (`http://localhost:8000/`), the relative address of the endpoint (""), the service operation to call ("EchoWithGet"), and a question mark followed by a list of named parameters separated by an ampersand (&).</span></span>

## <a name="to-call-service-operations-in-code"></a><span data-ttu-id="1f22c-132">Kod içinde hizmet işlemlerini aramak üzere</span><span class="sxs-lookup"><span data-stu-id="1f22c-132">To call service operations in code</span></span>

1. <span data-ttu-id="1f22c-133">Bir örneğini oluşturmak <xref:System.ServiceModel.ChannelFactory%601> içinde bir `using` blok.</span><span class="sxs-lookup"><span data-stu-id="1f22c-133">Create an instance of <xref:System.ServiceModel.ChannelFactory%601> within a `using` block.</span></span>

     [!code-csharp[htBasicService#6](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#6)]
     [!code-vb[htBasicService#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#6)]

2. <span data-ttu-id="1f22c-134">Ekleme <xref:System.ServiceModel.Description.WebHttpBehavior> uç noktasına <xref:System.ServiceModel.ChannelFactory%601> çağırır.</span><span class="sxs-lookup"><span data-stu-id="1f22c-134">Add <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint the <xref:System.ServiceModel.ChannelFactory%601> calls.</span></span>

     [!code-csharp[htBasicService#7](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#7)]
     [!code-vb[htBasicService#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#7)]

3. <span data-ttu-id="1f22c-135">Bir kanal oluşturmak ve hizmet çağırın.</span><span class="sxs-lookup"><span data-stu-id="1f22c-135">Create the channel and call the service.</span></span>

     [!code-csharp[htBasicService#8](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#8)]
     [!code-vb[htBasicService#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#8)]

4. <span data-ttu-id="1f22c-136">Kapat <xref:System.ServiceModel.Web.WebServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="1f22c-136">Close the <xref:System.ServiceModel.Web.WebServiceHost>.</span></span>

     [!code-csharp[htBasicService#9](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#9)]
     [!code-vb[htBasicService#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#9)]

## <a name="example"></a><span data-ttu-id="1f22c-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f22c-137">Example</span></span>

<span data-ttu-id="1f22c-138">Bu örnek için listeleme tam kod aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1f22c-138">The following is the full code listing for this example.</span></span>

[!code-csharp[htBasicService#10](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#10)]
[!code-vb[htBasicService#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#10)]

## <a name="compiling-the-code"></a><span data-ttu-id="1f22c-139">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="1f22c-139">Compiling the code</span></span>

<span data-ttu-id="1f22c-140">Adını da başvuru System.ServiceModel.dll ve System.ServiceModel.Web.dll derlenirken.</span><span class="sxs-lookup"><span data-stu-id="1f22c-140">When compiling Service.cs reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f22c-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f22c-141">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="1f22c-142">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="1f22c-142">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)