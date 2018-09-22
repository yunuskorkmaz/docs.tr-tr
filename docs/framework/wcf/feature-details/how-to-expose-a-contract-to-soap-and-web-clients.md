---
title: 'Nasıl yapılır: Bir Sözleşmeyi SOAP ve Web İstemcilerine Sunma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
ms.openlocfilehash: d82c5e3fc33528eadc3c404cca59a3dcf905e0e2
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46581200"
---
# <a name="how-to-expose-a-contract-to-soap-and-web-clients"></a><span data-ttu-id="2f5e5-102">Nasıl yapılır: Bir Sözleşmeyi SOAP ve Web İstemcilerine Sunma</span><span class="sxs-lookup"><span data-stu-id="2f5e5-102">How to: Expose a Contract to SOAP and Web Clients</span></span>

<span data-ttu-id="2f5e5-103">Varsayılan olarak, Windows Communication Foundation (WCF) uç noktalar yalnızca SOAP istemcilerin kullanımına sunuyor.</span><span class="sxs-lookup"><span data-stu-id="2f5e5-103">By default, Windows Communication Foundation (WCF) makes endpoints available only to SOAP clients.</span></span> <span data-ttu-id="2f5e5-104">İçinde [nasıl yapılır: temel bir WCF Web HTTP hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md), bir uç nokta SOAP olmayan istemciler için kullanılabilir hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="2f5e5-104">In [How to: Create a Basic WCF Web HTTP Service](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md), an endpoint is made available to non-SOAP clients.</span></span> <span data-ttu-id="2f5e5-105">Aynı anlaşmaya her iki yönde bir Web uç noktası ve bir SOAP uç noktası olarak kullanılabilir hale getirmek istediğinizde zamanlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="2f5e5-105">There may be times when you want to make the same contract available both ways, as a Web endpoint and as a SOAP endpoint.</span></span> <span data-ttu-id="2f5e5-106">Bu konuda bir örnek bunun nasıl yapılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2f5e5-106">This topic shows an example of how to do this.</span></span>

## <a name="to-define-the-service-contract"></a><span data-ttu-id="2f5e5-107">Hizmet sözleşmesini tanımlama</span><span class="sxs-lookup"><span data-stu-id="2f5e5-107">To define the service contract</span></span>

1. <span data-ttu-id="2f5e5-108">İle işaretlenmiş bir arabirim kullanarak bir hizmet sözleşmesini tanımlama <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> ve <xref:System.ServiceModel.Web.WebGetAttribute> , aşağıdaki kodda gösterildiği gibi öznitelikleri:</span><span class="sxs-lookup"><span data-stu-id="2f5e5-108">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> and the <xref:System.ServiceModel.Web.WebGetAttribute> attributes, as shown in the following code:</span></span>

    [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
    [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]

    > [!NOTE]
    > <span data-ttu-id="2f5e5-109">Varsayılan olarak <xref:System.ServiceModel.Web.WebInvokeAttribute> işlemi POST çağrısına eşler.</span><span class="sxs-lookup"><span data-stu-id="2f5e5-109">By default <xref:System.ServiceModel.Web.WebInvokeAttribute> maps POST calls to the operation.</span></span> <span data-ttu-id="2f5e5-110">Ancak, belirterek işlemi eşleştirmek için yöntemini belirtebilirsiniz bir "yöntemi =" parametresi.</span><span class="sxs-lookup"><span data-stu-id="2f5e5-110">You can, however, specify the method to map to the operation by specifying a "method=" parameter.</span></span> <span data-ttu-id="2f5e5-111"><xref:System.ServiceModel.Web.WebGetAttribute> olmayan bir "yöntemi =" parametresi ve yalnızca eşlemeler GET hizmet işlemine çağırır.</span><span class="sxs-lookup"><span data-stu-id="2f5e5-111"><xref:System.ServiceModel.Web.WebGetAttribute> does not have a "method=" parameter and only maps GET calls to the service operation.</span></span>

2. <span data-ttu-id="2f5e5-112">Hizmet sözleşmesi, aşağıdaki kodda gösterildiği şekilde uygulayın:</span><span class="sxs-lookup"><span data-stu-id="2f5e5-112">Implement the service contract, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]

## <a name="to-host-the-service"></a><span data-ttu-id="2f5e5-113">Ana bilgisayar hizmeti</span><span class="sxs-lookup"><span data-stu-id="2f5e5-113">To host the service</span></span>

1. <span data-ttu-id="2f5e5-114">Oluşturma bir <xref:System.ServiceModel.ServiceHost> aşağıdaki kodda gösterildiği gibi nesne:</span><span class="sxs-lookup"><span data-stu-id="2f5e5-114">Create a <xref:System.ServiceModel.ServiceHost> object, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#2)]
     [!code-vb[htSoapWeb#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#2)]

2. <span data-ttu-id="2f5e5-115">Ekleme bir <xref:System.ServiceModel.Description.ServiceEndpoint> ile <xref:System.ServiceModel.BasicHttpBinding> aşağıdaki kodda gösterildiği gibi SOAP uç noktası için:</span><span class="sxs-lookup"><span data-stu-id="2f5e5-115">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.BasicHttpBinding> for the SOAP endpoint, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#3)]
     [!code-vb[htSoapWeb#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#3)]

3. <span data-ttu-id="2f5e5-116">Ekleme bir <xref:System.ServiceModel.Description.ServiceEndpoint> ile <xref:System.ServiceModel.WebHttpBinding> olmayan SOAP uç noktası için ve ekleme <xref:System.ServiceModel.Description.WebHttpBehavior> aşağıdaki kodda gösterildiği gibi uç:</span><span class="sxs-lookup"><span data-stu-id="2f5e5-116">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.WebHttpBinding> for the non-SOAP endpoint and add the <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#4)]
     [!code-vb[htSoapWeb#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#4)]

4. <span data-ttu-id="2f5e5-117">Çağrı `Open()` üzerinde bir <xref:System.ServiceModel.ServiceHost> örneği, hizmet ana bilgisayarı, aşağıdaki kodda gösterildiği gibi açın:</span><span class="sxs-lookup"><span data-stu-id="2f5e5-117">Call `Open()` on a <xref:System.ServiceModel.ServiceHost> instance to open the service host, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#5)]
     [!code-vb[htSoapWeb#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#5)]

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a><span data-ttu-id="2f5e5-118">Internet Explorer'da GET eşlenen hizmet işlemlerini aramak üzere</span><span class="sxs-lookup"><span data-stu-id="2f5e5-118">To call service operations mapped to GET in Internet Explorer</span></span>

1. <span data-ttu-id="2f5e5-119">Internet Explorer ve tür açın "`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`" ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2f5e5-119">Open Internet Explorer and type "`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`" and press ENTER.</span></span> <span data-ttu-id="2f5e5-120">Hizmetin taban adresi URL içerir (`http://localhost:8000/`), ilgili uç nokta adresi (""), hizmet işlemine çağrı ("EchoWithGet") yanı sıra, bir soru işareti ve işareti tarafından ayrılmış, adlandırılan parametrelerin bir listesi ve ardından (&).</span><span class="sxs-lookup"><span data-stu-id="2f5e5-120">The URL contains the base address of the service (`http://localhost:8000/`), the relative address of the endpoint (""), the service operation to call ("EchoWithGet"), and a question mark followed by a list of named parameters separated by an ampersand (&).</span></span>

## <a name="to-call-service-operations-on-the-web-endpoint-in-code"></a><span data-ttu-id="2f5e5-121">Web uç noktasında hizmet işlemleri çağırmak için</span><span class="sxs-lookup"><span data-stu-id="2f5e5-121">To call service operations on the Web endpoint in code</span></span>

1. <span data-ttu-id="2f5e5-122">Bir örneğini oluşturmak <xref:System.ServiceModel.Web.WebChannelFactory%601> içinde bir `using` , aşağıdaki kodda gösterildiği gibi engelleyin.</span><span class="sxs-lookup"><span data-stu-id="2f5e5-122">Create an instance of <xref:System.ServiceModel.Web.WebChannelFactory%601> within a `using` block, as shown in the following code.</span></span>

     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]

> [!NOTE]
> <span data-ttu-id="2f5e5-123">`Close()` Kanal sonunda otomatik olarak çağrılır `using` blok.</span><span class="sxs-lookup"><span data-stu-id="2f5e5-123">`Close()` is automatically called on the channel at the end of the `using` block.</span></span>

1. <span data-ttu-id="2f5e5-124">Kanalı oluşturun ve aşağıdaki kodda gösterildiği gibi hizmetin çağırın.</span><span class="sxs-lookup"><span data-stu-id="2f5e5-124">Create the channel and call the service, as shown in the following code.</span></span>

     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]

## <a name="to-call-service-operations-on-the-soap-endpoint"></a><span data-ttu-id="2f5e5-125">SOAP uç noktasında hizmet işlemlerini aramak üzere</span><span class="sxs-lookup"><span data-stu-id="2f5e5-125">To call service operations on the SOAP endpoint</span></span>

1. <span data-ttu-id="2f5e5-126">Bir örneğini oluşturmak <xref:System.ServiceModel.ChannelFactory> içinde bir `using` , aşağıdaki kodda gösterildiği gibi engelleyin.</span><span class="sxs-lookup"><span data-stu-id="2f5e5-126">Create an instance of <xref:System.ServiceModel.ChannelFactory> within a `using` block, as shown in the following code.</span></span>

    [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
    [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]

2. <span data-ttu-id="2f5e5-127">Kanalı oluşturun ve aşağıdaki kodda gösterildiği gibi hizmetin çağırın.</span><span class="sxs-lookup"><span data-stu-id="2f5e5-127">Create the channel and call the service, as shown in the following code.</span></span>

    [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
    [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]

## <a name="to-close-the-service-host"></a><span data-ttu-id="2f5e5-128">Hizmet ana bilgisayarı kapatmak için</span><span class="sxs-lookup"><span data-stu-id="2f5e5-128">To close the service host</span></span>

1. <span data-ttu-id="2f5e5-129">Aşağıdaki kodda gösterildiği gibi hizmet konağı kapatın.</span><span class="sxs-lookup"><span data-stu-id="2f5e5-129">Close the service host, as shown in the following code.</span></span>

    [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
    [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]

## <a name="example"></a><span data-ttu-id="2f5e5-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="2f5e5-130">Example</span></span>

<span data-ttu-id="2f5e5-131">Bu konu için listeleme tam kod aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="2f5e5-131">The following is the full code listing for this topic:</span></span>

[!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
[!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]

## <a name="compiling-the-code"></a><span data-ttu-id="2f5e5-132">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="2f5e5-132">Compiling the code</span></span>

 <span data-ttu-id="2f5e5-133">Adını da derlenirken System.ServiceModel.dll ve System.ServiceModel.Web.dll başvuru.</span><span class="sxs-lookup"><span data-stu-id="2f5e5-133">When compiling Service.cs, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>

## <a name="see-also"></a><span data-ttu-id="2f5e5-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f5e5-134">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.ChannelFactory>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="2f5e5-135">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="2f5e5-135">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)