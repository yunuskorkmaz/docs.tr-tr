---
title: "Nasıl yapılır: Çift Yönlü Sözleşme Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- duplex contracts [WCF]
ms.assetid: 500a75b6-998a-47d5-8e3b-24e3aba2a434
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 003b07326612f3b51390d691c7bba0ef1c1b85dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-duplex-contract"></a><span data-ttu-id="c1a68-102">Nasıl yapılır: Çift Yönlü Sözleşme Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c1a68-102">How to: Create a Duplex Contract</span></span>
<span data-ttu-id="c1a68-103">Bu konuda, çift yönlü (iki yönlü) sözleşme kullanan yöntemleri oluşturmak için temel adımlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c1a68-103">This topic shows the basic steps to create methods that use a duplex (two-way) contract.</span></span> <span data-ttu-id="c1a68-104">Çift yönlü sözleşme, istemciler ve sunucular ya da diğer çağrıları başlatmak için birbiriyle bağımsız olarak iletişim kurması sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1a68-104">A duplex contract allows clients and servers to communicate with each other independently so that either can initiate calls to the other.</span></span> <span data-ttu-id="c1a68-105">Çift yönlü sözleşme kullanılabilir üç ileti modelinden biridir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Hizmetleri.</span><span class="sxs-lookup"><span data-stu-id="c1a68-105">The duplex contract is one of three message patterns available to [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services.</span></span> <span data-ttu-id="c1a68-106">Diğer iki desenleri iletisi olan tek yönlü ve istek-yanıt.</span><span class="sxs-lookup"><span data-stu-id="c1a68-106">The other two message patterns are one-way and request-reply.</span></span> <span data-ttu-id="c1a68-107">Çift yönlü sözleşme istemci ve sunucu arasında iki yönlü sözleşme oluşur ve yöntem çağrılarını ilintili olması gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="c1a68-107">A duplex contract consists of two one-way contracts between the client and the server and does not require that the method calls be correlated.</span></span> <span data-ttu-id="c1a68-108">Bu tür bir sözleşme hizmetiniz daha fazla bilgi için istemci sorgulamak veya açıkça istemci üzerindeki olaylara Yükselt kullanın.</span><span class="sxs-lookup"><span data-stu-id="c1a68-108">Use this kind of contract when your service must query the client for more information or explicitly raise events on the client.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="c1a68-109">bkz. çift yönlü bir sözleşme için bir istemci uygulaması oluşturma [nasıl yapılır: çift yönlü sözleşme ile Erişim Hizmetleri](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="c1a68-109"> creating a client application for a duplex contract, see [How to: Access Services with a Duplex Contract](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md).</span></span> <span data-ttu-id="c1a68-110">Çalışma örnek için bkz: [çift yönlü](../../../../docs/framework/wcf/samples/duplex.md) örnek.</span><span class="sxs-lookup"><span data-stu-id="c1a68-110">For a working sample, see the [Duplex](../../../../docs/framework/wcf/samples/duplex.md) sample.</span></span>  
  
### <a name="to-create-a-duplex-contract"></a><span data-ttu-id="c1a68-111">Çift yönlü sözleşme oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c1a68-111">To create a duplex contract</span></span>  
  
1.  <span data-ttu-id="c1a68-112">Çift yönlü sözleşme sunucu tarafı yapar arabirimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c1a68-112">Create the interface that makes up the server side of the duplex contract.</span></span>  
  
2.  <span data-ttu-id="c1a68-113">Uygulama <xref:System.ServiceModel.ServiceContractAttribute> arabirimi sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c1a68-113">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#3)]
     [!code-vb[S_WS_DualHttp#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#3)]  
  
3.  <span data-ttu-id="c1a68-114">Arabirimdeki yöntem imzaları bildirin.</span><span class="sxs-lookup"><span data-stu-id="c1a68-114">Declare the method signatures in the interface.</span></span>  
  
4.  <span data-ttu-id="c1a68-115">Uygulama <xref:System.ServiceModel.OperationContractAttribute> genel sözleşmesinin bir parçası olması her yöntem imzası sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c1a68-115">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
5.  <span data-ttu-id="c1a68-116">İstemcide hizmet çağırabileceği işlemler kümesini tanımlar geri çağırma arabirimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c1a68-116">Create the callback interface that defines the set of operations that the service can invoke on the client.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#4)]
     [!code-vb[S_WS_DualHttp#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#4)]  
  
6.  <span data-ttu-id="c1a68-117">Geri çağırma arabirimi yöntemi imzalarında bildirin.</span><span class="sxs-lookup"><span data-stu-id="c1a68-117">Declare the method signatures in the callback interface.</span></span>  
  
7.  <span data-ttu-id="c1a68-118">Uygulama <xref:System.ServiceModel.OperationContractAttribute> genel sözleşmesinin bir parçası olması her yöntem imzası sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c1a68-118">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method signature that must be part of the public contract.</span></span>  
  
8.  <span data-ttu-id="c1a68-119">Ayarlayarak çift yönlü bir sözleşme iki arabirim bağlantı <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> türde bir geri çağırma arabirimi birincil arabirim özelliği.</span><span class="sxs-lookup"><span data-stu-id="c1a68-119">Link the two interfaces into a duplex contract by setting the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> property in the primary interface to the type of the callback interface.</span></span>  
  
### <a name="to-call-methods-on-the-client"></a><span data-ttu-id="c1a68-120">İstemcide yöntemleri çağırmak için</span><span class="sxs-lookup"><span data-stu-id="c1a68-120">To call methods on the client</span></span>  
  
1.  <span data-ttu-id="c1a68-121">Birincil sözleşme hizmetin uygulamasında geri çağırma arabirimi için bir değişken bildirin.</span><span class="sxs-lookup"><span data-stu-id="c1a68-121">In the service's implementation of the primary contract, declare a variable for the callback interface.</span></span>  
  
2.  <span data-ttu-id="c1a68-122">Tarafından döndürülen nesne başvuru değişkenini <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> yöntemi <xref:System.ServiceModel.OperationContext> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c1a68-122">Set the variable to the object reference returned by the <xref:System.ServiceModel.OperationContext.GetCallbackChannel%2A> method of the <xref:System.ServiceModel.OperationContext> class.</span></span>  
  
     [!code-csharp[S_WS_DualHttp#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#1)]
     [!code-vb[S_WS_DualHttp#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#1)]  
  
     [!code-csharp[S_WS_DualHttp#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#2)]
     [!code-vb[S_WS_DualHttp#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#2)]  
  
3.  <span data-ttu-id="c1a68-123">Geri çağırma arabirimi tarafından tanımlanan yöntemler çağırın.</span><span class="sxs-lookup"><span data-stu-id="c1a68-123">Call the methods defined by the callback interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1a68-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1a68-124">Example</span></span>  
 <span data-ttu-id="c1a68-125">Aşağıdaki kod örneğinde, çift yönlü iletişimi gösterir.</span><span class="sxs-lookup"><span data-stu-id="c1a68-125">The following code example demonstrates duplex communication.</span></span> <span data-ttu-id="c1a68-126">Hizmetin sözleşme taşıma için hizmet işlemleri ileriye ve geriye doğru içerir.</span><span class="sxs-lookup"><span data-stu-id="c1a68-126">The service’s contract contains service operations for moving forward and backward.</span></span> <span data-ttu-id="c1a68-127">İstemcinin sözleşme konumuna raporlama için bir hizmet işlemi içerir.</span><span class="sxs-lookup"><span data-stu-id="c1a68-127">The client’s contract contains a service operation for reporting its position.</span></span>  
  
 [!code-csharp[S_WS_DualHttp#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ws_dualhttp/cs/service.cs#5)]
 [!code-vb[S_WS_DualHttp#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_ws_dualhttp/vb/service.vb#5)]  
  
-   <span data-ttu-id="c1a68-128">Uygulama <xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> öznitelikleri Web Hizmetleri Açıklama Dili (WSDL) hizmet sözleşmesi tanımları otomatik olarak oluşturulmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1a68-128">Applying the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes allows the automatic generation of service contract definitions in the Web Services Description Language (WSDL).</span></span>  
  
-   <span data-ttu-id="c1a68-129">Kullanım [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) WSDL belgesi (isteğe bağlı) kodu ve bir istemci için yapılandırma alınamadı.</span><span class="sxs-lookup"><span data-stu-id="c1a68-129">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to retrieve the WSDL document and (optional) code and configuration for a client.</span></span>  
  
-   <span data-ttu-id="c1a68-130">Çift yönlü hizmetler gösterme uç noktalarını güvenli hale getirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="c1a68-130">Endpoints exposing duplex services must be secured.</span></span> <span data-ttu-id="c1a68-131">Bir hizmet çift yönlü bir ileti aldığında, yanıt gönderileceği yeri belirlemek için bu gelen iletide ReplyTo bakar.</span><span class="sxs-lookup"><span data-stu-id="c1a68-131">When a service receives a duplex message, it looks at the ReplyTo in that incoming message to determine where to send the reply.</span></span> <span data-ttu-id="c1a68-132">Ardından kanal sağlanmazsa, güvenilmeyen bir istemci hedef makine hizmet reddine için önde gelen bir hedef makinenin ReplyTo içeren kötü amaçlı bir ileti gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="c1a68-132">If the channel is not secured, then an untrusted client could send a malicious message with a target machine's ReplyTo, leading to a denial of service of the target machine.</span></span> <span data-ttu-id="c1a68-133">Normal istek-yanıt iletileri, bu bir sorun ReplyTo dikkate alınmaz ve orijinal iletinin geldiği üzerinde kanalda gönderilen yanıtı olmadığından.</span><span class="sxs-lookup"><span data-stu-id="c1a68-133">With regular request-reply messages, this is not an issue, because the ReplyTo is ignored and the response is sent on the channel the original message came in on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1a68-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c1a68-134">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [<span data-ttu-id="c1a68-135">Nasıl yapılır: Çift Yönlü Sözleşme ile Hizmetlere Erişme</span><span class="sxs-lookup"><span data-stu-id="c1a68-135">How to: Access Services with a Duplex Contract</span></span>](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)  
 [<span data-ttu-id="c1a68-136">Çift Yönlü</span><span class="sxs-lookup"><span data-stu-id="c1a68-136">Duplex</span></span>](../../../../docs/framework/wcf/samples/duplex.md)  
 [<span data-ttu-id="c1a68-137">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="c1a68-137">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [<span data-ttu-id="c1a68-138">Nasıl yapılır: Bir Hizmet Anlaşması Tanımlama</span><span class="sxs-lookup"><span data-stu-id="c1a68-138">How to: Define a Service Contract</span></span>](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [<span data-ttu-id="c1a68-139">Oturum</span><span class="sxs-lookup"><span data-stu-id="c1a68-139">Session</span></span>](../../../../docs/framework/wcf/samples/session.md)
