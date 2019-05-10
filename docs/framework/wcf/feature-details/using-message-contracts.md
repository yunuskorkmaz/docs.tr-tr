---
title: İleti Sözleşmeleri Kullanılıyor
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message contracts [WCF]
ms.assetid: 1e19c64a-ae84-4c2f-9155-91c54a77c249
ms.openlocfilehash: 829bdda3f3302d8d3c41e704dc8caf88720d1ebc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64637590"
---
# <a name="using-message-contracts"></a><span data-ttu-id="ba1ea-102">İleti Sözleşmeleri Kullanılıyor</span><span class="sxs-lookup"><span data-stu-id="ba1ea-102">Using Message Contracts</span></span>
<span data-ttu-id="ba1ea-103">Genellikle Windows Communication Foundation (WCF) uygulamaları oluştururken geliştiriciler serileştirme sorunlarına ve veri yapıları Kapat dikkat ve kendilerini hangi verileri taşınan iletileri yapısı ile uğraşmak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-103">Typically when building Windows Communication Foundation (WCF) applications, developers pay close attention to the data structures and serialization issues and do not need to concern themselves with the structure of the messages in which the data is carried.</span></span> <span data-ttu-id="ba1ea-104">Bu uygulamalar için parametreleri veya dönüş değerleri için veri sözleşmeleri oluşturma oldukça basittir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-104">For these applications, creating data contracts for the parameters or return values is straightforward.</span></span> <span data-ttu-id="ba1ea-105">(Daha fazla bilgi için [hizmet sözleşmelerinde veri aktarımı belirtme](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).)</span><span class="sxs-lookup"><span data-stu-id="ba1ea-105">(For more information, see [Specifying Data Transfer in Service Contracts](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).)</span></span>  
  
 <span data-ttu-id="ba1ea-106">Ancak, bir SOAP ileti yapısını bazen tam kontrole yalnızca içeriği üzerinde denetim olarak da önemlidir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-106">However, sometimes complete control over the structure of a SOAP message is just as important as control over its contents.</span></span> <span data-ttu-id="ba1ea-107">Birlikte çalışabilirlik önemli olduğunda veya özellikle güvenlik denetlemek için ileti veya ileti bölümü düzeyinde sorunları özellikle doğrudur.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-107">This is especially true when interoperability is important or to specifically control security issues at the level of the message or message part.</span></span> <span data-ttu-id="ba1ea-108">Bu durumlarda, oluşturduğunuz bir *ileti anlaşması* gereken kesin SOAP iletisi yapısını belirtmenize imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-108">In these cases, you can create a *message contract* that enables you to specify the structure of the precise SOAP message required.</span></span>  
  
 <span data-ttu-id="ba1ea-109">Bu konu, çeşitli ileti anlaşması öznitelikleri oluşturma işlemi için bir özel ileti anlaşması için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-109">This topic discusses how to use the various message contract attributes to create a specific message contract for your operation.</span></span>  
  
## <a name="using-message-contracts-in-operations"></a><span data-ttu-id="ba1ea-110">İleti sözleşmeleri işlemlerinde kullanma</span><span class="sxs-lookup"><span data-stu-id="ba1ea-110">Using Message Contracts in Operations</span></span>  
 <span data-ttu-id="ba1ea-111">WCF desteklediği işlemleri üzerinde modellenmiş *uzak yordam çağrısı (RPC) stili* veya *stil Mesajlaşma*.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-111">WCF supports operations modeled on either the *remote procedure call (RPC) style* or the *messaging style*.</span></span> <span data-ttu-id="ba1ea-112">RPC stili işleminde, serializable bir tür kullanabilirsiniz ve birden çok parametre gibi yerel çağrıları kullanılabilir özelliklere erişiminiz ve `ref` ve `out` parametreleri.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-112">In an RPC-style operation, you can use any serializable type, and you have access to the features that are available to local calls, such as multiple parameters and `ref` and `out` parameters.</span></span> <span data-ttu-id="ba1ea-113">Bu stilde, temel alınan iletileri verilerin yapısını seçilen serileştirme biçimini denetler ve WCF çalıştırma zamanı işlemi desteklemek için iletileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-113">In this style, the form of serialization chosen controls the structure of the data in the underlying messages, and the WCF runtime creates the messages to support the operation.</span></span> <span data-ttu-id="ba1ea-114">Bu, SOAP ile tanıdık olmayan iletileri hızla SOAP ve kolayca oluşturun ve hizmet uygulamalarını kullanmak geliştiriciler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-114">This enables developers who are not familiar with SOAP and SOAP messages to quickly and easily create and use service applications.</span></span>  
  
 <span data-ttu-id="ba1ea-115">Aşağıdaki kod örneği bir hizmet işlemi RPC stili modellenmiş gösterir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-115">The following code example shows a service operation modeled on the RPC style.</span></span>  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 <span data-ttu-id="ba1ea-116">Normalde, bir veri anlaşması iletileri için şema tanımlamak yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-116">Normally, a data contract is sufficient to define the schema for the messages.</span></span> <span data-ttu-id="ba1ea-117">Örneğin, önceki örnekte, çoğu uygulama için yeterlidir, `BankingTransaction` ve `BankingTransactionResponse` temel SOAP iletilerinin içeriğini tanımlamak için veri sözleşmelerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-117">For instance, in the preceding example, it is sufficient for most applications if `BankingTransaction` and `BankingTransactionResponse` have data contracts to define the contents of the underlying SOAP messages.</span></span> <span data-ttu-id="ba1ea-118">Veri sözleşmeleri hakkında daha fazla bilgi için bkz: [kullanarak veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="ba1ea-118">For more information about data contracts, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="ba1ea-119">Ancak, bazen nasıl SOAP iletisi yapısını hat üzerinden iletilen tam olarak denetlemek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-119">However, occasionally it is necessary to precisely control how the structure of the SOAP message transmitted over the wire.</span></span> <span data-ttu-id="ba1ea-120">En yaygın senaryo için bu özel SOAP üstbilgileri ekliyor.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-120">The most common scenario for this is inserting custom SOAP headers.</span></span> <span data-ttu-id="ba1ea-121">Diğer bir deyişle ileti üstbilgileri ve gövdesi için güvenlik özelliklerini tanımlamak için bu öğeleri dijital olarak imzalanmış ve şifrelenmiş olmadığını karar vermek için başka bir yaygın bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-121">Another common scenario is to define security properties for the message's headers and body, that is, to decide whether these elements are digitally signed and encrypted.</span></span> <span data-ttu-id="ba1ea-122">Son olarak, bazı üçüncü taraf SOAP yığınları iletileri gerektiren belirli bir biçiminde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-122">Finally, some third-party SOAP stacks require messages be in a specific format.</span></span> <span data-ttu-id="ba1ea-123">İleti stili işlemleri bu denetimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-123">Messaging-style operations provide this control.</span></span>  
  
 <span data-ttu-id="ba1ea-124">Her iki ileti türleri olduğu en fazla bir parametre ve bir dönüş değeri bir Mesajlaşma stili işlemi var; diğer bir deyişle, doğrudan belirtilen bir SOAP ileti yapısına serileştirir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-124">A messaging-style operation has at most one parameter and one return value where both types are message types; that is, they serialize directly into a specified SOAP message structure.</span></span> <span data-ttu-id="ba1ea-125">Bu ile işaretlenen herhangi bir tür olabilir <xref:System.ServiceModel.MessageContractAttribute> veya <xref:System.ServiceModel.Channels.Message> türü.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-125">This may be any type marked with the <xref:System.ServiceModel.MessageContractAttribute> or the <xref:System.ServiceModel.Channels.Message> type.</span></span> <span data-ttu-id="ba1ea-126">Aşağıdaki kod örneği bir işlemi önceki RCP stil benzeyen gösterir, ancak ileti stili kullanır.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-126">The following code example shows an operation similar to the preceding RCP-style, but which uses the messaging style.</span></span>  
  
 <span data-ttu-id="ba1ea-127">Örneğin, varsa `BankingTransaction` ve `BankingTransactionResponse` kod aşağıdaki işlemleri içinde geçerli ise, ileti sözleşmeleri, her iki türlerdir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-127">For example, if `BankingTransaction` and `BankingTransactionResponse` are both types that are message contracts, then the code in the following operations is valid.</span></span>  
  
```csharp  
[OperationContract]  
BankingTransactionResponse Process(BankingTransaction bt);  
[OperationContract]  
void Store(BankingTransaction bt);  
[OperationContract]  
BankingTransactionResponse GetResponse();  
```  
  
 <span data-ttu-id="ba1ea-128">Ancak, aşağıdaki kodu geçersiz.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-128">However, the following code is invalid.</span></span>  
  
```csharp  
[OperationContract]  
bool Validate(BankingTransaction bt);  
// Invalid, the return type is not a message contract.  
[OperationContract]  
void Reconcile(BankingTransaction bt1, BankingTransaction bt2);  
// Invalid, there is more than one parameter.  
```  
  
 <span data-ttu-id="ba1ea-129">Bir özel durum, ileti anlaşması türü içerir ve bu geçerli desenlerden birini izlemez herhangi bir işlem için oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-129">An exception is thrown for any operation that involves a message contract type and that does not follow one of the valid patterns.</span></span> <span data-ttu-id="ba1ea-130">Elbette, ileti anlaşması türleri içermeyen işlemler bu sınırlamalara tabi değildir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-130">Of course, operations that do not involve message contract types are not subject to these restrictions.</span></span>  
  
 <span data-ttu-id="ba1ea-131">Bir ileti anlaşması hem de bir veri anlaşması türü varsa, yalnızca ileti anlaşması türü bir işleminde kullanıldığında olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-131">If a type has both a message contract and a data contract, only its message contract is considered when the type is used in an operation.</span></span>  
  
## <a name="defining-message-contracts"></a><span data-ttu-id="ba1ea-132">İleti sözleşmeleri tanımlama</span><span class="sxs-lookup"><span data-stu-id="ba1ea-132">Defining Message Contracts</span></span>  
 <span data-ttu-id="ba1ea-133">Bir tür için bir ileti anlaşması tanımlamak için (diğer bir deyişle, türü ve SOAP Zarfı arasındaki eşlemeyi tanımlamak için), uygulama <xref:System.ServiceModel.MessageContractAttribute> türü.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-133">To define a message contract for a type (that is, to define the mapping between the type and a SOAP envelope), apply the <xref:System.ServiceModel.MessageContractAttribute> to the type.</span></span> <span data-ttu-id="ba1ea-134">Daha sonra uygulamanızı <xref:System.ServiceModel.MessageHeaderAttribute> SOAP başlıkları ve uygulamak istediğiniz türü bu üye için <xref:System.ServiceModel.MessageBodyMemberAttribute> iletinin SOAP gövdesi parçalara yapmak istediğiniz bu üyelere.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-134">Then apply the <xref:System.ServiceModel.MessageHeaderAttribute> to those members of the type you want to make into SOAP headers, and apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to those members you want to make into parts of the SOAP body of the message.</span></span>  
  
 <span data-ttu-id="ba1ea-135">Aşağıdaki kod, bir ileti anlaşması kullanarak bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-135">The following code provides an example of using a message contract.</span></span>  
  
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
  
 <span data-ttu-id="ba1ea-136">Bu tür bir işlem parametresi olarak kullanırken, aşağıdaki SOAP Zarfı oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="ba1ea-136">When using this type as an operation parameter, the following SOAP envelope is generated:</span></span>  
  
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
  
 <span data-ttu-id="ba1ea-137">Dikkat `operation` ve `transactionDate` SOAP üst bilgi olarak görünür ve bir sarmalayıcı öğe SOAP gövdesi oluşur `BankingTransaction` içeren `sourceAccount`,`targetAccount`, ve `amount`.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-137">Notice that `operation` and `transactionDate` appear as SOAP headers and the SOAP body consists of a wrapper element `BankingTransaction` containing `sourceAccount`,`targetAccount`, and `amount`.</span></span>  
  
 <span data-ttu-id="ba1ea-138">Uygulayabileceğiniz <xref:System.ServiceModel.MessageHeaderAttribute> ve <xref:System.ServiceModel.MessageBodyMemberAttribute> için tüm alanlar, özellikler ve olaylar, genel, özel, korumalı veya iç olup olmadıkları ne olursa olsun.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-138">You can apply the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> to all fields, properties, and events, regardless of whether they are public, private, protected, or internal.</span></span>  
  
 <span data-ttu-id="ba1ea-139"><xref:System.ServiceModel.MessageContractAttribute> Kontrol SOAP ileti gövdesinde sarmalayıcı öğe adı WrapperName ve WrapperNamespace öznitelikler belirtmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-139">The <xref:System.ServiceModel.MessageContractAttribute> allows you to specify the WrapperName and WrapperNamespace attributes which control the name of the wrapper element in the body of the SOAP message.</span></span> <span data-ttu-id="ba1ea-140">İleti sözleşmesi adını varsayılan olarak tür sarmalayıcı ve ileti anlaşması tanımlanır ad alanı için kullanılan `http://tempuri.org/` varsayılan ad alanı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-140">By default the name of the message contract type is used for the wrapper and the namespace in which the message contract is defined `http://tempuri.org/` is used as the default namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ba1ea-141"><xref:System.Runtime.Serialization.KnownTypeAttribute> ileti sözleşmeleri öznitelikleri yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-141"><xref:System.Runtime.Serialization.KnownTypeAttribute> attributes are ignored in message contracts.</span></span> <span data-ttu-id="ba1ea-142">Varsa bir <xref:System.Runtime.Serialization.KnownTypeAttribute> olan gerekli, bunu, ileti anlaşması kullanarak işlemi söz konusu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-142">If a <xref:System.Runtime.Serialization.KnownTypeAttribute> is required, place it on the operation that is using the message contract in question.</span></span>  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a><span data-ttu-id="ba1ea-143">Başlık ve gövde bölümü adlarına ve ad alanları denetleme</span><span class="sxs-lookup"><span data-stu-id="ba1ea-143">Controlling Header and Body Part Names and Namespaces</span></span>  
 <span data-ttu-id="ba1ea-144">Bir ileti anlaşması SOAP gösterimini her başlık ve gövde bölümü bir ad ve bir ad alanı olan bir XML öğesi eşler.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-144">In the SOAP representation of a message contract, each header and body part maps to an XML element that has a name and a namespace.</span></span>  
  
 <span data-ttu-id="ba1ea-145">Varsayılan olarak, ad alanı ileti katılan ve ad üye adı belirlenir hizmet sözleşmesi ad alanı ile aynı olduğu <xref:System.ServiceModel.MessageHeaderAttribute> veya <xref:System.ServiceModel.MessageBodyMemberAttribute> öznitelikler uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-145">By default, the namespace is the same as the namespace of the service contract that the message is participating in, and the name is determined by the member name to which the <xref:System.ServiceModel.MessageHeaderAttribute> or the <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes are applied.</span></span>  
  
 <span data-ttu-id="ba1ea-146">Bu varsayılan işleyerek değiştirebileceğiniz <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> ve <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (üst sınıfı üzerinde <xref:System.ServiceModel.MessageHeaderAttribute> ve <xref:System.ServiceModel.MessageBodyMemberAttribute> öznitelikleri).</span><span class="sxs-lookup"><span data-stu-id="ba1ea-146">You can change these defaults by manipulating the <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (on the parent class of the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes).</span></span>  
  
 <span data-ttu-id="ba1ea-147">Aşağıdaki kod örneği sınıfında göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-147">Consider the class in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader(Namespace="http://schemas.contoso.com/auditing/2005")] public bool IsAudited;  
  [MessageBodyMember(Name="transactionData")] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="ba1ea-148">Bu örnekte, `IsAudited` başlığıdır kod ve gövde bölümünü temsil eden içinde belirtilen ad alanında `theData` üye bir XML öğesi adı ile temsil edilir `transactionData`.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-148">In this example, the `IsAudited` header is in the namespace specified in the code, and the body part that represents the `theData` member is represented by an XML element with the name `transactionData`.</span></span> <span data-ttu-id="ba1ea-149">Bu ileti anlaşması için oluşturulan XML gösterir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-149">The following shows the XML generated for this message contract.</span></span>  
  
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
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a><span data-ttu-id="ba1ea-150">SOAP gövdesi bölümleri sarmalanmış olup olmadığını denetleme</span><span class="sxs-lookup"><span data-stu-id="ba1ea-150">Controlling Whether the SOAP Body Parts Are Wrapped</span></span>  
 <span data-ttu-id="ba1ea-151">Varsayılan olarak, SOAP gövdesi bölümleri içinde sarmalanmış bir öğe olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-151">By default, the SOAP body parts are serialized inside a wrapped element.</span></span> <span data-ttu-id="ba1ea-152">Örneğin, aşağıdaki kod gösterir `HelloGreetingMessage` adından oluşturulmuş sarmalayıcı öğe <xref:System.ServiceModel.MessageContractAttribute> için ileti anlaşması türü `HelloGreetingMessage` ileti.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-152">For example, the following code shows the `HelloGreetingMessage` wrapper element generated from the name of the <xref:System.ServiceModel.MessageContractAttribute> type in the message contract for the `HelloGreetingMessage` message.</span></span>  
  
[!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
[!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 <span data-ttu-id="ba1ea-153">Sarmalayıcı öğe bastırmak için ayarlanmış <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> özelliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-153">To suppress the wrapper element, set the <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> property to `false`.</span></span> <span data-ttu-id="ba1ea-154">Ad ve sarmalayıcı öğe ad alanı denetlemek için kullanın <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> ve <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-154">To control the name and the namespace of the wrapper element, use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> and <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ba1ea-155">Birden fazla ileti Gövde bölümünün değil sarmalanır iletilerinde sahip WS ile uyumlu değil-ı Basic Profile 1.1 ve yeni ileti sözleşmeleri tasarlarken önerilmez.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-155">Having more than one message body part in messages that are not wrapped is not compliant with WS-I Basic Profile 1.1 and is not recommended when designing new message contracts.</span></span> <span data-ttu-id="ba1ea-156">Ancak, birden fazla sarmalanmış halden ileti Gövde bölümünün sahip belirli belirli birlikte çalışabilirlik senaryolarında gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-156">However, it may be necessary to have more than one unwrapped message body part in certain specific interoperability scenarios.</span></span> <span data-ttu-id="ba1ea-157">Birden fazla parça ileti gövdesinde veri iletmek için kullanacaksanız, varsayılan (sarmalanmış) modunu kullanmak için önerilir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-157">If you are going to transmit more than one piece of data in a message body, it is recommended to use the default (wrapped) mode.</span></span> <span data-ttu-id="ba1ea-158">Açılmamış iletiler içinde birden fazla ileti üst bilgisi sahip, tamamen kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-158">Having more than one message header in unwrapped messages is completely acceptable.</span></span>  
  
## <a name="using-custom-types-inside-message-contracts"></a><span data-ttu-id="ba1ea-159">İleti sözleşmeleri içinde özel türleri kullanma</span><span class="sxs-lookup"><span data-stu-id="ba1ea-159">Using Custom Types Inside Message Contracts</span></span>  
 <span data-ttu-id="ba1ea-160">(XML olarak açık) her ayrı ileti üst bilgisi ve ileti Gövde bölümünün serileştirilmiş ileti kullanıldığı hizmet sözleşmesi için seçilen serileştirme motoruna kullanarak.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-160">Each individual message header and message body part is serialized (turned into XML) using the chosen serialization engine for the service contract where the message is used.</span></span> <span data-ttu-id="ba1ea-161">Varsayılan serileştirme motoruna `XmlFormatter`, bir veri sözleşmesi ya da açıkça sahip herhangi bir türü işleyebilir (sahip <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) ya da örtük olarak (ilkel bir tür olan, sahip <xref:System.SerializableAttribute?displayProperty=nameWithType>, vb.).</span><span class="sxs-lookup"><span data-stu-id="ba1ea-161">The default serialization engine, the `XmlFormatter`, can handle any type that has a data contract, either explicitly (by having the <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) or implicitly (by being a primitive type, having the <xref:System.SerializableAttribute?displayProperty=nameWithType>, and so on).</span></span> <span data-ttu-id="ba1ea-162">Daha fazla bilgi için [kullanarak veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="ba1ea-162">For more information, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="ba1ea-163">Yukarıdaki örnekte, `Operation` ve `BankingTransactionData` türlerinin bir veri sözleşmesi olmalıdır ve `transactionDate` seri hale getirilemez çünkü <xref:System.DateTime> basit bir tür (ve bu nedenle bir örtük veri sözleşmesi).</span><span class="sxs-lookup"><span data-stu-id="ba1ea-163">In the preceding example, the `Operation` and `BankingTransactionData` types must have a data contract, and `transactionDate` is serializable because <xref:System.DateTime> is a primitive (and so has an implicit data contract).</span></span>  
  
 <span data-ttu-id="ba1ea-164">Ancak, farklı bir seri hale getirme altyapısı için geçiş yapmak olası `XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-164">However, it is possible to switch to a different serialization engine, the `XmlSerializer`.</span></span> <span data-ttu-id="ba1ea-165">Böyle bir geçiş yaparsanız, tüm ileti üstbilgileri ve gövde bölümleri için kullanılan türleri seri hale getirilebilir kullanarak olduğundan emin olmalı `XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-165">If you make such a switch, you should ensure that all of the types used for message headers and body parts are serializable using the `XmlSerializer`.</span></span>  
  
## <a name="using-arrays-inside-message-contracts"></a><span data-ttu-id="ba1ea-166">İleti sözleşmeleri içinde dizileri kullanma</span><span class="sxs-lookup"><span data-stu-id="ba1ea-166">Using Arrays Inside Message Contracts</span></span>  
 <span data-ttu-id="ba1ea-167">İleti sözleşmeleri iki yolla öğelerinde yineleme dizileri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-167">You can use arrays of repeating elements in message contracts in two ways.</span></span>  
  
 <span data-ttu-id="ba1ea-168">İlk kullanmaktır bir <xref:System.ServiceModel.MessageHeaderAttribute> veya <xref:System.ServiceModel.MessageBodyMemberAttribute> dizi üzerinde doğrudan.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-168">The first is to use a <xref:System.ServiceModel.MessageHeaderAttribute> or a <xref:System.ServiceModel.MessageBodyMemberAttribute> directly on the array.</span></span> <span data-ttu-id="ba1ea-169">Bu durumda, tüm dizi bir öğe (diğer bir deyişle, bir üst bilgi veya bir gövde bölümü) ile birden çok alt öğe olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-169">In this case, the entire array is serialized as one element (that is, one header or one body part) with multiple child elements.</span></span> <span data-ttu-id="ba1ea-170">Aşağıdaki örnekte sınıf göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-170">Consider the class in the following example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingDepositLog  
{  
  [MessageHeader] public int numRecords;  
  [MessageHeader] public DepositRecord[] records;  
  [MessageHeader] public int branchID;  
}  
```  
  
 <span data-ttu-id="ba1ea-171">SOAP üstbilgileri bu sonuçlar aşağıdakine benzer.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-171">This results in SOAP headers is similar to the following.</span></span>  
  
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
  
 <span data-ttu-id="ba1ea-172">Bu alternatif kullanmaktır <xref:System.ServiceModel.MessageHeaderArrayAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-172">An alternative to this is to use the <xref:System.ServiceModel.MessageHeaderArrayAttribute>.</span></span> <span data-ttu-id="ba1ea-173">Bu durumda, her dizi öğesi bağımsız olarak serileştirilmiş ve her dizi öğesi bir üst bilgi, aşağıdakine benzer olduğundan.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-173">In this case, each array element is serialized independently and so that each array element has one header, similar to the following.</span></span>  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 <span data-ttu-id="ba1ea-174">Dizi girişleri için varsayılan adı üyesine adıdır <xref:System.ServiceModel.MessageHeaderArrayAttribute> öznitelikler uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-174">The default name for array entries is the name of the member to which the <xref:System.ServiceModel.MessageHeaderArrayAttribute> attributes is applied.</span></span>  
  
 <span data-ttu-id="ba1ea-175"><xref:System.ServiceModel.MessageHeaderArrayAttribute> Özniteliğini devraldığı <xref:System.ServiceModel.MessageHeaderAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-175">The <xref:System.ServiceModel.MessageHeaderArrayAttribute> attribute inherits from the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="ba1ea-176">Dizi olmayan öznitelikleri aynı özellik kümesini vardır, örneğin sırada, adı ve üst bilgileri dizisi için ad alanı için tek bir başlık kümesi aynı şekilde ayarlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-176">It has the same set of features as the non-array attributes, for example, it is possible to set the order, name, and namespace for an array of headers in the same way you set it for a single header.</span></span> <span data-ttu-id="ba1ea-177">Kullanırken `Order` bir dizi özelliği, tüm dizi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-177">When you use the `Order` property on an array, it applies to the entire array.</span></span>  
  
 <span data-ttu-id="ba1ea-178">Uygulayabileceğiniz <xref:System.ServiceModel.MessageHeaderArrayAttribute> yalnızca diziler değil koleksiyonlar için.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-178">You can apply the <xref:System.ServiceModel.MessageHeaderArrayAttribute> only to arrays, not collections.</span></span>  
  
## <a name="using-byte-arrays-in-message-contracts"></a><span data-ttu-id="ba1ea-179">İleti sözleşmeleri bayt dizileri kullanma</span><span class="sxs-lookup"><span data-stu-id="ba1ea-179">Using Byte Arrays in Message Contracts</span></span>  
 <span data-ttu-id="ba1ea-180">Bayt dizileri, dizi olmayan özniteliklerle kullanıldığında (<xref:System.ServiceModel.MessageBodyMemberAttribute> ve <xref:System.ServiceModel.MessageHeaderAttribute>), diziler olarak ancak Base64 kodlamalı veri elde edilen XML olarak temsil edilen özel bir basit tür olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-180">Byte arrays, when used with the non-array attributes (<xref:System.ServiceModel.MessageBodyMemberAttribute> and <xref:System.ServiceModel.MessageHeaderAttribute>), are not treated as arrays but as a special primitive type represented as Base64-encoded data in the resulting XML.</span></span>  
  
 <span data-ttu-id="ba1ea-181">Bayt dizileri dizi özniteliğiyle kullanırken <xref:System.ServiceModel.MessageHeaderArrayAttribute>, sonuçları kullanımda seri hale getirici bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-181">When you use byte arrays with the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the results depend on the serializer in use.</span></span> <span data-ttu-id="ba1ea-182">Varsayılan serileştirici ile tek bir giriş için her bir bayt dizisi gösterilir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-182">With the default serializer, the array is represented as an individual entry for each byte.</span></span> <span data-ttu-id="ba1ea-183">Ancak, `XmlSerializer` seçildiğinde (kullanarak <xref:System.ServiceModel.XmlSerializerFormatAttribute> hizmet sözleşmesindeki), bayt dizileri dizisi veya dizi olmayan öznitelikler kullanılıp bağımsız olarak verileri Base64 olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-183">However, when the `XmlSerializer` is selected, (using the <xref:System.ServiceModel.XmlSerializerFormatAttribute> on the service contract), byte arrays are treated as Base64 data regardless of whether the array or non-array attributes are used.</span></span>  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a><span data-ttu-id="ba1ea-184">İmzalama ve şifreleme ileti bölümlerini</span><span class="sxs-lookup"><span data-stu-id="ba1ea-184">Signing and Encrypting Parts of the Message</span></span>  
 <span data-ttu-id="ba1ea-185">Bir ileti anlaşması, üst bilgiler ve/veya iletinin gövdesi dijital olarak İmzalanabilir ve şifrelenebilir olup olmadığını gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-185">A message contract can indicate whether the headers and/or body of the message should be digitally signed and encrypted.</span></span>  
  
 <span data-ttu-id="ba1ea-186">Bu ayarı gerçekleştirilir <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> özelliği <xref:System.ServiceModel.MessageHeaderAttribute> ve <xref:System.ServiceModel.MessageBodyMemberAttribute> öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-186">This is done by setting the <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> property on the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="ba1ea-187">Sabit listesi özelliği <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> yazın ve ayarlanabilir <xref:System.Net.Security.ProtectionLevel.None> (şifreleme veya imza), <xref:System.Net.Security.ProtectionLevel.Sign> (dijital imzası yalnızca), veya <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (şifreleme ve dijital imza).</span><span class="sxs-lookup"><span data-stu-id="ba1ea-187">The property is an enumeration of the <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> type and can be set to <xref:System.Net.Security.ProtectionLevel.None> (no encryption or signature), <xref:System.Net.Security.ProtectionLevel.Sign> (digital signature only), or <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (both encryption and a digital signature).</span></span> <span data-ttu-id="ba1ea-188">Varsayılan, <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> değeridir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-188">The default is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
 <span data-ttu-id="ba1ea-189">Bu güvenlik özellikleri çalışacak şekilde bağlama ve davranışları düzgün bir şekilde yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-189">For these security features to work, you must properly configure the binding and behaviors.</span></span> <span data-ttu-id="ba1ea-190">(Örneğin, bir ileti kimlik bilgilerinizi sağlamadan kapatmaya çalışırken) uygun bir yapılandırma olmadan bu güvenlik özellikleri kullanırsanız, doğrulamayı zamanında bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-190">If you use these security features without the proper configuration (for example, attempting to sign a message without supplying your credentials), an exception is thrown at validation time.</span></span>  
  
 <span data-ttu-id="ba1ea-191">İleti üstbilgileri için koruma düzeyi, tek tek her üst bilgisi için belirlenir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-191">For message headers, the protection level is determined individually for each header.</span></span>  
  
 <span data-ttu-id="ba1ea-192">İleti gövdesi bölümleri için koruma düzeyi "minimum koruma düzeyi." zorlayıcı olabilir</span><span class="sxs-lookup"><span data-stu-id="ba1ea-192">For message body parts, the protection level can be thought of as the "minimum protection level."</span></span> <span data-ttu-id="ba1ea-193">Gövde gövde parçalarının sayısı ne olursa olsun yalnızca bir koruma derecesine sahip.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-193">The body has only one protection level, regardless of the number of body parts.</span></span> <span data-ttu-id="ba1ea-194">Koruma düzeyi gövdesinin en yüksek tarafından belirlenir <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> tüm gövde bölümlerini özelliğin ayarı.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-194">The protection level of the body is determined by the highest <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> property setting of all the body parts.</span></span> <span data-ttu-id="ba1ea-195">Ancak, her bir gövde kısmının koruma düzeyini düzeyi gereken gerçek en küçük koruma için ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-195">However, you should set the protection level of each body part to the actual minimum protection level required.</span></span>  
  
 <span data-ttu-id="ba1ea-196">Aşağıdaki kod örneği sınıfında göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-196">Consider the class in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="ba1ea-197">Bu örnekte, `recordID` üstbilgi korunmuyor, `patientName` olduğu `signed`, ve `SSN` imzalanır ve şifrelenmiş.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-197">In this example, the `recordID` header is not protected, `patientName` is `signed`, and `SSN` is encrypted and signed.</span></span> <span data-ttu-id="ba1ea-198">En az bir gövde bölümü, `medicalHistory`, sahip <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> uygulanan ve bu nedenle tüm ileti gövdesi şifrelenir ve imzalanmış olsa da açıklamalar ve tanılama gövde parçalarının daha düşük koruma düzeyleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-198">At least one body part, `medicalHistory`, has <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> applied, and thus the entire message body is encrypted and signed, even though the comments and diagnosis body parts specify lower protection levels.</span></span>  
  
## <a name="soap-action"></a><span data-ttu-id="ba1ea-199">SOAP eylemi</span><span class="sxs-lookup"><span data-stu-id="ba1ea-199">SOAP Action</span></span>  
 <span data-ttu-id="ba1ea-200">SOAP ve ilgili Web hizmeti standartlarını adlı bir özellik tanımlayın `Action` , gönderilen her bir SOAP ileti mevcut olabilir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-200">SOAP and related Web services standards define a property called `Action` that can be present for every SOAP message sent.</span></span> <span data-ttu-id="ba1ea-201">İşlemin <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> ve <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> denetim özelliklerini bu özelliğin değeri.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-201">The operation's <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> properties control the value of this property.</span></span>  
  
## <a name="soap-header-attributes"></a><span data-ttu-id="ba1ea-202">SOAP üstbilgisi öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="ba1ea-202">SOAP Header Attributes</span></span>  
 <span data-ttu-id="ba1ea-203">SOAP standart bir üstbilgi varsa aşağıdaki öznitelikleri tanımlar:</span><span class="sxs-lookup"><span data-stu-id="ba1ea-203">The SOAP standard defines the following attributes that may exist on a header:</span></span>  
  
- <span data-ttu-id="ba1ea-204">`Actor/Role` (`Actor` SOAP 1.1 `Role` SOAP 1.2)</span><span class="sxs-lookup"><span data-stu-id="ba1ea-204">`Actor/Role` (`Actor` in SOAP 1.1, `Role` in SOAP 1.2)</span></span>  
  
- `MustUnderstand`  
  
- `Relay`  
  
 <span data-ttu-id="ba1ea-205">`Actor` Veya `Role` öznitelik sağlanan üstbilgisi amaçlanmıştır düğümünün Tekdüzen Kaynak Tanımlayıcısı (URI) belirtir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-205">The `Actor` or `Role` attribute specifies the Uniform Resource Identifier (URI) of the node for which a given header is intended.</span></span> <span data-ttu-id="ba1ea-206">`MustUnderstand` Özniteliği, üst bilgi işlem düğümü, anlamak olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-206">The `MustUnderstand` attribute specifies whether the node processing the header must understand it.</span></span> <span data-ttu-id="ba1ea-207">`Relay` Özniteliği, aşağı akış düğümlerine geçirilmesine üstbilgi olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-207">The `Relay` attribute specifies whether the header is to be relayed to downstream nodes.</span></span> <span data-ttu-id="ba1ea-208">WCF gerçekleştirmez gelen iletiler bu özniteliklerin herhangi bir işleme dışında `MustUnderstand` özniteliği, bu konunun ilerleyen bölümlerindeki "İleti sözleşmesi sürümü oluşturma" bölümünde belirtildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-208">WCF does not perform any processing of these attributes on incoming messages, except for the `MustUnderstand` attribute, as specified in the "Message Contract Versioning" section later in this topic.</span></span> <span data-ttu-id="ba1ea-209">Ancak, bu öznitelik aşağıdaki açıklama olduğu gibi gerekli olarak okuyup sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-209">However, it allows you to read and write these attributes as necessary, as in the following description.</span></span>  
  
 <span data-ttu-id="ba1ea-210">Bir ileti gönderirken, varsayılan olarak bu öznitelikler yayılan değil.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-210">When sending a message, these attributes are not emitted by default.</span></span> <span data-ttu-id="ba1ea-211">Bunu iki şekilde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-211">You can change this in two ways.</span></span> <span data-ttu-id="ba1ea-212">İlk olarak, statik olarak öznitelikleri için istenen tüm değerleri değiştirerek ayarlayabilir <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, ve <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> aşağıdaki kod örneğinde gösterildiği gibi özellikleri.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-212">First, you may statically set the attributes to any desired values by changing the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, and <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> properties, as shown in the following code example.</span></span> <span data-ttu-id="ba1ea-213">(Unutmayın hiçbir `Role` özelliği; ayarı <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> özelliğini yayan `Role` SOAP 1.2 kullanıyorsanız özniteliği).</span><span class="sxs-lookup"><span data-stu-id="ba1ea-213">(Note that there is no `Role` property; setting the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> property emits the `Role` attribute if you are using SOAP 1.2).</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="ba1ea-214">Bu öznitelikler denetlemek için ikinci yol dinamik olarak kodudur.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-214">The second way to control these attributes is dynamically, through code.</span></span> <span data-ttu-id="ba1ea-215">Bu istenen üst bilgi türünde sarmalama tarafından elde <xref:System.ServiceModel.MessageHeader%601> türü (Bu tür genel olmayan sürümüne sahip karıştırmamaya dikkat edin) ve türü ile birlikte kullanarak <xref:System.ServiceModel.MessageHeaderAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-215">You can achieve this by wrapping the desired header type in the <xref:System.ServiceModel.MessageHeader%601> type (be sure not to confuse this type with the non-generic version) and by using the type together with the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="ba1ea-216">Ardından özellikleri kullanabileceğinizi <xref:System.ServiceModel.MessageHeader%601> aşağıdaki kod örneğinde gösterildiği gibi SOAP öznitelikleri ayarlanamadı.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-216">Then, you can use properties on the <xref:System.ServiceModel.MessageHeader%601> to set the SOAP attributes, as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="ba1ea-217">Hem dinamik ve statik denetimi düzenekleri kullanırsanız, statik ayarlarını varsayılan olarak kullanılır, ancak daha sonra dinamik mekanizmasını kullanarak aşağıdaki kodda gösterildiği gibi geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-217">If you use both the dynamic and the static control mechanisms, the static settings are used as a default but can later be overridden by using the dynamic mechanism, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 <span data-ttu-id="ba1ea-218">Dinamik öznitelik denetimiyle yinelenen başlıkları oluşturma, aşağıdaki kodda gösterildiği gibi izin.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-218">Creating repeated headers with dynamic attribute control is allowed, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 <span data-ttu-id="ba1ea-219">Alıcı tarafında bu SOAP öznitelikleri okuma yalnızca varsa yapılabilir <xref:System.ServiceModel.MessageHeader%601> sınıfı türü üst bilgisi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-219">On the receiving side, reading these SOAP attributes can only be done if the <xref:System.ServiceModel.MessageHeader%601> class is used for the header in the type.</span></span> <span data-ttu-id="ba1ea-220">İnceleme `Actor`, `Relay`, veya `MustUnderstand` başlık özelliklerini <xref:System.ServiceModel.MessageHeader%601> alınan iletide öznitelik ayarlarını bulmak için yazın.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-220">Examine the `Actor`, `Relay`, or `MustUnderstand` properties of a header of the <xref:System.ServiceModel.MessageHeader%601> type to discover the attribute settings on the received message.</span></span>  
  
 <span data-ttu-id="ba1ea-221">Bir ileti alındı ve geri gönderilen, SOAP özniteliği yalnızca üst bilgilerinin gidiş dönüş gidin <xref:System.ServiceModel.MessageHeader%601> türü.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-221">When a message is received and then sent back, the SOAP attribute settings only go round-trip for headers of the <xref:System.ServiceModel.MessageHeader%601> type.</span></span>  
  
## <a name="order-of-soap-body-parts"></a><span data-ttu-id="ba1ea-222">SOAP gövdesi bölümleri sırası</span><span class="sxs-lookup"><span data-stu-id="ba1ea-222">Order of SOAP Body Parts</span></span>  
 <span data-ttu-id="ba1ea-223">Bazı durumlarda, gövde bölümlerinin sırasını denetlemek için gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-223">In some circumstances, you may need to control the order of the body parts.</span></span> <span data-ttu-id="ba1ea-224">Gövde öğelerin sırasını varsayılan olarak alfabetik kullanılır, ancak tarafından denetlenen <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-224">The order of the body elements is alphabetical by default, but can be controlled by the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="ba1ea-225">Bu özellik ile aynı semantiklere sahip <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> devralma senaryolarda (ileti sözleşmeleri, temel tür gövdesi üyeler türetilmiş tür gövdesi üyeleri önce sıralanmamış) davranışı dışında bir özellik.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-225">This property has the same semantics as the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> property, except for the behavior in inheritance scenarios (in message contracts, base type body members are not sorted before the derived type body members).</span></span> <span data-ttu-id="ba1ea-226">Daha fazla bilgi için [veri üye sırası](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span><span class="sxs-lookup"><span data-stu-id="ba1ea-226">For more information, see [Data Member Order](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span></span>  
  
 <span data-ttu-id="ba1ea-227">Aşağıdaki örnekte, `amount` alfabetik olarak ilk olduğundan normal olarak ilk gelecektir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-227">In the following example, `amount` would normally come first because it is first alphabetically.</span></span> <span data-ttu-id="ba1ea-228">Ancak, <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> özelliği onu üçüncü konumuna koyar.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-228">However, the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> property puts it into the third position.</span></span>  
  
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
  
## <a name="message-contract-versioning"></a><span data-ttu-id="ba1ea-229">İleti sözleşmesi sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="ba1ea-229">Message Contract Versioning</span></span>  
 <span data-ttu-id="ba1ea-230">Zaman zaman ileti anlaşmaları değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-230">Occasionally, you may need to change message contracts.</span></span> <span data-ttu-id="ba1ea-231">Örneğin, uygulamanızın yeni bir sürümünü iletiye ek bir üst bilgisi ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-231">For example, a new version of your application may add an extra header to a message.</span></span> <span data-ttu-id="ba1ea-232">Ardından, yeni sürümünden eski gönderirken, sistem bir ek üst bilgisi, yanı sıra üst bilgisi eksik diğer yönde geçerken ilgilenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-232">Then, when sending from the new version to the old, the system must deal with an extra header, as well as a missing header when going in the other direction.</span></span>  
  
 <span data-ttu-id="ba1ea-233">Sürüm üst bilgileri için aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="ba1ea-233">The following rules apply for versioning headers:</span></span>  
  
- <span data-ttu-id="ba1ea-234">WCF eksik üst nesne değildir — varsayılan değerlerine karşılık gelen üyeleri bırakılır.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-234">WCF does not object to the missing headers—the corresponding members are left at their default values.</span></span>  
  
- <span data-ttu-id="ba1ea-235">WCF da beklenmeyen fazladan üst bilgiler yok sayar.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-235">WCF also ignores unexpected extra headers.</span></span> <span data-ttu-id="ba1ea-236">Ek üstbilgi varsa bu kuralın tek özel durum olan bir `MustUnderstand` özniteliğini `true` gelen SOAP iletisi — bu durumda, anlaşılması gereken bir üstbilgi işlenemediği için bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-236">The one exception to this rule is if the extra header has a `MustUnderstand` attribute set to `true` in the incoming SOAP message—in this case, an exception is thrown because a header that must be understood cannot be processed.</span></span>  
  
 <span data-ttu-id="ba1ea-237">İleti gövdeleri benzer sürüm kurallara sahiptir — hem eksik hem de ek ileti gövdesi bölümü yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-237">Message bodies have similar versioning rules—both missing and additional message body parts are ignored.</span></span>  
  
## <a name="inheritance-considerations"></a><span data-ttu-id="ba1ea-238">Devralma konuları</span><span class="sxs-lookup"><span data-stu-id="ba1ea-238">Inheritance Considerations</span></span>  
 <span data-ttu-id="ba1ea-239">Temel türü bir ileti anlaşması de sahip olduğu sürece bir ileti anlaşması türü başka türden devralabilir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-239">A message contract type can inherit from another type, as long as the base type also has a message contract.</span></span>  
  
 <span data-ttu-id="ba1ea-240">Oluşturma veya diğer ileti anlaşması türlerinden devralan bir ileti anlaşması türü kullanarak ileti erişme, aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="ba1ea-240">When creating or accessing a message using a message contract type that inherits from other message contract types, the following rules apply:</span></span>  
  
- <span data-ttu-id="ba1ea-241">İleti üst bilgilerinde devralma hiyerarşisindeki tüm birlikte eksiksiz bir ileti üstbilgileri listesi oluşturmak için toplanır.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-241">All of the message headers in the inheritance hierarchy are collected together to form the full set of headers for the message.</span></span>  
  
- <span data-ttu-id="ba1ea-242">İleti gövde bölümlerinin devralma hiyerarşisindeki tüm birlikte tam ileti gövdesi oluşturmak için toplanır.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-242">All of the message body parts in the inheritance hierarchy are collected together to form the full message body.</span></span> <span data-ttu-id="ba1ea-243">Gövde parçalarının normal sıralama kurallara göre sıralanır (tarafından <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> özelliği ve ardından alfabetik), bunun yerine Devralma Hiyerarşisi Hiçbir ilgisi olan.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-243">The body parts are ordered according to the usual ordering rules (by <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property and then alphabetical), with no relevance to their place in the inheritance hierarchy.</span></span> <span data-ttu-id="ba1ea-244">İleti gövdesi bölümleri birden çok devralma ağacını düzeylerinde nerede meydana ileti anlaşma devralma kullanarak kesinlikle önerilmez.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-244">Using message contract inheritance where message body parts occur at multiple levels of the inheritance tree is strongly discouraged.</span></span> <span data-ttu-id="ba1ea-245">Bir temel sınıf ve türetilen sınıf bir üst bilgi veya aynı ada sahip bir gövde bölümü tanımlarsanız, en temel sınıftan üye bu üst bilgi veya gövde bölümü değerini depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-245">If a base class and a derived class define a header or a body part with the same name, the member from the base-most class is used to store the value of that header or body part.</span></span>  
  
 <span data-ttu-id="ba1ea-246">Aşağıdaki kod örneği sınıflarda göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-246">Consider the classes in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="ba1ea-247">`PatientRecord` Sınıfı olarak adlandırılan bir üstbilgiyle bir ileti açıklar `ID`.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-247">The `PatientRecord` class describes a message with one header called `ID`.</span></span> <span data-ttu-id="ba1ea-248">Üst bilgi karşılık gelen `personID` ve `patientID` üye, temel en üyesinin seçildiği için.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-248">The header corresponds to the `personID` and not the `patientID` member, because the base-most member is chosen.</span></span> <span data-ttu-id="ba1ea-249">Bu nedenle, `patientID` gereksiz bu durumda olan alan.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-249">Thus, the `patientID` field is useless in this case.</span></span> <span data-ttu-id="ba1ea-250">İleti gövdesini içeren `diagnosis` öğesi tarafından izlenen `patientName` öğesi, çünkü, alfabetik olarak sıralayın.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-250">The body of the message contains the `diagnosis` element followed by the `patientName` element, because that is the alphabetical order.</span></span> <span data-ttu-id="ba1ea-251">Örnek kesinlikle önerilmez bir desen gösterdiğine dikkat edin: hem temel hem de türetilmiş ileti sözleşmeleri, ileti gövdesi bölümden oluşur.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-251">Notice that the example shows a pattern that is strongly discouraged: both the base and the derived message contracts have message body parts.</span></span>  
  
## <a name="wsdl-considerations"></a><span data-ttu-id="ba1ea-252">WSDL konuları</span><span class="sxs-lookup"><span data-stu-id="ba1ea-252">WSDL Considerations</span></span>  
 <span data-ttu-id="ba1ea-253">Web Hizmetleri Açıklama Dili (WSDL) sözleşmesi ileti sözleşmeleri kullanan bir hizmetten oluştururken, tüm ileti anlaşması özellikleri elde edilen WSDL içinde yansıtılır unutmamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-253">When generating a Web Services Description Language (WSDL) contract from a service that uses message contracts, it is important to remember that not all message contract features are reflected in the resulting WSDL.</span></span> <span data-ttu-id="ba1ea-254">Aşağıdaki noktaları göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="ba1ea-254">Consider the following points:</span></span>  
  
- <span data-ttu-id="ba1ea-255">WSDL, üst bilgiler bir dizi kavramı hızlı olamaz.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-255">WSDL cannot express the concept of an array of headers.</span></span> <span data-ttu-id="ba1ea-256">İleti üst bilgileri kullanarak bir dizi oluştururken <xref:System.ServiceModel.MessageHeaderArrayAttribute>, dizi yerine yalnızca bir üst bilgi elde edilen WSDL yansıtır.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-256">When creating messages with an array of headers using the <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the resulting WSDL reflects only one header instead of the array.</span></span>  
  
- <span data-ttu-id="ba1ea-257">Sonuçta elde edilen WSDL belgesinde bazı koruma düzeyi bilgileri yansıtmaz.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-257">The resulting WSDL document may not reflect some protection-level information.</span></span>  
  
- <span data-ttu-id="ba1ea-258">WSDL içinde oluşturulan ileti türü, ileti anlaşması türü sınıf adı ile aynı ada sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-258">The message type generated in the WSDL has the same name as the class name of the message contract type.</span></span>  
  
- <span data-ttu-id="ba1ea-259">Birden çok ileti türü, aynı iletiyi kullanarak sözleşme, birden çok işlemlerinde, WSDL belgesinde üretilir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-259">When using the same message contract in multiple operations, multiple message types are generated in the WSDL document.</span></span> <span data-ttu-id="ba1ea-260">Sayı "2", "3" ekleyerek ve sonraki kullanımlar için vb. adları benzersiz yapılır.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-260">The names are made unique by adding the numbers "2", "3", and so on, for subsequent uses.</span></span> <span data-ttu-id="ba1ea-261">WSDL geri alırken, birden çok ileti anlaşması türleri oluşturulur ve bunların adları hariç olmak üzere aynıdır.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-261">When importing back the WSDL, multiple message contract types are created and are identical except for their names.</span></span>  
  
## <a name="soap-encoding-considerations"></a><span data-ttu-id="ba1ea-262">SOAP değerlendirmeleri kodlama</span><span class="sxs-lookup"><span data-stu-id="ba1ea-262">SOAP Encoding Considerations</span></span>  
 <span data-ttu-id="ba1ea-263">WCF eski SOAP XML stil kodlama kullanmanıza olanak tanır ancak kullanımı önerilmez.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-263">WCF allows you to use the legacy SOAP encoding style of XML, however, its use is not recommended.</span></span> <span data-ttu-id="ba1ea-264">Bu stil kullanırken (ayarlayarak `Use` özelliğini `Encoded` üzerinde <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> hizmet sözleşmesi için uygulanan), ek aşağıdaki maddeler geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="ba1ea-264">When using this style (by setting the `Use` property to `Encoded` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> applied to the service contract), the following additional considerations apply:</span></span>  
  
- <span data-ttu-id="ba1ea-265">İleti üstbilgilerini desteklenmez; Bu öznitelik anlamına <xref:System.ServiceModel.MessageHeaderAttribute> ve dizisi özniteliği <xref:System.ServiceModel.MessageHeaderArrayAttribute> SOAP kodlamasına ile uyumlu değildir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-265">The message headers are not supported; this means that the attribute <xref:System.ServiceModel.MessageHeaderAttribute> and the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute> are incompatible with SOAP encoding.</span></span>  
  
- <span data-ttu-id="ba1ea-266">İleti sözleşmesi, diğer bir deyişle, sarmalanmamış ise özellik <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> ayarlanır `false`, ileti anlaşması yalnızca bir gövde bölümü olabilir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-266">If the message contract is not wrapped, that is, if the property <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> is set to `false`, the message contract can have only one body part.</span></span>  
  
- <span data-ttu-id="ba1ea-267">İstek ileti anlaşması için sarmalayıcı öğe adı, işlem adı eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-267">The name of the wrapper element for the request message contract must match the operation name.</span></span> <span data-ttu-id="ba1ea-268">Kullanım `WrapperName` ileti anlaşması için bu özelliği.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-268">Use the `WrapperName` property of the message contract for this.</span></span>  
  
- <span data-ttu-id="ba1ea-269">Yanıt ileti anlaşması için sarmalayıcı öğe adı, 'Response' tarafından ve sonra işlemin adıyla aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-269">The name of the wrapper element for the response message contract must be the same as the name of the operation suffixed by 'Response'.</span></span> <span data-ttu-id="ba1ea-270">Kullanım <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> ileti anlaşması için bu özelliği.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-270">Use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> property of the message contract for this.</span></span>  
  
- <span data-ttu-id="ba1ea-271">SOAP kodlamasına nesne başvuruları korur.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-271">SOAP encoding preserves object references.</span></span> <span data-ttu-id="ba1ea-272">Örneğin, aşağıdaki kodu düşünün.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-272">For example, consider the following code.</span></span>  
  
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
  
 <span data-ttu-id="ba1ea-273">İletinin SOAP kodlaması kullanarak seri hale getirme sonra `changedFrom` ve `changedTo` kendi kopyalarını içermeyen `p`, ancak bunun yerine iç kopyayı işaret `changedBy` öğesi.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-273">After serializing the message using SOAP encoding, `changedFrom` and `changedTo` do not contain their own copies of `p`, but instead point to the copy inside the `changedBy` element.</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="ba1ea-274">Başarım Değerlendirmeleri</span><span class="sxs-lookup"><span data-stu-id="ba1ea-274">Performance Considerations</span></span>  
 <span data-ttu-id="ba1ea-275">Her ileti üst bilgisi ve ileti Gövde bölümünün diğerlerinden bağımsız olarak seri hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-275">Every message header and message body part is serialized independently of the others.</span></span> <span data-ttu-id="ba1ea-276">Bu nedenle, aynı ad alanları yeniden her başlık ve gövde bölümü için bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-276">Therefore, the same namespaces can be declared again for each header and body part.</span></span> <span data-ttu-id="ba1ea-277">Özellikle Tel üzerinde ileti boyutu bakımından performansı artırmak için tek bir üst bilgi veya gövde bölümüne birden çok üstbilgi ve gövde parçalarının birleştirin.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-277">To improve performance, especially in terms of the size of the message on the wire, consolidate multiple headers and body parts into a single header or body part.</span></span> <span data-ttu-id="ba1ea-278">Örneğin, aşağıdaki kodu yerine:</span><span class="sxs-lookup"><span data-stu-id="ba1ea-278">For example, instead of the following code:</span></span>  
  
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
  
 <span data-ttu-id="ba1ea-279">Bu kodu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-279">Use this code.</span></span>  
  
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
  
### <a name="event-based-asynchronous-and-message-contracts"></a><span data-ttu-id="ba1ea-280">Olay tabanlı zaman uyumsuz ve ileti sözleşmeleri</span><span class="sxs-lookup"><span data-stu-id="ba1ea-280">Event-based Asynchronous and Message Contracts</span></span>  
 <span data-ttu-id="ba1ea-281">Olay tabanlı zaman uyumsuz model için tasarım yönergeleri birden fazla değer döndürmüyorsa, bir değer olarak döndürülen durum `Result` özelliği ve diğerleri döndürülür özellikleri olarak üzerinde <xref:System.EventArgs> nesne.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-281">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="ba1ea-282">Bunun bir sonucu olduğundan, bu, bir istemci, olay tabanlı zaman uyumsuz komut seçeneklerini kullanarak meta verilerini içeri aktarır ve işlemin birden fazla değer, varsayılan döndürürse <xref:System.EventArgs> nesnesini bir değer olarak döndürür `Result` özelliği ve kalan özelliklerini <xref:System.EventArgs> nesne.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-282">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="ba1ea-283">İleti nesnesi olarak almak istiyorsanız `Result` özelliği ve o nesnenin özellikleri olarak döndürülen değerlerin `/messageContract` seçeneği komutu.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-283">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="ba1ea-284">Bu yanıt iletisi olarak döndüren bir imza oluşturur `Result` özelliği <xref:System.EventArgs> nesne.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-284">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="ba1ea-285">Tüm iç dönüş değerleri ardından yanıt iletisi nesnenin özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-285">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba1ea-286">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba1ea-286">See also</span></span>

- [<span data-ttu-id="ba1ea-287">Veri Anlaşmalarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="ba1ea-287">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="ba1ea-288">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="ba1ea-288">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)
