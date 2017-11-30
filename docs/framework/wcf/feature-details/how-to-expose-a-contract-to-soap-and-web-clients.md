---
title: "Nasıl yapılır: Bir Sözleşmeyi SOAP ve Web İstemcilerine Sunma"
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
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 06127af9c373987c02b2e53ff57e6f50a7f5baa5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-expose-a-contract-to-soap-and-web-clients"></a><span data-ttu-id="b14df-102">Nasıl yapılır: Bir Sözleşmeyi SOAP ve Web İstemcilerine Sunma</span><span class="sxs-lookup"><span data-stu-id="b14df-102">How to: Expose a Contract to SOAP and Web Clients</span></span>
<span data-ttu-id="b14df-103">Varsayılan olarak, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uç noktalar yalnızca SOAP istemciler için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="b14df-103">By default, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] makes endpoints available only to SOAP clients.</span></span> <span data-ttu-id="b14df-104">İçinde [nasıl yapılır: temel bir WCF Web HTTP hizmeti oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md), bir uç nokta SOAP olmayan istemciler için kullanılabilir hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="b14df-104">In [How to: Create a Basic WCF Web HTTP Service](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md), an endpoint is made available to non-SOAP clients.</span></span> <span data-ttu-id="b14df-105">Aynı sözleşme çift yönlü bir Web uç noktası ve bir SOAP uç noktası olarak kullanılabilir hale getirmek istediğinizde zamanlar olabilir.</span><span class="sxs-lookup"><span data-stu-id="b14df-105">There may be times when you want to make the same contract available both ways, as a Web endpoint and as a SOAP endpoint.</span></span> <span data-ttu-id="b14df-106">Bu konu bunun nasıl yapılacağı örneği gösterir.</span><span class="sxs-lookup"><span data-stu-id="b14df-106">This topic shows an example of how to do this.</span></span>  
  
### <a name="to-define-the-service-contract"></a><span data-ttu-id="b14df-107">Hizmet sözleşmesi tanımlamak için</span><span class="sxs-lookup"><span data-stu-id="b14df-107">To define the service contract</span></span>  
  
1.  <span data-ttu-id="b14df-108">İle işaretlenen arabirimini kullanarak bir hizmet sözleşmesini tanımlayan <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> ve <xref:System.ServiceModel.Web.WebGetAttribute> aşağıdaki kodda gösterildiği gibi öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="b14df-108">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> and the <xref:System.ServiceModel.Web.WebGetAttribute> attributes, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
     [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]  
  
    > [!NOTE]
    >  <span data-ttu-id="b14df-109">Varsayılan olarak <xref:System.ServiceModel.Web.WebInvokeAttribute> işlemi POST çağrıları eşler.</span><span class="sxs-lookup"><span data-stu-id="b14df-109">By default <xref:System.ServiceModel.Web.WebInvokeAttribute> maps POST calls to the operation.</span></span> <span data-ttu-id="b14df-110">Bununla birlikte, belirterek işlemi eşleştirmek için yöntemini belirleyebilirsiniz bir "yöntemi =" parametresi.</span><span class="sxs-lookup"><span data-stu-id="b14df-110">You can, however, specify the method to map to the operation by specifying a "method=" parameter.</span></span> <span data-ttu-id="b14df-111"><xref:System.ServiceModel.Web.WebGetAttribute>sahip olmayan bir "yöntemi =" GET parametre ve yalnızca eşlemeleri hizmet işlemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="b14df-111"><xref:System.ServiceModel.Web.WebGetAttribute> does not have a "method=" parameter and only maps GET calls to the service operation.</span></span>  
  
2.  <span data-ttu-id="b14df-112">Aşağıdaki kodda gösterildiği gibi hizmet sözleşmesini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="b14df-112">Implement the service contract, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="b14df-113">Ana bilgisayar hizmeti</span><span class="sxs-lookup"><span data-stu-id="b14df-113">To host the service</span></span>  
  
1.  <span data-ttu-id="b14df-114">Oluşturma bir <xref:System.ServiceModel.ServiceHost> aşağıdaki kodda gösterildiği gibi nesne.</span><span class="sxs-lookup"><span data-stu-id="b14df-114">Create a <xref:System.ServiceModel.ServiceHost> object, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#2)]
     [!code-vb[htSoapWeb#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#2)]  
  
2.  <span data-ttu-id="b14df-115">Ekleme bir <xref:System.ServiceModel.Description.ServiceEndpoint> ile <xref:System.ServiceModel.BasicHttpBinding> aşağıdaki kodda gösterildiği gibi SOAP uç için.</span><span class="sxs-lookup"><span data-stu-id="b14df-115">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.BasicHttpBinding> for the SOAP endpoint, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#3)]
     [!code-vb[htSoapWeb#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#3)]  
  
3.  <span data-ttu-id="b14df-116">Ekleme bir <xref:System.ServiceModel.Description.ServiceEndpoint> ile <xref:System.ServiceModel.WebHttpBinding> olmayan SOAP uç noktası için ve ekleme <xref:System.ServiceModel.Description.WebHttpBehavior> aşağıdaki kodda gösterildiği gibi uç.</span><span class="sxs-lookup"><span data-stu-id="b14df-116">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.WebHttpBinding> for the non-SOAP endpoint and add the <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#4)]
     [!code-vb[htSoapWeb#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#4)]  
  
4.  <span data-ttu-id="b14df-117">Çağrı `Open()` üzerinde bir <xref:System.ServiceModel.ServiceHost> aşağıdaki kodda gösterildiği gibi hizmet ana bilgisayarını açma örneği.</span><span class="sxs-lookup"><span data-stu-id="b14df-117">Call `Open()` on a <xref:System.ServiceModel.ServiceHost> instance to open the service host, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#5)]
     [!code-vb[htSoapWeb#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#5)]  
  
### <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a><span data-ttu-id="b14df-118">Internet Explorer'da GET eşlenen hizmet işlemleri çağırmak için</span><span class="sxs-lookup"><span data-stu-id="b14df-118">To call service operations mapped to GET in Internet Explorer</span></span>  
  
1.  <span data-ttu-id="b14df-119">Açık Internet Explorer ve türü "`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`" ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b14df-119">Open Internet Explorer and type "`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`" and press ENTER.</span></span> <span data-ttu-id="b14df-120">Hizmetin taban adresi URL içerir ("8000 /"), bitiş noktasının göreli adresi (""), hizmet işlemi çağrı ("EchoWithGet") ve bir soru işareti adlandırılmış parametreleri ampersan tarafından ayrılmış bir listesi ve ardından (&).</span><span class="sxs-lookup"><span data-stu-id="b14df-120">The URL contains the base address of the service ("http://localhost:8000/"), the relative address of the endpoint (""), the service operation to call ("EchoWithGet"), and a question mark followed by a list of named parameters separated by an ampersand (&).</span></span>  
  
### <a name="to-call-service-operations-on-the-web-endpoint-in-code"></a><span data-ttu-id="b14df-121">Kod içinde hizmet işlemleri üzerinde Web uç noktası çağırmak için</span><span class="sxs-lookup"><span data-stu-id="b14df-121">To call service operations on the Web endpoint in code</span></span>  
  
1.  <span data-ttu-id="b14df-122">Bir örneğini oluşturmak <xref:System.ServiceModel.Web.WebChannelFactory%601> içinde bir `using` aşağıdaki kodda gösterildiği gibi engelleyin.</span><span class="sxs-lookup"><span data-stu-id="b14df-122">Create an instance of <xref:System.ServiceModel.Web.WebChannelFactory%601> within a `using` block, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]  
  
> [!NOTE]
>  <span data-ttu-id="b14df-123">`Close()`kanalda sonunda otomatik olarak çağrılır `using` bloğu.</span><span class="sxs-lookup"><span data-stu-id="b14df-123">`Close()` is automatically called on the channel at the end of the `using` block.</span></span>  
  
1.  <span data-ttu-id="b14df-124">Kanal oluşturun ve aşağıdaki kodda gösterildiği gibi hizmet çağırın.</span><span class="sxs-lookup"><span data-stu-id="b14df-124">Create the channel and call the service, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]  
  
### <a name="to-call-service-operations-on-the-soap-endpoint"></a><span data-ttu-id="b14df-125">SOAP uç noktasındaki hizmet işlemleri çağırmak için</span><span class="sxs-lookup"><span data-stu-id="b14df-125">To call service operations on the SOAP endpoint</span></span>  
  
1.  <span data-ttu-id="b14df-126">Bir örneğini oluşturmak <xref:System.ServiceModel.ChannelFactory> içinde bir `using` aşağıdaki kodda gösterildiği gibi engelleyin.</span><span class="sxs-lookup"><span data-stu-id="b14df-126">Create an instance of <xref:System.ServiceModel.ChannelFactory> within a `using` block, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
     [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]  
  
2.  <span data-ttu-id="b14df-127">Kanal oluşturun ve aşağıdaki kodda gösterildiği gibi hizmet çağırın.</span><span class="sxs-lookup"><span data-stu-id="b14df-127">Create the channel and call the service, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
     [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]  
  
### <a name="to-close-the-service-host"></a><span data-ttu-id="b14df-128">Hizmet ana bilgisayarı kapatmak için</span><span class="sxs-lookup"><span data-stu-id="b14df-128">To close the service host</span></span>  
  
1.  <span data-ttu-id="b14df-129">Aşağıdaki kodda gösterildiği gibi hizmet ana bilgisayarını kapatın.</span><span class="sxs-lookup"><span data-stu-id="b14df-129">Close the service host, as shown in the following code.</span></span>  
  
     [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
     [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="b14df-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="b14df-130">Example</span></span>  
 <span data-ttu-id="b14df-131">Bu konu için tam kod verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b14df-131">The following is the full code listing for this topic.</span></span>  
  
 [!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
 [!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b14df-132">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b14df-132">Compiling the Code</span></span>  
 <span data-ttu-id="b14df-133">Adını da derlerken System.ServiceModel.dll ve System.ServiceModel.Web.dll başvuru.</span><span class="sxs-lookup"><span data-stu-id="b14df-133">When compiling Service.cs, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b14df-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b14df-134">See Also</span></span>  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Web.WebGetAttribute>  
 <xref:System.ServiceModel.Web.WebInvokeAttribute>  
 <xref:System.ServiceModel.Web.WebServiceHost>  
 <xref:System.ServiceModel.ChannelFactory>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [<span data-ttu-id="b14df-135">WCF Web HTTP programlama modeli</span><span class="sxs-lookup"><span data-stu-id="b14df-135">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
