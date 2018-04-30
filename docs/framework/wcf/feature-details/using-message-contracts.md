---
title: İleti Sözleşmeleri Kullanılıyor
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message contracts [WCF]
ms.assetid: 1e19c64a-ae84-4c2f-9155-91c54a77c249
caps.latest.revision: 46
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 600d938b8981ddfabcb79028ae66b5b9d02107b7
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="using-message-contracts"></a><span data-ttu-id="7977d-102">İleti Sözleşmeleri Kullanılıyor</span><span class="sxs-lookup"><span data-stu-id="7977d-102">Using Message Contracts</span></span>
<span data-ttu-id="7977d-103">Genellikle oluştururken [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uygulamaları, geliştiricilerin serileştirme sorunları ve veri yapıları Kapat dikkat ve kendilerini içinde veri yazımının iletileri yapısıyla ilgilendiren gerekmez.</span><span class="sxs-lookup"><span data-stu-id="7977d-103">Typically when building [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] applications, developers pay close attention to the data structures and serialization issues and do not need to concern themselves with the structure of the messages in which the data is carried.</span></span> <span data-ttu-id="7977d-104">Bu uygulamalar için parametreleri veya dönüş değerleri için veri sözleşmeleri oluşturma basittir.</span><span class="sxs-lookup"><span data-stu-id="7977d-104">For these applications, creating data contracts for the parameters or return values is straightforward.</span></span> <span data-ttu-id="7977d-105">(Daha fazla bilgi için bkz: [hizmet sözleşmelerinde veri aktarımı belirtme](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).)</span><span class="sxs-lookup"><span data-stu-id="7977d-105">(For more information, see [Specifying Data Transfer in Service Contracts](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).)</span></span>  
  
 <span data-ttu-id="7977d-106">Ancak, bir SOAP iletisi yapısını bazen tam kontrole yalnızca, içeriğini üzerinde denetim olarak önem taşır.</span><span class="sxs-lookup"><span data-stu-id="7977d-106">However, sometimes complete control over the structure of a SOAP message is just as important as control over its contents.</span></span> <span data-ttu-id="7977d-107">Birlikte çalışabilirlik önemli veya özellikle güvenlik denetlemek için ileti veya ileti bölümü düzeyinde sorunları olduğunda özellikle geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7977d-107">This is especially true when interoperability is important or to specifically control security issues at the level of the message or message part.</span></span> <span data-ttu-id="7977d-108">Bu durumlarda, oluşturduğunuz bir *ileti sözleşmesi* gerekli kesin SOAP iletisi yapısını belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7977d-108">In these cases, you can create a *message contract* that enables you to specify the structure of the precise SOAP message required.</span></span>  
  
 <span data-ttu-id="7977d-109">Bu konu çeşitli ileti sözleşmesi öznitelikleri belirli ileti sözleşmesi işleminiz oluşturmak için nasıl kullanıldığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="7977d-109">This topic discusses how to use the various message contract attributes to create a specific message contract for your operation.</span></span>  
  
## <a name="using-message-contracts-in-operations"></a><span data-ttu-id="7977d-110">İleti sözleşmeleri işlemlerinde kullanma</span><span class="sxs-lookup"><span data-stu-id="7977d-110">Using Message Contracts in Operations</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="7977d-111"> hakkında ya da Modellenen işlemlerini destekleyen *uzak yordam çağrısı (RPC) stili* veya *stili Mesajlaşma*.</span><span class="sxs-lookup"><span data-stu-id="7977d-111"> supports operations modeled on either the *remote procedure call (RPC) style* or the *messaging style*.</span></span> <span data-ttu-id="7977d-112">Bir RPC-style işleminde serializable bir tür kullanabilirsiniz ve birden çok parametre gibi yerel aramalar için kullanılabilen özellikleri erişimi ve `ref` ve `out` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="7977d-112">In an RPC-style operation, you can use any serializable type, and you have access to the features that are available to local calls, such as multiple parameters and `ref` and `out` parameters.</span></span> <span data-ttu-id="7977d-113">Bu stilde seçilen serileştirme form temel alınan iletilerde verilerin yapısını denetler ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çalışma zamanı işlemi desteklemek için iletileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7977d-113">In this style, the form of serialization chosen controls the structure of the data in the underlying messages, and the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime creates the messages to support the operation.</span></span> <span data-ttu-id="7977d-114">Bu, SOAP ile tanıdık olmayan ve iletileri kolayca SOAP ve kolayca oluşturup hizmet uygulamaları kullanın geliştiriciler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7977d-114">This enables developers who are not familiar with SOAP and SOAP messages to quickly and easily create and use service applications.</span></span>  
  
 <span data-ttu-id="7977d-115">Aşağıdaki kod örneğinde RPC stilini Modellenen bir hizmet işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7977d-115">The following code example shows a service operation modeled on the RPC style.</span></span>  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 <span data-ttu-id="7977d-116">Normalde, bir veri sözleşmesi şema iletileri tanımlamak yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="7977d-116">Normally, a data contract is sufficient to define the schema for the messages.</span></span> <span data-ttu-id="7977d-117">Örneğin, önceki örnekte, çoğu uygulama için yeterli değilse `BankingTransaction` ve `BankingTransactionResponse` temel alınan SOAP iletilerine içeriğini tanımlamak için veri sözleşmeleri sahip.</span><span class="sxs-lookup"><span data-stu-id="7977d-117">For instance, in the preceding example, it is sufficient for most applications if `BankingTransaction` and `BankingTransactionResponse` have data contracts to define the contents of the underlying SOAP messages.</span></span> <span data-ttu-id="7977d-118">Veri sözleşmeleri hakkında daha fazla bilgi için bkz: [kullanarak veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="7977d-118">For more information about data contracts, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="7977d-119">Ancak, bazen onu tam olarak nasıl SOAP iletisi yapısını kablo üzerinden aktarılan denetlemek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7977d-119">However, occasionally it is necessary to precisely control how the structure of the SOAP message transmitted over the wire.</span></span> <span data-ttu-id="7977d-120">Bunun en yaygın senaryo özel SOAP üstbilgileri ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="7977d-120">The most common scenario for this is inserting custom SOAP headers.</span></span> <span data-ttu-id="7977d-121">Başka bir yaygın senaryodur güvenlik özelliklerini ileti üstbilgi ve gövde, yani tanımlamak için bu öğeler dijital olarak imzalanmış ve şifrelenmiş olup olmadığını karar vermek için.</span><span class="sxs-lookup"><span data-stu-id="7977d-121">Another common scenario is to define security properties for the message's headers and body, that is, to decide whether these elements are digitally signed and encrypted.</span></span> <span data-ttu-id="7977d-122">Son olarak, bazı üçüncü taraf SOAP yığınları iletileri gerektiren belirli bir biçimde olabilir.</span><span class="sxs-lookup"><span data-stu-id="7977d-122">Finally, some third-party SOAP stacks require messages be in a specific format.</span></span> <span data-ttu-id="7977d-123">Mesajlaşma stili operations bu denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="7977d-123">Messaging-style operations provide this control.</span></span>  
  
 <span data-ttu-id="7977d-124">Bir ileti stili işlemi, her iki tür ileti türlerini nerede en fazla bir parametre ve dönüş değerini sahiptir; diğer bir deyişle, doğrudan belirtilen bir SOAP iletisi yapısına serileştirir.</span><span class="sxs-lookup"><span data-stu-id="7977d-124">A messaging-style operation has at most one parameter and one return value where both types are message types; that is, they serialize directly into a specified SOAP message structure.</span></span> <span data-ttu-id="7977d-125">Bu ile işaretlenen herhangi bir tür olabilir <xref:System.ServiceModel.MessageContractAttribute> veya <xref:System.ServiceModel.Channels.Message> türü.</span><span class="sxs-lookup"><span data-stu-id="7977d-125">This may be any type marked with the <xref:System.ServiceModel.MessageContractAttribute> or the <xref:System.ServiceModel.Channels.Message> type.</span></span> <span data-ttu-id="7977d-126">Aşağıdaki kod örneğinde bir işlem benzer şekilde önceki RCP stili gösterir ancak Mesajlaşma stili kullanır.</span><span class="sxs-lookup"><span data-stu-id="7977d-126">The following code example shows an operation similar to the preceding RCP-style, but which uses the messaging style.</span></span>  
  
 <span data-ttu-id="7977d-127">Örneğin, varsa `BankingTransaction` ve `BankingTransactionResponse` kod aşağıdaki işlemleri içinde geçerli ise ileti sözleşmeleri olan iki türleridir.</span><span class="sxs-lookup"><span data-stu-id="7977d-127">For example, if `BankingTransaction` and `BankingTransactionResponse` are both types that are message contracts, then the code in the following operations is valid.</span></span>  
  
```csharp  
[OperationContract]  
BankingTransactionResponse Process(BankingTransaction bt);  
[OperationContract]  
void Store(BankingTransaction bt);  
[OperationContract]  
BankingTransactionResponse GetResponse();  
```  
  
 <span data-ttu-id="7977d-128">Ancak, aşağıdaki kodu geçersiz.</span><span class="sxs-lookup"><span data-stu-id="7977d-128">However, the following code is invalid.</span></span>  
  
```csharp  
[OperationContract]  
bool Validate(BankingTransaction bt);  
// Invalid, the return type is not a message contract.  
[OperationContract]  
void Reconcile(BankingTransaction bt1, BankingTransaction bt2);  
// Invalid, there is more than one parameter.  
```  
  
 <span data-ttu-id="7977d-129">Sözleşme türden bir ileti içerir ve, geçerli desenleri birini izlemez herhangi bir işlem için bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="7977d-129">An exception is thrown for any operation that involves a message contract type and that does not follow one of the valid patterns.</span></span> <span data-ttu-id="7977d-130">Elbette, ileti sözleşme türleri içermeyen operations bu sınırlamalara tabi değildir.</span><span class="sxs-lookup"><span data-stu-id="7977d-130">Of course, operations that do not involve message contract types are not subject to these restrictions.</span></span>  
  
 <span data-ttu-id="7977d-131">Bir türü bir ileti sözleşmesi ve bir veri sözleşmesi varsa, yalnızca ileti sözleşmesi türü bir işlemde kullanıldığında olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="7977d-131">If a type has both a message contract and a data contract, only its message contract is considered when the type is used in an operation.</span></span>  
  
## <a name="defining-message-contracts"></a><span data-ttu-id="7977d-132">İleti sözleşmeleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="7977d-132">Defining Message Contracts</span></span>  
 <span data-ttu-id="7977d-133">Bir tür için bir ileti sözleşmesi tanımlamak için (diğer bir deyişle, türü ve SOAP Zarfı arasında eşleme tanımlamak için), geçerli <xref:System.ServiceModel.MessageContractAttribute> türü.</span><span class="sxs-lookup"><span data-stu-id="7977d-133">To define a message contract for a type (that is, to define the mapping between the type and a SOAP envelope), apply the <xref:System.ServiceModel.MessageContractAttribute> to the type.</span></span> <span data-ttu-id="7977d-134">Daha sonra uygulamanız <xref:System.ServiceModel.MessageHeaderAttribute> SOAP üstbilgileri yapıp uygulamak istediğiniz türü bu üyeler için <xref:System.ServiceModel.MessageBodyMemberAttribute> iletinin SOAP gövdesi parçalara yapmak istediğiniz bu üyelere.</span><span class="sxs-lookup"><span data-stu-id="7977d-134">Then apply the <xref:System.ServiceModel.MessageHeaderAttribute> to those members of the type you want to make into SOAP headers, and apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to those members you want to make into parts of the SOAP body of the message.</span></span>  
  
 <span data-ttu-id="7977d-135">Aşağıdaki kod bir ileti sözleşmesi kullanmaya ilişkin bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="7977d-135">The following code provides an example of using a message contract.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader] public DateTime transactionDate;  
  [MessageBodyMember] private Account sourceAccount;  
  [MessageBodyMember] private Account targetAccount;  
  [MessageBodyMember] public int amount;  
}  
```  
  
 <span data-ttu-id="7977d-136">Bu tür bir işlem parametresi olarak kullanırken, aşağıdaki SOAP Zarfı oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="7977d-136">When using this type as an operation parameter, the following SOAP envelope is generated:</span></span>  
  
```xml  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <h:operation xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">Deposit</h:operation>  
    <h:transactionDate xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">2012-02-16T16:10:00</h:transactionDate>  
  </s:Header>  
  <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <BankingTransaction xmlns="http://tempuri.org/">  
      <amount>0</amount>  
      <sourceAccount xsi:nil="true"/>  
      <targetAccount xsi:nil="true"/>  
    </BankingTransaction>  
  </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="7977d-137">Dikkat `operation` ve `transactionDate` SOAP üstbilgileri görünür ve SOAP gövdesi bir sarmalayıcı öğesi oluşur `BankingTransaction` içeren `sourceAccount`,`targetAccount`, ve `amount`.</span><span class="sxs-lookup"><span data-stu-id="7977d-137">Notice that `operation` and `transactionDate` appear as SOAP headers and the SOAP body consists of a wrapper element `BankingTransaction` containing `sourceAccount`,`targetAccount`, and `amount`.</span></span>  
  
 <span data-ttu-id="7977d-138">Uygulayabileceğiniz <xref:System.ServiceModel.MessageHeaderAttribute> ve <xref:System.ServiceModel.MessageBodyMemberAttribute> tüm alanlar, özellikleri ve genel, özel, korumalı veya iç olup olmadıkları bakılmaksızın, olaylar.</span><span class="sxs-lookup"><span data-stu-id="7977d-138">You can apply the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> to all fields, properties, and events, regardless of whether they are public, private, protected, or internal.</span></span>  
  
 <span data-ttu-id="7977d-139"><xref:System.ServiceModel.MessageContractAttribute> SOAP iletisi gövdesinde sarmalayıcı öğesinin adı kontrol WrapperName ve WrapperNamespace öznitelikleri belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="7977d-139">The <xref:System.ServiceModel.MessageContractAttribute> allows you to specify the WrapperName and WrapperNamespace attributes which control the name of the wrapper element in the body of the SOAP message.</span></span> <span data-ttu-id="7977d-140">Varsayılan ileti sözleşmesi adını türü sarmalayıcı ve ileti sözleşmesi tanımlanır ad alanı için kullanılan `HYPERLINK "http://tempuri.org/" http://tempuri.org/` varsayılan ad alanı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7977d-140">By default the name of the message contract type is used for the wrapper and the namespace in which the message contract is defined  `HYPERLINK "http://tempuri.org/" http://tempuri.org/` is used as the default namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7977d-141"><xref:System.Runtime.Serialization.KnownTypeAttribute> ileti sözleşmeleri öznitelikleri göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="7977d-141"><xref:System.Runtime.Serialization.KnownTypeAttribute> attributes are ignored in message contracts.</span></span> <span data-ttu-id="7977d-142">Varsa bir <xref:System.Runtime.Serialization.KnownTypeAttribute> olan gerekli, bunu ileti sözleşmesi kullanan işlemi söz konusu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="7977d-142">If a <xref:System.Runtime.Serialization.KnownTypeAttribute> is required, place it on the operation that is using the message contract in question.</span></span>  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a><span data-ttu-id="7977d-143">Üstbilgi ve gövde bölümü adlarına ve ad alanlarını denetleme</span><span class="sxs-lookup"><span data-stu-id="7977d-143">Controlling Header and Body Part Names and Namespaces</span></span>  
 <span data-ttu-id="7977d-144">İleti sözleşmesi SOAP gösterimini her üstbilgi ve gövde bölümü bir ad ve bir ad alanı olan bir XML öğesi eşler.</span><span class="sxs-lookup"><span data-stu-id="7977d-144">In the SOAP representation of a message contract, each header and body part maps to an XML element that has a name and a namespace.</span></span>  
  
 <span data-ttu-id="7977d-145">Varsayılan olarak, ileti katılıyor ve ad üye adına belirlenir hizmet sözleşmesi ad alanı ile aynı ad alanıdır <xref:System.ServiceModel.MessageHeaderAttribute> veya <xref:System.ServiceModel.MessageBodyMemberAttribute> öznitelikler uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7977d-145">By default, the namespace is the same as the namespace of the service contract that the message is participating in, and the name is determined by the member name to which the <xref:System.ServiceModel.MessageHeaderAttribute> or the <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes are applied.</span></span>  
  
 <span data-ttu-id="7977d-146">Bu varsayılan işleyerek değiştirebileceğiniz <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> ve <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (üst sınıfı üzerinde <xref:System.ServiceModel.MessageHeaderAttribute> ve <xref:System.ServiceModel.MessageBodyMemberAttribute> öznitelikleri).</span><span class="sxs-lookup"><span data-stu-id="7977d-146">You can change these defaults by manipulating the <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (on the parent class of the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes).</span></span>  
  
 <span data-ttu-id="7977d-147">Aşağıdaki kod örneğinde sınıfında göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="7977d-147">Consider the class in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader(Namespace="http://schemas.contoso.com/auditing/2005")] public bool IsAudited;  
  [MessageBodyMember(Name="transactionData")] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="7977d-148">Bu örnekte, `IsAudited` başlığıdır kodu ve temsil eden gövde bölümü belirtilen ad alanında `theData` üye ada sahip bir XML öğesi ile temsil edilir `transactionData`.</span><span class="sxs-lookup"><span data-stu-id="7977d-148">In this example, the `IsAudited` header is in the namespace specified in the code, and the body part that represents the `theData` member is represented by an XML element with the name `transactionData`.</span></span> <span data-ttu-id="7977d-149">Bu ileti sözleşmesi için oluşturulan XML gösterir.</span><span class="sxs-lookup"><span data-stu-id="7977d-149">The following shows the XML generated for this message contract.</span></span>  
  
```xml  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <h:IsAudited xmlns:h="http://schemas.contoso.com/auditing/2005" xmlns="http://schemas.contoso.com/auditing/2005">false</h:IsAudited>  
    <h:operation xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">Deposit</h:operation>  
  </s:Header>  
  <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <AuditedBankingTransaction xmlns="http://tempuri.org/">  
      <transactionData/>  
    </AuditedBankingTransaction>  
  </s:Body>  
</s:Envelope>  
```  
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a><span data-ttu-id="7977d-150">SOAP gövdesi bölümleri Sarmalanan olup olmadığını denetleme</span><span class="sxs-lookup"><span data-stu-id="7977d-150">Controlling Whether the SOAP Body Parts Are Wrapped</span></span>  
 <span data-ttu-id="7977d-151">Varsayılan olarak, SOAP gövdesi bölümleri Sarmalanan bir öğesiyle iç serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="7977d-151">By default, the SOAP body parts are serialized inside a wrapped element.</span></span> <span data-ttu-id="7977d-152">Örneğin, aşağıdaki gösterir kod `HelloGreetingMessage` adından oluşturulan sarmalayıcı öğeyi <xref:System.ServiceModel.MessageContractAttribute> için ileti sözleşmesi türü `HelloGreetingMessage` ileti.</span><span class="sxs-lookup"><span data-stu-id="7977d-152">For example, the following code shows the `HelloGreetingMessage` wrapper element generated from the name of the <xref:System.ServiceModel.MessageContractAttribute> type in the message contract for the `HelloGreetingMessage` message.</span></span>  
  
 [!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
 [!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 <span data-ttu-id="7977d-153">Kapsayıcı öğe gizlemek için ayarlanmış <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> özelliğine `false`.</span><span class="sxs-lookup"><span data-stu-id="7977d-153">To suppress the wrapper element, set the <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> property to `false`.</span></span> <span data-ttu-id="7977d-154">Ad ve sarmalayıcı öğesinin ad alanı denetlemek için kullandığı <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> ve <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="7977d-154">To control the name and the namespace of the wrapper element, use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> and <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7977d-155">Birden fazla ileti Gövde bölümünün değil sarılır iletilerinde sahip WS ile uyumlu değil-ı temel Profil 1.1 ve yeni ileti sözleşmeleri tasarlarken önerilmez.</span><span class="sxs-lookup"><span data-stu-id="7977d-155">Having more than one message body part in messages that are not wrapped is not compliant with WS-I Basic Profile 1.1 and is not recommended when designing new message contracts.</span></span> <span data-ttu-id="7977d-156">Ancak, birden fazla sarmalanmamış ileti Gövde bölümünün belirli belirli birlikte çalışabilirlik senaryolarda sağlamak gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="7977d-156">However, it may be necessary to have more than one unwrapped message body part in certain specific interoperability scenarios.</span></span> <span data-ttu-id="7977d-157">Birden fazla parça ileti gövdesinde veri iletmek için kullanacaksanız, varsayılan (Sarmalanan) modunu kullanmak için önerilir.</span><span class="sxs-lookup"><span data-stu-id="7977d-157">If you are going to transmit more than one piece of data in a message body, it is recommended to use the default (wrapped) mode.</span></span> <span data-ttu-id="7977d-158">Birden fazla ileti üstbilgisi sarmalanmamış iletilerinde sahip tamamen kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="7977d-158">Having more than one message header in unwrapped messages is completely acceptable.</span></span>  
  
## <a name="using-custom-types-inside-message-contracts"></a><span data-ttu-id="7977d-159">İleti sözleşmeleri içinde özel türleri kullanma</span><span class="sxs-lookup"><span data-stu-id="7977d-159">Using Custom Types Inside Message Contracts</span></span>  
 <span data-ttu-id="7977d-160">(XML içinde açık) her bireysel ileti başlığı ve ileti Gövde bölümünün serileştirilir seçilen serileştirme motoruna ileti kullanıldığı için hizmet sözleşmesini kullanma.</span><span class="sxs-lookup"><span data-stu-id="7977d-160">Each individual message header and message body part is serialized (turned into XML) using the chosen serialization engine for the service contract where the message is used.</span></span> <span data-ttu-id="7977d-161">Varsayılan serileştirme motoruna `XmlFormatter`, bir veri sözleşmesi ya da açıkça olan herhangi bir tür işleyebilir (sahip <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) ya da örtük olarak (Basit tür olması, sahip <xref:System.SerializableAttribute?displayProperty=nameWithType>, vb.).</span><span class="sxs-lookup"><span data-stu-id="7977d-161">The default serialization engine, the `XmlFormatter`, can handle any type that has a data contract, either explicitly (by having the <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) or implicitly (by being a primitive type, having the <xref:System.SerializableAttribute?displayProperty=nameWithType>, and so on).</span></span> <span data-ttu-id="7977d-162">Daha fazla bilgi için bkz: [kullanarak veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="7977d-162">For more information, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="7977d-163">Önceki örnekte `Operation` ve `BankingTransactionData` türleri, bir veri sözleşmesi olmalıdır ve `transactionDate` seri hale getirilemez çünkü <xref:System.DateTime> bir primitive (ve bu nedenle bir örtük veri sözleşmesi).</span><span class="sxs-lookup"><span data-stu-id="7977d-163">In the preceding example, the `Operation` and `BankingTransactionData` types must have a data contract, and `transactionDate` is serializable because <xref:System.DateTime> is a primitive (and so has an implicit data contract).</span></span>  
  
 <span data-ttu-id="7977d-164">Ancak, farklı seri hale getirme altyapısı için mümkün `XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="7977d-164">However, it is possible to switch to a different serialization engine, the `XmlSerializer`.</span></span> <span data-ttu-id="7977d-165">Bu tür bir geçiş yaparsanız, tüm ileti üstbilgilerini ve gövde bölümleri için kullanılan türleri seri hale getirilebilir kullanarak emin olun `XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="7977d-165">If you make such a switch, you should ensure that all of the types used for message headers and body parts are serializable using the `XmlSerializer`.</span></span>  
  
## <a name="using-arrays-inside-message-contracts"></a><span data-ttu-id="7977d-166">İleti sözleşmeleri içinde dizileri kullanma</span><span class="sxs-lookup"><span data-stu-id="7977d-166">Using Arrays Inside Message Contracts</span></span>  
 <span data-ttu-id="7977d-167">İleti sözleşmeleri iki yolla öğelerinde yineleme dizileri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7977d-167">You can use arrays of repeating elements in message contracts in two ways.</span></span>  
  
 <span data-ttu-id="7977d-168">İlk kullanmaktır bir <xref:System.ServiceModel.MessageHeaderAttribute> veya <xref:System.ServiceModel.MessageBodyMemberAttribute> dizisi üzerinde doğrudan.</span><span class="sxs-lookup"><span data-stu-id="7977d-168">The first is to use a <xref:System.ServiceModel.MessageHeaderAttribute> or a <xref:System.ServiceModel.MessageBodyMemberAttribute> directly on the array.</span></span> <span data-ttu-id="7977d-169">Bu durumda, bir öğesiyle (diğer bir deyişle, bir üst bilgi veya bir gövde bölümü) birden çok alt öğesi olarak tüm diziyi serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="7977d-169">In this case, the entire array is serialized as one element (that is, one header or one body part) with multiple child elements.</span></span> <span data-ttu-id="7977d-170">Aşağıdaki örnek sınıfında göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="7977d-170">Consider the class in the following example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingDepositLog  
{  
  [MessageHeader] public int numRecords;  
  [MessageHeader] public DepositRecord[] records;  
  [MessageHeader] public int branchID;  
}  
```  
  
 <span data-ttu-id="7977d-171">SOAP üstbilgileri bu sonuçlarında aşağıdakine benzer.</span><span class="sxs-lookup"><span data-stu-id="7977d-171">This results in SOAP headers is similar to the following.</span></span>  
  
```xml  
<BankingDepositLog>  
<numRecords>3</numRecords>  
<records>  
  <DepositRecord>Record1</DepositRecord>  
  <DepositRecord>Record2</DepositRecord>  
  <DepositRecord>Record3</DepositRecord>  
</records>  
<branchID>20643</branchID>  
</BankingDepositLog>  
```  
  
 <span data-ttu-id="7977d-172">Bu alternatif kullanmaktır <xref:System.ServiceModel.MessageHeaderArrayAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7977d-172">An alternative to this is to use the <xref:System.ServiceModel.MessageHeaderArrayAttribute>.</span></span> <span data-ttu-id="7977d-173">Bu durumda, her dizi öğesi bağımsız olarak serileştirilmiş ve her dizi öğesi bir üst bilgi, aşağıdakine benzer bulunduğundan.</span><span class="sxs-lookup"><span data-stu-id="7977d-173">In this case, each array element is serialized independently and so that each array element has one header, similar to the following.</span></span>  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 <span data-ttu-id="7977d-174">Dizi girdiler için varsayılan adı üyesine adıdır <xref:System.ServiceModel.MessageHeaderArrayAttribute> öznitelikler uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7977d-174">The default name for array entries is the name of the member to which the <xref:System.ServiceModel.MessageHeaderArrayAttribute> attributes is applied.</span></span>  
  
 <span data-ttu-id="7977d-175"><xref:System.ServiceModel.MessageHeaderArrayAttribute> Özniteliği devraldığı <xref:System.ServiceModel.MessageHeaderAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7977d-175">The <xref:System.ServiceModel.MessageHeaderArrayAttribute> attribute inherits from the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="7977d-176">Dizi olmayan öznitelikleri özellikleri kümesinin aynısını sahipse, örneğin, sipariş, adı ve üst bilgileri dizisi için ad alanı için tek bir başlık kümesi aynı şekilde ayarlamak mümkün olur.</span><span class="sxs-lookup"><span data-stu-id="7977d-176">It has the same set of features as the non-array attributes, for example, it is possible to set the order, name, and namespace for an array of headers in the same way you set it for a single header.</span></span> <span data-ttu-id="7977d-177">Kullandığınızda `Order` bir dizi özellik, dizinin tamamı için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7977d-177">When you use the `Order` property on an array, it applies to the entire array.</span></span>  
  
 <span data-ttu-id="7977d-178">Uygulayabileceğiniz <xref:System.ServiceModel.MessageHeaderArrayAttribute> yalnızca dizileri, değil koleksiyonlar için.</span><span class="sxs-lookup"><span data-stu-id="7977d-178">You can apply the <xref:System.ServiceModel.MessageHeaderArrayAttribute> only to arrays, not collections.</span></span>  
  
## <a name="using-byte-arrays-in-message-contracts"></a><span data-ttu-id="7977d-179">İleti sözleşmeleri bayt dizileri kullanma</span><span class="sxs-lookup"><span data-stu-id="7977d-179">Using Byte Arrays in Message Contracts</span></span>  
 <span data-ttu-id="7977d-180">Dizi olmayan özniteliklerle kullanıldığında bayt dizileri (<xref:System.ServiceModel.MessageBodyMemberAttribute> ve <xref:System.ServiceModel.MessageHeaderAttribute>), dizi olarak ancak Base64 ile kodlanmış veriler sonuç XML olarak gösterilen özel bir basit tür olarak kabul edilmediği.</span><span class="sxs-lookup"><span data-stu-id="7977d-180">Byte arrays, when used with the non-array attributes (<xref:System.ServiceModel.MessageBodyMemberAttribute> and <xref:System.ServiceModel.MessageHeaderAttribute>), are not treated as arrays but as a special primitive type represented as Base64-encoded data in the resulting XML.</span></span>  
  
 <span data-ttu-id="7977d-181">Bayt dizileri dizi özniteliğiyle kullandığınızda <xref:System.ServiceModel.MessageHeaderArrayAttribute>, kullanımdaki seri hale getirici sonuçları bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="7977d-181">When you use byte arrays with the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the results depend on the serializer in use.</span></span> <span data-ttu-id="7977d-182">Varsayılan serileştirici ile dizinin her bir bayt için tek bir giriş olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="7977d-182">With the default serializer, the array is represented as an individual entry for each byte.</span></span> <span data-ttu-id="7977d-183">Ancak, ne zaman `XmlSerializer` seçili (kullanarak <xref:System.ServiceModel.XmlSerializerFormatAttribute> hizmet sözleşmesi üzerinde), bayt dizileri Base64 veri dizisi veya dizi olmayan öznitelikleri kullanılıp bağımsız olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="7977d-183">However, when the `XmlSerializer` is selected, (using the <xref:System.ServiceModel.XmlSerializerFormatAttribute> on the service contract), byte arrays are treated as Base64 data regardless of whether the array or non-array attributes are used.</span></span>  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a><span data-ttu-id="7977d-184">İmzalama ve şifreleme iletinin bölümleri</span><span class="sxs-lookup"><span data-stu-id="7977d-184">Signing and Encrypting Parts of the Message</span></span>  
 <span data-ttu-id="7977d-185">İleti sözleşmesi üstbilgileri ve/veya ileti gövdesini dijital olarak İmzalanabilir ve şifrelenebilir olup olmadığını gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="7977d-185">A message contract can indicate whether the headers and/or body of the message should be digitally signed and encrypted.</span></span>  
  
 <span data-ttu-id="7977d-186">Bu ayarlayarak yapılır <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> özelliği <xref:System.ServiceModel.MessageHeaderAttribute> ve <xref:System.ServiceModel.MessageBodyMemberAttribute> öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="7977d-186">This is done by setting the <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> property on the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="7977d-187">Sabit listesi özelliktir <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> yazın ve ayarlanabilir <xref:System.Net.Security.ProtectionLevel.None> (şifreleme veya imza), <xref:System.Net.Security.ProtectionLevel.Sign> (dijital imza yalnızca), veya <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (şifreleme ve dijital imza).</span><span class="sxs-lookup"><span data-stu-id="7977d-187">The property is an enumeration of the <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> type and can be set to <xref:System.Net.Security.ProtectionLevel.None> (no encryption or signature), <xref:System.Net.Security.ProtectionLevel.Sign> (digital signature only), or <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (both encryption and a digital signature).</span></span> <span data-ttu-id="7977d-188">Varsayılan, <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> değeridir.</span><span class="sxs-lookup"><span data-stu-id="7977d-188">The default is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
 <span data-ttu-id="7977d-189">Bu güvenlik özellikleri çalışacak şekilde bağlama ve davranışları düzgün şekilde yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7977d-189">For these security features to work, you must properly configure the binding and behaviors.</span></span> <span data-ttu-id="7977d-190">Bu güvenlik özellikleri uygun yapılandırma olmadan (örneğin, bir ileti kimlik bilgilerinizi girmeden oturum çalışılıyor) kullanırsanız, doğrulama aynı anda özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="7977d-190">If you use these security features without the proper configuration (for example, attempting to sign a message without supplying your credentials), an exception is thrown at validation time.</span></span>  
  
 <span data-ttu-id="7977d-191">İleti üstbilgilerini koruma düzeyi ayrı ayrı her bir üstbilgisi belirlenir.</span><span class="sxs-lookup"><span data-stu-id="7977d-191">For message headers, the protection level is determined individually for each header.</span></span>  
  
 <span data-ttu-id="7977d-192">İleti gövdesi bölümleri için koruma düzeyi, "düşük koruma düzeyi." değerlendirilebilir</span><span class="sxs-lookup"><span data-stu-id="7977d-192">For message body parts, the protection level can be thought of as the "minimum protection level."</span></span> <span data-ttu-id="7977d-193">Gövde gövde bölümlerinin sayısını bağımsız olarak yalnızca bir koruma düzeyi vardır.</span><span class="sxs-lookup"><span data-stu-id="7977d-193">The body has only one protection level, regardless of the number of body parts.</span></span> <span data-ttu-id="7977d-194">Gövde koruma düzeyi yüksek tarafından belirlenir <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> tüm gövde bölümlerini özellik ayarı.</span><span class="sxs-lookup"><span data-stu-id="7977d-194">The protection level of the body is determined by the highest <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> property setting of all the body parts.</span></span> <span data-ttu-id="7977d-195">Bununla birlikte, her bir gövde kısmının koruma düzeyini düzeyi gereken gerçek minimum koruma için ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7977d-195">However, you should set the protection level of each body part to the actual minimum protection level required.</span></span>  
  
 <span data-ttu-id="7977d-196">Aşağıdaki kod örneğinde sınıfında göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="7977d-196">Consider the class in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class PatientRecord  
{  
   [MessageHeader(ProtectionLevel=None)] public int recordID;  
   [MessageHeader(ProtectionLevel=Sign)] public string patientName;  
   [MessageHeader(ProtectionLevel=EncryptAndSign)] public string SSN;  
   [MessageBodyMember(ProtectionLevel=None)] public string comments;  
   [MessageBodyMember(ProtectionLevel=Sign)] public string diagnosis;  
   [MessageBodyMember(ProtectionLevel=EncryptAndSign)] public string medicalHistory;  
}  
```  
  
 <span data-ttu-id="7977d-197">Bu örnekte, `recordID` üstbilgi korumalı değil, `patientName` olan `signed`, ve `SSN` imzalı ve şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="7977d-197">In this example, the `recordID` header is not protected, `patientName` is `signed`, and `SSN` is encrypted and signed.</span></span> <span data-ttu-id="7977d-198">En az bir gövde bölümü `medicalHistory`, sahip <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> uygulanan ve dolayısıyla tüm ileti gövdesi şifrelenir ve imzalanmış rağmen açıklamalar ve tanılama gövde bölümlerinin daha düşük koruma düzeyleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="7977d-198">At least one body part, `medicalHistory`, has <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> applied, and thus the entire message body is encrypted and signed, even though the comments and diagnosis body parts specify lower protection levels.</span></span>  
  
## <a name="soap-action"></a><span data-ttu-id="7977d-199">SOAP eylemi</span><span class="sxs-lookup"><span data-stu-id="7977d-199">SOAP Action</span></span>  
 <span data-ttu-id="7977d-200">SOAP ve ilgili Web hizmeti standartlarını tanımlamak adlı bir özellik `Action` , olabilir gönderilen her SOAP iletisi için mevcut.</span><span class="sxs-lookup"><span data-stu-id="7977d-200">SOAP and related Web services standards define a property called `Action` that can be present for every SOAP message sent.</span></span> <span data-ttu-id="7977d-201">İşlem <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> ve <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> denetim özelliklerini bu özelliğin değeri.</span><span class="sxs-lookup"><span data-stu-id="7977d-201">The operation's <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> properties control the value of this property.</span></span>  
  
## <a name="soap-header-attributes"></a><span data-ttu-id="7977d-202">SOAP üstbilgi öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="7977d-202">SOAP Header Attributes</span></span>  
 <span data-ttu-id="7977d-203">SOAP standart üstbilgi bulunabilir aşağıdaki öznitelikleri tanımlar:</span><span class="sxs-lookup"><span data-stu-id="7977d-203">The SOAP standard defines the following attributes that may exist on a header:</span></span>  
  
-   <span data-ttu-id="7977d-204">`Actor/Role` (`Actor` SOAP 1.1 `Role` SOAP 1.2)</span><span class="sxs-lookup"><span data-stu-id="7977d-204">`Actor/Role` (`Actor` in SOAP 1.1, `Role` in SOAP 1.2)</span></span>  
  
-   `MustUnderstand`  
  
-   `Relay`  
  
 <span data-ttu-id="7977d-205">`Actor` Veya `Role` özniteliği, verili bir üstbilginin amaçlanmıştır düğümü Tekdüzen Kaynak Tanımlayıcısı'nı (URI) belirtir.</span><span class="sxs-lookup"><span data-stu-id="7977d-205">The `Actor` or `Role` attribute specifies the Uniform Resource Identifier (URI) of the node for which a given header is intended.</span></span> <span data-ttu-id="7977d-206">`MustUnderstand` Özniteliği, üst bilgi işlem düğümü, anlamak olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7977d-206">The `MustUnderstand` attribute specifies whether the node processing the header must understand it.</span></span> <span data-ttu-id="7977d-207">`Relay` Özniteliği, üstbilgi aşağı akış düğümlerine geçirilmesine izin olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="7977d-207">The `Relay` attribute specifies whether the header is to be relayed to downstream nodes.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="7977d-208"> dışında bu özniteliklerin gelen iletileri üzerinde herhangi bir işlem gerçekleştirmez `MustUnderstand` özniteliği, bu konunun devamındaki "İleti sözleşmesi sürümü oluşturma" bölümünde belirtildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="7977d-208"> does not perform any processing of these attributes on incoming messages, except for the `MustUnderstand` attribute, as specified in the "Message Contract Versioning" section later in this topic.</span></span> <span data-ttu-id="7977d-209">Ancak, gerekirse aşağıdaki açıklama olduğu gibi bu öznitelikler okumasına ve yazmasına sağlar.</span><span class="sxs-lookup"><span data-stu-id="7977d-209">However, it allows you to read and write these attributes as necessary, as in the following description.</span></span>  
  
 <span data-ttu-id="7977d-210">İleti gönderirken bu öznitelikler varsayılan olarak gösterilen değil.</span><span class="sxs-lookup"><span data-stu-id="7977d-210">When sending a message, these attributes are not emitted by default.</span></span> <span data-ttu-id="7977d-211">Bunu iki şekilde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7977d-211">You can change this in two ways.</span></span> <span data-ttu-id="7977d-212">İlk olarak, statik olarak öznitelikleri için istenen tüm değerleri değiştirerek ayarladığınız <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, ve <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> aşağıdaki kod örneğinde gösterildiği gibi özellikler.</span><span class="sxs-lookup"><span data-stu-id="7977d-212">First, you may statically set the attributes to any desired values by changing the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, and <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> properties, as shown in the following code example.</span></span> <span data-ttu-id="7977d-213">(Unutmayın hiçbir `Role` özellik; ayarı <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> özelliği yayar `Role` SOAP 1.2 kullanıyorsanız özniteliği).</span><span class="sxs-lookup"><span data-stu-id="7977d-213">(Note that there is no `Role` property; setting the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> property emits the `Role` attribute if you are using SOAP 1.2).</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="7977d-214">Bu öznitelikler denetlemek için ikinci yol dinamik olarak kodudur.</span><span class="sxs-lookup"><span data-stu-id="7977d-214">The second way to control these attributes is dynamically, through code.</span></span> <span data-ttu-id="7977d-215">Bu istenen üstbilgi türünde kaydırma tarafından elde <xref:System.ServiceModel.MessageHeader%601> türü (Bu tür genel olmayan sürümüyle karıştırır değil emin olun) ve türü ile birlikte kullanarak <xref:System.ServiceModel.MessageHeaderAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7977d-215">You can achieve this by wrapping the desired header type in the <xref:System.ServiceModel.MessageHeader%601> type (be sure not to confuse this type with the non-generic version) and by using the type together with the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="7977d-216">Daha sonra özellikleri kullanabileceğinizi <xref:System.ServiceModel.MessageHeader%601> aşağıdaki kod örneğinde gösterildiği gibi SOAP öznitelikleri ayarlamak için.</span><span class="sxs-lookup"><span data-stu-id="7977d-216">Then, you can use properties on the <xref:System.ServiceModel.MessageHeader%601> to set the SOAP attributes, as shown in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public MessageHeader<bool> IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
// application code:  
BankingTransaction bt = new BankingTransaction();  
bt.IsAudited = new MessageHeader<bool>();  
bt.IsAudited.Content = false; // Set IsAudited header value to "false"  
bt.IsAudited.Actor="http://auditingservice.contoso.com";  
bt.IsAudited.MustUnderstand=true;  
```  
  
 <span data-ttu-id="7977d-217">Dinamik ve statik denetimi düzenekleri kullanırsanız, statik ayarları varsayılan olarak kullanılır, ancak daha sonra dinamik mekanizmasını kullanarak aşağıdaki kodda gösterildiği gibi geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="7977d-217">If you use both the dynamic and the static control mechanisms, the static settings are used as a default but can later be overridden by using the dynamic mechanism, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 <span data-ttu-id="7977d-218">Dinamik öznitelik denetimi ile yinelenen başlıkları oluşturma, aşağıdaki kodda gösterildiği olarak izin verilir.</span><span class="sxs-lookup"><span data-stu-id="7977d-218">Creating repeated headers with dynamic attribute control is allowed, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 <span data-ttu-id="7977d-219">Alıcı tarafında SOAP özniteliklerden okuma yalnızca varsa yapılabilir <xref:System.ServiceModel.MessageHeader%601> sınıfı türü üstbilgisinde için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7977d-219">On the receiving side, reading these SOAP attributes can only be done if the <xref:System.ServiceModel.MessageHeader%601> class is used for the header in the type.</span></span> <span data-ttu-id="7977d-220">İncelemek `Actor`, `Relay`, veya `MustUnderstand` başlık özelliklerini <xref:System.ServiceModel.MessageHeader%601> alınan iletide öznitelik ayarlarını bulmak için türü.</span><span class="sxs-lookup"><span data-stu-id="7977d-220">Examine the `Actor`, `Relay`, or `MustUnderstand` properties of a header of the <xref:System.ServiceModel.MessageHeader%601> type to discover the attribute settings on the received message.</span></span>  
  
 <span data-ttu-id="7977d-221">Bir ileti alındı ve geri gönderilen zaman SOAP özniteliği ayarları yalnızca üst bilgilerinin gidiş dönüş gidin <xref:System.ServiceModel.MessageHeader%601> türü.</span><span class="sxs-lookup"><span data-stu-id="7977d-221">When a message is received and then sent back, the SOAP attribute settings only go round-trip for headers of the <xref:System.ServiceModel.MessageHeader%601> type.</span></span>  
  
## <a name="order-of-soap-body-parts"></a><span data-ttu-id="7977d-222">SOAP gövdesi bölümleri sırasını</span><span class="sxs-lookup"><span data-stu-id="7977d-222">Order of SOAP Body Parts</span></span>  
 <span data-ttu-id="7977d-223">Bazı durumlarda, gövde bölümlerinin sırasını denetlemek gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="7977d-223">In some circumstances, you may need to control the order of the body parts.</span></span> <span data-ttu-id="7977d-224">Gövde öğelerin sırasını varsayılan olarak alfabetik ancak tarafından denetlenen <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="7977d-224">The order of the body elements is alphabetical by default, but can be controlled by the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="7977d-225">Bu özellik olarak aynı semantiklerine sahip <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> devralma senaryolarda (ileti sözleşmeleri, temel türü gövdesi üyeleri önce türetilen tür gövde üyeleri sıralanmamış) davranış dışında özelliği.</span><span class="sxs-lookup"><span data-stu-id="7977d-225">This property has the same semantics as the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> property, except for the behavior in inheritance scenarios (in message contracts, base type body members are not sorted before the derived type body members).</span></span> <span data-ttu-id="7977d-226">Daha fazla bilgi için bkz: [veri üye sırası](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span><span class="sxs-lookup"><span data-stu-id="7977d-226">For more information, see [Data Member Order](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span></span>  
  
 <span data-ttu-id="7977d-227">Aşağıdaki örnekte, `amount` alfabetik olarak ilk olduğundan normal olarak ilk gelecektir.</span><span class="sxs-lookup"><span data-stu-id="7977d-227">In the following example, `amount` would normally come first because it is first alphabetically.</span></span> <span data-ttu-id="7977d-228">Ancak, <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> özelliği, üçüncü yerine koyar.</span><span class="sxs-lookup"><span data-stu-id="7977d-228">However, the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> property puts it into the third position.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember(Order=1)] public Account sourceAccount;  
  [MessageBodyMember(Order=2)] public Account targetAccount;  
  [MessageBodyMember(Order=3)] public int amount;  
}  
```  
  
## <a name="message-contract-versioning"></a><span data-ttu-id="7977d-229">İleti sözleşmesi sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="7977d-229">Message Contract Versioning</span></span>  
 <span data-ttu-id="7977d-230">Bazen, ileti sözleşmeleri değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="7977d-230">Occasionally, you may need to change message contracts.</span></span> <span data-ttu-id="7977d-231">Örneğin, uygulamanızın yeni bir sürümünü iletiye ek üstbilgi ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="7977d-231">For example, a new version of your application may add an extra header to a message.</span></span> <span data-ttu-id="7977d-232">Ardından, gelen yeni sürümü eski gönderirken, sistem bir ek üstbilgi yanı sıra ile üstbilgisi eksik ters yönde geçerken ilgilenmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7977d-232">Then, when sending from the new version to the old, the system must deal with an extra header, as well as a missing header when going in the other direction.</span></span>  
  
 <span data-ttu-id="7977d-233">Sürüm üstbilgilerini aşağıdaki kurallar geçerli olur:</span><span class="sxs-lookup"><span data-stu-id="7977d-233">The following rules apply for versioning headers:</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="7977d-234"> eksik üstbilgileri nesne değildir — varsayılan değerlerine karşılık gelen üyeleri bırakılır.</span><span class="sxs-lookup"><span data-stu-id="7977d-234"> does not object to the missing headers—the corresponding members are left at their default values.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="7977d-235"> Ayrıca beklenmeyen fazladan üstbilgiler yoksayar.</span><span class="sxs-lookup"><span data-stu-id="7977d-235"> also ignores unexpected extra headers.</span></span> <span data-ttu-id="7977d-236">Ek üstbilgi varsa bu kuralın tek özel durum olan bir `MustUnderstand` özniteliğini `true` gelen SOAP iletisi — anlaşılmalıdır bir üstbilgi işlenemediği için bu durumda, bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="7977d-236">The one exception to this rule is if the extra header has a `MustUnderstand` attribute set to `true` in the incoming SOAP message—in this case, an exception is thrown because a header that must be understood cannot be processed.</span></span>  
  
 <span data-ttu-id="7977d-237">İleti gövdeleri sahip benzer sürüm oluşturma kuralları — eksik ve ek İleti gövde bölümü yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="7977d-237">Message bodies have similar versioning rules—both missing and additional message body parts are ignored.</span></span>  
  
## <a name="inheritance-considerations"></a><span data-ttu-id="7977d-238">Devralma hakkında önemli noktalar</span><span class="sxs-lookup"><span data-stu-id="7977d-238">Inheritance Considerations</span></span>  
 <span data-ttu-id="7977d-239">Temel türü bir ileti sözleşmesi de sahip olduğu sürece başka bir türden bir ileti sözleşmesi türü devralabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7977d-239">A message contract type can inherit from another type, as long as the base type also has a message contract.</span></span>  
  
 <span data-ttu-id="7977d-240">Oluşturma veya diğer ileti sözleşme türlerinden devralan bir ileti sözleşmesi türü kullanarak ileti erişme, aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="7977d-240">When creating or accessing a message using a message contract type that inherits from other message contract types, the following rules apply:</span></span>  
  
-   <span data-ttu-id="7977d-241">Tüm devralma hiyerarşisinde iletisi üstbilgilerinin birlikte ileti üstbilgilerini kümesini oluşturmak için toplanır.</span><span class="sxs-lookup"><span data-stu-id="7977d-241">All of the message headers in the inheritance hierarchy are collected together to form the full set of headers for the message.</span></span>  
  
-   <span data-ttu-id="7977d-242">Tüm devralma hiyerarşisi içinde ileti gövdesi parçalarını birlikte tam ileti gövdesini form için toplanır.</span><span class="sxs-lookup"><span data-stu-id="7977d-242">All of the message body parts in the inheritance hierarchy are collected together to form the full message body.</span></span> <span data-ttu-id="7977d-243">Gövde bölümlerinin normal sıralama kurallara göre sıralanır (tarafından <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> özelliği ve ardından alfabetik), hiçbir göreli kendi yerleştirmek için devralma hiyerarşisi.</span><span class="sxs-lookup"><span data-stu-id="7977d-243">The body parts are ordered according to the usual ordering rules (by <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property and then alphabetical), with no relevance to their place in the inheritance hierarchy.</span></span> <span data-ttu-id="7977d-244">İleti gövde bölümlerinin birden çok devralma ağacında düzeylerinde gerçekleştiği ileti sözleşme devralma kullanımı kesinlikle önerilmez.</span><span class="sxs-lookup"><span data-stu-id="7977d-244">Using message contract inheritance where message body parts occur at multiple levels of the inheritance tree is strongly discouraged.</span></span> <span data-ttu-id="7977d-245">Bir taban sınıf ve türetilmiş bir sınıf bir üstbilgi veya aynı ada sahip bir gövde bölümü tanımlarsanız, çoğu temel sınıfından üye Bu üstbilgi veya gövde bölümü değeri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7977d-245">If a base class and a derived class define a header or a body part with the same name, the member from the base-most class is used to store the value of that header or body part.</span></span>  
  
 <span data-ttu-id="7977d-246">Aşağıdaki kod örneğinde sınıflarda göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="7977d-246">Consider the classes in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class PersonRecord  
{  
  [MessageHeader(Name="ID")] public int personID;  
  [MessageBodyMember] public string patientName;  
}  
  
[MessageContract]  
public class PatientRecord : PersonRecord  
{  
  [MessageHeader(Name="ID")] public int patientID;  
  [MessageBodyMember] public string diagnosis;  
}  
```  
  
 <span data-ttu-id="7977d-247">`PatientRecord` Sınıfı açıklayan bir ileti adlı bir üstbilgiyle `ID`.</span><span class="sxs-lookup"><span data-stu-id="7977d-247">The `PatientRecord` class describes a message with one header called `ID`.</span></span> <span data-ttu-id="7977d-248">Üstbilgi karşılık gelen `personID` ve `patientID` üye, temel çoğu üyesi seçilir olduğundan.</span><span class="sxs-lookup"><span data-stu-id="7977d-248">The header corresponds to the `personID` and not the `patientID` member, because the base-most member is chosen.</span></span> <span data-ttu-id="7977d-249">Bu nedenle, `patientID` alandır gereksiz bu durumda.</span><span class="sxs-lookup"><span data-stu-id="7977d-249">Thus, the `patientID` field is useless in this case.</span></span> <span data-ttu-id="7977d-250">İleti gövdesini içeren `diagnosis` öğesi arkasından `patientName` öğesi alfabetik olduğu için.</span><span class="sxs-lookup"><span data-stu-id="7977d-250">The body of the message contains the `diagnosis` element followed by the `patientName` element, because that is the alphabetical order.</span></span> <span data-ttu-id="7977d-251">Örnek kesinlikle önerilmez bir desen gösterdiğine dikkat edin: hem temel hem de türetilmiş ileti sözleşmeleri ileti gövdesi bölümden oluşur.</span><span class="sxs-lookup"><span data-stu-id="7977d-251">Notice that the example shows a pattern that is strongly discouraged: both the base and the derived message contracts have message body parts.</span></span>  
  
## <a name="wsdl-considerations"></a><span data-ttu-id="7977d-252">WSDL konuları</span><span class="sxs-lookup"><span data-stu-id="7977d-252">WSDL Considerations</span></span>  
 <span data-ttu-id="7977d-253">Web Hizmetleri Açıklama Dili (WSDL) sözleşme ileti sözleşmeleri kullanan bir hizmetinden oluştururken, tüm ileti sözleşmesi özellikleri elde edilen WSDL içinde yansıtılır hatırlamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="7977d-253">When generating a Web Services Description Language (WSDL) contract from a service that uses message contracts, it is important to remember that not all message contract features are reflected in the resulting WSDL.</span></span> <span data-ttu-id="7977d-254">Aşağıdaki noktaları göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="7977d-254">Consider the following points:</span></span>  
  
-   <span data-ttu-id="7977d-255">WSDL üstbilgileri dizisi kavramı hızlı olamaz.</span><span class="sxs-lookup"><span data-stu-id="7977d-255">WSDL cannot express the concept of an array of headers.</span></span> <span data-ttu-id="7977d-256">İletileri kullanarak üstbilgileri bir dizi oluşturulurken <xref:System.ServiceModel.MessageHeaderArrayAttribute>, sonuçta elde edilen WSDL dizi yerine yalnızca bir üstbilgi yansıtır.</span><span class="sxs-lookup"><span data-stu-id="7977d-256">When creating messages with an array of headers using the <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the resulting WSDL reflects only one header instead of the array.</span></span>  
  
-   <span data-ttu-id="7977d-257">Sonuçta elde edilen WSDL belgesinde bazı koruma düzeyi bilgileri yansıtmaz.</span><span class="sxs-lookup"><span data-stu-id="7977d-257">The resulting WSDL document may not reflect some protection-level information.</span></span>  
  
-   <span data-ttu-id="7977d-258">WSDL içinde oluşturulan ileti türü ileti sözleşme türü sınıf adı ile aynı ada sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7977d-258">The message type generated in the WSDL has the same name as the class name of the message contract type.</span></span>  
  
-   <span data-ttu-id="7977d-259">Birden çok işlemlerinde aynı iletiyi kullanarak sözleşme, birden çok ileti türlerini WSDL belgesinde üretilir.</span><span class="sxs-lookup"><span data-stu-id="7977d-259">When using the same message contract in multiple operations, multiple message types are generated in the WSDL document.</span></span> <span data-ttu-id="7977d-260">Adları "3", numaraları "2" ekleyerek ve benzeri sonraki kullanımlar için benzersiz yapılır.</span><span class="sxs-lookup"><span data-stu-id="7977d-260">The names are made unique by adding the numbers "2", "3", and so on, for subsequent uses.</span></span> <span data-ttu-id="7977d-261">Geri WSDL içe aktarırken, birden çok ileti sözleşme türleri oluşturulur ve adlarını dışında aynıdır.</span><span class="sxs-lookup"><span data-stu-id="7977d-261">When importing back the WSDL, multiple message contract types are created and are identical except for their names.</span></span>  
  
## <a name="soap-encoding-considerations"></a><span data-ttu-id="7977d-262">SOAP konuları kodlama</span><span class="sxs-lookup"><span data-stu-id="7977d-262">SOAP Encoding Considerations</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="7977d-263"> eski SOAP kodlama stilini XML kullanmanıza olanak tanır ancak kullanımı önerilmez.</span><span class="sxs-lookup"><span data-stu-id="7977d-263"> allows you to use the legacy SOAP encoding style of XML, however, its use is not recommended.</span></span> <span data-ttu-id="7977d-264">Bu stili kullanırken (ayarlayarak `Use` özelliğine `Encoded` üzerinde <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> hizmet sözleşmesini uygulanan), aşağıdaki ek maddeler geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="7977d-264">When using this style (by setting the `Use` property to `Encoded` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> applied to the service contract), the following additional considerations apply:</span></span>  
  
-   <span data-ttu-id="7977d-265">İleti üstbilgilerini desteklenmez; Bu öznitelik anlamına <xref:System.ServiceModel.MessageHeaderAttribute> ve dizi öznitelik <xref:System.ServiceModel.MessageHeaderArrayAttribute> SOAP kodlama ile uyumlu değil.</span><span class="sxs-lookup"><span data-stu-id="7977d-265">The message headers are not supported; this means that the attribute <xref:System.ServiceModel.MessageHeaderAttribute> and the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute> are incompatible with SOAP encoding.</span></span>  
  
-   <span data-ttu-id="7977d-266">İleti sözleşmesi, diğer bir deyişle, sarmalanmamış varsa özelliği <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> ayarlanır `false`, ileti sözleşmesi yalnızca bir gövde bölümü olabilir.</span><span class="sxs-lookup"><span data-stu-id="7977d-266">If the message contract is not wrapped, that is, if the property <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> is set to `false`, the message contract can have only one body part.</span></span>  
  
-   <span data-ttu-id="7977d-267">İstek ileti sözleşmesi için sarmalayıcı öğesi adını, işlem adı eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="7977d-267">The name of the wrapper element for the request message contract must match the operation name.</span></span> <span data-ttu-id="7977d-268">Kullanım `WrapperName` bu ileti sözleşmesi özelliği.</span><span class="sxs-lookup"><span data-stu-id="7977d-268">Use the `WrapperName` property of the message contract for this.</span></span>  
  
-   <span data-ttu-id="7977d-269">Yanıt ileti sözleşmesi için kapsayıcı öğe adını 'Yanıtıyla' sonekine işlemin adı ile aynı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7977d-269">The name of the wrapper element for the response message contract must be the same as the name of the operation suffixed by 'Response'.</span></span> <span data-ttu-id="7977d-270">Kullanım <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> bu ileti sözleşmesi özelliği.</span><span class="sxs-lookup"><span data-stu-id="7977d-270">Use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> property of the message contract for this.</span></span>  
  
-   <span data-ttu-id="7977d-271">SOAP kodlama nesne başvuruları korur.</span><span class="sxs-lookup"><span data-stu-id="7977d-271">SOAP encoding preserves object references.</span></span> <span data-ttu-id="7977d-272">Örneğin, aşağıdaki kodu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="7977d-272">For example, consider the following code.</span></span>  
  
    ```csharp  
    [MessageContract(WrapperName="updateChangeRecord")]  
    public class ChangeRecordRequest  
    {  
      [MessageBodyMember] Person changedBy;  
      [MessageBodyMember] Person changedFrom;  
      [MessageBodyMember] Person changedTo;  
    }  
  
    [MessageContract(WrapperName="updateChangeRecordResponse")]  
    public class ChangeRecordResponse  
    {  
      [MessageBodyMember] Person changedBy;  
      [MessageBodyMember] Person changedFrom;  
      [MessageBodyMember] Person changedTo;  
    }  
  
    // application code:  
    ChangeRecordRequest cr = new ChangeRecordRequest();  
    Person p = new Person("John Doe");  
    cr.changedBy=p;  
    cr.changedFrom=p;  
    cr.changedTo=p;  
    ```  
  
 <span data-ttu-id="7977d-273">İletinin SOAP kodlama, kullanılarak seri hale getirme sonra `changedFrom` ve `changedTo` kendi kopyalarını içermeyen `p`, ancak bunun yerine iç kopyayı işaret `changedBy` öğesi.</span><span class="sxs-lookup"><span data-stu-id="7977d-273">After serializing the message using SOAP encoding, `changedFrom` and `changedTo` do not contain their own copies of `p`, but instead point to the copy inside the `changedBy` element.</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="7977d-274">Başarım Değerlendirmeleri</span><span class="sxs-lookup"><span data-stu-id="7977d-274">Performance Considerations</span></span>  
 <span data-ttu-id="7977d-275">Her ileti başlığı ve ileti Gövde bölümünün bağımsız olarak diğer serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="7977d-275">Every message header and message body part is serialized independently of the others.</span></span> <span data-ttu-id="7977d-276">Bu nedenle, aynı ad alanları yeniden her başlık ve gövde bölümü için bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="7977d-276">Therefore, the same namespaces can be declared again for each header and body part.</span></span> <span data-ttu-id="7977d-277">Özellikle Tel üzerinde iletinin boyutunu bakımından performansını artırmak için birden çok üst bilgiler ve gövde bölümlerinin tek bir üstbilgi veya gövde bölümüne birleştirin.</span><span class="sxs-lookup"><span data-stu-id="7977d-277">To improve performance, especially in terms of the size of the message on the wire, consolidate multiple headers and body parts into a single header or body part.</span></span> <span data-ttu-id="7977d-278">Örneğin, aşağıdaki kodu yerine:</span><span class="sxs-lookup"><span data-stu-id="7977d-278">For example, instead of the following code:</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public Account sourceAccount;  
  [MessageBodyMember] public Account targetAccount;  
  [MessageBodyMember] public int amount;  
}  
```  
  
 <span data-ttu-id="7977d-279">Bu kodu kullanın.</span><span class="sxs-lookup"><span data-stu-id="7977d-279">Use this code.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public OperationDetails details;  
}  
  
[DataContract]  
public class OperationDetails  
{  
  [DataMember] public Account sourceAccount;  
  [DataMember] public Account targetAccount;  
  [DataMember] public int amount;  
}  
```  
  
### <a name="event-based-asynchronous-and-message-contracts"></a><span data-ttu-id="7977d-280">Olay tabanlı zaman uyumsuz ve ileti sözleşmeleri</span><span class="sxs-lookup"><span data-stu-id="7977d-280">Event-based Asynchronous and Message Contracts</span></span>  
 <span data-ttu-id="7977d-281">Olay tabanlı zaman uyumsuz modeli için tasarım yönergeleri birden fazla değer döndürülürse, tek bir değer olarak döndürülen durum `Result` özelliği ve diğerleri döndürülür özellikleri olarak üzerinde <xref:System.EventArgs> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="7977d-281">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="7977d-282">Bunun bir sonucu olduğundan, bu, istemci olay tabanlı zaman uyumsuz komut seçeneklerini kullanarak meta verilerini alır ve birden fazla değer, varsayılan işlemi döndürürse <xref:System.EventArgs> nesnesi döndüren bir değer olarak `Result` özelliği ve geri kalan özelliklerini <xref:System.EventArgs> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="7977d-282">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="7977d-283">İleti nesnesi olarak almak istiyorsanız `Result` özelliği ve bu nesne üzerinde özellikleri kullanma gibi döndürülen değerlere sahip `/messageContract` komut seçeneği.</span><span class="sxs-lookup"><span data-stu-id="7977d-283">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="7977d-284">Bu olarak yanıt iletisi döndüren bir imza oluşturur `Result` özellikte <xref:System.EventArgs> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="7977d-284">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="7977d-285">Tüm iç dönüş değerleri yanıt iletisi nesnesi sonra özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="7977d-285">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7977d-286">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7977d-286">See Also</span></span>  
 [<span data-ttu-id="7977d-287">Veri Anlaşmalarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="7977d-287">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="7977d-288">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="7977d-288">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)
