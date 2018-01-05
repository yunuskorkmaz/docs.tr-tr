---
title: "Nasıl yapılır: ProtectionLevel Özelliğini Ayarlama"
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
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 3d4e8f80-0f9e-4a26-9899-beb6584e78df
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9b90df85259dfe48f071ca2b4b8404cfe8e673e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-protectionlevel-property"></a><span data-ttu-id="ad0e1-102">Nasıl yapılır: ProtectionLevel Özelliğini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="ad0e1-102">How to: Set the ProtectionLevel Property</span></span>
<span data-ttu-id="ad0e1-103">Uygun bir öznitelik uygulama ve özelliğini ayarlayarak koruma düzeyi ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad0e1-103">You can set the protection level by applying an appropriate attribute and setting the property.</span></span> <span data-ttu-id="ad0e1-104">Her ileti tüm parçalarını etkilemek için hizmet düzeyinde koruma ayarlayabilirsiniz veya yöntemlerden ileti bölümleri için giderek daha çok parçalı düzeyde koruma ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad0e1-104">You can set protection at the service level to affect all parts of every message, or you can set protection at increasingly granular levels, from methods to message parts.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="ad0e1-105">`ProtectionLevel` özelliği, bkz: [anlama koruma düzeyi](../../../docs/framework/wcf/understanding-protection-level.md).</span><span class="sxs-lookup"><span data-stu-id="ad0e1-105"> the `ProtectionLevel` property, see [Understanding Protection Level](../../../docs/framework/wcf/understanding-protection-level.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad0e1-106">Koruma düzeyleri yalnızca kodda, yapılandırmada yok ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad0e1-106">You can set protection levels only in code, not in configuration.</span></span>  
  
### <a name="to-sign-all-messages-for-a-service"></a><span data-ttu-id="ad0e1-107">Bir hizmet için tüm iletileri imzalamak için</span><span class="sxs-lookup"><span data-stu-id="ad0e1-107">To sign all messages for a service</span></span>  
  
1.  <span data-ttu-id="ad0e1-108">Hizmet için bir arabirimi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ad0e1-108">Create an interface for the service.</span></span>  
  
2.  <span data-ttu-id="ad0e1-109">Uygulama <xref:System.ServiceModel.ServiceContractAttribute> özniteliği hizmete ve ayarlayın <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> özelliğine <xref:System.Net.Security.ProtectionLevel.Sign>aşağıdaki kodda gösterildiği gibi (varsayılan düzeyi <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).</span><span class="sxs-lookup"><span data-stu-id="ad0e1-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the service and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code (the default level is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).</span></span>  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a><span data-ttu-id="ad0e1-110">Bir işlem için tüm ileti bölümleri imzalamak için</span><span class="sxs-lookup"><span data-stu-id="ad0e1-110">To sign all message parts for an operation</span></span>  
  
1.  <span data-ttu-id="ad0e1-111">Hizmeti için bir arabirim oluşturma ve uygulama <xref:System.ServiceModel.ServiceContractAttribute> özniteliği için arabirim.</span><span class="sxs-lookup"><span data-stu-id="ad0e1-111">Create an interface for the service and apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
2.  <span data-ttu-id="ad0e1-112">Bir yöntem bildirimi arabirimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ad0e1-112">Add a method declaration to the interface.</span></span>  
  
3.  <span data-ttu-id="ad0e1-113">Uygulama <xref:System.ServiceModel.OperationContractAttribute> özniteliğini yöntemine ve ayarlayın <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> özelliğine <xref:System.Net.Security.ProtectionLevel.Sign>aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="ad0e1-113">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to the method, and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a><span data-ttu-id="ad0e1-114">Koruma hata iletileri</span><span class="sxs-lookup"><span data-stu-id="ad0e1-114">Protecting Fault Messages</span></span>  
 <span data-ttu-id="ad0e1-115">Bir hizmette oluşturulan özel durumlar SOAP hatalarının istemciye gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="ad0e1-115">Exceptions that are thrown on a service can be sent to a client as SOAP faults.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="ad0e1-116">kesinlikle oluşturma yazılan hataları, bkz: [belirtme ve işleme hataları sözleşme ve hizmetlerde](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) ve [nasıl yapılır: hizmet sözleşmelerinde hata bildirme](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="ad0e1-116"> creating strongly typed faults, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) and [How to: Declare Faults in Service Contracts](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md).</span></span>  
  
#### <a name="to-protect-a-fault-message"></a><span data-ttu-id="ad0e1-117">Bir hata iletisi koruma</span><span class="sxs-lookup"><span data-stu-id="ad0e1-117">To protect a fault message</span></span>  
  
1.  <span data-ttu-id="ad0e1-118">Hata iletisini temsil eden bir tür oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ad0e1-118">Create a type that represents the fault message.</span></span> <span data-ttu-id="ad0e1-119">Aşağıdaki örnek adlı bir sınıf oluşturur `MathFault` iki alanlara sahip.</span><span class="sxs-lookup"><span data-stu-id="ad0e1-119">The following example creates a class named `MathFault` with two fields.</span></span>  
  
2.  <span data-ttu-id="ad0e1-120">Uygulama <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği türü ve <xref:System.Runtime.Serialization.DataMemberAttribute> aşağıdaki kodda gösterildiği gibi serileştirilmelidir, her bir alan özniteliği.</span><span class="sxs-lookup"><span data-stu-id="ad0e1-120">Apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the type and a <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each field that should be serialized, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3.  <span data-ttu-id="ad0e1-121">Hata döndürecektir arabiriminde uygulamak <xref:System.ServiceModel.FaultContractAttribute> özniteliği hataya dönün ve ayarlama yöntemi `detailType` hata sınıfı tür parametresi.</span><span class="sxs-lookup"><span data-stu-id="ad0e1-121">In the interface that will return the fault, apply the <xref:System.ServiceModel.FaultContractAttribute> attribute to the method that will return the fault and set the `detailType` parameter to the type of the fault class.</span></span>  
  
4.  <span data-ttu-id="ad0e1-122">Ayrıca oluşturucuda ayarlamak <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> özelliğine <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>aşağıdaki kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="ad0e1-122">Also in the constructor, set the <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a><span data-ttu-id="ad0e1-123">İleti bölümleri koruma</span><span class="sxs-lookup"><span data-stu-id="ad0e1-123">Protecting Message Parts</span></span>  
 <span data-ttu-id="ad0e1-124">Bir ileti kısımlarını korumak için bir ileti sözleşmesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="ad0e1-124">Use a message contract to protect parts of a message.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="ad0e1-125">ileti sözleşmeleri için bkz: [kullanarak ileti sözleşmeleri](../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="ad0e1-125"> message contracts, see [Using Message Contracts](../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span></span>  
  
#### <a name="to-protect-a-message-body"></a><span data-ttu-id="ad0e1-126">İleti gövdesi korumak için</span><span class="sxs-lookup"><span data-stu-id="ad0e1-126">To protect a message body</span></span>  
  
1.  <span data-ttu-id="ad0e1-127">İletiyi temsil eden bir tür oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ad0e1-127">Create a type that represents the message.</span></span> <span data-ttu-id="ad0e1-128">Aşağıdaki örnekte bir `Company` iki alanlarla sınıfı `CompanyName` ve `CompanyID`.</span><span class="sxs-lookup"><span data-stu-id="ad0e1-128">The following example creates a `Company` class with two fields, `CompanyName` and `CompanyID`.</span></span>  
  
2.  <span data-ttu-id="ad0e1-129">Uygulama <xref:System.ServiceModel.MessageContractAttribute> öznitelik sınıfını ve ayarlayın <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> özelliğine <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="ad0e1-129">Apply the <xref:System.ServiceModel.MessageContractAttribute> attribute to the class and set the <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
3.  <span data-ttu-id="ad0e1-130">Uygulama <xref:System.ServiceModel.MessageHeaderAttribute> özniteliği, ileti başlığı ifade edilen ve ayarlanmış bir alana `ProtectionLevel` özelliğine <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="ad0e1-130">Apply the <xref:System.ServiceModel.MessageHeaderAttribute> attribute to a field that will be expressed as a message header and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
4.  <span data-ttu-id="ad0e1-131">Uygulama <xref:System.ServiceModel.MessageBodyMemberAttribute> ileti gövdesi bir parçası olarak ifade edilen, ve ayarlanmış herhangi bir alan için `ProtectionLevel` özelliğine <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="ad0e1-131">Apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to any field that will be expressed as part of the message body, and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following example.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="ad0e1-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="ad0e1-132">Example</span></span>  
 <span data-ttu-id="ad0e1-133">Aşağıdaki örnek kümeleri `ProtectionLevel` bir hizmet çeşitli yerlerde birkaç öznitelik sınıfları özelliği.</span><span class="sxs-lookup"><span data-stu-id="ad0e1-133">The following example sets the `ProtectionLevel` property of several attribute classes at various places in a service.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ad0e1-134">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="ad0e1-134">Compiling the Code</span></span>  
 <span data-ttu-id="ad0e1-135">Aşağıdaki kod örnek kodu derlemek için gereken ad alanlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ad0e1-135">The following code shows the namespaces required to compile the example code.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="ad0e1-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ad0e1-136">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 <xref:System.ServiceModel.FaultContractAttribute>  
 <xref:System.ServiceModel.MessageContractAttribute>  
 <xref:System.ServiceModel.MessageBodyMemberAttribute>  
 [<span data-ttu-id="ad0e1-137">Koruma Düzeylerini Anlama</span><span class="sxs-lookup"><span data-stu-id="ad0e1-137">Understanding Protection Level</span></span>](../../../docs/framework/wcf/understanding-protection-level.md)
