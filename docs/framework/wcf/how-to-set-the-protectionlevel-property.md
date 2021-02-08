---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: ProtectionLevel özelliğini ayarlama'
title: 'Nasıl yapılır: ProtectionLevel Özelliğini Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 3d4e8f80-0f9e-4a26-9899-beb6584e78df
ms.openlocfilehash: 526ed923d254f0312c9a2c6d17b7306973d88902
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779250"
---
# <a name="how-to-set-the-protectionlevel-property"></a><span data-ttu-id="b6721-103">Nasıl yapılır: ProtectionLevel Özelliğini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="b6721-103">How to: Set the ProtectionLevel Property</span></span>

<span data-ttu-id="b6721-104">Uygun bir öznitelik uygulayıp özelliği ayarlayarak koruma düzeyini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6721-104">You can set the protection level by applying an appropriate attribute and setting the property.</span></span> <span data-ttu-id="b6721-105">Her iletinin tüm bölümlerini etkilemek için hizmet düzeyinde koruma ayarlayabilir veya yöntemlerle ileti bölümlerine kadar artan parçalı düzeylerde koruma ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6721-105">You can set protection at the service level to affect all parts of every message, or you can set protection at increasingly granular levels, from methods to message parts.</span></span> <span data-ttu-id="b6721-106">Özelliği hakkında daha fazla bilgi için `ProtectionLevel` bkz. [koruma düzeyini anlama](understanding-protection-level.md).</span><span class="sxs-lookup"><span data-stu-id="b6721-106">For more information about the `ProtectionLevel` property, see [Understanding Protection Level](understanding-protection-level.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6721-107">Yapılandırma bölümünde değil, yalnızca kodda koruma düzeylerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b6721-107">You can set protection levels only in code, not in configuration.</span></span>  
  
### <a name="to-sign-all-messages-for-a-service"></a><span data-ttu-id="b6721-108">Bir hizmetin tüm iletilerini imzalamak için</span><span class="sxs-lookup"><span data-stu-id="b6721-108">To sign all messages for a service</span></span>  
  
1. <span data-ttu-id="b6721-109">Hizmet için bir arabirim oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b6721-109">Create an interface for the service.</span></span>  
  
2. <span data-ttu-id="b6721-110"><xref:System.ServiceModel.ServiceContractAttribute>Özniteliğini hizmetine uygulayın ve <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> <xref:System.Net.Security.ProtectionLevel.Sign> aşağıdaki kodda gösterildiği gibi özelliğini olarak ayarlayın (varsayılan düzeyi <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> ).</span><span class="sxs-lookup"><span data-stu-id="b6721-110">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the service and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code (the default level is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).</span></span>  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a><span data-ttu-id="b6721-111">Bir işlemin tüm ileti parçalarını imzalamak için</span><span class="sxs-lookup"><span data-stu-id="b6721-111">To sign all message parts for an operation</span></span>  
  
1. <span data-ttu-id="b6721-112">Hizmet için bir arabirim oluşturun ve <xref:System.ServiceModel.ServiceContractAttribute> özniteliği arabirimine uygulayın.</span><span class="sxs-lookup"><span data-stu-id="b6721-112">Create an interface for the service and apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
2. <span data-ttu-id="b6721-113">Arabirime bir yöntem bildirimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b6721-113">Add a method declaration to the interface.</span></span>  
  
3. <span data-ttu-id="b6721-114"><xref:System.ServiceModel.OperationContractAttribute>Özniteliğini yöntemine uygulayın ve <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> <xref:System.Net.Security.ProtectionLevel.Sign> aşağıdaki kodda gösterildiği gibi özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b6721-114">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to the method, and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a><span data-ttu-id="b6721-115">Hata Iletilerini koruma</span><span class="sxs-lookup"><span data-stu-id="b6721-115">Protecting Fault Messages</span></span>  

 <span data-ttu-id="b6721-116">Bir hizmette oluşturulan özel durumlar, bir istemciye SOAP hatası olarak gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="b6721-116">Exceptions that are thrown on a service can be sent to a client as SOAP faults.</span></span> <span data-ttu-id="b6721-117">Türü kesin belirlenmiş hatalar oluşturma hakkında daha fazla bilgi için bkz. [sözleşmelerdeki ve hizmetlerde hataları belirtme ve işleme](specifying-and-handling-faults-in-contracts-and-services.md) ve [nasıl yapılır: hizmet sözleşmelerinde hata bildirme](how-to-declare-faults-in-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="b6721-117">For more information about creating strongly typed faults, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md) and [How to: Declare Faults in Service Contracts](how-to-declare-faults-in-service-contracts.md).</span></span>  
  
#### <a name="to-protect-a-fault-message"></a><span data-ttu-id="b6721-118">Bir hata iletisini korumak için</span><span class="sxs-lookup"><span data-stu-id="b6721-118">To protect a fault message</span></span>  
  
1. <span data-ttu-id="b6721-119">Hata iletisini temsil eden bir tür oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b6721-119">Create a type that represents the fault message.</span></span> <span data-ttu-id="b6721-120">Aşağıdaki örnek, iki alanı olan adlı bir sınıf oluşturur `MathFault` .</span><span class="sxs-lookup"><span data-stu-id="b6721-120">The following example creates a class named `MathFault` with two fields.</span></span>  
  
2. <span data-ttu-id="b6721-121"><xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> Aşağıdaki kodda gösterildiği gibi, özniteliğini türüne ve serileştirilmesi gereken her alana bir özniteliğe uygulayın.</span><span class="sxs-lookup"><span data-stu-id="b6721-121">Apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the type and a <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each field that should be serialized, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3. <span data-ttu-id="b6721-122">Hatayı döndürecek arabirimde, <xref:System.ServiceModel.FaultContractAttribute> özniteliği hatayı döndürecek yönteme uygulayın ve `detailType` parametreyi hata sınıfının türü olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b6721-122">In the interface that will return the fault, apply the <xref:System.ServiceModel.FaultContractAttribute> attribute to the method that will return the fault and set the `detailType` parameter to the type of the fault class.</span></span>  
  
4. <span data-ttu-id="b6721-123">Ayrıca oluşturucuda, <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> aşağıdaki kodda gösterildiği gibi özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b6721-123">Also in the constructor, set the <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a><span data-ttu-id="b6721-124">Ileti parçalarını koruma</span><span class="sxs-lookup"><span data-stu-id="b6721-124">Protecting Message Parts</span></span>  

 <span data-ttu-id="b6721-125">İleti parçalarını korumak için bir ileti sözleşmesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="b6721-125">Use a message contract to protect parts of a message.</span></span> <span data-ttu-id="b6721-126">İleti sözleşmeleri hakkında daha fazla bilgi için bkz. [Ileti sözleşmelerini kullanma](./feature-details/using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="b6721-126">For more information about message contracts, see [Using Message Contracts](./feature-details/using-message-contracts.md).</span></span>  
  
#### <a name="to-protect-a-message-body"></a><span data-ttu-id="b6721-127">İleti gövdesini korumak için</span><span class="sxs-lookup"><span data-stu-id="b6721-127">To protect a message body</span></span>  
  
1. <span data-ttu-id="b6721-128">İletiyi temsil eden bir tür oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b6721-128">Create a type that represents the message.</span></span> <span data-ttu-id="b6721-129">Aşağıdaki örnek `Company` , iki alan ve içeren bir sınıf oluşturur `CompanyName` `CompanyID` .</span><span class="sxs-lookup"><span data-stu-id="b6721-129">The following example creates a `Company` class with two fields, `CompanyName` and `CompanyID`.</span></span>  
  
2. <span data-ttu-id="b6721-130"><xref:System.ServiceModel.MessageContractAttribute>Özniteliğini sınıfına uygulayın ve <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> özelliğini olarak ayarlayın <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> .</span><span class="sxs-lookup"><span data-stu-id="b6721-130">Apply the <xref:System.ServiceModel.MessageContractAttribute> attribute to the class and set the <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
3. <span data-ttu-id="b6721-131">Özniteliğini, <xref:System.ServiceModel.MessageHeaderAttribute> ileti üst bilgisi olarak ifade edilecek bir alana uygulayın ve `ProtectionLevel` özelliğini olarak ayarlayın <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> .</span><span class="sxs-lookup"><span data-stu-id="b6721-131">Apply the <xref:System.ServiceModel.MessageHeaderAttribute> attribute to a field that will be expressed as a message header and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
4. <span data-ttu-id="b6721-132"><xref:System.ServiceModel.MessageBodyMemberAttribute>İleti gövdesinin bir parçası olarak ifade edilecek herhangi bir alana uygulayın ve `ProtectionLevel` <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> Aşağıdaki örnekte gösterildiği gibi özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b6721-132">Apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to any field that will be expressed as part of the message body, and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following example.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="b6721-133">Örnek</span><span class="sxs-lookup"><span data-stu-id="b6721-133">Example</span></span>  

 <span data-ttu-id="b6721-134">Aşağıdaki örnek, `ProtectionLevel` bir hizmetin çeşitli yerlerinde birkaç öznitelik sınıfının özelliğini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b6721-134">The following example sets the `ProtectionLevel` property of several attribute classes at various places in a service.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b6721-135">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b6721-135">Compiling the Code</span></span>  

 <span data-ttu-id="b6721-136">Aşağıdaki kod, örnek kodu derlemek için gereken ad alanlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b6721-136">The following code shows the namespaces required to compile the example code.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="b6721-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6721-137">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- [<span data-ttu-id="b6721-138">Koruma Düzeylerini Anlama</span><span class="sxs-lookup"><span data-stu-id="b6721-138">Understanding Protection Level</span></span>](understanding-protection-level.md)
