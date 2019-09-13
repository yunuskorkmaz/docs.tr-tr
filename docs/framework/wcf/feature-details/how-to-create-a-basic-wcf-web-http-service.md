---
title: 'Nasıl yapılır: Temel Bir WCF Web HTTP Hizmeti Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 877662d3-d372-4e08-b417-51f66a0095cd
ms.openlocfilehash: e9646235f9423f2a4df9cfe09a5e83a91dcdcace
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895184"
---
# <a name="how-to-create-a-basic-wcf-web-http-service"></a><span data-ttu-id="2ae7a-102">Nasıl yapılır: Temel Bir WCF Web HTTP Hizmeti Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2ae7a-102">How to: Create a Basic WCF Web HTTP Service</span></span>

<span data-ttu-id="2ae7a-103">Windows Communication Foundation (WCF), bir Web uç noktası sunan bir hizmet oluşturmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a Web endpoint.</span></span> <span data-ttu-id="2ae7a-104">Web uç noktaları, verileri XML veya JSON ile gönderir, hiç SOAP Zarfı yoktur.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-104">Web endpoints send data by XML or JSON, there is no SOAP envelope.</span></span> <span data-ttu-id="2ae7a-105">Bu konuda, bu tür bir uç noktanın nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-105">This topic demonstrates how to expose such an endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="2ae7a-106">Web uç noktasını güvenli hale getirmenin tek yolu, aktarım güvenliği kullanılarak HTTPS üzerinden kullanıma sunulmasıdır.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-106">The only way to secure a Web endpoint is to expose it through HTTPS, using transport security.</span></span> <span data-ttu-id="2ae7a-107">İleti tabanlı güvenlik kullanırken, güvenlik bilgileri genellikle SOAP üst bilgilerine yerleştirilir ve SOAP olmayan uç noktalara gönderilen iletiler SOAP Zarfı içermediği için, güvenlik bilgilerinin yerleştirilmesi ve aktarım güvenliğine güvenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-107">When using message-based security, security information is usually placed in SOAP headers and because the messages sent to non-SOAP endpoints contain no SOAP envelope, there is nowhere to place the security information and you must rely on transport security.</span></span>

## <a name="to-create-a-web-endpoint"></a><span data-ttu-id="2ae7a-108">Web uç noktası oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2ae7a-108">To create a Web endpoint</span></span>

1. <span data-ttu-id="2ae7a-109"><xref:System.ServiceModel.Web.WebInvokeAttribute> <xref:System.ServiceModel.ServiceContractAttribute> Ve<xref:System.ServiceModel.Web.WebGetAttribute> öznitelikleri ile işaretlenmiş bir arabirim kullanarak bir hizmet sözleşmesi tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-109">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> and the <xref:System.ServiceModel.Web.WebGetAttribute> attributes.</span></span>

     [!code-csharp[htBasicService#0](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#0)]
     [!code-vb[htBasicService#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#0)]

    > [!NOTE]
    > <span data-ttu-id="2ae7a-110">Varsayılan olarak, <xref:System.ServiceModel.Web.WebInvokeAttribute> eşleme çağrıları işleme gönderisini.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-110">By default, <xref:System.ServiceModel.Web.WebInvokeAttribute> maps POST calls to the operation.</span></span> <span data-ttu-id="2ae7a-111">Ancak, bir "method =" parametresi belirterek, işleme eşlenecek HTTP yöntemini (örneğin, HEAD, PUT veya DELETE) belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-111">You can, however, specify the HTTP method (for example, HEAD, PUT, or DELETE) to map to the operation by specifying a "method=" parameter.</span></span> <span data-ttu-id="2ae7a-112"><xref:System.ServiceModel.Web.WebGetAttribute>"method =" parametresine sahip değildir ve yalnızca hizmet işlemine yapılan çağrıları eşler.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-112"><xref:System.ServiceModel.Web.WebGetAttribute> does not have a "method=" parameter and only maps GET calls to the service operation.</span></span>

2. <span data-ttu-id="2ae7a-113">Hizmet sözleşmesini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-113">Implement the service contract.</span></span>

     [!code-csharp[htBasicService#1](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#1)]
     [!code-vb[htBasicService#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#1)]

## <a name="to-host-the-service"></a><span data-ttu-id="2ae7a-114">Hizmeti barındırmak için</span><span class="sxs-lookup"><span data-stu-id="2ae7a-114">To host the service</span></span>

1. <span data-ttu-id="2ae7a-115">Bir <xref:System.ServiceModel.Web.WebServiceHost> nesne oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-115">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>

     [!code-csharp[htBasicService#2](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#2)]
     [!code-vb[htBasicService#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#2)]

2. <span data-ttu-id="2ae7a-116">İle bir <xref:System.ServiceModel.Description.ServiceEndpoint>ekleyin. <xref:System.ServiceModel.Description.WebHttpBehavior></span><span class="sxs-lookup"><span data-stu-id="2ae7a-116">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>

     [!code-csharp[htBasicService#3](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#3)]
     [!code-vb[htBasicService#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#3)]

    > [!NOTE]
    > <span data-ttu-id="2ae7a-117">Uç nokta eklemedıysanız, <xref:System.ServiceModel.Web.WebServiceHost> otomatik olarak varsayılan bir uç nokta oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-117">If you do not add an endpoint, <xref:System.ServiceModel.Web.WebServiceHost> automatically creates a default endpoint.</span></span> <span data-ttu-id="2ae7a-118"><xref:System.ServiceModel.Web.WebServiceHost>Ayrıca, <xref:System.ServiceModel.Description.WebHttpBehavior> http yardım sayfasını ve Web Hizmetleri Açıklama Dili (wsdl) Al işlevini ekler ve devre dışı bırakır, böylece meta veri uç noktası varsayılan HTTP uç noktasına müdahale etmez.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-118"><xref:System.ServiceModel.Web.WebServiceHost> also adds <xref:System.ServiceModel.Description.WebHttpBehavior> and disables the HTTP Help page and the Web Services Description Language (WSDL) GET functionality so the metadata endpoint does not interfere with the default HTTP endpoint.</span></span>
    >
    >  <span data-ttu-id="2ae7a-119">"" URL 'SI ile SOAP olmayan bir uç nokta eklemek, uç noktada bir işlemi çağırmak için bir girişim yapıldığında beklenmeyen davranışlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-119">Adding a non-SOAP endpoint with a URL of "" causes unexpected behavior when an attempt is made to call an operation on the endpoint.</span></span> <span data-ttu-id="2ae7a-120">Bunun nedeni, uç noktanın dinleme URI 'si, yardım sayfasının URI 'siyle aynıdır (bir WCF hizmetinin temel adresine gözattığınızda görüntülenen sayfa).</span><span class="sxs-lookup"><span data-stu-id="2ae7a-120">The reason for this is the listen URI of the endpoint is the same as the URI for the help page (the page that is displayed when you browse to the base address of a WCF service).</span></span>

     <span data-ttu-id="2ae7a-121">Bunun oluşmasını engellemek için aşağıdaki eylemlerden birini yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2ae7a-121">You can do one of the following actions to prevent this from happening:</span></span>

    - <span data-ttu-id="2ae7a-122">SOAP olmayan bir uç nokta için her zaman boş olmayan bir URI belirtin.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-122">Always specify a non-blank URI for a non-SOAP endpoint.</span></span>

    - <span data-ttu-id="2ae7a-123">Yardım sayfasını kapatın.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-123">Turn off the help page.</span></span> <span data-ttu-id="2ae7a-124">Bu, aşağıdaki kodla yapılabilir:</span><span class="sxs-lookup"><span data-stu-id="2ae7a-124">This can be done with the following code:</span></span>

     [!code-csharp[htBasicService#4](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#4)]
     [!code-vb[htBasicService#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#4)]

3. <span data-ttu-id="2ae7a-125">Hizmet konağını açın ve Kullanıcı ENTER tuşuna basana kadar bekleyin.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-125">Open the service host and wait until the user presses ENTER.</span></span>

     [!code-csharp[htBasicService#5](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#5)]
     [!code-vb[htBasicService#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#5)]

     <span data-ttu-id="2ae7a-126">Bu örnek, bir konsol uygulamasıyla bir Web stili hizmetin nasıl barındırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-126">This sample demonstrates how to host a Web-Style service with a console application.</span></span> <span data-ttu-id="2ae7a-127">Bu hizmeti IIS içinde de barındırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-127">You can also host such a service within IIS.</span></span> <span data-ttu-id="2ae7a-128">Bunu yapmak için, aşağıdaki kodda <xref:System.ServiceModel.Activation.WebServiceHostFactory> gösterildiği gibi bir. svc dosyasında sınıfını belirtin.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-128">To do this, specify the <xref:System.ServiceModel.Activation.WebServiceHostFactory> class in a .svc file as the following code demonstrates.</span></span>

    ```text
    <%ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Samples.Service"
        Factory=System.ServiceModel.Activation.WebServiceHostFactory%>
    ```

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a><span data-ttu-id="2ae7a-129">Internet Explorer 'da almak üzere eşlenmiş hizmet işlemlerini çağırmak için</span><span class="sxs-lookup"><span data-stu-id="2ae7a-129">To call service operations mapped to GET in Internet Explorer</span></span>

1. <span data-ttu-id="2ae7a-130">Internet Explorer 'ı açın ve "`http://localhost:8000/EchoWithGet?s=Hello, world!`" yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-130">Open Internet Explorer and type "`http://localhost:8000/EchoWithGet?s=Hello, world!`" and press ENTER.</span></span> <span data-ttu-id="2ae7a-131">URL, hizmetin temel adresini (`http://localhost:8000/`), uç noktanın göreli adresini (""), çağrı yapılacak hizmet işlemini ("yankı \ al") ve ardından bir ve işareti (&) ile ayrılmış adlandırılmış parametrelerin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-131">The URL contains the base address of the service (`http://localhost:8000/`), the relative address of the endpoint (""), the service operation to call ("EchoWithGet"), and a question mark followed by a list of named parameters separated by an ampersand (&).</span></span>

## <a name="to-call-service-operations-in-code"></a><span data-ttu-id="2ae7a-132">Koddaki hizmet işlemlerini çağırmak için</span><span class="sxs-lookup"><span data-stu-id="2ae7a-132">To call service operations in code</span></span>

1. <span data-ttu-id="2ae7a-133"><xref:System.ServiceModel.ChannelFactory%601> Bir`using` blok içinde bir örnek oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-133">Create an instance of <xref:System.ServiceModel.ChannelFactory%601> within a `using` block.</span></span>

     [!code-csharp[htBasicService#6](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#6)]
     [!code-vb[htBasicService#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#6)]

2. <span data-ttu-id="2ae7a-134">Çağrıları uç noktaya ekleyin <xref:System.ServiceModel.Description.WebHttpBehavior>. <xref:System.ServiceModel.ChannelFactory%601></span><span class="sxs-lookup"><span data-stu-id="2ae7a-134">Add <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint the <xref:System.ServiceModel.ChannelFactory%601> calls.</span></span>

     [!code-csharp[htBasicService#7](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#7)]
     [!code-vb[htBasicService#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#7)]

3. <span data-ttu-id="2ae7a-135">Kanalı oluşturun ve hizmeti çağırın.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-135">Create the channel and call the service.</span></span>

     [!code-csharp[htBasicService#8](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#8)]
     [!code-vb[htBasicService#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#8)]

4. <span data-ttu-id="2ae7a-136">Öğesini kapatın <xref:System.ServiceModel.Web.WebServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-136">Close the <xref:System.ServiceModel.Web.WebServiceHost>.</span></span>

     [!code-csharp[htBasicService#9](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#9)]
     [!code-vb[htBasicService#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#9)]

## <a name="example"></a><span data-ttu-id="2ae7a-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="2ae7a-137">Example</span></span>

<span data-ttu-id="2ae7a-138">Bu örnek için tam kod listesi aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-138">The following is the full code listing for this example.</span></span>

[!code-csharp[htBasicService#10](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#10)]
[!code-vb[htBasicService#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#10)]

## <a name="compiling-the-code"></a><span data-ttu-id="2ae7a-139">Kodu derleme</span><span class="sxs-lookup"><span data-stu-id="2ae7a-139">Compiling the code</span></span>

<span data-ttu-id="2ae7a-140">System. ServiceModel. dll ve System. ServiceModel. Web. dll Service.cs başvurusunu derlerken.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-140">When compiling Service.cs reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ae7a-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ae7a-141">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="2ae7a-142">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="2ae7a-142">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
