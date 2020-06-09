---
title: 'Nasıl yapılır: Çift Yönlü Sözleşme Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
ms.openlocfilehash: e5b6c7eecce08a23490b6ab1991e4561d9462469
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598989"
---
# <a name="how-to-create-a-duplex-contract"></a><span data-ttu-id="5708c-102">Nasıl yapılır: Çift Yönlü Sözleşme Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5708c-102">How to: Create a Duplex Contract</span></span>
<span data-ttu-id="5708c-103">Bu konuda, çift yönlü (çift yönlü) bir sözleşme kullanan Yöntemler oluşturmaya yönelik temel adımlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5708c-103">This topic shows the basic steps to create methods that use a duplex (two-way) contract.</span></span> <span data-ttu-id="5708c-104">Çift yönlü bir anlaşma, istemcilerin ve sunucuların birbirleriyle her ikisi ile iletişim kurmasına olanak tanır; böylece birbirlerine çağrı başlatabilir.</span><span class="sxs-lookup"><span data-stu-id="5708c-104">A duplex contract allows clients and servers to communicate with each other independently so that either can initiate calls to the other.</span></span> <span data-ttu-id="5708c-105">Çift yönlü sözleşme Windows Communication Foundation (WCF) Hizmetleri için kullanılabilen üç ileti deseninden biridir.</span><span class="sxs-lookup"><span data-stu-id="5708c-105">The duplex contract is one of three message patterns available to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="5708c-106">Diğer iki ileti deseni tek yönlü ve istek-yanıt ' dir.</span><span class="sxs-lookup"><span data-stu-id="5708c-106">The other two message patterns are one-way and request-reply.</span></span> <span data-ttu-id="5708c-107">Çift yönlü sözleşme, istemci ve sunucu arasındaki 2 1 yönlü sözleşmelerden oluşur ve yöntemin bağıntılı olmasını gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="5708c-107">A duplex contract consists of two one-way contracts between the client and the server and does not require that the method calls be correlated.</span></span> <span data-ttu-id="5708c-108">Hizmetiniz daha fazla bilgi için istemciyi sorgulayıp istemci üzerinde açık bir olay oluşturması gerektiğinde bu tür bir sözleşmeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="5708c-108">Use this kind of contract when your service must query the client for more information or explicitly raise events on the client.</span></span> <span data-ttu-id="5708c-109">Bir çift yönlü sözleşme için istemci uygulaması oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: çift yönlü sözleşme Ile hizmetlere erişme](how-to-access-services-with-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="5708c-109">For more information about creating a client application for a duplex contract, see [How to: Access Services with a Duplex Contract](how-to-access-services-with-a-duplex-contract.md).</span></span> <span data-ttu-id="5708c-110">Çalışan bir örnek için bkz. [çift yönlü](../samples/duplex.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="5708c-110">For a working sample, see the [Duplex](../samples/duplex.md) sample.</span></span>  
  
### <a name="to-create-a-duplex-contract"></a><span data-ttu-id="5708c-111">Çift yönlü sözleşme oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="5708c-111">To create a duplex contract</span></span>  
  
1. <span data-ttu-id="5708c-112">Çift yönlü sözleşmenin sunucu tarafını oluşturan arabirimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5708c-112">Create the interface that makes up the server side of the duplex contract.</span></span>  
  
2. <span data-ttu-id="5708c-113"><xref:System.ServiceModel.ServiceContractAttribute>Sınıfı arabirime uygulayın.</span><span class="sxs-lookup"><span data-stu-id="5708c-113">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3. <span data-ttu-id="5708c-114">Arabirimde Yöntem imzalarını bildirin.</span><span class="sxs-lookup"><span data-stu-id="5708c-114">Declare the method signatures in the interface.</span></span>  
  
4. <span data-ttu-id="5708c-115">Sınıfı, <xref:System.ServiceModel.OperationContractAttribute> ortak sözleşmenin bir parçası olması gereken her yöntem imzasına uygulayın.</span><span class="sxs-lookup"><span data-stu-id="5708c-115">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
5. <span data-ttu-id="5708c-116">Hizmetin istemcide çağırabileceği işlem kümesini tanımlayan geri arama arabirimini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5708c-116">Create the callback interface that defines the set of operations that the service can invoke on the client.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6. <span data-ttu-id="5708c-117">Çağrı arabirimindeki Yöntem imzalarını bildirin.</span><span class="sxs-lookup"><span data-stu-id="5708c-117">Declare the method signatures in the callback interface.</span></span>  
  
7. <span data-ttu-id="5708c-118">Sınıfı, <xref:System.ServiceModel.OperationContractAttribute> ortak sözleşmenin bir parçası olması gereken her yöntem imzasına uygulayın.</span><span class="sxs-lookup"><span data-stu-id="5708c-118">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
8. <span data-ttu-id="5708c-119"><xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A>Birincil arabirimdeki özelliği geri çağırma arabiriminin türüne ayarlayarak iki arabirimi çift yönlü bir sözleşmeye bağlayın.</span><span class="sxs-lookup"><span data-stu-id="5708c-119">Link the two interfaces into a duplex contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> property in the primary interface to the type of the callback interface.</span></span>  
  
### <a name="to-call-methods-on-the-client"></a><span data-ttu-id="5708c-120">İstemcideki yöntemleri çağırmak için</span><span class="sxs-lookup"><span data-stu-id="5708c-120">To call methods on the client</span></span>  
  
1. <span data-ttu-id="5708c-121">Hizmetin birincil sözleşme uygulamasında geri çağırma arabirimi için bir değişken bildirin.</span><span class="sxs-lookup"><span data-stu-id="5708c-121">In the service's implementation of the primary contract, declare a variable for the callback interface.</span></span>  
  
2. <span data-ttu-id="5708c-122">Değişkenini, sınıfının metodu tarafından döndürülen nesne başvurusu olarak ayarlayın <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> <xref:System.ServiceModel.OperationContext> .</span><span class="sxs-lookup"><span data-stu-id="5708c-122">Set the variable to the object reference returned by the <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> method of the <xref:System.ServiceModel.OperationContext> class.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3. <span data-ttu-id="5708c-123">Geri çağırma arabirimi tarafından tanımlanan yöntemleri çağırın.</span><span class="sxs-lookup"><span data-stu-id="5708c-123">Call the methods defined by the callback interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5708c-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="5708c-124">Example</span></span>  
 <span data-ttu-id="5708c-125">Aşağıdaki kod örneği çift yönlü iletişimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="5708c-125">The following code example demonstrates duplex communication.</span></span> <span data-ttu-id="5708c-126">Hizmetin sözleşmesi, ileri ve geri gitmek için hizmet işlemlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="5708c-126">The service’s contract contains service operations for moving forward and backward.</span></span> <span data-ttu-id="5708c-127">İstemci sözleşmesi, konumunu raporlamak için bir hizmet işlemi içerir.</span><span class="sxs-lookup"><span data-stu-id="5708c-127">The client’s contract contains a service operation for reporting its position.</span></span>  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
- <span data-ttu-id="5708c-128"><xref:System.ServiceModel.ServiceContractAttribute>Ve özniteliklerinin uygulanması, <xref:System.ServiceModel.OperationContractAttribute> Web Hizmetleri Açıklama DILI (wsdl) içinde hizmet sözleşmesi tanımlarının otomatik olarak oluşturulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5708c-128">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes allows the automatic generation of service contract definitions in the Web Services Description Language (WSDL).</span></span>  
  
- <span data-ttu-id="5708c-129">İstemci için WSDL belgesi ve (isteğe bağlı) kodu ve yapılandırmasını almak üzere [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="5708c-129">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to retrieve the WSDL document and (optional) code and configuration for a client.</span></span>  
  
- <span data-ttu-id="5708c-130">Çift yönlü hizmetleri açığa çıkaran uç noktalar güvenli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5708c-130">Endpoints exposing duplex services must be secured.</span></span> <span data-ttu-id="5708c-131">Bir hizmet çift yönlü bir ileti aldığında, yanıtın nereye gönderileceğini belirlemede bu gelen iletideki ReplyTo 'ya bakar.</span><span class="sxs-lookup"><span data-stu-id="5708c-131">When a service receives a duplex message, it looks at the ReplyTo in that incoming message to determine where to send the reply.</span></span> <span data-ttu-id="5708c-132">Kanal güvenli değilse, güvenilir olmayan bir istemci hedef makinenin ReplyTo olan kötü amaçlı bir ileti gönderebilir ve hedef makinenin hizmet reddine neden olur.</span><span class="sxs-lookup"><span data-stu-id="5708c-132">If the channel is not secured, then an untrusted client could send a malicious message with a target machine's ReplyTo, leading to a denial of service of the target machine.</span></span> <span data-ttu-id="5708c-133">Normal istek-yanıt iletileriyle bu bir sorun değildir, çünkü ReplyTo yoksayıldı ve yanıt özgün iletinin tarihinde geldiği kanalda gönderilir.</span><span class="sxs-lookup"><span data-stu-id="5708c-133">With regular request-reply messages, this is not an issue, because the ReplyTo is ignored and the response is sent on the channel the original message came in on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5708c-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5708c-134">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="5708c-135">Nasıl yapılır: Çift Yönlü Sözleşme ile Hizmetlere Erişme</span><span class="sxs-lookup"><span data-stu-id="5708c-135">How to: Access Services with a Duplex Contract</span></span>](how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="5708c-136">Çift Yönlü</span><span class="sxs-lookup"><span data-stu-id="5708c-136">Duplex</span></span>](../samples/duplex.md)
- [<span data-ttu-id="5708c-137">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="5708c-137">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)
- [<span data-ttu-id="5708c-138">Nasıl yapılır: Bir Hizmet Anlaşması Tanımlama</span><span class="sxs-lookup"><span data-stu-id="5708c-138">How to: Define a Service Contract</span></span>](../how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="5708c-139">Oturum</span><span class="sxs-lookup"><span data-stu-id="5708c-139">Session</span></span>](../samples/session.md)
