---
title: İleti Sözleşmeleri Kullanılıyor
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message contracts [WCF]
ms.assetid: 1e19c64a-ae84-4c2f-9155-91c54a77c249
ms.openlocfilehash: 18d0ea97f1de40044d40fa85c9792c809fb73346
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959878"
---
# <a name="using-message-contracts"></a>İleti Sözleşmeleri Kullanılıyor
Genellikle Windows Communication Foundation (WCF) uygulamaları oluştururken, geliştiriciler veri yapılarına ve serileştirme sorunlarına yakın ilgi çekici bir şekilde ödeme yapar ve verilerin gerçekleştirildiği iletilerin yapısıyla ilgilenmenize gerek kalmaz. Bu uygulamalar için, parametreler veya dönüş değerleri için veri sözleşmeleri oluşturmak basittir. (Daha fazla bilgi için bkz. [hizmet sözleşmeleri içinde veri aktarımı belirtme](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).)  
  
 Ancak, bazen bir SOAP iletisinin yapısına ilişkin denetim, içeriğinin üzerinde denetim kadar önemli olur. Bu özellikle, birlikte çalışabilirlik önemli olduğunda veya ileti veya ileti parçası düzeyinde güvenlik sorunlarını özellikle denetlemek için geçerlidir. Bu durumlarda, gereken kesin SOAP iletisinin yapısını belirtmenizi sağlayan bir *ileti sözleşmesi* oluşturabilirsiniz.  
  
 Bu konuda, işlem için belirli bir ileti sözleşmesi oluşturmak üzere çeşitli ileti sözleşmesi özniteliklerinin nasıl kullanılacağı ele alınmaktadır.  
  
## <a name="using-message-contracts-in-operations"></a>Işlemlerde Ileti sözleşmeleri kullanma  
 WCF, *uzak yordam çağrısı (RPC) stili* veya *mesajlaşma stili*üzerinde modellenen işlemleri destekler. Bir RPC stili işleminde, herhangi bir serileştirilebilir türü kullanabilir ve birden çok parametre ve `ref` `out` parametre gibi yerel çağrılar için kullanılabilen özelliklere erişebilirsiniz. Bu stilde, seçilen serileştirme formu, temel iletilerdeki verilerin yapısını denetler ve WCF çalışma zamanı, işlemi destekleyecek iletileri oluşturur. Bu, SOAP ve SOAP iletileri hakkında bilgi sahibi olmayan geliştiricilerin, hizmet uygulamalarını hızla ve kolayca oluşturup kullanmasını sağlar.  
  
 Aşağıdaki kod örneğinde, RPC stilinde modellenen bir hizmet işlemi gösterilmektedir.  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 Normalde, bir veri sözleşmesi, iletilerin şemasını tanımlamak için yeterlidir. Örneğin, önceki örnekte, çoğu uygulama `BankingTransaction` için yeterlidir ve `BankingTransactionResponse` temel alınan SOAP iletilerinin içeriğini tanımlamak için veri sözleşmeleri vardır. Veri sözleşmeleri hakkında daha fazla bilgi için bkz. [Veri Sözleşmelerini Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Ancak, bazen SOAP iletisinin yapısının hat üzerinden nasıl iletildiğini tam olarak denetlemek gereklidir. Bunun için en yaygın senaryo özel SOAP üstbilgileri ekliyor. Diğer bir yaygın senaryo, bu öğelerin dijital olarak imzalanıp imzalanmadığını ve şifrelenmeyeceğine karar vermek için ileti üst bilgileri ve gövdesi için güvenlik özellikleri tanımlamaktır. Son olarak, bazı üçüncü taraf SOAP yığınları, iletilerin belirli bir biçimde olmasını gerektirir. Mesajlaşma stili işlemler bu denetimi sağlar.  
  
 Mesajlaşma stili bir işlem, en fazla bir parametreye ve her iki türün de ileti türü olduğu bir dönüş değerine sahiptir; diğer bir deyişle, doğrudan belirtilen bir SOAP ileti yapısına serileştirilir. Bu, <xref:System.ServiceModel.MessageContractAttribute> <xref:System.ServiceModel.Channels.Message> ya da türü ile işaretlenmiş herhangi bir tür olabilir. Aşağıdaki kod örneği, önceki RCP stili gibi bir işlemi gösterir, ancak mesajlaşma stilini kullanır.  
  
 Örneğin, `BankingTransaction` ve `BankingTransactionResponse` her iki tür de ileti sözleşmelerinde, aşağıdaki işlemlerdeki kod geçerli olur.  
  
```csharp  
[OperationContract]  
BankingTransactionResponse Process(BankingTransaction bt);  
[OperationContract]  
void Store(BankingTransaction bt);  
[OperationContract]  
BankingTransactionResponse GetResponse();  
```  
  
 Ancak, aşağıdaki kod geçersiz.  
  
```csharp  
[OperationContract]  
bool Validate(BankingTransaction bt);  
// Invalid, the return type is not a message contract.  
[OperationContract]  
void Reconcile(BankingTransaction bt1, BankingTransaction bt2);  
// Invalid, there is more than one parameter.  
```  
  
 İleti sözleşmesi türünü içeren ve geçerli desenlerden birini takip eden tüm işlemler için bir özel durum oluşturulur. Kuşkusuz, ileti anlaşması türleri içermeyen işlemler bu kısıtlamalara tabi değildir.  
  
 Bir tür hem bir ileti sözleşmesine hem de bir veri sözleşmesine sahipse, tür bir işlemde kullanıldığında yalnızca ileti anlaşması kabul edilir.  
  
## <a name="defining-message-contracts"></a>Ileti sözleşmelerini tanımlama  
 Bir tür için bir ileti sözleşmesi tanımlamak (yani, türü ve bir soap Zarfı arasındaki eşlemeyi tanımlamak için), türünü türüne uygulayın <xref:System.ServiceModel.MessageContractAttribute> . Ardından öğesini SOAP <xref:System.ServiceModel.MessageHeaderAttribute> üst bilgilerinde yapmak istediğiniz türdeki üyelere uygulayın ve ' ı iletinin SOAP gövdesinin bölümlerinde yapmak istediğiniz üyelere <xref:System.ServiceModel.MessageBodyMemberAttribute> uygulayın.  
  
 Aşağıdaki kod, bir ileti sözleşmesinin kullanılmasına bir örnek sağlar.  
  
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
  
 Bu tür bir işlem parametresi olarak kullanıldığında, aşağıdaki SOAP Zarfı oluşturulur:  
  
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
  
 `BankingTransaction` `sourceAccount` `amount``targetAccount`Bunun ve SOAP üst bilgisi olarak göründüğünüveSOAPgövdesinin,,veiçerenbirsarmalayıcıöğesindenoluştuğunugörürsünüz.`transactionDate` `operation`  
  
 Genel, özel, <xref:System.ServiceModel.MessageHeaderAttribute> korumalı <xref:System.ServiceModel.MessageBodyMemberAttribute> veya dahili olsun etmeksizin bağımsız olarak, ve tüm alanları, özellikleri ve olayları uygulayabilirsiniz.  
  
 , <xref:System.ServiceModel.MessageContractAttribute> Soap iletisinin gövdesinde sarmalayıcı öğenin adını denetleyen WrapperName ve WrapperNamespace özniteliklerini belirtmenize olanak tanır. Varsayılan olarak, ileti anlaşması türünün adı sarmalayıcı için kullanılır ve ileti sözleşmesinin tanımlandığı `http://tempuri.org/` ad alanı varsayılan ad alanı olarak kullanılır.  
  
> [!NOTE]
> <xref:System.Runtime.Serialization.KnownTypeAttribute>ileti sözleşmelerinde öznitelikler yok sayılır. Bir <xref:System.Runtime.Serialization.KnownTypeAttribute> gerekliyse, söz konusu iletiyi söz konusu ileti sözleşmesinin kullanıldığı işleme yerleştirin.  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a>Üst bilgi ve gövde bölüm adlarını ve ad alanlarını denetleme  
 Bir ileti sözleşmesinin SOAP gösteriminde, her başlık ve gövde bölümü, adı ve ad alanı olan bir XML öğesiyle eşlenir.  
  
 Varsayılan olarak, ad alanı, iletinin katıldığı hizmet sözleşmesinin ad alanıyla aynıdır ve ad, <xref:System.ServiceModel.MessageHeaderAttribute> <xref:System.ServiceModel.MessageBodyMemberAttribute> veya özniteliklerinin uygulandığı üye adına göre belirlenir.  
  
 <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> <xref:System.ServiceModel.MessageHeaderAttribute> Ve değerlerini(<xref:System.ServiceModel.MessageBodyMemberAttribute> ve özniteliklerinin üst sınıfında) işleyerek bu varsayılanları değiştirebilirsiniz. <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType>  
  
 Aşağıdaki kod örneğinde sınıfını göz önünde bulundurun.  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader(Namespace="http://schemas.contoso.com/auditing/2005")] public bool IsAudited;  
  [MessageBodyMember(Name="transactionData")] public BankingTransactionData theData;  
}  
```  
  
 Bu örnekte, `IsAudited` üst bilgi kodda belirtilen ad alanıdır ve `theData` üyeyi temsil eden gövde bölümü, adında `transactionData`bir XML öğesiyle temsil edilir. Aşağıda bu ileti sözleşmesi için oluşturulan XML gösterilmektedir.  
  
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
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a>SOAP gövdesi bölümlerinin sarmalanmış olup olmadığını denetleme  
 Varsayılan olarak, SOAP gövdesi parçaları sarmalanmış bir öğe içinde serileştirilir. Örneğin, aşağıdaki kod, `HelloGreetingMessage` `HelloGreetingMessage` ileti için ileti sözleşmesindeki <xref:System.ServiceModel.MessageContractAttribute> tür adından oluşturulan sarmalayıcı öğesini gösterir.  
  
[!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
[!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 Sarmalayıcı öğesini gizlemek için <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> özelliğini olarak `false`ayarlayın. Sarmalayıcı öğesinin adını ve ad alanını denetlemek için <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> ve <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> özelliklerini kullanın.  
  
> [!NOTE]
> Sarmalanmamış iletilerde birden fazla ileti gövdesinin parçası olan WS-ı temel profili 1,1 ile uyumlu değil ve yeni ileti sözleşmeleri tasarlarken önerilmez. Ancak, belirli bir birlikte çalışabilirlik senaryolarında birden fazla sarmalanmamış ileti gövdesinin parçası olması gerekebilir. Bir ileti gövdesinde birden fazla veri parçası iletileyecekseniz, varsayılan (sarmalanmış) modunun kullanılması önerilir. Sarmalanmamış iletilerde birden fazla ileti üstbilgisinin bulunması tamamen kabul edilebilir.  
  
## <a name="using-custom-types-inside-message-contracts"></a>Ileti sözleşmeleri Içinde özel türler kullanma  
 Her bir ileti üst bilgisi ve ileti gövdesi bölümü, iletinin kullanıldığı hizmet sözleşmesi için seçilen serileştirme altyapısını kullanarak serileştirilir (XML 'e açıktır). Varsayılan serileştirme altyapısı `XmlFormatter`olan, açıkça ( <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>sahip olunarak) veya örtük olarak ( <xref:System.SerializableAttribute?displayProperty=nameWithType>temel bir tür, vb.) bir veri sözleşmesine sahip herhangi bir türü işleyebilir. Daha fazla bilgi için bkz. [Veri Sözleşmelerini Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Yukarıdaki örnekte `Operation` , ve `BankingTransactionData` türleri bir veri sözleşmesine sahip olmalı ve `transactionDate` <xref:System.DateTime> bir ilkel olduğundan (ve bu nedenle örtük bir veri sözleşmesine sahiptir).  
  
 Ancak, farklı bir serileştirme altyapısına `XmlSerializer`geçiş yapmak mümkündür. Böyle bir anahtar yaparsanız, ileti üstbilgileri ve gövde parçaları için kullanılan tüm türlerin, `XmlSerializer`kullanılarak serileştirilebilir olduğundan emin olmanız gerekir.  
  
## <a name="using-arrays-inside-message-contracts"></a>Ileti sözleşmeleri Içinde dizileri kullanma  
 İleti sözleşmelerinde yinelenen öğe dizilerini iki şekilde kullanabilirsiniz.  
  
 Birincisi, doğrudan dizide bir <xref:System.ServiceModel.MessageHeaderAttribute> veya bir <xref:System.ServiceModel.MessageBodyMemberAttribute> kullanmaktır. Bu durumda, tüm dizi birden çok alt öğe içeren tek bir öğe (yani, bir üst bilgi veya bir gövde bölümü) olarak serileştirilir. Aşağıdaki örnekte sınıfını göz önünde bulundurun.  
  
```csharp  
[MessageContract]  
public class BankingDepositLog  
{  
  [MessageHeader] public int numRecords;  
  [MessageHeader] public DepositRecord[] records;  
  [MessageHeader] public int branchID;  
}  
```  
  
 Bu, SOAP üst bilgilerinin sonucu aşağıdakine benzer.  
  
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
  
 Bunun bir alternatifi, <xref:System.ServiceModel.MessageHeaderArrayAttribute>kullanmaktır. Bu durumda, her dizi öğesi bağımsız olarak serileştirilir ve böylece her dizi öğesinin aşağıdakine benzer bir üst bilgi vardır.  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 Dizi girdilerinin varsayılan adı, <xref:System.ServiceModel.MessageHeaderArrayAttribute> özniteliklerin uygulandığı üyenin adıdır.  
  
 <xref:System.ServiceModel.MessageHeaderArrayAttribute> Özniteliği öğesinden<xref:System.ServiceModel.MessageHeaderAttribute>devralır. Dizi olmayan özniteliklerle aynı özellik kümesine sahiptir, örneğin, bir üst bilgi dizisinin sıra, ad ve ad alanını tek bir üstbilgi için ayarladığınız şekilde ayarlamak mümkündür. `Order` Özelliğini bir dizide kullandığınızda, bu, tüm dizi için geçerlidir.  
  
 Koleksiyonları değil, <xref:System.ServiceModel.MessageHeaderArrayAttribute> yalnızca dizilere uygulayabilirsiniz.  
  
## <a name="using-byte-arrays-in-message-contracts"></a>Ileti sözleşmelerinde Byte dizilerini kullanma  
 Dizi olmayan özniteliklerle (<xref:System.ServiceModel.MessageBodyMemberAttribute> ve <xref:System.ServiceModel.MessageHeaderAttribute>) birlikte kullanıldığında bayt dizileri diziler olarak değerlendirilmez, ancak sonuçta elde edilen XML 'de Base64 kodlamalı veriler olarak temsil edilen özel bir ilkel tür olarak kabul edilmez.  
  
 Dizi özniteliğiyle <xref:System.ServiceModel.MessageHeaderArrayAttribute>byte dizileri kullandığınızda, sonuçlar kullanımdaki seri hale getiriciye göre değişir. Varsayılan serileştirici ile, dizi her bir bayt için tek bir girdi olarak gösterilir. Ancak, seçildiğinde (hizmet sözleşmesinde öğesini <xref:System.ServiceModel.XmlSerializerFormatAttribute> kullanarak), dizi veya dizi olmayan özniteliklerin kullanılıp kullanılmadığına bakılmaksızın bayt dizileri Base64 verileri olarak değerlendirilir. `XmlSerializer`  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a>Ileti parçalarını imzalama ve şifreleme  
 İleti anlaşması, ileti başlıklarının ve/veya gövdesinin dijital olarak imzalanıp imzalanmayacağını ve şifrelenmeyeceğini belirtebilir.  
  
 Bu, <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> <xref:System.ServiceModel.MessageHeaderAttribute> ve özniteliklerindeözelliğiayarlanarakyapılır.<xref:System.ServiceModel.MessageBodyMemberAttribute> Özelliği, <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> türün bir numaralandırmadır ve (şifreleme veya imza yok) <xref:System.Net.Security.ProtectionLevel.None> , <xref:System.Net.Security.ProtectionLevel.Sign> (yalnızca dijital imza) veya <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (hem şifreleme hem de dijital imza) olarak ayarlanabilir. Varsayılan, <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> değeridir.  
  
 Bu güvenlik özelliklerinin çalışması için bağlama ve davranışları doğru şekilde yapılandırmanız gerekir. Bu güvenlik özelliklerini uygun yapılandırma olmadan (örneğin, kimlik bilgilerinizi vermeden bir iletiyi imzalamaya çalışırken) kullanırsanız, doğrulama zamanında bir özel durum oluşturulur.  
  
 İleti üstbilgileri için, her üst bilgi için koruma düzeyi ayrı ayrı belirlenir.  
  
 İleti gövdesi parçaları için, koruma düzeyi "En düşük koruma düzeyi" olarak düşünülebilir. Gövde, gövde bölümlerinin sayısından bağımsız olarak yalnızca bir koruma düzeyine sahiptir. Gövdenin koruma düzeyi, tüm gövde bölümlerinin en yüksek <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> özellik ayarına göre belirlenir. Ancak, her gövde bölümünün koruma düzeyini gereken gerçek en düşük koruma düzeyine ayarlamanız gerekir.  
  
 Aşağıdaki kod örneğinde sınıfını göz önünde bulundurun.  
  
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
  
 Bu örnekte, `recordID` üst bilgi `signed`korunmaz, `patientName` ,, ve `SSN` şifrelenir ve imzalanır. En az bir gövde bölümü `medicalHistory` <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> , ve bu nedenle, açıklamalar ve tanılama gövdesi parçaları alt koruma düzeylerini belirtse bile, tüm ileti gövdesinin şifrelenmesi ve imzalanması gerekir.  
  
## <a name="soap-action"></a>SOAP eylemi  
 Soap ve ilgili Web Hizmetleri standartları, gönderilen her SOAP `Action` iletisi için mevcut olabilecek adlı bir özelliği tanımlar. İşlemin <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> ve<xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> özellikleri bu özelliğin değerini denetler.  
  
## <a name="soap-header-attributes"></a>SOAP üst bilgisi öznitelikleri  
 SOAP standardı, bir üst bilgide mevcut olabilecek aşağıdaki öznitelikleri tanımlar:  
  
- `Actor/Role`(`Actor` SOAP 1,1 ' de `Role` , soap 1,2 ' de)  
  
- `MustUnderstand`  
  
- `Relay`  
  
 `Actor` Or`Role` özniteliği, belirli bir üst bilginin istendiği düğümün Tekdüzen Kaynak tanımlayıcısını (URI) belirtir. `MustUnderstand` Öznitelik, üstbilgiyi işleyen düğümün onu anlaması gerekip gerekmediğini belirtir. `Relay` Öznitelik, üstbilginin aşağı akış düğümlerine geçirilip geçirilmeyeceğini belirtir. WCF, bu konunun ilerleyen kısımlarında yer alan "ileti sözleşmesi sürümü oluşturma" bölümünde belirtildiği `MustUnderstand` gibi, bu özniteliklerin, öznitelik hariç, bu özniteliklerin herhangi bir işlemesini gerçekleştirmez. Ancak, aşağıdaki açıklamada olduğu gibi bu öznitelikleri gerektiği gibi okuyup yazmanızı sağlar.  
  
 İleti gönderilirken, bu öznitelikler varsayılan olarak yayılmaz. Bunu iki şekilde değiştirebilirsiniz. İlk olarak <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, aşağıdaki kod örneğinde gösterildiği gibi,, ve <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> özelliklerini değiştirerek, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>öznitelikleri istediğiniz herhangi bir değere statik olarak ayarlayabilirsiniz. ( `Role` Özellik olmadığını unutmayın; SOAP 1,2 kullanıyorsanız, <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> özelliğin bu `Role` özniteliği yayar olarak ayarlanması).  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 Bu öznitelikleri denetlemek için ikinci yöntem kod aracılığıyla dinamik olarak gerçekleştirilir. Bunu, <xref:System.ServiceModel.MessageHeader%601> <xref:System.ServiceModel.MessageHeaderAttribute>istenen üst bilgi türünü (genel olmayan sürüm ile karıştırmayı unutmayın) ve türünü ile birlikte kullanarak elde edebilirsiniz. Ardından, aşağıdaki kod örneğinde gösterildiği gibi SOAP <xref:System.ServiceModel.MessageHeader%601> özniteliklerini ayarlamak için üzerinde özellikleri kullanabilirsiniz.  
  
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
  
 Hem dinamik hem de statik denetim mekanizmalarını kullanırsanız, statik ayarlar varsayılan olarak kullanılır, ancak daha sonra aşağıdaki kodda gösterildiği gibi dinamik mekanizma kullanılarak geçersiz kılınabilir.  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 Aşağıdaki kodda gösterildiği gibi, dinamik öznitelik denetimiyle yinelenen üst bilgilerin oluşturulmasına izin verilir.  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 Alma tarafında, bu soap özniteliklerini okumak yalnızca, türündeki üst bilgi için <xref:System.ServiceModel.MessageHeader%601> sınıf kullanılıyorsa yapılabilir. Alınan iletideki öznitelik `Relay`ayarlarını saptamak `MustUnderstand` için <xref:System.ServiceModel.MessageHeader%601> türün bir üst bilgisinin ,veyaözellikleriniinceleyin.`Actor`  
  
 Bir ileti alındığında ve sonra geri gönderildiğinde, soap öznitelik ayarları yalnızca <xref:System.ServiceModel.MessageHeader%601> türün üst bilgileri için gidiş dönüş ' ı gider.  
  
## <a name="order-of-soap-body-parts"></a>SOAP gövdesi bölümlerinin sırası  
 Bazı durumlarda, gövde bölümlerinin sırasını kontrol etmeniz gerekebilir. Gövde öğelerinin sırası varsayılan olarak alfabetik şekilde belirlenir, ancak <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> özelliği tarafından denetlenebilir. Bu özellik, devralma senaryolarındaki davranış dışında <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> , özelliği ile aynı semantiğe sahiptir (ileti sözleşmelerinde, temel tür gövde üyeleri türetilmiş tür gövde üyelerinden önce sıralanmaz). Daha fazla bilgi için bkz. [veri üye sıralaması](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 Aşağıdaki örnekte, `amount` normal olarak ilk alfabetik olduğu için ilk olarak gelir. Ancak, <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> özelliği üçüncü konuma koyar.  
  
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
 Bazen ileti sözleşmelerini değiştirmeniz gerekebilir. Örneğin, uygulamanızın yeni bir sürümü bir iletiye ek bir üst bilgi ekleyebilir. Daha sonra, yeni sürümden eski sürümüne gönderirken sistemin ek bir üst bilgiyle ve diğer yönde gitirken eksik bir üst bilgi ile uğraşmanız gerekir.  
  
 Sürüm oluşturma üstbilgileri için aşağıdaki kurallar geçerlidir:  
  
- WCF eksik üstbilgilere nesne yapmaz — ilgili Üyeler varsayılan değerlerinde bırakılır.  
  
- WCF Ayrıca beklenmeyen Ek üstbilgileri yoksayar. Bu kuralın tek istisnası, ek üstbilginin gelen SOAP iletisinde olarak ayarlanmış bir `MustUnderstand` özniteliği varsa — `true` bu durumda, anlaşılması gereken bir üst bilgi işlenemediği için bir özel durum oluşturulur.  
  
 İleti gövdelerinin benzer sürüm kuralları vardır — hem eksik hem de ek ileti gövdesi parçaları yok sayılır.  
  
## <a name="inheritance-considerations"></a>Devralma konuları  
 Temel türün da bir ileti anlaşması olduğu sürece, bir ileti sözleşmesi türü başka bir türden devralınabilir.  
  
 Diğer ileti anlaşması türlerinden devralan bir ileti sözleşmesi türü kullanarak bir ileti oluştururken veya erişirken, aşağıdaki kurallar geçerlidir:  
  
- Devralma hiyerarşisindeki tüm ileti üstbilgileri, ileti için tüm üst bilgi kümesini oluşturmak üzere birlikte toplanır.  
  
- Devralma hiyerarşisindeki tüm ileti gövdesi parçaları, tam ileti gövdesini oluşturmak için birlikte toplanır. Gövde parçaları, devralma hiyerarşisinde yer almayla ilgili hiçbir ilgisi olmadan olağan sıralama <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> kurallarına (özelliğe göre ve ardından alfabetik olarak) göre sıralanır. İleti metni parçalarının devralma ağacının birden çok düzeyinde gerçekleştiği ileti sözleşmesi devralımı kullanılması önerilmez. Bir temel sınıf ve türetilmiş bir sınıf, aynı ada sahip bir üst bilgi veya gövde parçasını tanımladıysanız, temel sınıfın üyesi bu üst bilgi veya gövde bölümünün değerini depolamak için kullanılır.  
  
 Aşağıdaki kod örneğinde bulunan sınıfları göz önünde bulundurun.  
  
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
  
 Sınıfı `PatientRecord` , bir üst bilgiyle çağrılan `ID`bir ileti tanımlar. Üst düzey üye seçildiği için `personID` üst bilgi `patientID` üyeye değil öğesine karşılık gelir. Bu nedenle, `patientID` bu durumda alan gereksizdir. İletinin gövdesi, bu `diagnosis` öğenin alfabetik sırası olduğu için öğesi `patientName` tarafından izlenen öğesi içerir. Örnekte kesinlikle önerilmez: hem temel hem de türetilmiş ileti sözleşmelerinin ileti gövdesi parçaları vardır.  
  
## <a name="wsdl-considerations"></a>WSDL konuları  
 İleti sözleşmeleri kullanan bir hizmetten bir Web Hizmetleri Açıklama Dili (WSDL) Sözleşmesi oluştururken, tüm ileti sözleşmesi özelliklerinin sonuçta elde edilen WSDL 'de yansıtıldığını unutmamak önemlidir. Aşağıdaki noktaları göz önünde bulundurun:  
  
- WSDL, bir üst bilgi dizisi kavramını ifade edemez. Kullanılarak bir üst bilgi dizisiyle ileti oluştururken <xref:System.ServiceModel.MessageHeaderArrayAttribute>, sonuçta elde edilen WSDL dizi yerine yalnızca bir üst bilgi yansıtır.  
  
- Elde edilen WSDL belgesi, bazı koruma düzeyi bilgileri yansıtmayabilir.  
  
- WSDL içinde oluşturulan ileti türü, ileti sözleşmesi türünün sınıf adı ile aynı ada sahiptir.  
  
- Birden çok işlemde aynı ileti sözleşmesini kullanırken, WSDL belgesinde birden çok ileti türü oluşturulur. Adlar, sonraki kullanımlar için "2", "3" ve benzeri sayılar eklenerek benzersiz hale getirilir. WSDL geri alınırken, birden çok ileti sözleşme türü oluşturulur ve adları dışında aynıdır.  
  
## <a name="soap-encoding-considerations"></a>SOAP kodlama konuları  
 WCF, XML 'nin eski SOAP kodlama stilini kullanmanıza olanak tanır, ancak kullanımı önerilmez. Bu stil kullanılırken ( `Use` `Encoded` özelliğini <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> hizmet sözleşmesine uygulanan olarak ayarlayarak) aşağıdaki ek konular geçerlidir:  
  
- İleti üstbilgileri desteklenmez; Bu, özniteliği <xref:System.ServiceModel.MessageHeaderAttribute> ve dizi özniteliğinin <xref:System.ServiceModel.MessageHeaderArrayAttribute> SOAP kodlamasıyla uyumsuz olduğu anlamına gelir.  
  
- İleti anlaşması sarmalanmamış ise, bu, özelliği <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> olarak `false`ayarlandıysa, ileti sözleşmesinin yalnızca bir gövde bölümü olabilir.  
  
- İstek iletisi sözleşmesinin sarmalayıcı öğesinin adı işlem adıyla eşleşmelidir. Bunun için ileti sözleşmesinin özelliğinikullanın.`WrapperName`  
  
- Yanıt iletisi sözleşmesinin sarmalayıcı öğesinin adı, ' Response ' ile düzeltilen işlem soneki adı ile aynı olmalıdır. Bunun için ileti sözleşmesinin özelliğinikullanın.<xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A>  
  
- SOAP Encoding nesne başvurularını korur. Örneğin, aşağıdaki kodu göz önünde bulundurun.  
  
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
  
 SOAP kodlaması `changedFrom` kullanarak iletiyi serileştirdikten ve `changedTo` kendi kopyalarını `p`içermediğinden, bunun yerine `changedBy` öğesinin içindeki kopyaya gelin.  
  
## <a name="performance-considerations"></a>Başarım Değerlendirmeleri  
 Her ileti üst bilgisi ve ileti gövdesi bölümü diğerlerinden bağımsız olarak serileştirilir. Bu nedenle, her başlık ve gövde bölümü için aynı ad alanları yeniden bildirilemez. Performansı artırmak için, özellikle de iletişimdeki iletinin boyutu açısından birden çok üstbilgiyi ve gövde parçalarını tek bir üstbilgi veya gövde bölümünde birleştirin. Örneğin, aşağıdaki kod yerine:  
  
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
  
### <a name="event-based-asynchronous-and-message-contracts"></a>Olay tabanlı zaman uyumsuz ve Ileti sözleşmeleri  
 Olay tabanlı zaman uyumsuz model için, birden fazla değer döndürülürse, `Result` özellik olarak bir değer döndürülür ve diğerleri <xref:System.EventArgs> nesne üzerinde özellikler olarak döndürülür. Bunun sonucunda, bir istemci, olay tabanlı zaman uyumsuz komut seçeneklerini kullanarak meta verileri içeri aktardığında ve işlem birden fazla değer döndürürse, varsayılan <xref:System.EventArgs> nesne `Result` özellik olarak bir değer döndürür ve geri kalanı <xref:System.EventArgs> nesnenin özellikleri.  
  
 İleti nesnesini `Result` özellik olarak almak ve döndürülen değerlerin bu nesnede özellikler olarak elde etmek istiyorsanız, `/messageContract` komut seçeneğini kullanın. Bu, `Result` <xref:System.EventArgs> nesne üzerindeki özelliği olarak yanıt iletisini döndüren bir imza oluşturur. Tüm iç dönüş değerleri, yanıt iletisi nesnesinin özellikleridir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Anlaşmalarını Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Hizmetleri Tasarlama ve Uygulama](../../../../docs/framework/wcf/designing-and-implementing-services.md)
