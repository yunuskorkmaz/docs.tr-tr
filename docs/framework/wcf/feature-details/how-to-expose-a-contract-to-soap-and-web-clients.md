---
title: 'Nasıl yapılır: Bir Sözleşmeyi SOAP ve Web İstemcilerine Sunma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
ms.openlocfilehash: fa02260976c710401a05cce3d723cc0f66804c6e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593139"
---
# <a name="how-to-expose-a-contract-to-soap-and-web-clients"></a><span data-ttu-id="8e7bf-102">Nasıl yapılır: Bir Sözleşmeyi SOAP ve Web İstemcilerine Sunma</span><span class="sxs-lookup"><span data-stu-id="8e7bf-102">How to: Expose a Contract to SOAP and Web Clients</span></span>

<span data-ttu-id="8e7bf-103">Varsayılan olarak, Windows Communication Foundation (WCF) uç noktaları yalnızca SOAP istemcileri için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="8e7bf-103">By default, Windows Communication Foundation (WCF) makes endpoints available only to SOAP clients.</span></span> <span data-ttu-id="8e7bf-104">[Nasıl yapılır: temel BIR WCF Web http hizmeti oluşturma](how-to-create-a-basic-wcf-web-http-service.md)bölümünde, soap olmayan istemciler için bir uç nokta kullanılabilir hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="8e7bf-104">In [How to: Create a Basic WCF Web HTTP Service](how-to-create-a-basic-wcf-web-http-service.md), an endpoint is made available to non-SOAP clients.</span></span> <span data-ttu-id="8e7bf-105">Aynı sözleşmeyi bir Web uç noktası ve bir SOAP uç noktası olarak her iki şekilde de kullanılabilir hale getirmek istediğiniz zamanlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="8e7bf-105">There may be times when you want to make the same contract available both ways, as a Web endpoint and as a SOAP endpoint.</span></span> <span data-ttu-id="8e7bf-106">Bu konu, bunun nasıl yapılacağını gösteren bir örnek gösterir.</span><span class="sxs-lookup"><span data-stu-id="8e7bf-106">This topic shows an example of how to do this.</span></span>

## <a name="to-define-the-service-contract"></a><span data-ttu-id="8e7bf-107">Hizmet sözleşmesini tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="8e7bf-107">To define the service contract</span></span>

1. <span data-ttu-id="8e7bf-108"><xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> Aşağıdaki kodda gösterildiği gibi, ve öznitelikleri ile işaretlenmiş bir arabirim kullanarak bir hizmet sözleşmesi tanımlayın <xref:System.ServiceModel.Web.WebGetAttribute> :</span><span class="sxs-lookup"><span data-stu-id="8e7bf-108">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> and the <xref:System.ServiceModel.Web.WebGetAttribute> attributes, as shown in the following code:</span></span>

    [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
    [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]

    > [!NOTE]
    > <span data-ttu-id="8e7bf-109">Varsayılan olarak <xref:System.ServiceModel.Web.WebInvokeAttribute> , işleme yapılan çağrıları eşler.</span><span class="sxs-lookup"><span data-stu-id="8e7bf-109">By default <xref:System.ServiceModel.Web.WebInvokeAttribute> maps POST calls to the operation.</span></span> <span data-ttu-id="8e7bf-110">Bununla birlikte, bir "method =" parametresi belirterek, işleme eşlemek için yöntemi belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e7bf-110">You can, however, specify the method to map to the operation by specifying a "method=" parameter.</span></span> <span data-ttu-id="8e7bf-111"><xref:System.ServiceModel.Web.WebGetAttribute>"method =" parametresine sahip değildir ve yalnızca hizmet işlemine yapılan çağrıları eşler.</span><span class="sxs-lookup"><span data-stu-id="8e7bf-111"><xref:System.ServiceModel.Web.WebGetAttribute> does not have a "method=" parameter and only maps GET calls to the service operation.</span></span>

2. <span data-ttu-id="8e7bf-112">Aşağıdaki kodda gösterildiği gibi hizmet sözleşmesini uygulayın:</span><span class="sxs-lookup"><span data-stu-id="8e7bf-112">Implement the service contract, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]

## <a name="to-host-the-service"></a><span data-ttu-id="8e7bf-113">Hizmeti barındırmak için</span><span class="sxs-lookup"><span data-stu-id="8e7bf-113">To host the service</span></span>

1. <span data-ttu-id="8e7bf-114"><xref:System.ServiceModel.ServiceHost>Aşağıdaki kodda gösterildiği gibi bir nesne oluşturun:</span><span class="sxs-lookup"><span data-stu-id="8e7bf-114">Create a <xref:System.ServiceModel.ServiceHost> object, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#2)]
     [!code-vb[htSoapWeb#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#2)]

2. <span data-ttu-id="8e7bf-115"><xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.BasicHttpBinding> SOAP uç noktası için aşağıdaki kodda gösterildiği gibi bir ile ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8e7bf-115">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.BasicHttpBinding> for the SOAP endpoint, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#3)]
     [!code-vb[htSoapWeb#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#3)]

3. <span data-ttu-id="8e7bf-116"><xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.WebHttpBinding> SOAP olmayan uç nokta için bir ile ekleyin ve <xref:System.ServiceModel.Description.WebHttpBehavior> aşağıdaki kodda gösterildiği gibi uç noktaya ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8e7bf-116">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.WebHttpBinding> for the non-SOAP endpoint and add the <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#4)]
     [!code-vb[htSoapWeb#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#4)]

4. <span data-ttu-id="8e7bf-117">`Open()` <xref:System.ServiceModel.ServiceHost> Aşağıdaki kodda gösterildiği gibi, hizmet ana bilgisayarını açmak için bir örneği çağırın:</span><span class="sxs-lookup"><span data-stu-id="8e7bf-117">Call `Open()` on a <xref:System.ServiceModel.ServiceHost> instance to open the service host, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#5)]
     [!code-vb[htSoapWeb#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#5)]

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a><span data-ttu-id="8e7bf-118">Internet Explorer 'da almak üzere eşlenmiş hizmet işlemlerini çağırmak için</span><span class="sxs-lookup"><span data-stu-id="8e7bf-118">To call service operations mapped to GET in Internet Explorer</span></span>

1. <span data-ttu-id="8e7bf-119">Internet Explorer 'ı açın ve " `http://localhost:8000/Web/EchoWithGet?s=Hello, world!` " yazın ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8e7bf-119">Open Internet Explorer and type "`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`" and press ENTER.</span></span> <span data-ttu-id="8e7bf-120">URL, hizmetin temel adresini ( `http://localhost:8000/` ), uç noktanın göreli adresini (""), çağrı yapılacak hizmet işlemini ("yankı \ al") ve ardından bir ve işareti (&) ile ayrılmış adlandırılmış parametrelerin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="8e7bf-120">The URL contains the base address of the service (`http://localhost:8000/`), the relative address of the endpoint (""), the service operation to call ("EchoWithGet"), and a question mark followed by a list of named parameters separated by an ampersand (&).</span></span>

## <a name="to-call-service-operations-on-the-web-endpoint-in-code"></a><span data-ttu-id="8e7bf-121">Koddaki Web uç noktasında hizmet işlemlerini çağırmak için</span><span class="sxs-lookup"><span data-stu-id="8e7bf-121">To call service operations on the Web endpoint in code</span></span>

1. <span data-ttu-id="8e7bf-122"><xref:System.ServiceModel.Web.WebChannelFactory%601>Aşağıdaki kodda gösterildiği gibi bir blok içinde öğesinin bir örneğini oluşturun `using` .</span><span class="sxs-lookup"><span data-stu-id="8e7bf-122">Create an instance of <xref:System.ServiceModel.Web.WebChannelFactory%601> within a `using` block, as shown in the following code.</span></span>

     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]

> [!NOTE]
> <span data-ttu-id="8e7bf-123">`Close()`, blok sonundaki kanalda otomatik olarak çağrılır `using` .</span><span class="sxs-lookup"><span data-stu-id="8e7bf-123">`Close()` is automatically called on the channel at the end of the `using` block.</span></span>

1. <span data-ttu-id="8e7bf-124">Aşağıdaki kodda gösterildiği gibi kanalı oluşturun ve hizmeti çağırın.</span><span class="sxs-lookup"><span data-stu-id="8e7bf-124">Create the channel and call the service, as shown in the following code.</span></span>

     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]

## <a name="to-call-service-operations-on-the-soap-endpoint"></a><span data-ttu-id="8e7bf-125">SOAP uç noktasındaki hizmet işlemlerini çağırmak için</span><span class="sxs-lookup"><span data-stu-id="8e7bf-125">To call service operations on the SOAP endpoint</span></span>

1. <span data-ttu-id="8e7bf-126"><xref:System.ServiceModel.ChannelFactory>Aşağıdaki kodda gösterildiği gibi bir blok içinde öğesinin bir örneğini oluşturun `using` .</span><span class="sxs-lookup"><span data-stu-id="8e7bf-126">Create an instance of <xref:System.ServiceModel.ChannelFactory> within a `using` block, as shown in the following code.</span></span>

    [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
    [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]

2. <span data-ttu-id="8e7bf-127">Aşağıdaki kodda gösterildiği gibi kanalı oluşturun ve hizmeti çağırın.</span><span class="sxs-lookup"><span data-stu-id="8e7bf-127">Create the channel and call the service, as shown in the following code.</span></span>

    [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
    [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]

## <a name="to-close-the-service-host"></a><span data-ttu-id="8e7bf-128">Hizmet konağını kapatmak için</span><span class="sxs-lookup"><span data-stu-id="8e7bf-128">To close the service host</span></span>

1. <span data-ttu-id="8e7bf-129">Aşağıdaki kodda gösterildiği gibi hizmet ana bilgisayarını kapatın.</span><span class="sxs-lookup"><span data-stu-id="8e7bf-129">Close the service host, as shown in the following code.</span></span>

    [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
    [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]

## <a name="example"></a><span data-ttu-id="8e7bf-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="8e7bf-130">Example</span></span>

<span data-ttu-id="8e7bf-131">Aşağıda, bu konunun tam kod listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="8e7bf-131">The following is the full code listing for this topic:</span></span>

[!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
[!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]

## <a name="compiling-the-code"></a><span data-ttu-id="8e7bf-132">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="8e7bf-132">Compiling the code</span></span>

 <span data-ttu-id="8e7bf-133">Service.cs derlenirken, System. ServiceModel. dll ve System. ServiceModel. Web. dll dosyasına başvurun.</span><span class="sxs-lookup"><span data-stu-id="8e7bf-133">When compiling Service.cs, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e7bf-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e7bf-134">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.ChannelFactory>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="8e7bf-135">WCF Web HTTP Programlama Modeli</span><span class="sxs-lookup"><span data-stu-id="8e7bf-135">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
