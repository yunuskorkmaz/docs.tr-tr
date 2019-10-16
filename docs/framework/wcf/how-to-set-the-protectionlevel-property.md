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
ms.openlocfilehash: 4ff835f767852da586a3a35b7f4ce2edf99db283
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320908"
---
# <a name="how-to-set-the-protectionlevel-property"></a><span data-ttu-id="2ef35-102">Nasıl yapılır: ProtectionLevel Özelliğini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="2ef35-102">How to: Set the ProtectionLevel Property</span></span>
<span data-ttu-id="2ef35-103">Uygun bir öznitelik uygulayıp özelliği ayarlayarak koruma düzeyini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ef35-103">You can set the protection level by applying an appropriate attribute and setting the property.</span></span> <span data-ttu-id="2ef35-104">Her iletinin tüm bölümlerini etkilemek için hizmet düzeyinde koruma ayarlayabilir veya yöntemlerle ileti bölümlerine kadar artan parçalı düzeylerde koruma ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ef35-104">You can set protection at the service level to affect all parts of every message, or you can set protection at increasingly granular levels, from methods to message parts.</span></span> <span data-ttu-id="2ef35-105">@No__t-0 özelliği hakkında daha fazla bilgi için bkz. [koruma düzeyini anlama](understanding-protection-level.md).</span><span class="sxs-lookup"><span data-stu-id="2ef35-105">For more information about the `ProtectionLevel` property, see [Understanding Protection Level](understanding-protection-level.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2ef35-106">Yapılandırma bölümünde değil, yalnızca kodda koruma düzeylerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ef35-106">You can set protection levels only in code, not in configuration.</span></span>  
  
### <a name="to-sign-all-messages-for-a-service"></a><span data-ttu-id="2ef35-107">Bir hizmetin tüm iletilerini imzalamak için</span><span class="sxs-lookup"><span data-stu-id="2ef35-107">To sign all messages for a service</span></span>  
  
1. <span data-ttu-id="2ef35-108">Hizmet için bir arabirim oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2ef35-108">Create an interface for the service.</span></span>  
  
2. <span data-ttu-id="2ef35-109">@No__t-0 özniteliğini hizmete uygulayın ve <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> özelliğini aşağıdaki kodda gösterildiği gibi <xref:System.Net.Security.ProtectionLevel.Sign> olarak ayarlayın (varsayılan düzey, <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> ' dir).</span><span class="sxs-lookup"><span data-stu-id="2ef35-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the service and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code (the default level is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).</span></span>  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a><span data-ttu-id="2ef35-110">Bir işlemin tüm ileti parçalarını imzalamak için</span><span class="sxs-lookup"><span data-stu-id="2ef35-110">To sign all message parts for an operation</span></span>  
  
1. <span data-ttu-id="2ef35-111">Hizmet için bir arabirim oluşturun ve arabirime <xref:System.ServiceModel.ServiceContractAttribute> özniteliğini uygulayın.</span><span class="sxs-lookup"><span data-stu-id="2ef35-111">Create an interface for the service and apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
2. <span data-ttu-id="2ef35-112">Arabirime bir yöntem bildirimi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2ef35-112">Add a method declaration to the interface.</span></span>  
  
3. <span data-ttu-id="2ef35-113">Yöntemine <xref:System.ServiceModel.OperationContractAttribute> özniteliğini uygulayın ve <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> özelliğini aşağıdaki kodda gösterildiği gibi <xref:System.Net.Security.ProtectionLevel.Sign> olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2ef35-113">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to the method, and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a><span data-ttu-id="2ef35-114">Hata Iletilerini koruma</span><span class="sxs-lookup"><span data-stu-id="2ef35-114">Protecting Fault Messages</span></span>  
 <span data-ttu-id="2ef35-115">Bir hizmette oluşturulan özel durumlar, bir istemciye SOAP hatası olarak gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="2ef35-115">Exceptions that are thrown on a service can be sent to a client as SOAP faults.</span></span> <span data-ttu-id="2ef35-116">Türü kesin belirlenmiş hatalar oluşturma hakkında daha fazla bilgi için bkz. [sözleşmelerdeki ve hizmetlerde hataları belirtme ve işleme](specifying-and-handling-faults-in-contracts-and-services.md) ve [nasıl yapılır: hizmet sözleşmelerinde hata bildirme](how-to-declare-faults-in-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="2ef35-116">For more information about creating strongly typed faults, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md) and [How to: Declare Faults in Service Contracts](how-to-declare-faults-in-service-contracts.md).</span></span>  
  
#### <a name="to-protect-a-fault-message"></a><span data-ttu-id="2ef35-117">Bir hata iletisini korumak için</span><span class="sxs-lookup"><span data-stu-id="2ef35-117">To protect a fault message</span></span>  
  
1. <span data-ttu-id="2ef35-118">Hata iletisini temsil eden bir tür oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2ef35-118">Create a type that represents the fault message.</span></span> <span data-ttu-id="2ef35-119">Aşağıdaki örnek iki alanı olan `MathFault` adlı bir sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2ef35-119">The following example creates a class named `MathFault` with two fields.</span></span>  
  
2. <span data-ttu-id="2ef35-120">Aşağıdaki kodda gösterildiği gibi, <xref:System.Runtime.Serialization.DataContractAttribute> özniteliğini türe ve serileştirilmesi gereken her alana bir <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliğine uygulayın.</span><span class="sxs-lookup"><span data-stu-id="2ef35-120">Apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the type and a <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each field that should be serialized, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3. <span data-ttu-id="2ef35-121">Hatayı döndürecek arabirimde, <xref:System.ServiceModel.FaultContractAttribute> özniteliğini hatayı döndürecek yönteme uygulayın ve `detailType` parametresini hata sınıfının türüne ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2ef35-121">In the interface that will return the fault, apply the <xref:System.ServiceModel.FaultContractAttribute> attribute to the method that will return the fault and set the `detailType` parameter to the type of the fault class.</span></span>  
  
4. <span data-ttu-id="2ef35-122">Oluşturucuda Ayrıca, aşağıdaki kodda gösterildiği gibi <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> özelliğini <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2ef35-122">Also in the constructor, set the <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a><span data-ttu-id="2ef35-123">Ileti parçalarını koruma</span><span class="sxs-lookup"><span data-stu-id="2ef35-123">Protecting Message Parts</span></span>  
 <span data-ttu-id="2ef35-124">İleti parçalarını korumak için bir ileti sözleşmesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="2ef35-124">Use a message contract to protect parts of a message.</span></span> <span data-ttu-id="2ef35-125">İleti sözleşmeleri hakkında daha fazla bilgi için bkz. [Ileti sözleşmelerini kullanma](./feature-details/using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="2ef35-125">For more information about message contracts, see [Using Message Contracts](./feature-details/using-message-contracts.md).</span></span>  
  
#### <a name="to-protect-a-message-body"></a><span data-ttu-id="2ef35-126">İleti gövdesini korumak için</span><span class="sxs-lookup"><span data-stu-id="2ef35-126">To protect a message body</span></span>  
  
1. <span data-ttu-id="2ef35-127">İletiyi temsil eden bir tür oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2ef35-127">Create a type that represents the message.</span></span> <span data-ttu-id="2ef35-128">Aşağıdaki örnek, iki alanı `CompanyName` ve `CompanyID` olan `Company` sınıfı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2ef35-128">The following example creates a `Company` class with two fields, `CompanyName` and `CompanyID`.</span></span>  
  
2. <span data-ttu-id="2ef35-129">Sınıfına <xref:System.ServiceModel.MessageContractAttribute> özniteliğini uygulayın ve <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> özelliğini <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2ef35-129">Apply the <xref:System.ServiceModel.MessageContractAttribute> attribute to the class and set the <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
3. <span data-ttu-id="2ef35-130">@No__t-0 özniteliğini, ileti üst bilgisi olarak ifade edilecek bir alana uygulayın ve `ProtectionLevel` özelliğini <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2ef35-130">Apply the <xref:System.ServiceModel.MessageHeaderAttribute> attribute to a field that will be expressed as a message header and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
4. <span data-ttu-id="2ef35-131">@No__t-0 ' ı ileti gövdesinin parçası olarak ifade edilecek herhangi bir alana uygulayın ve aşağıdaki örnekte gösterildiği gibi `ProtectionLevel` özelliğini <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2ef35-131">Apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to any field that will be expressed as part of the message body, and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following example.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="2ef35-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="2ef35-132">Example</span></span>  
 <span data-ttu-id="2ef35-133">Aşağıdaki örnek, bir hizmetin çeşitli yerlerinde birkaç öznitelik sınıfının `ProtectionLevel` özelliğini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2ef35-133">The following example sets the `ProtectionLevel` property of several attribute classes at various places in a service.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2ef35-134">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="2ef35-134">Compiling the Code</span></span>  
 <span data-ttu-id="2ef35-135">Aşağıdaki kod, örnek kodu derlemek için gereken ad alanlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2ef35-135">The following code shows the namespaces required to compile the example code.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="2ef35-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ef35-136">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- [<span data-ttu-id="2ef35-137">Koruma Düzeylerini Anlama</span><span class="sxs-lookup"><span data-stu-id="2ef35-137">Understanding Protection Level</span></span>](understanding-protection-level.md)
