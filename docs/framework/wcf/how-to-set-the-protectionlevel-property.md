---
title: 'Nasıl yapılır: ProtectionLevel Özelliğini Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 3d4e8f80-0f9e-4a26-9899-beb6584e78df
ms.openlocfilehash: 222fda180923cdc7b0d7b7ab413c151c69add259
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950973"
---
# <a name="how-to-set-the-protectionlevel-property"></a><span data-ttu-id="e2eb5-102">Nasıl yapılır: ProtectionLevel Özelliğini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="e2eb5-102">How to: Set the ProtectionLevel Property</span></span>
<span data-ttu-id="e2eb5-103">Uygun bir öznitelik uygulayıp özelliği ayarlayarak koruma düzeyini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2eb5-103">You can set the protection level by applying an appropriate attribute and setting the property.</span></span> <span data-ttu-id="e2eb5-104">Her iletinin tüm bölümlerini etkilemek için hizmet düzeyinde koruma ayarlayabilir veya yöntemlerle ileti bölümlerine kadar artan parçalı düzeylerde koruma ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2eb5-104">You can set protection at the service level to affect all parts of every message, or you can set protection at increasingly granular levels, from methods to message parts.</span></span> <span data-ttu-id="e2eb5-105">`ProtectionLevel` Özelliği hakkında daha fazla bilgi için bkz. [koruma düzeyini anlama](../../../docs/framework/wcf/understanding-protection-level.md).</span><span class="sxs-lookup"><span data-stu-id="e2eb5-105">For more information about the `ProtectionLevel` property, see [Understanding Protection Level](../../../docs/framework/wcf/understanding-protection-level.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2eb5-106">Yapılandırma bölümünde değil, yalnızca kodda koruma düzeylerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2eb5-106">You can set protection levels only in code, not in configuration.</span></span>  
  
### <a name="to-sign-all-messages-for-a-service"></a><span data-ttu-id="e2eb5-107">Bir hizmetin tüm iletilerini imzalamak için</span><span class="sxs-lookup"><span data-stu-id="e2eb5-107">To sign all messages for a service</span></span>  
  
1. <span data-ttu-id="e2eb5-108">Hizmet için bir arabirim oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e2eb5-108">Create an interface for the service.</span></span>  
  
2. <span data-ttu-id="e2eb5-109">Özniteliğini hizmetine uygulayın ve aşağıdaki kodda gösterildiği gibi <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> özelliğini <xref:System.Net.Security.ProtectionLevel.Sign>olarak ayarlayın (varsayılan düzeyi <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>). <xref:System.ServiceModel.ServiceContractAttribute></span><span class="sxs-lookup"><span data-stu-id="e2eb5-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the service and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code (the default level is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).</span></span>  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a><span data-ttu-id="e2eb5-110">Bir işlemin tüm ileti parçalarını imzalamak için</span><span class="sxs-lookup"><span data-stu-id="e2eb5-110">To sign all message parts for an operation</span></span>  
  
1. <span data-ttu-id="e2eb5-111">Hizmet için bir arabirim oluşturun ve <xref:System.ServiceModel.ServiceContractAttribute> özniteliği arabirimine uygulayın.</span><span class="sxs-lookup"><span data-stu-id="e2eb5-111">Create an interface for the service and apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
2. <span data-ttu-id="e2eb5-112">Arabirime bir yöntem bildirimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e2eb5-112">Add a method declaration to the interface.</span></span>  
  
3. <span data-ttu-id="e2eb5-113">Özniteliğini yöntemine uygulayın ve aşağıdaki kodda gösterildiği gibi <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> özelliğini olarak <xref:System.Net.Security.ProtectionLevel.Sign>ayarlayın. <xref:System.ServiceModel.OperationContractAttribute></span><span class="sxs-lookup"><span data-stu-id="e2eb5-113">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to the method, and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a><span data-ttu-id="e2eb5-114">Hata Iletilerini koruma</span><span class="sxs-lookup"><span data-stu-id="e2eb5-114">Protecting Fault Messages</span></span>  
 <span data-ttu-id="e2eb5-115">Bir hizmette oluşturulan özel durumlar, bir istemciye SOAP hatası olarak gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="e2eb5-115">Exceptions that are thrown on a service can be sent to a client as SOAP faults.</span></span> <span data-ttu-id="e2eb5-116">Türü kesin belirlenmiş hatalar oluşturma hakkında daha fazla bilgi için bkz. [sözleşmelerdeki ve hizmetlerde hataları belirtme ve işleme](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) ve [nasıl yapılır: Hizmet sözleşmeleri](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md)hatalarını bildirin.</span><span class="sxs-lookup"><span data-stu-id="e2eb5-116">For more information about creating strongly typed faults, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) and [How to: Declare Faults in Service Contracts](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md).</span></span>  
  
#### <a name="to-protect-a-fault-message"></a><span data-ttu-id="e2eb5-117">Bir hata iletisini korumak için</span><span class="sxs-lookup"><span data-stu-id="e2eb5-117">To protect a fault message</span></span>  
  
1. <span data-ttu-id="e2eb5-118">Hata iletisini temsil eden bir tür oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e2eb5-118">Create a type that represents the fault message.</span></span> <span data-ttu-id="e2eb5-119">Aşağıdaki örnek, iki alanı olan adlı `MathFault` bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e2eb5-119">The following example creates a class named `MathFault` with two fields.</span></span>  
  
2. <span data-ttu-id="e2eb5-120">Aşağıdaki kodda gösterildiği gibi, <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliğinitürüneveserileştirilmesigerekenheralanabirözniteliğeuygulayın.<xref:System.Runtime.Serialization.DataContractAttribute></span><span class="sxs-lookup"><span data-stu-id="e2eb5-120">Apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the type and a <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each field that should be serialized, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3. <span data-ttu-id="e2eb5-121">Hatayı döndürecek arabirimde, <xref:System.ServiceModel.FaultContractAttribute> özniteliği hatayı döndürecek yönteme uygulayın ve `detailType` parametreyi hata sınıfının türü olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e2eb5-121">In the interface that will return the fault, apply the <xref:System.ServiceModel.FaultContractAttribute> attribute to the method that will return the fault and set the `detailType` parameter to the type of the fault class.</span></span>  
  
4. <span data-ttu-id="e2eb5-122">Ayrıca oluşturucuda, aşağıdaki kodda gösterildiği gibi <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> özelliğini olarak <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e2eb5-122">Also in the constructor, set the <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a><span data-ttu-id="e2eb5-123">Ileti parçalarını koruma</span><span class="sxs-lookup"><span data-stu-id="e2eb5-123">Protecting Message Parts</span></span>  
 <span data-ttu-id="e2eb5-124">İleti parçalarını korumak için bir ileti sözleşmesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="e2eb5-124">Use a message contract to protect parts of a message.</span></span> <span data-ttu-id="e2eb5-125">İleti sözleşmeleri hakkında daha fazla bilgi için bkz. [Ileti sözleşmelerini kullanma](../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="e2eb5-125">For more information about message contracts, see [Using Message Contracts](../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span></span>  
  
#### <a name="to-protect-a-message-body"></a><span data-ttu-id="e2eb5-126">İleti gövdesini korumak için</span><span class="sxs-lookup"><span data-stu-id="e2eb5-126">To protect a message body</span></span>  
  
1. <span data-ttu-id="e2eb5-127">İletiyi temsil eden bir tür oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e2eb5-127">Create a type that represents the message.</span></span> <span data-ttu-id="e2eb5-128">Aşağıdaki örnek, `CompanyName` iki alan `Company` ve `CompanyID`içeren bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e2eb5-128">The following example creates a `Company` class with two fields, `CompanyName` and `CompanyID`.</span></span>  
  
2. <span data-ttu-id="e2eb5-129">Özniteliğini sınıfına uygulayın ve <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> özelliğini olarak <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>ayarlayın. <xref:System.ServiceModel.MessageContractAttribute></span><span class="sxs-lookup"><span data-stu-id="e2eb5-129">Apply the <xref:System.ServiceModel.MessageContractAttribute> attribute to the class and set the <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
3. <span data-ttu-id="e2eb5-130">Özniteliğini, <xref:System.ServiceModel.MessageHeaderAttribute> ileti üst bilgisi olarak ifade edilecek bir alana uygulayın ve `ProtectionLevel` özelliğini olarak <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e2eb5-130">Apply the <xref:System.ServiceModel.MessageHeaderAttribute> attribute to a field that will be expressed as a message header and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
4. <span data-ttu-id="e2eb5-131">İleti gövdesinin bir parçası olarak ifade edilecek herhangi bir alana uygulayın ve aşağıdaki örnekte gösterildiği gibi `ProtectionLevel` özelliğini olarak <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>ayarlayın. <xref:System.ServiceModel.MessageBodyMemberAttribute></span><span class="sxs-lookup"><span data-stu-id="e2eb5-131">Apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to any field that will be expressed as part of the message body, and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following example.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="e2eb5-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="e2eb5-132">Example</span></span>  
 <span data-ttu-id="e2eb5-133">Aşağıdaki örnek, bir hizmetin `ProtectionLevel` çeşitli yerlerinde birkaç öznitelik sınıfının özelliğini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e2eb5-133">The following example sets the `ProtectionLevel` property of several attribute classes at various places in a service.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e2eb5-134">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e2eb5-134">Compiling the Code</span></span>  
 <span data-ttu-id="e2eb5-135">Aşağıdaki kod, örnek kodu derlemek için gereken ad alanlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2eb5-135">The following code shows the namespaces required to compile the example code.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="e2eb5-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2eb5-136">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- [<span data-ttu-id="e2eb5-137">Koruma Düzeylerini Anlama</span><span class="sxs-lookup"><span data-stu-id="e2eb5-137">Understanding Protection Level</span></span>](../../../docs/framework/wcf/understanding-protection-level.md)
