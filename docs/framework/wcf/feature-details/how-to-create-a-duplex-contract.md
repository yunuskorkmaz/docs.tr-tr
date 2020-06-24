---
title: 'Nasıl yapılır: Çift Yönlü Sözleşme Oluşturma'
description: WCF istemcilerinin ve sunucularının birbirleriyle bağımsız olarak iletişim kurmasına izin veren bir çift yönlü sözleşme yapmayı öğrenin. Birbirlerine çağrılar başlatabilir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
ms.openlocfilehash: 9320e5b36b8faba3602fbe1df1b95c05dcc7fa7e
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247097"
---
# <a name="how-to-create-a-duplex-contract"></a><span data-ttu-id="8146d-104">Nasıl yapılır: Çift Yönlü Sözleşme Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8146d-104">How to: Create a Duplex Contract</span></span>
<span data-ttu-id="8146d-105">Bu konuda, çift yönlü (çift yönlü) bir sözleşme kullanan Yöntemler oluşturmaya yönelik temel adımlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8146d-105">This topic shows the basic steps to create methods that use a duplex (two-way) contract.</span></span> <span data-ttu-id="8146d-106">Çift yönlü bir anlaşma, istemcilerin ve sunucuların birbirleriyle her ikisi ile iletişim kurmasına olanak tanır; böylece birbirlerine çağrı başlatabilir.</span><span class="sxs-lookup"><span data-stu-id="8146d-106">A duplex contract allows clients and servers to communicate with each other independently so that either can initiate calls to the other.</span></span> <span data-ttu-id="8146d-107">Çift yönlü sözleşme Windows Communication Foundation (WCF) Hizmetleri için kullanılabilen üç ileti deseninden biridir.</span><span class="sxs-lookup"><span data-stu-id="8146d-107">The duplex contract is one of three message patterns available to Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="8146d-108">Diğer iki ileti deseni tek yönlü ve istek-yanıt ' dir.</span><span class="sxs-lookup"><span data-stu-id="8146d-108">The other two message patterns are one-way and request-reply.</span></span> <span data-ttu-id="8146d-109">Çift yönlü sözleşme, istemci ve sunucu arasındaki 2 1 yönlü sözleşmelerden oluşur ve yöntemin bağıntılı olmasını gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="8146d-109">A duplex contract consists of two one-way contracts between the client and the server and does not require that the method calls be correlated.</span></span> <span data-ttu-id="8146d-110">Hizmetiniz daha fazla bilgi için istemciyi sorgulayıp istemci üzerinde açık bir olay oluşturması gerektiğinde bu tür bir sözleşmeyi kullanın.</span><span class="sxs-lookup"><span data-stu-id="8146d-110">Use this kind of contract when your service must query the client for more information or explicitly raise events on the client.</span></span> <span data-ttu-id="8146d-111">Bir çift yönlü sözleşme için istemci uygulaması oluşturma hakkında daha fazla bilgi için bkz. [nasıl yapılır: çift yönlü sözleşme Ile hizmetlere erişme](how-to-access-services-with-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="8146d-111">For more information about creating a client application for a duplex contract, see [How to: Access Services with a Duplex Contract](how-to-access-services-with-a-duplex-contract.md).</span></span> <span data-ttu-id="8146d-112">Çalışan bir örnek için bkz. [çift yönlü](../samples/duplex.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="8146d-112">For a working sample, see the [Duplex](../samples/duplex.md) sample.</span></span>  
  
### <a name="to-create-a-duplex-contract"></a><span data-ttu-id="8146d-113">Çift yönlü sözleşme oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="8146d-113">To create a duplex contract</span></span>  
  
1. <span data-ttu-id="8146d-114">Çift yönlü sözleşmenin sunucu tarafını oluşturan arabirimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8146d-114">Create the interface that makes up the server side of the duplex contract.</span></span>  
  
2. <span data-ttu-id="8146d-115"><xref:System.ServiceModel.ServiceContractAttribute>Sınıfı arabirime uygulayın.</span><span class="sxs-lookup"><span data-stu-id="8146d-115">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3. <span data-ttu-id="8146d-116">Arabirimde Yöntem imzalarını bildirin.</span><span class="sxs-lookup"><span data-stu-id="8146d-116">Declare the method signatures in the interface.</span></span>  
  
4. <span data-ttu-id="8146d-117">Sınıfı, <xref:System.ServiceModel.OperationContractAttribute> ortak sözleşmenin bir parçası olması gereken her yöntem imzasına uygulayın.</span><span class="sxs-lookup"><span data-stu-id="8146d-117">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
5. <span data-ttu-id="8146d-118">Hizmetin istemcide çağırabileceği işlem kümesini tanımlayan geri arama arabirimini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8146d-118">Create the callback interface that defines the set of operations that the service can invoke on the client.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6. <span data-ttu-id="8146d-119">Çağrı arabirimindeki Yöntem imzalarını bildirin.</span><span class="sxs-lookup"><span data-stu-id="8146d-119">Declare the method signatures in the callback interface.</span></span>  
  
7. <span data-ttu-id="8146d-120">Sınıfı, <xref:System.ServiceModel.OperationContractAttribute> ortak sözleşmenin bir parçası olması gereken her yöntem imzasına uygulayın.</span><span class="sxs-lookup"><span data-stu-id="8146d-120">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
8. <span data-ttu-id="8146d-121"><xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A>Birincil arabirimdeki özelliği geri çağırma arabiriminin türüne ayarlayarak iki arabirimi çift yönlü bir sözleşmeye bağlayın.</span><span class="sxs-lookup"><span data-stu-id="8146d-121">Link the two interfaces into a duplex contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> property in the primary interface to the type of the callback interface.</span></span>  
  
### <a name="to-call-methods-on-the-client"></a><span data-ttu-id="8146d-122">İstemcideki yöntemleri çağırmak için</span><span class="sxs-lookup"><span data-stu-id="8146d-122">To call methods on the client</span></span>  
  
1. <span data-ttu-id="8146d-123">Hizmetin birincil sözleşme uygulamasında geri çağırma arabirimi için bir değişken bildirin.</span><span class="sxs-lookup"><span data-stu-id="8146d-123">In the service's implementation of the primary contract, declare a variable for the callback interface.</span></span>  
  
2. <span data-ttu-id="8146d-124">Değişkenini, sınıfının metodu tarafından döndürülen nesne başvurusu olarak ayarlayın <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> <xref:System.ServiceModel.OperationContext> .</span><span class="sxs-lookup"><span data-stu-id="8146d-124">Set the variable to the object reference returned by the <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> method of the <xref:System.ServiceModel.OperationContext> class.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3. <span data-ttu-id="8146d-125">Geri çağırma arabirimi tarafından tanımlanan yöntemleri çağırın.</span><span class="sxs-lookup"><span data-stu-id="8146d-125">Call the methods defined by the callback interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8146d-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="8146d-126">Example</span></span>  
 <span data-ttu-id="8146d-127">Aşağıdaki kod örneği çift yönlü iletişimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="8146d-127">The following code example demonstrates duplex communication.</span></span> <span data-ttu-id="8146d-128">Hizmetin sözleşmesi, ileri ve geri gitmek için hizmet işlemlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="8146d-128">The service’s contract contains service operations for moving forward and backward.</span></span> <span data-ttu-id="8146d-129">İstemci sözleşmesi, konumunu raporlamak için bir hizmet işlemi içerir.</span><span class="sxs-lookup"><span data-stu-id="8146d-129">The client’s contract contains a service operation for reporting its position.</span></span>  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
- <span data-ttu-id="8146d-130"><xref:System.ServiceModel.ServiceContractAttribute>Ve özniteliklerinin uygulanması, <xref:System.ServiceModel.OperationContractAttribute> Web Hizmetleri Açıklama DILI (wsdl) içinde hizmet sözleşmesi tanımlarının otomatik olarak oluşturulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8146d-130">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes allows the automatic generation of service contract definitions in the Web Services Description Language (WSDL).</span></span>  
  
- <span data-ttu-id="8146d-131">İstemci için WSDL belgesi ve (isteğe bağlı) kodu ve yapılandırmasını almak üzere [ServiceModel meta veri yardımcı programı aracını (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="8146d-131">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to retrieve the WSDL document and (optional) code and configuration for a client.</span></span>  
  
- <span data-ttu-id="8146d-132">Çift yönlü hizmetleri açığa çıkaran uç noktalar güvenli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8146d-132">Endpoints exposing duplex services must be secured.</span></span> <span data-ttu-id="8146d-133">Bir hizmet çift yönlü bir ileti aldığında, yanıtın nereye gönderileceğini belirlemede bu gelen iletideki ReplyTo 'ya bakar.</span><span class="sxs-lookup"><span data-stu-id="8146d-133">When a service receives a duplex message, it looks at the ReplyTo in that incoming message to determine where to send the reply.</span></span> <span data-ttu-id="8146d-134">Kanal güvenli değilse, güvenilir olmayan bir istemci hedef makinenin ReplyTo olan kötü amaçlı bir ileti gönderebilir ve hedef makinenin hizmet reddine neden olur.</span><span class="sxs-lookup"><span data-stu-id="8146d-134">If the channel is not secured, then an untrusted client could send a malicious message with a target machine's ReplyTo, leading to a denial of service of the target machine.</span></span> <span data-ttu-id="8146d-135">Normal istek-yanıt iletileriyle bu bir sorun değildir, çünkü ReplyTo yoksayıldı ve yanıt özgün iletinin tarihinde geldiği kanalda gönderilir.</span><span class="sxs-lookup"><span data-stu-id="8146d-135">With regular request-reply messages, this is not an issue, because the ReplyTo is ignored and the response is sent on the channel the original message came in on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8146d-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8146d-136">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="8146d-137">Nasıl yapılır: Çift Yönlü Sözleşme ile Hizmetlere Erişme</span><span class="sxs-lookup"><span data-stu-id="8146d-137">How to: Access Services with a Duplex Contract</span></span>](how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="8146d-138">Çift Yönlü</span><span class="sxs-lookup"><span data-stu-id="8146d-138">Duplex</span></span>](../samples/duplex.md)
- [<span data-ttu-id="8146d-139">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="8146d-139">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)
- [<span data-ttu-id="8146d-140">Nasıl yapılır: Bir Hizmet Anlaşması Tanımlama</span><span class="sxs-lookup"><span data-stu-id="8146d-140">How to: Define a Service Contract</span></span>](../how-to-define-a-wcf-service-contract.md)
- [<span data-ttu-id="8146d-141">Oturum</span><span class="sxs-lookup"><span data-stu-id="8146d-141">Session</span></span>](../samples/session.md)
