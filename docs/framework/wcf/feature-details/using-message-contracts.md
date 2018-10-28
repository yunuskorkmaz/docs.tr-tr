---
title: İleti Sözleşmeleri Kullanılıyor
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message contracts [WCF]
ms.assetid: 1e19c64a-ae84-4c2f-9155-91c54a77c249
ms.openlocfilehash: c3f979d26c7e9c36fc242476ae5b3420b2e7d3ac
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194091"
---
# <a name="using-message-contracts"></a>İleti Sözleşmeleri Kullanılıyor
Genellikle Windows Communication Foundation (WCF) uygulamaları oluştururken geliştiriciler serileştirme sorunlarına ve veri yapıları Kapat dikkat ve kendilerini hangi verileri taşınan iletileri yapısı ile uğraşmak zorunda değildir. Bu uygulamalar için parametreleri veya dönüş değerleri için veri sözleşmeleri oluşturma oldukça basittir. (Daha fazla bilgi için [hizmet sözleşmelerinde veri aktarımı belirtme](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).)  
  
 Ancak, bir SOAP ileti yapısını bazen tam kontrole yalnızca içeriği üzerinde denetim olarak da önemlidir. Birlikte çalışabilirlik önemli olduğunda veya özellikle güvenlik denetlemek için ileti veya ileti bölümü düzeyinde sorunları özellikle doğrudur. Bu durumlarda, oluşturduğunuz bir *ileti anlaşması* gereken kesin SOAP iletisi yapısını belirtmenize imkan tanır.  
  
 Bu konu, çeşitli ileti anlaşması öznitelikleri oluşturma işlemi için bir özel ileti anlaşması için nasıl kullanılacağını açıklar.  
  
## <a name="using-message-contracts-in-operations"></a>İleti sözleşmeleri işlemlerinde kullanma  
 WCF desteklediği işlemleri üzerinde modellenmiş *uzak yordam çağrısı (RPC) stili* veya *stil Mesajlaşma*. RPC stili işleminde, serializable bir tür kullanabilirsiniz ve birden çok parametre gibi yerel çağrıları kullanılabilir özelliklere erişiminiz ve `ref` ve `out` parametreleri. Bu stilde, temel alınan iletileri verilerin yapısını seçilen serileştirme biçimini denetler ve WCF çalıştırma zamanı işlemi desteklemek için iletileri oluşturur. Bu, SOAP ile tanıdık olmayan iletileri hızla SOAP ve kolayca oluşturun ve hizmet uygulamalarını kullanmak geliştiriciler sağlar.  
  
 Aşağıdaki kod örneği bir hizmet işlemi RPC stili modellenmiş gösterir.  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 Normalde, bir veri anlaşması iletileri için şema tanımlamak yeterlidir. Örneğin, önceki örnekte, çoğu uygulama için yeterlidir, `BankingTransaction` ve `BankingTransactionResponse` temel SOAP iletilerinin içeriğini tanımlamak için veri sözleşmelerine sahiptir. Veri sözleşmeleri hakkında daha fazla bilgi için bkz: [kullanarak veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Ancak, bazen nasıl SOAP iletisi yapısını hat üzerinden iletilen tam olarak denetlemek gereklidir. En yaygın senaryo için bu özel SOAP üstbilgileri ekliyor. Diğer bir deyişle ileti üstbilgileri ve gövdesi için güvenlik özelliklerini tanımlamak için bu öğeleri dijital olarak imzalanmış ve şifrelenmiş olmadığını karar vermek için başka bir yaygın bir senaryodur. Son olarak, bazı üçüncü taraf SOAP yığınları iletileri gerektiren belirli bir biçiminde olmalıdır. İleti stili işlemleri bu denetimi sağlar.  
  
 Her iki ileti türleri olduğu en fazla bir parametre ve bir dönüş değeri bir Mesajlaşma stili işlemi var; diğer bir deyişle, doğrudan belirtilen bir SOAP ileti yapısına serileştirir. Bu ile işaretlenen herhangi bir tür olabilir <xref:System.ServiceModel.MessageContractAttribute> veya <xref:System.ServiceModel.Channels.Message> türü. Aşağıdaki kod örneği bir işlemi önceki RCP stil benzeyen gösterir, ancak ileti stili kullanır.  
  
 Örneğin, varsa `BankingTransaction` ve `BankingTransactionResponse` kod aşağıdaki işlemleri içinde geçerli ise, ileti sözleşmeleri, her iki türlerdir.  
  
```csharp  
[OperationContract]  
BankingTransactionResponse Process(BankingTransaction bt);  
[OperationContract]  
void Store(BankingTransaction bt);  
[OperationContract]  
BankingTransactionResponse GetResponse();  
```  
  
 Ancak, aşağıdaki kodu geçersiz.  
  
```csharp  
[OperationContract]  
bool Validate(BankingTransaction bt);  
// Invalid, the return type is not a message contract.  
[OperationContract]  
void Reconcile(BankingTransaction bt1, BankingTransaction bt2);  
// Invalid, there is more than one parameter.  
```  
  
 Bir özel durum, ileti anlaşması türü içerir ve bu geçerli desenlerden birini izlemez herhangi bir işlem için oluşturulur. Elbette, ileti anlaşması türleri içermeyen işlemler bu sınırlamalara tabi değildir.  
  
 Bir ileti anlaşması hem de bir veri anlaşması türü varsa, yalnızca ileti anlaşması türü bir işleminde kullanıldığında olarak kabul edilir.  
  
## <a name="defining-message-contracts"></a>İleti sözleşmeleri tanımlama  
 Bir tür için bir ileti anlaşması tanımlamak için (diğer bir deyişle, türü ve SOAP Zarfı arasındaki eşlemeyi tanımlamak için), uygulama <xref:System.ServiceModel.MessageContractAttribute> türü. Daha sonra uygulamanızı <xref:System.ServiceModel.MessageHeaderAttribute> SOAP başlıkları ve uygulamak istediğiniz türü bu üye için <xref:System.ServiceModel.MessageBodyMemberAttribute> iletinin SOAP gövdesi parçalara yapmak istediğiniz bu üyelere.  
  
 Aşağıdaki kod, bir ileti anlaşması kullanarak bir örnek sağlar.  
  
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
  
 Bu tür bir işlem parametresi olarak kullanırken, aşağıdaki SOAP Zarfı oluşturulur:  
  
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
  
 Dikkat `operation` ve `transactionDate` SOAP üst bilgi olarak görünür ve bir sarmalayıcı öğe SOAP gövdesi oluşur `BankingTransaction` içeren `sourceAccount`,`targetAccount`, ve `amount`.  
  
 Uygulayabileceğiniz <xref:System.ServiceModel.MessageHeaderAttribute> ve <xref:System.ServiceModel.MessageBodyMemberAttribute> için tüm alanlar, özellikler ve olaylar, genel, özel, korumalı veya iç olup olmadıkları ne olursa olsun.  
  
 <xref:System.ServiceModel.MessageContractAttribute> Kontrol SOAP ileti gövdesinde sarmalayıcı öğe adı WrapperName ve WrapperNamespace öznitelikler belirtmenizi sağlar. İleti sözleşmesi adını varsayılan olarak tür sarmalayıcı ve ileti anlaşması tanımlanır ad alanı için kullanılan `http://tempuri.org/` varsayılan ad alanı olarak kullanılır.  
  
> [!NOTE]
>  <xref:System.Runtime.Serialization.KnownTypeAttribute> ileti sözleşmeleri öznitelikleri yoksayılır. Varsa bir <xref:System.Runtime.Serialization.KnownTypeAttribute> olan gerekli, bunu, ileti anlaşması kullanarak işlemi söz konusu yerleştirin.  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a>Başlık ve gövde bölümü adlarına ve ad alanları denetleme  
 Bir ileti anlaşması SOAP gösterimini her başlık ve gövde bölümü bir ad ve bir ad alanı olan bir XML öğesi eşler.  
  
 Varsayılan olarak, ad alanı ileti katılan ve ad üye adı belirlenir hizmet sözleşmesi ad alanı ile aynı olduğu <xref:System.ServiceModel.MessageHeaderAttribute> veya <xref:System.ServiceModel.MessageBodyMemberAttribute> öznitelikler uygulanır.  
  
 Bu varsayılan işleyerek değiştirebileceğiniz <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> ve <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (üst sınıfı üzerinde <xref:System.ServiceModel.MessageHeaderAttribute> ve <xref:System.ServiceModel.MessageBodyMemberAttribute> öznitelikleri).  
  
 Aşağıdaki kod örneği sınıfında göz önünde bulundurun.  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader(Namespace="http://schemas.contoso.com/auditing/2005")] public bool IsAudited;  
  [MessageBodyMember(Name="transactionData")] public BankingTransactionData theData;  
}  
```  
  
 Bu örnekte, `IsAudited` başlığıdır kod ve gövde bölümünü temsil eden içinde belirtilen ad alanında `theData` üye bir XML öğesi adı ile temsil edilir `transactionData`. Bu ileti anlaşması için oluşturulan XML gösterir.  
  
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
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a>SOAP gövdesi bölümleri sarmalanmış olup olmadığını denetleme  
 Varsayılan olarak, SOAP gövdesi bölümleri içinde sarmalanmış bir öğe olarak serileştirilir. Örneğin, aşağıdaki kod gösterir `HelloGreetingMessage` adından oluşturulmuş sarmalayıcı öğe <xref:System.ServiceModel.MessageContractAttribute> için ileti anlaşması türü `HelloGreetingMessage` ileti.  
  
[!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
[!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 Sarmalayıcı öğe bastırmak için ayarlanmış <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> özelliğini `false`. Ad ve sarmalayıcı öğe ad alanı denetlemek için kullanın <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> ve <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> özellikleri.  
  
> [!NOTE]
>  Birden fazla ileti Gövde bölümünün değil sarmalanır iletilerinde sahip WS ile uyumlu değil-ı Basic Profile 1.1 ve yeni ileti sözleşmeleri tasarlarken önerilmez. Ancak, birden fazla sarmalanmış halden ileti Gövde bölümünün sahip belirli belirli birlikte çalışabilirlik senaryolarında gerekli olabilir. Birden fazla parça ileti gövdesinde veri iletmek için kullanacaksanız, varsayılan (sarmalanmış) modunu kullanmak için önerilir. Açılmamış iletiler içinde birden fazla ileti üst bilgisi sahip, tamamen kabul edilebilir.  
  
## <a name="using-custom-types-inside-message-contracts"></a>İleti sözleşmeleri içinde özel türleri kullanma  
 (XML olarak açık) her ayrı ileti üst bilgisi ve ileti Gövde bölümünün serileştirilmiş ileti kullanıldığı hizmet sözleşmesi için seçilen serileştirme motoruna kullanarak. Varsayılan serileştirme motoruna `XmlFormatter`, bir veri sözleşmesi ya da açıkça sahip herhangi bir türü işleyebilir (sahip <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) ya da örtük olarak (ilkel bir tür olan, sahip <xref:System.SerializableAttribute?displayProperty=nameWithType>, vb.). Daha fazla bilgi için [kullanarak veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Yukarıdaki örnekte, `Operation` ve `BankingTransactionData` türlerinin bir veri sözleşmesi olmalıdır ve `transactionDate` seri hale getirilemez çünkü <xref:System.DateTime> basit bir tür (ve bu nedenle bir örtük veri sözleşmesi).  
  
 Ancak, farklı bir seri hale getirme altyapısı için geçiş yapmak olası `XmlSerializer`. Böyle bir geçiş yaparsanız, tüm ileti üstbilgileri ve gövde bölümleri için kullanılan türleri seri hale getirilebilir kullanarak olduğundan emin olmalı `XmlSerializer`.  
  
## <a name="using-arrays-inside-message-contracts"></a>İleti sözleşmeleri içinde dizileri kullanma  
 İleti sözleşmeleri iki yolla öğelerinde yineleme dizileri kullanabilirsiniz.  
  
 İlk kullanmaktır bir <xref:System.ServiceModel.MessageHeaderAttribute> veya <xref:System.ServiceModel.MessageBodyMemberAttribute> dizi üzerinde doğrudan. Bu durumda, tüm dizi bir öğe (diğer bir deyişle, bir üst bilgi veya bir gövde bölümü) ile birden çok alt öğe olarak serileştirilir. Aşağıdaki örnekte sınıf göz önünde bulundurun.  
  
```csharp  
[MessageContract]  
public class BankingDepositLog  
{  
  [MessageHeader] public int numRecords;  
  [MessageHeader] public DepositRecord[] records;  
  [MessageHeader] public int branchID;  
}  
```  
  
 SOAP üstbilgileri bu sonuçlar aşağıdakine benzer.  
  
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
  
 Bu alternatif kullanmaktır <xref:System.ServiceModel.MessageHeaderArrayAttribute>. Bu durumda, her dizi öğesi bağımsız olarak serileştirilmiş ve her dizi öğesi bir üst bilgi, aşağıdakine benzer olduğundan.  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 Dizi girişleri için varsayılan adı üyesine adıdır <xref:System.ServiceModel.MessageHeaderArrayAttribute> öznitelikler uygulanır.  
  
 <xref:System.ServiceModel.MessageHeaderArrayAttribute> Özniteliğini devraldığı <xref:System.ServiceModel.MessageHeaderAttribute>. Dizi olmayan öznitelikleri aynı özellik kümesini vardır, örneğin sırada, adı ve üst bilgileri dizisi için ad alanı için tek bir başlık kümesi aynı şekilde ayarlamak mümkündür. Kullanırken `Order` bir dizi özelliği, tüm dizi için geçerlidir.  
  
 Uygulayabileceğiniz <xref:System.ServiceModel.MessageHeaderArrayAttribute> yalnızca diziler değil koleksiyonlar için.  
  
## <a name="using-byte-arrays-in-message-contracts"></a>İleti sözleşmeleri bayt dizileri kullanma  
 Bayt dizileri, dizi olmayan özniteliklerle kullanıldığında (<xref:System.ServiceModel.MessageBodyMemberAttribute> ve <xref:System.ServiceModel.MessageHeaderAttribute>), diziler olarak ancak Base64 kodlamalı veri elde edilen XML olarak temsil edilen özel bir basit tür olarak değerlendirilir.  
  
 Bayt dizileri dizi özniteliğiyle kullanırken <xref:System.ServiceModel.MessageHeaderArrayAttribute>, sonuçları kullanımda seri hale getirici bağlıdır. Varsayılan serileştirici ile tek bir giriş için her bir bayt dizisi gösterilir. Ancak, `XmlSerializer` seçildiğinde (kullanarak <xref:System.ServiceModel.XmlSerializerFormatAttribute> hizmet sözleşmesindeki), bayt dizileri dizisi veya dizi olmayan öznitelikler kullanılıp bağımsız olarak verileri Base64 olarak kabul edilir.  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a>İmzalama ve şifreleme ileti bölümlerini  
 Bir ileti anlaşması, üst bilgiler ve/veya iletinin gövdesi dijital olarak İmzalanabilir ve şifrelenebilir olup olmadığını gösterebilir.  
  
 Bu ayarı gerçekleştirilir <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> özelliği <xref:System.ServiceModel.MessageHeaderAttribute> ve <xref:System.ServiceModel.MessageBodyMemberAttribute> öznitelikleri. Sabit listesi özelliği <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> yazın ve ayarlanabilir <xref:System.Net.Security.ProtectionLevel.None> (şifreleme veya imza), <xref:System.Net.Security.ProtectionLevel.Sign> (dijital imzası yalnızca), veya <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (şifreleme ve dijital imza). Varsayılan, <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> değeridir.  
  
 Bu güvenlik özellikleri çalışacak şekilde bağlama ve davranışları düzgün bir şekilde yapılandırmanız gerekir. (Örneğin, bir ileti kimlik bilgilerinizi sağlamadan kapatmaya çalışırken) uygun bir yapılandırma olmadan bu güvenlik özellikleri kullanırsanız, doğrulamayı zamanında bir özel durum oluşturulur.  
  
 İleti üstbilgileri için koruma düzeyi, tek tek her üst bilgisi için belirlenir.  
  
 İleti gövdesi bölümleri için koruma düzeyi "minimum koruma düzeyi." zorlayıcı olabilir Gövde gövde parçalarının sayısı ne olursa olsun yalnızca bir koruma derecesine sahip. Koruma düzeyi gövdesinin en yüksek tarafından belirlenir <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> tüm gövde bölümlerini özelliğin ayarı. Ancak, her bir gövde kısmının koruma düzeyini düzeyi gereken gerçek en küçük koruma için ayarlamanız gerekir.  
  
 Aşağıdaki kod örneği sınıfında göz önünde bulundurun.  
  
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
  
 Bu örnekte, `recordID` üstbilgi korunmuyor, `patientName` olduğu `signed`, ve `SSN` imzalanır ve şifrelenmiş. En az bir gövde bölümü, `medicalHistory`, sahip <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> uygulanan ve bu nedenle tüm ileti gövdesi şifrelenir ve imzalanmış olsa da açıklamalar ve tanılama gövde parçalarının daha düşük koruma düzeyleri belirtin.  
  
## <a name="soap-action"></a>SOAP eylemi  
 SOAP ve ilgili Web hizmeti standartlarını adlı bir özellik tanımlayın `Action` , gönderilen her bir SOAP ileti mevcut olabilir. İşlemin <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> ve <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> denetim özelliklerini bu özelliğin değeri.  
  
## <a name="soap-header-attributes"></a>SOAP üstbilgisi öznitelikleri  
 SOAP standart bir üstbilgi varsa aşağıdaki öznitelikleri tanımlar:  
  
-   `Actor/Role` (`Actor` SOAP 1.1 `Role` SOAP 1.2)  
  
-   `MustUnderstand`  
  
-   `Relay`  
  
 `Actor` Veya `Role` öznitelik sağlanan üstbilgisi amaçlanmıştır düğümünün Tekdüzen Kaynak Tanımlayıcısı (URI) belirtir. `MustUnderstand` Özniteliği, üst bilgi işlem düğümü, anlamak olup olmadığını belirtir. `Relay` Özniteliği, aşağı akış düğümlerine geçirilmesine üstbilgi olup olmadığını belirtir. WCF gerçekleştirmez gelen iletiler bu özniteliklerin herhangi bir işleme dışında `MustUnderstand` özniteliği, bu konunun ilerleyen bölümlerindeki "İleti sözleşmesi sürümü oluşturma" bölümünde belirtildiği gibi. Ancak, bu öznitelik aşağıdaki açıklama olduğu gibi gerekli olarak okuyup sağlar.  
  
 Bir ileti gönderirken, varsayılan olarak bu öznitelikler yayılan değil. Bunu iki şekilde değiştirebilirsiniz. İlk olarak, statik olarak öznitelikleri için istenen tüm değerleri değiştirerek ayarlayabilir <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, ve <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> aşağıdaki kod örneğinde gösterildiği gibi özellikleri. (Unutmayın hiçbir `Role` özelliği; ayarı <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> özelliğini yayan `Role` SOAP 1.2 kullanıyorsanız özniteliği).  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 Bu öznitelikler denetlemek için ikinci yol dinamik olarak kodudur. Bu istenen üst bilgi türünde sarmalama tarafından elde <xref:System.ServiceModel.MessageHeader%601> türü (Bu tür genel olmayan sürümüne sahip karıştırmamaya dikkat edin) ve türü ile birlikte kullanarak <xref:System.ServiceModel.MessageHeaderAttribute>. Ardından özellikleri kullanabileceğinizi <xref:System.ServiceModel.MessageHeader%601> aşağıdaki kod örneğinde gösterildiği gibi SOAP öznitelikleri ayarlanamadı.  
  
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
  
 Hem dinamik ve statik denetimi düzenekleri kullanırsanız, statik ayarlarını varsayılan olarak kullanılır, ancak daha sonra dinamik mekanizmasını kullanarak aşağıdaki kodda gösterildiği gibi geçersiz kılınabilir.  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 Dinamik öznitelik denetimiyle yinelenen başlıkları oluşturma, aşağıdaki kodda gösterildiği gibi izin.  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 Alıcı tarafında bu SOAP öznitelikleri okuma yalnızca varsa yapılabilir <xref:System.ServiceModel.MessageHeader%601> sınıfı türü üst bilgisi için kullanılır. İnceleme `Actor`, `Relay`, veya `MustUnderstand` başlık özelliklerini <xref:System.ServiceModel.MessageHeader%601> alınan iletide öznitelik ayarlarını bulmak için yazın.  
  
 Bir ileti alındı ve geri gönderilen, SOAP özniteliği yalnızca üst bilgilerinin gidiş dönüş gidin <xref:System.ServiceModel.MessageHeader%601> türü.  
  
## <a name="order-of-soap-body-parts"></a>SOAP gövdesi bölümleri sırası  
 Bazı durumlarda, gövde bölümlerinin sırasını denetlemek için gerekebilir. Gövde öğelerin sırasını varsayılan olarak alfabetik kullanılır, ancak tarafından denetlenen <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> özelliği. Bu özellik ile aynı semantiklere sahip <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> devralma senaryolarda (ileti sözleşmeleri, temel tür gövdesi üyeler türetilmiş tür gövdesi üyeleri önce sıralanmamış) davranışı dışında bir özellik. Daha fazla bilgi için [veri üye sırası](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 Aşağıdaki örnekte, `amount` alfabetik olarak ilk olduğundan normal olarak ilk gelecektir. Ancak, <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> özelliği onu üçüncü konumuna koyar.  
  
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
  
## <a name="message-contract-versioning"></a>İleti sözleşmesi sürümü oluşturma  
 Zaman zaman ileti anlaşmaları değiştirmeniz gerekebilir. Örneğin, uygulamanızın yeni bir sürümünü iletiye ek bir üst bilgisi ekleyebilir. Ardından, yeni sürümünden eski gönderirken, sistem bir ek üst bilgisi, yanı sıra üst bilgisi eksik diğer yönde geçerken ilgilenmesi gerekir.  
  
 Sürüm üst bilgileri için aşağıdaki kurallar geçerlidir:  
  
-   WCF eksik üst nesne değildir — varsayılan değerlerine karşılık gelen üyeleri bırakılır.  
  
-   WCF da beklenmeyen fazladan üst bilgiler yok sayar. Ek üstbilgi varsa bu kuralın tek özel durum olan bir `MustUnderstand` özniteliğini `true` gelen SOAP iletisi — bu durumda, anlaşılması gereken bir üstbilgi işlenemediği için bir özel durum oluşturulur.  
  
 İleti gövdeleri benzer sürüm kurallara sahiptir — hem eksik hem de ek ileti gövdesi bölümü yok sayılır.  
  
## <a name="inheritance-considerations"></a>Devralma konuları  
 Temel türü bir ileti anlaşması de sahip olduğu sürece bir ileti anlaşması türü başka türden devralabilir.  
  
 Oluşturma veya diğer ileti anlaşması türlerinden devralan bir ileti anlaşması türü kullanarak ileti erişme, aşağıdaki kurallar geçerlidir:  
  
-   İleti üst bilgilerinde devralma hiyerarşisindeki tüm birlikte eksiksiz bir ileti üstbilgileri listesi oluşturmak için toplanır.  
  
-   İleti gövde bölümlerinin devralma hiyerarşisindeki tüm birlikte tam ileti gövdesi oluşturmak için toplanır. Gövde parçalarının normal sıralama kurallara göre sıralanır (tarafından <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> özelliği ve ardından alfabetik), bunun yerine Devralma Hiyerarşisi Hiçbir ilgisi olan. İleti gövdesi bölümleri birden çok devralma ağacını düzeylerinde nerede meydana ileti anlaşma devralma kullanarak kesinlikle önerilmez. Bir temel sınıf ve türetilen sınıf bir üst bilgi veya aynı ada sahip bir gövde bölümü tanımlarsanız, en temel sınıftan üye bu üst bilgi veya gövde bölümü değerini depolamak için kullanılır.  
  
 Aşağıdaki kod örneği sınıflarda göz önünde bulundurun.  
  
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
  
 `PatientRecord` Sınıfı olarak adlandırılan bir üstbilgiyle bir ileti açıklar `ID`. Üst bilgi karşılık gelen `personID` ve `patientID` üye, temel en üyesinin seçildiği için. Bu nedenle, `patientID` gereksiz bu durumda olan alan. İleti gövdesini içeren `diagnosis` öğesi tarafından izlenen `patientName` öğesi, çünkü, alfabetik olarak sıralayın. Örnek kesinlikle önerilmez bir desen gösterdiğine dikkat edin: hem temel hem de türetilmiş ileti sözleşmeleri, ileti gövdesi bölümden oluşur.  
  
## <a name="wsdl-considerations"></a>WSDL konuları  
 Web Hizmetleri Açıklama Dili (WSDL) sözleşmesi ileti sözleşmeleri kullanan bir hizmetten oluştururken, tüm ileti anlaşması özellikleri elde edilen WSDL içinde yansıtılır unutmamak önemlidir. Aşağıdaki noktaları göz önünde bulundurun:  
  
-   WSDL, üst bilgiler bir dizi kavramı hızlı olamaz. İleti üst bilgileri kullanarak bir dizi oluştururken <xref:System.ServiceModel.MessageHeaderArrayAttribute>, dizi yerine yalnızca bir üst bilgi elde edilen WSDL yansıtır.  
  
-   Sonuçta elde edilen WSDL belgesinde bazı koruma düzeyi bilgileri yansıtmaz.  
  
-   WSDL içinde oluşturulan ileti türü, ileti anlaşması türü sınıf adı ile aynı ada sahiptir.  
  
-   Birden çok ileti türü, aynı iletiyi kullanarak sözleşme, birden çok işlemlerinde, WSDL belgesinde üretilir. Sayı "2", "3" ekleyerek ve sonraki kullanımlar için vb. adları benzersiz yapılır. WSDL geri alırken, birden çok ileti anlaşması türleri oluşturulur ve bunların adları hariç olmak üzere aynıdır.  
  
## <a name="soap-encoding-considerations"></a>SOAP değerlendirmeleri kodlama  
 WCF eski SOAP XML stil kodlama kullanmanıza olanak tanır ancak kullanımı önerilmez. Bu stil kullanırken (ayarlayarak `Use` özelliğini `Encoded` üzerinde <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> hizmet sözleşmesi için uygulanan), ek aşağıdaki maddeler geçerlidir:  
  
-   İleti üstbilgilerini desteklenmez; Bu öznitelik anlamına <xref:System.ServiceModel.MessageHeaderAttribute> ve dizisi özniteliği <xref:System.ServiceModel.MessageHeaderArrayAttribute> SOAP kodlamasına ile uyumlu değildir.  
  
-   İleti sözleşmesi, diğer bir deyişle, sarmalanmamış ise özellik <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> ayarlanır `false`, ileti anlaşması yalnızca bir gövde bölümü olabilir.  
  
-   İstek ileti anlaşması için sarmalayıcı öğe adı, işlem adı eşleşmelidir. Kullanım `WrapperName` ileti anlaşması için bu özelliği.  
  
-   Yanıt ileti anlaşması için sarmalayıcı öğe adı, 'Response' tarafından ve sonra işlemin adıyla aynı olmalıdır. Kullanım <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> ileti anlaşması için bu özelliği.  
  
-   SOAP kodlamasına nesne başvuruları korur. Örneğin, aşağıdaki kodu düşünün.  
  
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
  
 İletinin SOAP kodlaması kullanarak seri hale getirme sonra `changedFrom` ve `changedTo` kendi kopyalarını içermeyen `p`, ancak bunun yerine iç kopyayı işaret `changedBy` öğesi.  
  
## <a name="performance-considerations"></a>Başarım Değerlendirmeleri  
 Her ileti üst bilgisi ve ileti Gövde bölümünün diğerlerinden bağımsız olarak seri hale getirilir. Bu nedenle, aynı ad alanları yeniden her başlık ve gövde bölümü için bildirilebilir. Özellikle Tel üzerinde ileti boyutu bakımından performansı artırmak için tek bir üst bilgi veya gövde bölümüne birden çok üstbilgi ve gövde parçalarının birleştirin. Örneğin, aşağıdaki kodu yerine:  
  
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
  
 Bu kodu kullanın.  
  
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
  
### <a name="event-based-asynchronous-and-message-contracts"></a>Olay tabanlı zaman uyumsuz ve ileti sözleşmeleri  
 Olay tabanlı zaman uyumsuz model için tasarım yönergeleri birden fazla değer döndürmüyorsa, bir değer olarak döndürülen durum `Result` özelliği ve diğerleri döndürülür özellikleri olarak üzerinde <xref:System.EventArgs> nesne. Bunun bir sonucu olduğundan, bu, bir istemci, olay tabanlı zaman uyumsuz komut seçeneklerini kullanarak meta verilerini içeri aktarır ve işlemin birden fazla değer, varsayılan döndürürse <xref:System.EventArgs> nesnesini bir değer olarak döndürür `Result` özelliği ve kalan özelliklerini <xref:System.EventArgs> nesne.  
  
 İleti nesnesi olarak almak istiyorsanız `Result` özelliği ve o nesnenin özellikleri olarak döndürülen değerlerin `/messageContract` seçeneği komutu. Bu yanıt iletisi olarak döndüren bir imza oluşturur `Result` özelliği <xref:System.EventArgs> nesne. Tüm iç dönüş değerleri ardından yanıt iletisi nesnenin özellikleridir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Anlaşmalarını Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Hizmetleri Tasarlama ve Uygulama](../../../../docs/framework/wcf/designing-and-implementing-services.md)
