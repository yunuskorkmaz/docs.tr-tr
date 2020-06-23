---
title: İleti Sözleşmeleri Kullanılıyor
description: WFC 'de bir SOAP iletisinin yapısını belirten bir ileti sözleşmesi oluşturmak için ileti sözleşmesi özniteliklerini nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message contracts [WCF]
ms.assetid: 1e19c64a-ae84-4c2f-9155-91c54a77c249
ms.openlocfilehash: 0a75298b50df74ddf15904af43a0eb62c5ba8496
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244718"
---
# <a name="using-message-contracts"></a><span data-ttu-id="73f6d-103">İleti Sözleşmeleri Kullanılıyor</span><span class="sxs-lookup"><span data-stu-id="73f6d-103">Using Message Contracts</span></span>
<span data-ttu-id="73f6d-104">Genellikle Windows Communication Foundation (WCF) uygulamaları oluştururken, geliştiriciler veri yapılarına ve serileştirme sorunlarına yakın ilgi çekici bir şekilde ödeme yapar ve verilerin gerçekleştirildiği iletilerin yapısıyla ilgilenmenize gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="73f6d-104">Typically when building Windows Communication Foundation (WCF) applications, developers pay close attention to the data structures and serialization issues and do not need to concern themselves with the structure of the messages in which the data is carried.</span></span> <span data-ttu-id="73f6d-105">Bu uygulamalar için, parametreler veya dönüş değerleri için veri sözleşmeleri oluşturmak basittir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-105">For these applications, creating data contracts for the parameters or return values is straightforward.</span></span> <span data-ttu-id="73f6d-106">(Daha fazla bilgi için bkz. [hizmet sözleşmeleri içinde veri aktarımı belirtme](specifying-data-transfer-in-service-contracts.md).)</span><span class="sxs-lookup"><span data-stu-id="73f6d-106">(For more information, see [Specifying Data Transfer in Service Contracts](specifying-data-transfer-in-service-contracts.md).)</span></span>  
  
 <span data-ttu-id="73f6d-107">Ancak, bazen bir SOAP iletisinin yapısına ilişkin denetim, içeriğinin üzerinde denetim kadar önemli olur.</span><span class="sxs-lookup"><span data-stu-id="73f6d-107">However, sometimes complete control over the structure of a SOAP message is just as important as control over its contents.</span></span> <span data-ttu-id="73f6d-108">Bu özellikle, birlikte çalışabilirlik önemli olduğunda veya ileti veya ileti parçası düzeyinde güvenlik sorunlarını özellikle denetlemek için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-108">This is especially true when interoperability is important or to specifically control security issues at the level of the message or message part.</span></span> <span data-ttu-id="73f6d-109">Bu durumlarda, gereken kesin SOAP iletisinin yapısını belirtmenizi sağlayan bir *ileti sözleşmesi* oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73f6d-109">In these cases, you can create a *message contract* that enables you to specify the structure of the precise SOAP message required.</span></span>  
  
 <span data-ttu-id="73f6d-110">Bu konuda, işlem için belirli bir ileti sözleşmesi oluşturmak üzere çeşitli ileti sözleşmesi özniteliklerinin nasıl kullanılacağı ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73f6d-110">This topic discusses how to use the various message contract attributes to create a specific message contract for your operation.</span></span>  
  
## <a name="using-message-contracts-in-operations"></a><span data-ttu-id="73f6d-111">Işlemlerde Ileti sözleşmeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="73f6d-111">Using Message Contracts in Operations</span></span>  
 <span data-ttu-id="73f6d-112">WCF, *uzak yordam çağrısı (RPC) stili* veya *mesajlaşma stili*üzerinde modellenen işlemleri destekler.</span><span class="sxs-lookup"><span data-stu-id="73f6d-112">WCF supports operations modeled on either the *remote procedure call (RPC) style* or the *messaging style*.</span></span> <span data-ttu-id="73f6d-113">Bir RPC stili işleminde, herhangi bir serileştirilebilir türü kullanabilir ve birden çok parametre ve parametre gibi yerel çağrılar için kullanılabilen özelliklere erişebilirsiniz `ref` `out` .</span><span class="sxs-lookup"><span data-stu-id="73f6d-113">In an RPC-style operation, you can use any serializable type, and you have access to the features that are available to local calls, such as multiple parameters and `ref` and `out` parameters.</span></span> <span data-ttu-id="73f6d-114">Bu stilde, seçilen serileştirme formu, temel iletilerdeki verilerin yapısını denetler ve WCF çalışma zamanı, işlemi destekleyecek iletileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="73f6d-114">In this style, the form of serialization chosen controls the structure of the data in the underlying messages, and the WCF runtime creates the messages to support the operation.</span></span> <span data-ttu-id="73f6d-115">Bu, SOAP ve SOAP iletileri hakkında bilgi sahibi olmayan geliştiricilerin, hizmet uygulamalarını hızla ve kolayca oluşturup kullanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="73f6d-115">This enables developers who are not familiar with SOAP and SOAP messages to quickly and easily create and use service applications.</span></span>  
  
 <span data-ttu-id="73f6d-116">Aşağıdaki kod örneğinde, RPC stilinde modellenen bir hizmet işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-116">The following code example shows a service operation modeled on the RPC style.</span></span>  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 <span data-ttu-id="73f6d-117">Normalde, bir veri sözleşmesi, iletilerin şemasını tanımlamak için yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-117">Normally, a data contract is sufficient to define the schema for the messages.</span></span> <span data-ttu-id="73f6d-118">Örneğin, önceki örnekte, çoğu uygulama için yeterlidir `BankingTransaction` ve `BankingTransactionResponse` temel alınan SOAP iletilerinin içeriğini tanımlamak için veri sözleşmeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="73f6d-118">For instance, in the preceding example, it is sufficient for most applications if `BankingTransaction` and `BankingTransactionResponse` have data contracts to define the contents of the underlying SOAP messages.</span></span> <span data-ttu-id="73f6d-119">Veri sözleşmeleri hakkında daha fazla bilgi için bkz. [Veri Sözleşmelerini Kullanma](using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="73f6d-119">For more information about data contracts, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="73f6d-120">Ancak, bazen SOAP iletisinin yapısının hat üzerinden nasıl iletildiğini tam olarak denetlemek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-120">However, occasionally it is necessary to precisely control how the structure of the SOAP message transmitted over the wire.</span></span> <span data-ttu-id="73f6d-121">Bunun için en yaygın senaryo özel SOAP üstbilgileri ekliyor.</span><span class="sxs-lookup"><span data-stu-id="73f6d-121">The most common scenario for this is inserting custom SOAP headers.</span></span> <span data-ttu-id="73f6d-122">Diğer bir yaygın senaryo, bu öğelerin dijital olarak imzalanıp imzalanmadığını ve şifrelenmeyeceğine karar vermek için ileti üst bilgileri ve gövdesi için güvenlik özellikleri tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="73f6d-122">Another common scenario is to define security properties for the message's headers and body, that is, to decide whether these elements are digitally signed and encrypted.</span></span> <span data-ttu-id="73f6d-123">Son olarak, bazı üçüncü taraf SOAP yığınları, iletilerin belirli bir biçimde olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-123">Finally, some third-party SOAP stacks require messages be in a specific format.</span></span> <span data-ttu-id="73f6d-124">Mesajlaşma stili işlemler bu denetimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="73f6d-124">Messaging-style operations provide this control.</span></span>  
  
 <span data-ttu-id="73f6d-125">Mesajlaşma stili bir işlem, en fazla bir parametreye ve her iki türün de ileti türü olduğu bir dönüş değerine sahiptir; diğer bir deyişle, doğrudan belirtilen bir SOAP ileti yapısına serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-125">A messaging-style operation has at most one parameter and one return value where both types are message types; that is, they serialize directly into a specified SOAP message structure.</span></span> <span data-ttu-id="73f6d-126">Bu, ya da türü ile işaretlenmiş herhangi bir tür olabilir <xref:System.ServiceModel.MessageContractAttribute> <xref:System.ServiceModel.Channels.Message> .</span><span class="sxs-lookup"><span data-stu-id="73f6d-126">This may be any type marked with the <xref:System.ServiceModel.MessageContractAttribute> or the <xref:System.ServiceModel.Channels.Message> type.</span></span> <span data-ttu-id="73f6d-127">Aşağıdaki kod örneği, önceki RCP stili gibi bir işlemi gösterir, ancak mesajlaşma stilini kullanır.</span><span class="sxs-lookup"><span data-stu-id="73f6d-127">The following code example shows an operation similar to the preceding RCP-style, but which uses the messaging style.</span></span>  
  
 <span data-ttu-id="73f6d-128">Örneğin, `BankingTransaction` ve `BankingTransactionResponse` her iki tür de ileti sözleşmelerinde, aşağıdaki işlemlerdeki kod geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="73f6d-128">For example, if `BankingTransaction` and `BankingTransactionResponse` are both types that are message contracts, then the code in the following operations is valid.</span></span>  
  
```csharp  
[OperationContract]  
BankingTransactionResponse Process(BankingTransaction bt);  
[OperationContract]  
void Store(BankingTransaction bt);  
[OperationContract]  
BankingTransactionResponse GetResponse();  
```  
  
 <span data-ttu-id="73f6d-129">Ancak, aşağıdaki kod geçersiz.</span><span class="sxs-lookup"><span data-stu-id="73f6d-129">However, the following code is invalid.</span></span>  
  
```csharp  
[OperationContract]  
bool Validate(BankingTransaction bt);  
// Invalid, the return type is not a message contract.  
[OperationContract]  
void Reconcile(BankingTransaction bt1, BankingTransaction bt2);  
// Invalid, there is more than one parameter.  
```  
  
 <span data-ttu-id="73f6d-130">İleti sözleşmesi türünü içeren ve geçerli desenlerden birini takip eden tüm işlemler için bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="73f6d-130">An exception is thrown for any operation that involves a message contract type and that does not follow one of the valid patterns.</span></span> <span data-ttu-id="73f6d-131">Kuşkusuz, ileti anlaşması türleri içermeyen işlemler bu kısıtlamalara tabi değildir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-131">Of course, operations that do not involve message contract types are not subject to these restrictions.</span></span>  
  
 <span data-ttu-id="73f6d-132">Bir tür hem bir ileti sözleşmesine hem de bir veri sözleşmesine sahipse, tür bir işlemde kullanıldığında yalnızca ileti anlaşması kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-132">If a type has both a message contract and a data contract, only its message contract is considered when the type is used in an operation.</span></span>  
  
## <a name="defining-message-contracts"></a><span data-ttu-id="73f6d-133">Ileti sözleşmelerini tanımlama</span><span class="sxs-lookup"><span data-stu-id="73f6d-133">Defining Message Contracts</span></span>  
 <span data-ttu-id="73f6d-134">Bir tür için bir ileti sözleşmesi tanımlamak (yani, türü ve bir SOAP Zarfı arasındaki eşlemeyi tanımlamak için), <xref:System.ServiceModel.MessageContractAttribute> türünü türüne uygulayın.</span><span class="sxs-lookup"><span data-stu-id="73f6d-134">To define a message contract for a type (that is, to define the mapping between the type and a SOAP envelope), apply the <xref:System.ServiceModel.MessageContractAttribute> to the type.</span></span> <span data-ttu-id="73f6d-135">Ardından öğesini <xref:System.ServiceModel.MessageHeaderAttribute> SOAP üst bilgilerinde yapmak istediğiniz türdeki üyelere uygulayın ve ' ı <xref:System.ServiceModel.MessageBodyMemberAttribute> iletinin SOAP gövdesinin bölümlerinde yapmak istediğiniz üyelere uygulayın.</span><span class="sxs-lookup"><span data-stu-id="73f6d-135">Then apply the <xref:System.ServiceModel.MessageHeaderAttribute> to those members of the type you want to make into SOAP headers, and apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to those members you want to make into parts of the SOAP body of the message.</span></span>  
  
 <span data-ttu-id="73f6d-136">Aşağıdaki kod, bir ileti sözleşmesinin kullanılmasına bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="73f6d-136">The following code provides an example of using a message contract.</span></span>  
  
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
  
 <span data-ttu-id="73f6d-137">Bu tür bir işlem parametresi olarak kullanıldığında, aşağıdaki SOAP Zarfı oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="73f6d-137">When using this type as an operation parameter, the following SOAP envelope is generated:</span></span>  
  
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
  
 <span data-ttu-id="73f6d-138">Bunun ve `operation` `transactionDate` SOAP üst bilgisi olarak GÖRÜNDÜĞÜNÜ ve SOAP gövdesinin,, ve içeren bir sarmalayıcı öğesinden oluştuğunu görürsünüz `BankingTransaction` `sourceAccount` `targetAccount` `amount` .</span><span class="sxs-lookup"><span data-stu-id="73f6d-138">Notice that `operation` and `transactionDate` appear as SOAP headers and the SOAP body consists of a wrapper element `BankingTransaction` containing `sourceAccount`,`targetAccount`, and `amount`.</span></span>  
  
 <span data-ttu-id="73f6d-139"><xref:System.ServiceModel.MessageHeaderAttribute> <xref:System.ServiceModel.MessageBodyMemberAttribute> Genel, özel, korumalı veya dahili olsun etmeksizin bağımsız olarak, ve tüm alanları, özellikleri ve olayları uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73f6d-139">You can apply the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> to all fields, properties, and events, regardless of whether they are public, private, protected, or internal.</span></span>  
  
 <span data-ttu-id="73f6d-140">, <xref:System.ServiceModel.MessageContractAttribute> SOAP iletisinin gövdesinde sarmalayıcı öğenin adını denetleyen WrapperName ve WrapperNamespace özniteliklerini belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="73f6d-140">The <xref:System.ServiceModel.MessageContractAttribute> allows you to specify the WrapperName and WrapperNamespace attributes which control the name of the wrapper element in the body of the SOAP message.</span></span> <span data-ttu-id="73f6d-141">Varsayılan olarak, ileti anlaşması türünün adı sarmalayıcı için kullanılır ve ileti sözleşmesinin tanımlandığı ad alanı `http://tempuri.org/` varsayılan ad alanı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="73f6d-141">By default the name of the message contract type is used for the wrapper and the namespace in which the message contract is defined `http://tempuri.org/` is used as the default namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73f6d-142"><xref:System.Runtime.Serialization.KnownTypeAttribute>ileti sözleşmelerinde öznitelikler yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="73f6d-142"><xref:System.Runtime.Serialization.KnownTypeAttribute> attributes are ignored in message contracts.</span></span> <span data-ttu-id="73f6d-143">Bir <xref:System.Runtime.Serialization.KnownTypeAttribute> gerekliyse, söz konusu iletiyi söz konusu ileti sözleşmesinin kullanıldığı işleme yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="73f6d-143">If a <xref:System.Runtime.Serialization.KnownTypeAttribute> is required, place it on the operation that is using the message contract in question.</span></span>  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a><span data-ttu-id="73f6d-144">Üst bilgi ve gövde bölüm adlarını ve ad alanlarını denetleme</span><span class="sxs-lookup"><span data-stu-id="73f6d-144">Controlling Header and Body Part Names and Namespaces</span></span>  
 <span data-ttu-id="73f6d-145">Bir ileti sözleşmesinin SOAP gösteriminde, her başlık ve gövde bölümü, adı ve ad alanı olan bir XML öğesiyle eşlenir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-145">In the SOAP representation of a message contract, each header and body part maps to an XML element that has a name and a namespace.</span></span>  
  
 <span data-ttu-id="73f6d-146">Varsayılan olarak, ad alanı, iletinin katıldığı hizmet sözleşmesinin ad alanıyla aynıdır ve ad, <xref:System.ServiceModel.MessageHeaderAttribute> veya özniteliklerinin uygulandığı üye adına göre belirlenir <xref:System.ServiceModel.MessageBodyMemberAttribute> .</span><span class="sxs-lookup"><span data-stu-id="73f6d-146">By default, the namespace is the same as the namespace of the service contract that the message is participating in, and the name is determined by the member name to which the <xref:System.ServiceModel.MessageHeaderAttribute> or the <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes are applied.</span></span>  
  
 <span data-ttu-id="73f6d-147"><xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType>Ve değerlerini <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> ( <xref:System.ServiceModel.MessageHeaderAttribute> ve özniteliklerinin üst sınıfında <xref:System.ServiceModel.MessageBodyMemberAttribute> ) işleyerek bu varsayılanları değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73f6d-147">You can change these defaults by manipulating the <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (on the parent class of the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes).</span></span>  
  
 <span data-ttu-id="73f6d-148">Aşağıdaki kod örneğinde sınıfını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="73f6d-148">Consider the class in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader(Namespace="http://schemas.contoso.com/auditing/2005")] public bool IsAudited;  
  [MessageBodyMember(Name="transactionData")] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="73f6d-149">Bu örnekte, `IsAudited` üst bilgi kodda belirtilen ad alanıdır ve üyeyi temsil eden gövde bölümü, `theData` ADıNDA bir XML öğesiyle temsil edilir `transactionData` .</span><span class="sxs-lookup"><span data-stu-id="73f6d-149">In this example, the `IsAudited` header is in the namespace specified in the code, and the body part that represents the `theData` member is represented by an XML element with the name `transactionData`.</span></span> <span data-ttu-id="73f6d-150">Aşağıda bu ileti sözleşmesi için oluşturulan XML gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-150">The following shows the XML generated for this message contract.</span></span>  
  
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
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a><span data-ttu-id="73f6d-151">SOAP gövdesi bölümlerinin sarmalanmış olup olmadığını denetleme</span><span class="sxs-lookup"><span data-stu-id="73f6d-151">Controlling Whether the SOAP Body Parts Are Wrapped</span></span>  
 <span data-ttu-id="73f6d-152">Varsayılan olarak, SOAP gövdesi parçaları sarmalanmış bir öğe içinde serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-152">By default, the SOAP body parts are serialized inside a wrapped element.</span></span> <span data-ttu-id="73f6d-153">Örneğin, aşağıdaki kod, `HelloGreetingMessage` <xref:System.ServiceModel.MessageContractAttribute> ileti için ileti sözleşmesindeki tür adından oluşturulan sarmalayıcı öğesini gösterir `HelloGreetingMessage` .</span><span class="sxs-lookup"><span data-stu-id="73f6d-153">For example, the following code shows the `HelloGreetingMessage` wrapper element generated from the name of the <xref:System.ServiceModel.MessageContractAttribute> type in the message contract for the `HelloGreetingMessage` message.</span></span>  
  
[!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
[!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 <span data-ttu-id="73f6d-154">Sarmalayıcı öğesini gizlemek için <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> özelliğini olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="73f6d-154">To suppress the wrapper element, set the <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> property to `false`.</span></span> <span data-ttu-id="73f6d-155">Sarmalayıcı öğesinin adını ve ad alanını denetlemek için <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> ve <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> özelliklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="73f6d-155">To control the name and the namespace of the wrapper element, use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> and <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73f6d-156">Sarmalanmamış iletilerde birden fazla ileti gövdesinin parçası olan WS-ı temel profili 1,1 ile uyumlu değil ve yeni ileti sözleşmeleri tasarlarken önerilmez.</span><span class="sxs-lookup"><span data-stu-id="73f6d-156">Having more than one message body part in messages that are not wrapped is not compliant with WS-I Basic Profile 1.1 and is not recommended when designing new message contracts.</span></span> <span data-ttu-id="73f6d-157">Ancak, belirli bir birlikte çalışabilirlik senaryolarında birden fazla sarmalanmamış ileti gövdesinin parçası olması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-157">However, it may be necessary to have more than one unwrapped message body part in certain specific interoperability scenarios.</span></span> <span data-ttu-id="73f6d-158">Bir ileti gövdesinde birden fazla veri parçası iletileyecekseniz, varsayılan (sarmalanmış) modunun kullanılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-158">If you are going to transmit more than one piece of data in a message body, it is recommended to use the default (wrapped) mode.</span></span> <span data-ttu-id="73f6d-159">Sarmalanmamış iletilerde birden fazla ileti üstbilgisinin bulunması tamamen kabul edilebilir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-159">Having more than one message header in unwrapped messages is completely acceptable.</span></span>  
  
## <a name="using-custom-types-inside-message-contracts"></a><span data-ttu-id="73f6d-160">Ileti sözleşmeleri Içinde özel türler kullanma</span><span class="sxs-lookup"><span data-stu-id="73f6d-160">Using Custom Types Inside Message Contracts</span></span>  
 <span data-ttu-id="73f6d-161">Her bir ileti üst bilgisi ve ileti gövdesi bölümü, iletinin kullanıldığı hizmet sözleşmesi için seçilen serileştirme altyapısını kullanarak serileştirilir (XML 'e açıktır).</span><span class="sxs-lookup"><span data-stu-id="73f6d-161">Each individual message header and message body part is serialized (turned into XML) using the chosen serialization engine for the service contract where the message is used.</span></span> <span data-ttu-id="73f6d-162">Varsayılan serileştirme altyapısı olan, `XmlFormatter` açıkça (sahip olunarak <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> ) veya örtük olarak (temel bir tür, vb.) bir veri sözleşmesine sahip herhangi bir türü işleyebilir <xref:System.SerializableAttribute?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="73f6d-162">The default serialization engine, the `XmlFormatter`, can handle any type that has a data contract, either explicitly (by having the <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) or implicitly (by being a primitive type, having the <xref:System.SerializableAttribute?displayProperty=nameWithType>, and so on).</span></span> <span data-ttu-id="73f6d-163">Daha fazla bilgi için bkz. [Veri Sözleşmelerini Kullanma](using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="73f6d-163">For more information, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="73f6d-164">Yukarıdaki örnekte, `Operation` ve `BankingTransactionData` türleri bir veri sözleşmesine sahip olmalı ve bir `transactionDate` ilkel olduğundan <xref:System.DateTime> (ve bu nedenle örtük bir veri sözleşmesine sahiptir).</span><span class="sxs-lookup"><span data-stu-id="73f6d-164">In the preceding example, the `Operation` and `BankingTransactionData` types must have a data contract, and `transactionDate` is serializable because <xref:System.DateTime> is a primitive (and so has an implicit data contract).</span></span>  
  
 <span data-ttu-id="73f6d-165">Ancak, farklı bir serileştirme altyapısına geçiş yapmak mümkündür `XmlSerializer` .</span><span class="sxs-lookup"><span data-stu-id="73f6d-165">However, it is possible to switch to a different serialization engine, the `XmlSerializer`.</span></span> <span data-ttu-id="73f6d-166">Böyle bir anahtar yaparsanız, ileti üstbilgileri ve gövde parçaları için kullanılan tüm türlerin, kullanılarak serileştirilebilir olduğundan emin olmanız gerekir `XmlSerializer` .</span><span class="sxs-lookup"><span data-stu-id="73f6d-166">If you make such a switch, you should ensure that all of the types used for message headers and body parts are serializable using the `XmlSerializer`.</span></span>  
  
## <a name="using-arrays-inside-message-contracts"></a><span data-ttu-id="73f6d-167">Ileti sözleşmeleri Içinde dizileri kullanma</span><span class="sxs-lookup"><span data-stu-id="73f6d-167">Using Arrays Inside Message Contracts</span></span>  
 <span data-ttu-id="73f6d-168">İleti sözleşmelerinde yinelenen öğe dizilerini iki şekilde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73f6d-168">You can use arrays of repeating elements in message contracts in two ways.</span></span>  
  
 <span data-ttu-id="73f6d-169">Birincisi, <xref:System.ServiceModel.MessageHeaderAttribute> doğrudan dizide bir veya bir kullanmaktır <xref:System.ServiceModel.MessageBodyMemberAttribute> .</span><span class="sxs-lookup"><span data-stu-id="73f6d-169">The first is to use a <xref:System.ServiceModel.MessageHeaderAttribute> or a <xref:System.ServiceModel.MessageBodyMemberAttribute> directly on the array.</span></span> <span data-ttu-id="73f6d-170">Bu durumda, tüm dizi birden çok alt öğe içeren tek bir öğe (yani, bir üst bilgi veya bir gövde bölümü) olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-170">In this case, the entire array is serialized as one element (that is, one header or one body part) with multiple child elements.</span></span> <span data-ttu-id="73f6d-171">Aşağıdaki örnekte sınıfını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="73f6d-171">Consider the class in the following example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingDepositLog  
{  
  [MessageHeader] public int numRecords;  
  [MessageHeader] public DepositRecord[] records;  
  [MessageHeader] public int branchID;  
}  
```  
  
 <span data-ttu-id="73f6d-172">Bu, SOAP üst bilgilerinin sonucu aşağıdakine benzer.</span><span class="sxs-lookup"><span data-stu-id="73f6d-172">This results in SOAP headers is similar to the following.</span></span>  
  
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
  
 <span data-ttu-id="73f6d-173">Bunun bir alternatifi, kullanmaktır <xref:System.ServiceModel.MessageHeaderArrayAttribute> .</span><span class="sxs-lookup"><span data-stu-id="73f6d-173">An alternative to this is to use the <xref:System.ServiceModel.MessageHeaderArrayAttribute>.</span></span> <span data-ttu-id="73f6d-174">Bu durumda, her dizi öğesi bağımsız olarak serileştirilir ve böylece her dizi öğesinin aşağıdakine benzer bir üst bilgi vardır.</span><span class="sxs-lookup"><span data-stu-id="73f6d-174">In this case, each array element is serialized independently and so that each array element has one header, similar to the following.</span></span>  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 <span data-ttu-id="73f6d-175">Dizi girdilerinin varsayılan adı, <xref:System.ServiceModel.MessageHeaderArrayAttribute> özniteliklerin uygulandığı üyenin adıdır.</span><span class="sxs-lookup"><span data-stu-id="73f6d-175">The default name for array entries is the name of the member to which the <xref:System.ServiceModel.MessageHeaderArrayAttribute> attributes is applied.</span></span>  
  
 <span data-ttu-id="73f6d-176"><xref:System.ServiceModel.MessageHeaderArrayAttribute>Özniteliği öğesinden devralır <xref:System.ServiceModel.MessageHeaderAttribute> .</span><span class="sxs-lookup"><span data-stu-id="73f6d-176">The <xref:System.ServiceModel.MessageHeaderArrayAttribute> attribute inherits from the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="73f6d-177">Dizi olmayan özniteliklerle aynı özellik kümesine sahiptir, örneğin, bir üst bilgi dizisinin sıra, ad ve ad alanını tek bir üstbilgi için ayarladığınız şekilde ayarlamak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="73f6d-177">It has the same set of features as the non-array attributes, for example, it is possible to set the order, name, and namespace for an array of headers in the same way you set it for a single header.</span></span> <span data-ttu-id="73f6d-178">`Order`Özelliğini bir dizide kullandığınızda, bu, tüm dizi için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-178">When you use the `Order` property on an array, it applies to the entire array.</span></span>  
  
 <span data-ttu-id="73f6d-179"><xref:System.ServiceModel.MessageHeaderArrayAttribute>Koleksiyonları değil, yalnızca dizilere uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73f6d-179">You can apply the <xref:System.ServiceModel.MessageHeaderArrayAttribute> only to arrays, not collections.</span></span>  
  
## <a name="using-byte-arrays-in-message-contracts"></a><span data-ttu-id="73f6d-180">Ileti sözleşmelerinde Byte dizilerini kullanma</span><span class="sxs-lookup"><span data-stu-id="73f6d-180">Using Byte Arrays in Message Contracts</span></span>  
 <span data-ttu-id="73f6d-181">Dizi olmayan özniteliklerle (ve) birlikte kullanıldığında bayt dizileri <xref:System.ServiceModel.MessageBodyMemberAttribute> <xref:System.ServiceModel.MessageHeaderAttribute> diziler olarak değerlendirilmez, ancak sonuçta elde edilen XML 'de Base64 kodlamalı veriler olarak temsil edilen özel bir ilkel tür olarak kabul edilmez.</span><span class="sxs-lookup"><span data-stu-id="73f6d-181">Byte arrays, when used with the non-array attributes (<xref:System.ServiceModel.MessageBodyMemberAttribute> and <xref:System.ServiceModel.MessageHeaderAttribute>), are not treated as arrays but as a special primitive type represented as Base64-encoded data in the resulting XML.</span></span>  
  
 <span data-ttu-id="73f6d-182">Dizi özniteliğiyle byte dizileri kullandığınızda <xref:System.ServiceModel.MessageHeaderArrayAttribute> , sonuçlar kullanımdaki seri hale getiriciye göre değişir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-182">When you use byte arrays with the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the results depend on the serializer in use.</span></span> <span data-ttu-id="73f6d-183">Varsayılan serileştirici ile, dizi her bir bayt için tek bir girdi olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-183">With the default serializer, the array is represented as an individual entry for each byte.</span></span> <span data-ttu-id="73f6d-184">Ancak, `XmlSerializer` seçildiğinde (hizmet sözleşmesinde öğesini kullanarak), <xref:System.ServiceModel.XmlSerializerFormatAttribute> dizi veya dizi olmayan özniteliklerin kullanılıp kullanılmadığına bakılmaksızın bayt dizileri Base64 verileri olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-184">However, when the `XmlSerializer` is selected, (using the <xref:System.ServiceModel.XmlSerializerFormatAttribute> on the service contract), byte arrays are treated as Base64 data regardless of whether the array or non-array attributes are used.</span></span>  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a><span data-ttu-id="73f6d-185">Ileti parçalarını imzalama ve şifreleme</span><span class="sxs-lookup"><span data-stu-id="73f6d-185">Signing and Encrypting Parts of the Message</span></span>  
 <span data-ttu-id="73f6d-186">İleti anlaşması, ileti başlıklarının ve/veya gövdesinin dijital olarak imzalanıp imzalanmayacağını ve şifrelenmeyeceğini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-186">A message contract can indicate whether the headers and/or body of the message should be digitally signed and encrypted.</span></span>  
  
 <span data-ttu-id="73f6d-187">Bu <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> , ve özniteliklerinde özelliği ayarlanarak yapılır <xref:System.ServiceModel.MessageHeaderAttribute> <xref:System.ServiceModel.MessageBodyMemberAttribute> .</span><span class="sxs-lookup"><span data-stu-id="73f6d-187">This is done by setting the <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> property on the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="73f6d-188">Özelliği, türün bir numaralandırmadır <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> ve ( <xref:System.Net.Security.ProtectionLevel.None> şifreleme veya imza yok), <xref:System.Net.Security.ProtectionLevel.Sign> (yalnızca dijital imza) veya <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (hem şifreleme hem de dijital imza) olarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-188">The property is an enumeration of the <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> type and can be set to <xref:System.Net.Security.ProtectionLevel.None> (no encryption or signature), <xref:System.Net.Security.ProtectionLevel.Sign> (digital signature only), or <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (both encryption and a digital signature).</span></span> <span data-ttu-id="73f6d-189">Varsayılan değer: <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="73f6d-189">The default is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
 <span data-ttu-id="73f6d-190">Bu güvenlik özelliklerinin çalışması için bağlama ve davranışları doğru şekilde yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-190">For these security features to work, you must properly configure the binding and behaviors.</span></span> <span data-ttu-id="73f6d-191">Bu güvenlik özelliklerini uygun yapılandırma olmadan (örneğin, kimlik bilgilerinizi vermeden bir iletiyi imzalamaya çalışırken) kullanırsanız, doğrulama zamanında bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="73f6d-191">If you use these security features without the proper configuration (for example, attempting to sign a message without supplying your credentials), an exception is thrown at validation time.</span></span>  
  
 <span data-ttu-id="73f6d-192">İleti üstbilgileri için, her üst bilgi için koruma düzeyi ayrı ayrı belirlenir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-192">For message headers, the protection level is determined individually for each header.</span></span>  
  
 <span data-ttu-id="73f6d-193">İleti gövdesi parçaları için, koruma düzeyi "En düşük koruma düzeyi" olarak düşünülebilir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-193">For message body parts, the protection level can be thought of as the "minimum protection level."</span></span> <span data-ttu-id="73f6d-194">Gövde, gövde bölümlerinin sayısından bağımsız olarak yalnızca bir koruma düzeyine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-194">The body has only one protection level, regardless of the number of body parts.</span></span> <span data-ttu-id="73f6d-195">Gövdenin koruma düzeyi, <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> tüm gövde bölümlerinin en yüksek özellik ayarına göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-195">The protection level of the body is determined by the highest <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> property setting of all the body parts.</span></span> <span data-ttu-id="73f6d-196">Ancak, her gövde bölümünün koruma düzeyini gereken gerçek en düşük koruma düzeyine ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-196">However, you should set the protection level of each body part to the actual minimum protection level required.</span></span>  
  
 <span data-ttu-id="73f6d-197">Aşağıdaki kod örneğinde sınıfını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="73f6d-197">Consider the class in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="73f6d-198">Bu örnekte, `recordID` üst bilgi korunmaz,, `patientName` `signed` , ve `SSN` şifrelenir ve imzalanır.</span><span class="sxs-lookup"><span data-stu-id="73f6d-198">In this example, the `recordID` header is not protected, `patientName` is `signed`, and `SSN` is encrypted and signed.</span></span> <span data-ttu-id="73f6d-199">En az bir gövde bölümü, `medicalHistory` ve bu <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> nedenle, açıklamalar ve tanılama gövdesi parçaları alt koruma düzeylerini belirtse bile, tüm ileti gövdesinin şifrelenmesi ve imzalanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-199">At least one body part, `medicalHistory`, has <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> applied, and thus the entire message body is encrypted and signed, even though the comments and diagnosis body parts specify lower protection levels.</span></span>  
  
## <a name="soap-action"></a><span data-ttu-id="73f6d-200">SOAP eylemi</span><span class="sxs-lookup"><span data-stu-id="73f6d-200">SOAP Action</span></span>  
 <span data-ttu-id="73f6d-201">SOAP ve ilgili Web Hizmetleri standartları, `Action` gönderilen her soap iletisi için mevcut olabilecek adlı bir özelliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="73f6d-201">SOAP and related Web services standards define a property called `Action` that can be present for every SOAP message sent.</span></span> <span data-ttu-id="73f6d-202">İşlemin <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> ve <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> özellikleri bu özelliğin değerini denetler.</span><span class="sxs-lookup"><span data-stu-id="73f6d-202">The operation's <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> properties control the value of this property.</span></span>  
  
## <a name="soap-header-attributes"></a><span data-ttu-id="73f6d-203">SOAP üst bilgisi öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="73f6d-203">SOAP Header Attributes</span></span>  
 <span data-ttu-id="73f6d-204">SOAP standardı, bir üst bilgide mevcut olabilecek aşağıdaki öznitelikleri tanımlar:</span><span class="sxs-lookup"><span data-stu-id="73f6d-204">The SOAP standard defines the following attributes that may exist on a header:</span></span>  
  
- <span data-ttu-id="73f6d-205">`Actor/Role`(SOAP `Actor` 1,1 ' de, `Role` SOAP 1,2 ' de)</span><span class="sxs-lookup"><span data-stu-id="73f6d-205">`Actor/Role` (`Actor` in SOAP 1.1, `Role` in SOAP 1.2)</span></span>  
  
- `MustUnderstand`  
  
- `Relay`  
  
 <span data-ttu-id="73f6d-206">`Actor`Or `Role` özniteliği, belirli bir üst bilginin Istendiği düğümün Tekdüzen Kaynak tanımlayıcısını (URI) belirtir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-206">The `Actor` or `Role` attribute specifies the Uniform Resource Identifier (URI) of the node for which a given header is intended.</span></span> <span data-ttu-id="73f6d-207">`MustUnderstand`Öznitelik, üstbilgiyi işleyen düğümün onu anlaması gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-207">The `MustUnderstand` attribute specifies whether the node processing the header must understand it.</span></span> <span data-ttu-id="73f6d-208">`Relay`Öznitelik, üstbilginin aşağı akış düğümlerine geçirilip geçirilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-208">The `Relay` attribute specifies whether the header is to be relayed to downstream nodes.</span></span> <span data-ttu-id="73f6d-209">WCF, `MustUnderstand` Bu konunun ilerleyen kısımlarında yer alan "Ileti sözleşmesi sürümü oluşturma" bölümünde belirtildiği gibi, bu özniteliklerin, öznitelik hariç, bu özniteliklerin herhangi bir işlemesini gerçekleştirmez.</span><span class="sxs-lookup"><span data-stu-id="73f6d-209">WCF does not perform any processing of these attributes on incoming messages, except for the `MustUnderstand` attribute, as specified in the "Message Contract Versioning" section later in this topic.</span></span> <span data-ttu-id="73f6d-210">Ancak, aşağıdaki açıklamada olduğu gibi bu öznitelikleri gerektiği gibi okuyup yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="73f6d-210">However, it allows you to read and write these attributes as necessary, as in the following description.</span></span>  
  
 <span data-ttu-id="73f6d-211">İleti gönderilirken, bu öznitelikler varsayılan olarak yayılmaz.</span><span class="sxs-lookup"><span data-stu-id="73f6d-211">When sending a message, these attributes are not emitted by default.</span></span> <span data-ttu-id="73f6d-212">Bunu iki şekilde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73f6d-212">You can change this in two ways.</span></span> <span data-ttu-id="73f6d-213">İlk olarak <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType> , <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType> <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> Aşağıdaki kod örneğinde gösterildiği gibi,, ve özelliklerini değiştirerek, öznitelikleri istediğiniz herhangi bir değere statik olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73f6d-213">First, you may statically set the attributes to any desired values by changing the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, and <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> properties, as shown in the following code example.</span></span> <span data-ttu-id="73f6d-214">(Özellik olmadığını unutmayın `Role` ; <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> SOAP 1,2 kullanıyorsanız, özelliğin bu özniteliği yayar olarak ayarlanması `Role` ).</span><span class="sxs-lookup"><span data-stu-id="73f6d-214">(Note that there is no `Role` property; setting the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> property emits the `Role` attribute if you are using SOAP 1.2).</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="73f6d-215">Bu öznitelikleri denetlemek için ikinci yöntem kod aracılığıyla dinamik olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-215">The second way to control these attributes is dynamically, through code.</span></span> <span data-ttu-id="73f6d-216">Bunu, istenen üst bilgi türünü <xref:System.ServiceModel.MessageHeader%601> (genel olmayan sürüm ile karıştırmayı unutmayın) ve türünü ile birlikte kullanarak elde edebilirsiniz <xref:System.ServiceModel.MessageHeaderAttribute> .</span><span class="sxs-lookup"><span data-stu-id="73f6d-216">You can achieve this by wrapping the desired header type in the <xref:System.ServiceModel.MessageHeader%601> type (be sure not to confuse this type with the non-generic version) and by using the type together with the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="73f6d-217">Ardından, <xref:System.ServiceModel.MessageHeader%601> Aşağıdaki kod örneğinde gösterildiği gıbı soap özniteliklerini ayarlamak için üzerinde özellikleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73f6d-217">Then, you can use properties on the <xref:System.ServiceModel.MessageHeader%601> to set the SOAP attributes, as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="73f6d-218">Hem dinamik hem de statik denetim mekanizmalarını kullanırsanız, statik ayarlar varsayılan olarak kullanılır, ancak daha sonra aşağıdaki kodda gösterildiği gibi dinamik mekanizma kullanılarak geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-218">If you use both the dynamic and the static control mechanisms, the static settings are used as a default but can later be overridden by using the dynamic mechanism, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 <span data-ttu-id="73f6d-219">Aşağıdaki kodda gösterildiği gibi, dinamik öznitelik denetimiyle yinelenen üst bilgilerin oluşturulmasına izin verilir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-219">Creating repeated headers with dynamic attribute control is allowed, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 <span data-ttu-id="73f6d-220">Alma tarafında, bu SOAP özniteliklerini okumak yalnızca, <xref:System.ServiceModel.MessageHeader%601> türündeki üst bilgi için sınıf kullanılıyorsa yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-220">On the receiving side, reading these SOAP attributes can only be done if the <xref:System.ServiceModel.MessageHeader%601> class is used for the header in the type.</span></span> <span data-ttu-id="73f6d-221">`Actor` `Relay` `MustUnderstand` <xref:System.ServiceModel.MessageHeader%601> Alınan iletideki öznitelik ayarlarını saptamak için türün bir üst bilgisinin, veya özelliklerini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="73f6d-221">Examine the `Actor`, `Relay`, or `MustUnderstand` properties of a header of the <xref:System.ServiceModel.MessageHeader%601> type to discover the attribute settings on the received message.</span></span>  
  
 <span data-ttu-id="73f6d-222">Bir ileti alındığında ve sonra geri gönderildiğinde, SOAP öznitelik ayarları yalnızca türün üst bilgileri için gidiş dönüş ' ı gider <xref:System.ServiceModel.MessageHeader%601> .</span><span class="sxs-lookup"><span data-stu-id="73f6d-222">When a message is received and then sent back, the SOAP attribute settings only go round-trip for headers of the <xref:System.ServiceModel.MessageHeader%601> type.</span></span>  
  
## <a name="order-of-soap-body-parts"></a><span data-ttu-id="73f6d-223">SOAP gövdesi bölümlerinin sırası</span><span class="sxs-lookup"><span data-stu-id="73f6d-223">Order of SOAP Body Parts</span></span>  
 <span data-ttu-id="73f6d-224">Bazı durumlarda, gövde bölümlerinin sırasını kontrol etmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-224">In some circumstances, you may need to control the order of the body parts.</span></span> <span data-ttu-id="73f6d-225">Gövde öğelerinin sırası varsayılan olarak alfabetik şekilde belirlenir, ancak özelliği tarafından denetlenebilir <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="73f6d-225">The order of the body elements is alphabetical by default, but can be controlled by the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="73f6d-226">Bu özellik, <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> Devralma senaryolarındaki davranış dışında, özelliği ile aynı semantiğe sahiptir (ileti sözleşmelerinde, temel tür gövde üyeleri türetilmiş tür gövde üyelerinden önce sıralanmaz).</span><span class="sxs-lookup"><span data-stu-id="73f6d-226">This property has the same semantics as the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> property, except for the behavior in inheritance scenarios (in message contracts, base type body members are not sorted before the derived type body members).</span></span> <span data-ttu-id="73f6d-227">Daha fazla bilgi için bkz. [veri üye sıralaması](data-member-order.md).</span><span class="sxs-lookup"><span data-stu-id="73f6d-227">For more information, see [Data Member Order](data-member-order.md).</span></span>  
  
 <span data-ttu-id="73f6d-228">Aşağıdaki örnekte, `amount` normal olarak ilk alfabetik olduğu için ilk olarak gelir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-228">In the following example, `amount` would normally come first because it is first alphabetically.</span></span> <span data-ttu-id="73f6d-229">Ancak, <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> özelliği üçüncü konuma koyar.</span><span class="sxs-lookup"><span data-stu-id="73f6d-229">However, the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> property puts it into the third position.</span></span>  
  
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
  
## <a name="message-contract-versioning"></a><span data-ttu-id="73f6d-230">İleti sözleşmesi sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="73f6d-230">Message Contract Versioning</span></span>  
 <span data-ttu-id="73f6d-231">Bazen ileti sözleşmelerini değiştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-231">Occasionally, you may need to change message contracts.</span></span> <span data-ttu-id="73f6d-232">Örneğin, uygulamanızın yeni bir sürümü bir iletiye ek bir üst bilgi ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-232">For example, a new version of your application may add an extra header to a message.</span></span> <span data-ttu-id="73f6d-233">Daha sonra, yeni sürümden eski sürümüne gönderirken sistemin ek bir üst bilgiyle ve diğer yönde gitirken eksik bir üst bilgi ile uğraşmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-233">Then, when sending from the new version to the old, the system must deal with an extra header, as well as a missing header when going in the other direction.</span></span>  
  
 <span data-ttu-id="73f6d-234">Sürüm oluşturma üstbilgileri için aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="73f6d-234">The following rules apply for versioning headers:</span></span>  
  
- <span data-ttu-id="73f6d-235">WCF eksik üstbilgilere nesne yapmaz — ilgili Üyeler varsayılan değerlerinde bırakılır.</span><span class="sxs-lookup"><span data-stu-id="73f6d-235">WCF does not object to the missing headers—the corresponding members are left at their default values.</span></span>  
  
- <span data-ttu-id="73f6d-236">WCF Ayrıca beklenmeyen Ek üstbilgileri yoksayar.</span><span class="sxs-lookup"><span data-stu-id="73f6d-236">WCF also ignores unexpected extra headers.</span></span> <span data-ttu-id="73f6d-237">Bu kuralın tek istisnası, ek üstbilginin `MustUnderstand` gelen SOAP iletisinde olarak ayarlanmış bir özniteliği varsa `true` — Bu durumda, anlaşılması gereken bir üst bilgi işlenemediği için bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="73f6d-237">The one exception to this rule is if the extra header has a `MustUnderstand` attribute set to `true` in the incoming SOAP message—in this case, an exception is thrown because a header that must be understood cannot be processed.</span></span>  
  
 <span data-ttu-id="73f6d-238">İleti gövdelerinin benzer sürüm kuralları vardır — hem eksik hem de ek ileti gövdesi parçaları yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="73f6d-238">Message bodies have similar versioning rules—both missing and additional message body parts are ignored.</span></span>  
  
## <a name="inheritance-considerations"></a><span data-ttu-id="73f6d-239">Devralma konuları</span><span class="sxs-lookup"><span data-stu-id="73f6d-239">Inheritance Considerations</span></span>  
 <span data-ttu-id="73f6d-240">Temel türün da bir ileti anlaşması olduğu sürece, bir ileti sözleşmesi türü başka bir türden devralınabilir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-240">A message contract type can inherit from another type, as long as the base type also has a message contract.</span></span>  
  
 <span data-ttu-id="73f6d-241">Diğer ileti anlaşması türlerinden devralan bir ileti sözleşmesi türü kullanarak bir ileti oluştururken veya erişirken, aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="73f6d-241">When creating or accessing a message using a message contract type that inherits from other message contract types, the following rules apply:</span></span>  
  
- <span data-ttu-id="73f6d-242">Devralma hiyerarşisindeki tüm ileti üstbilgileri, ileti için tüm üst bilgi kümesini oluşturmak üzere birlikte toplanır.</span><span class="sxs-lookup"><span data-stu-id="73f6d-242">All of the message headers in the inheritance hierarchy are collected together to form the full set of headers for the message.</span></span>  
  
- <span data-ttu-id="73f6d-243">Devralma hiyerarşisindeki tüm ileti gövdesi parçaları, tam ileti gövdesini oluşturmak için birlikte toplanır.</span><span class="sxs-lookup"><span data-stu-id="73f6d-243">All of the message body parts in the inheritance hierarchy are collected together to form the full message body.</span></span> <span data-ttu-id="73f6d-244">Gövde parçaları, <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> Devralma hiyerarşisinde yer almayla ilgili hiçbir ilgisi olmadan olağan sıralama kurallarına (özelliğe göre ve ardından alfabetik olarak) göre sıralanır.</span><span class="sxs-lookup"><span data-stu-id="73f6d-244">The body parts are ordered according to the usual ordering rules (by <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property and then alphabetical), with no relevance to their place in the inheritance hierarchy.</span></span> <span data-ttu-id="73f6d-245">İleti metni parçalarının devralma ağacının birden çok düzeyinde gerçekleştiği ileti sözleşmesi devralımı kullanılması önerilmez.</span><span class="sxs-lookup"><span data-stu-id="73f6d-245">Using message contract inheritance where message body parts occur at multiple levels of the inheritance tree is strongly discouraged.</span></span> <span data-ttu-id="73f6d-246">Bir temel sınıf ve türetilmiş bir sınıf, aynı ada sahip bir üst bilgi veya gövde parçasını tanımladıysanız, temel sınıfın üyesi bu üst bilgi veya gövde bölümünün değerini depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="73f6d-246">If a base class and a derived class define a header or a body part with the same name, the member from the base-most class is used to store the value of that header or body part.</span></span>  
  
 <span data-ttu-id="73f6d-247">Aşağıdaki kod örneğinde bulunan sınıfları göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="73f6d-247">Consider the classes in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="73f6d-248">`PatientRecord`Sınıfı, bir üst bilgiyle çağrılan bir ileti tanımlar `ID` .</span><span class="sxs-lookup"><span data-stu-id="73f6d-248">The `PatientRecord` class describes a message with one header called `ID`.</span></span> <span data-ttu-id="73f6d-249">Üst `personID` düzey üye seçildiği için üst bilgi üyeye değil öğesine karşılık gelir `patientID` .</span><span class="sxs-lookup"><span data-stu-id="73f6d-249">The header corresponds to the `personID` and not the `patientID` member, because the base-most member is chosen.</span></span> <span data-ttu-id="73f6d-250">Bu nedenle, `patientID` Bu durumda alan gereksizdir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-250">Thus, the `patientID` field is useless in this case.</span></span> <span data-ttu-id="73f6d-251">İletinin gövdesi, `diagnosis` Bu öğenin alfabetik sırası olduğu için öğesi tarafından izlenen öğesi içerir `patientName` .</span><span class="sxs-lookup"><span data-stu-id="73f6d-251">The body of the message contains the `diagnosis` element followed by the `patientName` element, because that is the alphabetical order.</span></span> <span data-ttu-id="73f6d-252">Örnekte kesinlikle önerilmez: hem temel hem de türetilmiş ileti sözleşmelerinin ileti gövdesi parçaları vardır.</span><span class="sxs-lookup"><span data-stu-id="73f6d-252">Notice that the example shows a pattern that is strongly discouraged: both the base and the derived message contracts have message body parts.</span></span>  
  
## <a name="wsdl-considerations"></a><span data-ttu-id="73f6d-253">WSDL konuları</span><span class="sxs-lookup"><span data-stu-id="73f6d-253">WSDL Considerations</span></span>  
 <span data-ttu-id="73f6d-254">İleti sözleşmeleri kullanan bir hizmetten bir Web Hizmetleri Açıklama Dili (WSDL) Sözleşmesi oluştururken, tüm ileti sözleşmesi özelliklerinin sonuçta elde edilen WSDL 'de yansıtıldığını unutmamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-254">When generating a Web Services Description Language (WSDL) contract from a service that uses message contracts, it is important to remember that not all message contract features are reflected in the resulting WSDL.</span></span> <span data-ttu-id="73f6d-255">Aşağıdaki noktaları göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="73f6d-255">Consider the following points:</span></span>  
  
- <span data-ttu-id="73f6d-256">WSDL, bir üst bilgi dizisi kavramını ifade edemez.</span><span class="sxs-lookup"><span data-stu-id="73f6d-256">WSDL cannot express the concept of an array of headers.</span></span> <span data-ttu-id="73f6d-257">Kullanılarak bir üst bilgi dizisiyle ileti oluştururken <xref:System.ServiceModel.MessageHeaderArrayAttribute> , sonuçta elde EDILEN WSDL dizi yerine yalnızca bir üst bilgi yansıtır.</span><span class="sxs-lookup"><span data-stu-id="73f6d-257">When creating messages with an array of headers using the <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the resulting WSDL reflects only one header instead of the array.</span></span>  
  
- <span data-ttu-id="73f6d-258">Elde edilen WSDL belgesi, bazı koruma düzeyi bilgileri yansıtmayabilir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-258">The resulting WSDL document may not reflect some protection-level information.</span></span>  
  
- <span data-ttu-id="73f6d-259">WSDL içinde oluşturulan ileti türü, ileti sözleşmesi türünün sınıf adı ile aynı ada sahiptir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-259">The message type generated in the WSDL has the same name as the class name of the message contract type.</span></span>  
  
- <span data-ttu-id="73f6d-260">Birden çok işlemde aynı ileti sözleşmesini kullanırken, WSDL belgesinde birden çok ileti türü oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="73f6d-260">When using the same message contract in multiple operations, multiple message types are generated in the WSDL document.</span></span> <span data-ttu-id="73f6d-261">Adlar, sonraki kullanımlar için "2", "3" ve benzeri sayılar eklenerek benzersiz hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-261">The names are made unique by adding the numbers "2", "3", and so on, for subsequent uses.</span></span> <span data-ttu-id="73f6d-262">WSDL geri alınırken, birden çok ileti sözleşme türü oluşturulur ve adları dışında aynıdır.</span><span class="sxs-lookup"><span data-stu-id="73f6d-262">When importing back the WSDL, multiple message contract types are created and are identical except for their names.</span></span>  
  
## <a name="soap-encoding-considerations"></a><span data-ttu-id="73f6d-263">SOAP kodlama konuları</span><span class="sxs-lookup"><span data-stu-id="73f6d-263">SOAP Encoding Considerations</span></span>  
 <span data-ttu-id="73f6d-264">WCF, XML 'nin eski SOAP kodlama stilini kullanmanıza olanak tanır, ancak kullanımı önerilmez.</span><span class="sxs-lookup"><span data-stu-id="73f6d-264">WCF allows you to use the legacy SOAP encoding style of XML, however, its use is not recommended.</span></span> <span data-ttu-id="73f6d-265">Bu stil kullanılırken ( `Use` özelliğini `Encoded` <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> hizmet sözleşmesine uygulanan olarak ayarlayarak) aşağıdaki ek konular geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="73f6d-265">When using this style (by setting the `Use` property to `Encoded` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> applied to the service contract), the following additional considerations apply:</span></span>  
  
- <span data-ttu-id="73f6d-266">İleti üstbilgileri desteklenmez; Bu, özniteliği <xref:System.ServiceModel.MessageHeaderAttribute> ve dizi ÖZNITELIĞININ <xref:System.ServiceModel.MessageHeaderArrayAttribute> SOAP kodlamasıyla uyumsuz olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-266">The message headers are not supported; this means that the attribute <xref:System.ServiceModel.MessageHeaderAttribute> and the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute> are incompatible with SOAP encoding.</span></span>  
  
- <span data-ttu-id="73f6d-267">İleti anlaşması sarmalanmamış ise, bu, özelliği <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> olarak ayarlandıysa, `false` ileti sözleşmesinin yalnızca bir gövde bölümü olabilir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-267">If the message contract is not wrapped, that is, if the property <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> is set to `false`, the message contract can have only one body part.</span></span>  
  
- <span data-ttu-id="73f6d-268">İstek iletisi sözleşmesinin sarmalayıcı öğesinin adı işlem adıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-268">The name of the wrapper element for the request message contract must match the operation name.</span></span> <span data-ttu-id="73f6d-269">`WrapperName`Bunun için ileti sözleşmesinin özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="73f6d-269">Use the `WrapperName` property of the message contract for this.</span></span>  
  
- <span data-ttu-id="73f6d-270">Yanıt iletisi sözleşmesinin sarmalayıcı öğesinin adı, ' Response ' ile düzeltilen işlem soneki adı ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="73f6d-270">The name of the wrapper element for the response message contract must be the same as the name of the operation suffixed by 'Response'.</span></span> <span data-ttu-id="73f6d-271"><xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A>Bunun için ileti sözleşmesinin özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="73f6d-271">Use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> property of the message contract for this.</span></span>  
  
- <span data-ttu-id="73f6d-272">SOAP Encoding nesne başvurularını korur.</span><span class="sxs-lookup"><span data-stu-id="73f6d-272">SOAP encoding preserves object references.</span></span> <span data-ttu-id="73f6d-273">Örneğin, aşağıdaki kodu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="73f6d-273">For example, consider the following code.</span></span>  
  
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
  
 <span data-ttu-id="73f6d-274">SOAP kodlaması kullanarak iletiyi serileştirdikten `changedFrom` ve `changedTo` kendi kopyalarını içermediğinden `p` , bunun yerine öğesinin içindeki kopyaya gelin `changedBy` .</span><span class="sxs-lookup"><span data-stu-id="73f6d-274">After serializing the message using SOAP encoding, `changedFrom` and `changedTo` do not contain their own copies of `p`, but instead point to the copy inside the `changedBy` element.</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="73f6d-275">Başarım Değerlendirmeleri</span><span class="sxs-lookup"><span data-stu-id="73f6d-275">Performance Considerations</span></span>  
 <span data-ttu-id="73f6d-276">Her ileti üst bilgisi ve ileti gövdesi bölümü diğerlerinden bağımsız olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-276">Every message header and message body part is serialized independently of the others.</span></span> <span data-ttu-id="73f6d-277">Bu nedenle, her başlık ve gövde bölümü için aynı ad alanları yeniden bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="73f6d-277">Therefore, the same namespaces can be declared again for each header and body part.</span></span> <span data-ttu-id="73f6d-278">Performansı artırmak için, özellikle de iletişimdeki iletinin boyutu açısından birden çok üstbilgiyi ve gövde parçalarını tek bir üstbilgi veya gövde bölümünde birleştirin.</span><span class="sxs-lookup"><span data-stu-id="73f6d-278">To improve performance, especially in terms of the size of the message on the wire, consolidate multiple headers and body parts into a single header or body part.</span></span> <span data-ttu-id="73f6d-279">Örneğin, aşağıdaki kod yerine:</span><span class="sxs-lookup"><span data-stu-id="73f6d-279">For example, instead of the following code:</span></span>  
  
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
  
 <span data-ttu-id="73f6d-280">Bu kodu kullanın.</span><span class="sxs-lookup"><span data-stu-id="73f6d-280">Use this code.</span></span>  
  
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
  
### <a name="event-based-asynchronous-and-message-contracts"></a><span data-ttu-id="73f6d-281">Olay tabanlı zaman uyumsuz ve Ileti sözleşmeleri</span><span class="sxs-lookup"><span data-stu-id="73f6d-281">Event-based Asynchronous and Message Contracts</span></span>  
 <span data-ttu-id="73f6d-282">Olay tabanlı zaman uyumsuz model için, birden fazla değer döndürülürse, özellik olarak bir değer döndürülür `Result` ve diğerleri nesne üzerinde özellikler olarak döndürülür <xref:System.EventArgs> .</span><span class="sxs-lookup"><span data-stu-id="73f6d-282">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="73f6d-283">Bunun sonucunda, bir istemci, olay tabanlı zaman uyumsuz komut seçeneklerini kullanarak meta verileri içeri aktardığında ve işlem birden fazla değer döndürürse, varsayılan <xref:System.EventArgs> nesne özellik olarak bir değer döndürür `Result` ve geri kalanı <xref:System.EventArgs> nesnenin özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-283">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="73f6d-284">İleti nesnesini özellik olarak almak `Result` ve döndürülen değerlerin bu nesnede özellikler olarak elde etmek istiyorsanız, `/messageContract` komut seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="73f6d-284">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="73f6d-285">Bu, nesne üzerindeki özelliği olarak yanıt iletisini döndüren bir imza oluşturur `Result` <xref:System.EventArgs> .</span><span class="sxs-lookup"><span data-stu-id="73f6d-285">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="73f6d-286">Tüm iç dönüş değerleri, yanıt iletisi nesnesinin özellikleridir.</span><span class="sxs-lookup"><span data-stu-id="73f6d-286">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73f6d-287">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73f6d-287">See also</span></span>

- [<span data-ttu-id="73f6d-288">Veri Anlaşmalarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="73f6d-288">Using Data Contracts</span></span>](using-data-contracts.md)
- [<span data-ttu-id="73f6d-289">Hizmetleri Tasarlama ve Uygulama</span><span class="sxs-lookup"><span data-stu-id="73f6d-289">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)
