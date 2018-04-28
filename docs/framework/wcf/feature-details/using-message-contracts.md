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
ms.openlocfilehash: e9f6d0e9d64c510b47b0697d02178f1c0a95f61b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="using-message-contracts"></a>İleti Sözleşmeleri Kullanılıyor
Genellikle oluştururken [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uygulamaları, geliştiricilerin serileştirme sorunları ve veri yapıları Kapat dikkat ve kendilerini içinde veri yazımının iletileri yapısıyla ilgilendiren gerekmez. Bu uygulamalar için parametreleri veya dönüş değerleri için veri sözleşmeleri oluşturma basittir. (Daha fazla bilgi için bkz: [hizmet sözleşmelerinde veri aktarımı belirtme](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).)  
  
 Ancak, bir SOAP iletisi yapısını bazen tam kontrole yalnızca, içeriğini üzerinde denetim olarak önem taşır. Birlikte çalışabilirlik önemli veya özellikle güvenlik denetlemek için ileti veya ileti bölümü düzeyinde sorunları olduğunda özellikle geçerlidir. Bu durumlarda, oluşturduğunuz bir *ileti sözleşmesi* gerekli kesin SOAP iletisi yapısını belirtmenize olanak sağlar.  
  
 Bu konu çeşitli ileti sözleşmesi öznitelikleri belirli ileti sözleşmesi işleminiz oluşturmak için nasıl kullanıldığını açıklar.  
  
## <a name="using-message-contracts-in-operations"></a>İleti sözleşmeleri işlemlerinde kullanma  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hakkında ya da Modellenen işlemlerini destekleyen *uzak yordam çağrısı (RPC) stili* veya *stili Mesajlaşma*. Bir RPC-style işleminde serializable bir tür kullanabilirsiniz ve birden çok parametre gibi yerel aramalar için kullanılabilen özellikleri erişimi ve `ref` ve `out` parametreleri. Bu stilde seçilen serileştirme form temel alınan iletilerde verilerin yapısını denetler ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çalışma zamanı işlemi desteklemek için iletileri oluşturur. Bu, SOAP ile tanıdık olmayan ve iletileri kolayca SOAP ve kolayca oluşturup hizmet uygulamaları kullanın geliştiriciler sağlar.  
  
 Aşağıdaki kod örneğinde RPC stilini Modellenen bir hizmet işlemi gösterilmektedir.  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 Normalde, bir veri sözleşmesi şema iletileri tanımlamak yeterlidir. Örneğin, önceki örnekte, çoğu uygulama için yeterli değilse `BankingTransaction` ve `BankingTransactionResponse` temel alınan SOAP iletilerine içeriğini tanımlamak için veri sözleşmeleri sahip. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Veri sözleşmeleri bkz [kullanarak veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Ancak, bazen onu tam olarak nasıl SOAP iletisi yapısını kablo üzerinden aktarılan denetlemek gereklidir. Bunun en yaygın senaryo özel SOAP üstbilgileri ekleniyor. Başka bir yaygın senaryodur güvenlik özelliklerini ileti üstbilgi ve gövde, yani tanımlamak için bu öğeler dijital olarak imzalanmış ve şifrelenmiş olup olmadığını karar vermek için. Son olarak, bazı üçüncü taraf SOAP yığınları iletileri gerektiren belirli bir biçimde olabilir. Mesajlaşma stili operations bu denetim sağlar.  
  
 Bir ileti stili işlemi, her iki tür ileti türlerini nerede en fazla bir parametre ve dönüş değerini sahiptir; diğer bir deyişle, doğrudan belirtilen bir SOAP iletisi yapısına serileştirir. Bu ile işaretlenen herhangi bir tür olabilir <xref:System.ServiceModel.MessageContractAttribute> veya <xref:System.ServiceModel.Channels.Message> türü. Aşağıdaki kod örneğinde bir işlem benzer şekilde önceki RCP stili gösterir ancak Mesajlaşma stili kullanır.  
  
 Örneğin, varsa `BankingTransaction` ve `BankingTransactionResponse` kod aşağıdaki işlemleri içinde geçerli ise ileti sözleşmeleri olan iki türleridir.  
  
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
  
 Sözleşme türden bir ileti içerir ve, geçerli desenleri birini izlemez herhangi bir işlem için bir özel durum oluşur. Elbette, ileti sözleşme türleri içermeyen operations bu sınırlamalara tabi değildir.  
  
 Bir türü bir ileti sözleşmesi ve bir veri sözleşmesi varsa, yalnızca ileti sözleşmesi türü bir işlemde kullanıldığında olarak kabul edilir.  
  
## <a name="defining-message-contracts"></a>İleti sözleşmeleri tanımlama  
 Bir tür için bir ileti sözleşmesi tanımlamak için (diğer bir deyişle, türü ve SOAP Zarfı arasında eşleme tanımlamak için), geçerli <xref:System.ServiceModel.MessageContractAttribute> türü. Daha sonra uygulamanız <xref:System.ServiceModel.MessageHeaderAttribute> SOAP üstbilgileri yapıp uygulamak istediğiniz türü bu üyeler için <xref:System.ServiceModel.MessageBodyMemberAttribute> iletinin SOAP gövdesi parçalara yapmak istediğiniz bu üyelere.  
  
 Aşağıdaki kod bir ileti sözleşmesi kullanmaya ilişkin bir örnek sağlar.  
  
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
  
 Dikkat `operation` ve `transactionDate` SOAP üstbilgileri görünür ve SOAP gövdesi bir sarmalayıcı öğesi oluşur `BankingTransaction` içeren `sourceAccount`,`targetAccount`, ve `amount`.  
  
 Uygulayabileceğiniz <xref:System.ServiceModel.MessageHeaderAttribute> ve <xref:System.ServiceModel.MessageBodyMemberAttribute> tüm alanlar, özellikleri ve genel, özel, korumalı veya iç olup olmadıkları bakılmaksızın, olaylar.  
  
 <xref:System.ServiceModel.MessageContractAttribute> SOAP iletisi gövdesinde sarmalayıcı öğesinin adı kontrol WrapperName ve WrapperNamespace öznitelikleri belirtmenize olanak tanır. Varsayılan ileti sözleşmesi adını türü sarmalayıcı ve ileti sözleşmesi tanımlanır ad alanı için kullanılan `HYPERLINK "http://tempuri.org/" http://tempuri.org/` varsayılan ad alanı olarak kullanılır.  
  
> [!NOTE]
>  <xref:System.Runtime.Serialization.KnownTypeAttribute> ileti sözleşmeleri öznitelikleri göz ardı edilir. Varsa bir <xref:System.Runtime.Serialization.KnownTypeAttribute> olan gerekli, bunu ileti sözleşmesi kullanan işlemi söz konusu yerleştirin.  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a>Üstbilgi ve gövde bölümü adlarına ve ad alanlarını denetleme  
 İleti sözleşmesi SOAP gösterimini her üstbilgi ve gövde bölümü bir ad ve bir ad alanı olan bir XML öğesi eşler.  
  
 Varsayılan olarak, ileti katılıyor ve ad üye adına belirlenir hizmet sözleşmesi ad alanı ile aynı ad alanıdır <xref:System.ServiceModel.MessageHeaderAttribute> veya <xref:System.ServiceModel.MessageBodyMemberAttribute> öznitelikler uygulanır.  
  
 Bu varsayılan işleyerek değiştirebileceğiniz <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> ve <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (üst sınıfı üzerinde <xref:System.ServiceModel.MessageHeaderAttribute> ve <xref:System.ServiceModel.MessageBodyMemberAttribute> öznitelikleri).  
  
 Aşağıdaki kod örneğinde sınıfında göz önünde bulundurun.  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader(Namespace="http://schemas.contoso.com/auditing/2005")] public bool IsAudited;  
  [MessageBodyMember(Name="transactionData")] public BankingTransactionData theData;  
}  
```  
  
 Bu örnekte, `IsAudited` başlığıdır kodu ve temsil eden gövde bölümü belirtilen ad alanında `theData` üye ada sahip bir XML öğesi ile temsil edilir `transactionData`. Bu ileti sözleşmesi için oluşturulan XML gösterir.  
  
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
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a>SOAP gövdesi bölümleri Sarmalanan olup olmadığını denetleme  
 Varsayılan olarak, SOAP gövdesi bölümleri Sarmalanan bir öğesiyle iç serileştirilir. Örneğin, aşağıdaki gösterir kod `HelloGreetingMessage` adından oluşturulan sarmalayıcı öğeyi <xref:System.ServiceModel.MessageContractAttribute> için ileti sözleşmesi türü `HelloGreetingMessage` ileti.  
  
 [!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
 [!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 Kapsayıcı öğe gizlemek için ayarlanmış <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> özelliğine `false`. Ad ve sarmalayıcı öğesinin ad alanı denetlemek için kullandığı <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> ve <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> özellikleri.  
  
> [!NOTE]
>  Birden fazla ileti Gövde bölümünün değil sarılır iletilerinde sahip WS ile uyumlu değil-ı temel Profil 1.1 ve yeni ileti sözleşmeleri tasarlarken önerilmez. Ancak, birden fazla sarmalanmamış ileti Gövde bölümünün belirli belirli birlikte çalışabilirlik senaryolarda sağlamak gerekli olabilir. Birden fazla parça ileti gövdesinde veri iletmek için kullanacaksanız, varsayılan (Sarmalanan) modunu kullanmak için önerilir. Birden fazla ileti üstbilgisi sarmalanmamış iletilerinde sahip tamamen kabul edilebilir.  
  
## <a name="using-custom-types-inside-message-contracts"></a>İleti sözleşmeleri içinde özel türleri kullanma  
 (XML içinde açık) her bireysel ileti başlığı ve ileti Gövde bölümünün serileştirilir seçilen serileştirme motoruna ileti kullanıldığı için hizmet sözleşmesini kullanma. Varsayılan serileştirme motoruna `XmlFormatter`, bir veri sözleşmesi ya da açıkça olan herhangi bir tür işleyebilir (sahip <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) ya da örtük olarak (Basit tür olması, sahip <xref:System.SerializableAttribute?displayProperty=nameWithType>, vb.). Daha fazla bilgi için bkz: [kullanarak veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Önceki örnekte `Operation` ve `BankingTransactionData` türleri, bir veri sözleşmesi olmalıdır ve `transactionDate` seri hale getirilemez çünkü <xref:System.DateTime> bir primitive (ve bu nedenle bir örtük veri sözleşmesi).  
  
 Ancak, farklı seri hale getirme altyapısı için mümkün `XmlSerializer`. Bu tür bir geçiş yaparsanız, tüm ileti üstbilgilerini ve gövde bölümleri için kullanılan türleri seri hale getirilebilir kullanarak emin olun `XmlSerializer`.  
  
## <a name="using-arrays-inside-message-contracts"></a>İleti sözleşmeleri içinde dizileri kullanma  
 İleti sözleşmeleri iki yolla öğelerinde yineleme dizileri kullanabilirsiniz.  
  
 İlk kullanmaktır bir <xref:System.ServiceModel.MessageHeaderAttribute> veya <xref:System.ServiceModel.MessageBodyMemberAttribute> dizisi üzerinde doğrudan. Bu durumda, bir öğesiyle (diğer bir deyişle, bir üst bilgi veya bir gövde bölümü) birden çok alt öğesi olarak tüm diziyi serileştirilir. Aşağıdaki örnek sınıfında göz önünde bulundurun.  
  
```csharp  
[MessageContract]  
public class BankingDepositLog  
{  
  [MessageHeader] public int numRecords;  
  [MessageHeader] public DepositRecord[] records;  
  [MessageHeader] public int branchID;  
}  
```  
  
 SOAP üstbilgileri bu sonuçlarında aşağıdakine benzer.  
  
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
  
 Bu alternatif kullanmaktır <xref:System.ServiceModel.MessageHeaderArrayAttribute>. Bu durumda, her dizi öğesi bağımsız olarak serileştirilmiş ve her dizi öğesi bir üst bilgi, aşağıdakine benzer bulunduğundan.  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 Dizi girdiler için varsayılan adı üyesine adıdır <xref:System.ServiceModel.MessageHeaderArrayAttribute> öznitelikler uygulanır.  
  
 <xref:System.ServiceModel.MessageHeaderArrayAttribute> Özniteliği devraldığı <xref:System.ServiceModel.MessageHeaderAttribute>. Dizi olmayan öznitelikleri özellikleri kümesinin aynısını sahipse, örneğin, sipariş, adı ve üst bilgileri dizisi için ad alanı için tek bir başlık kümesi aynı şekilde ayarlamak mümkün olur. Kullandığınızda `Order` bir dizi özellik, dizinin tamamı için geçerlidir.  
  
 Uygulayabileceğiniz <xref:System.ServiceModel.MessageHeaderArrayAttribute> yalnızca dizileri, değil koleksiyonlar için.  
  
## <a name="using-byte-arrays-in-message-contracts"></a>İleti sözleşmeleri bayt dizileri kullanma  
 Dizi olmayan özniteliklerle kullanıldığında bayt dizileri (<xref:System.ServiceModel.MessageBodyMemberAttribute> ve <xref:System.ServiceModel.MessageHeaderAttribute>), dizi olarak ancak Base64 ile kodlanmış veriler sonuç XML olarak gösterilen özel bir basit tür olarak kabul edilmediği.  
  
 Bayt dizileri dizi özniteliğiyle kullandığınızda <xref:System.ServiceModel.MessageHeaderArrayAttribute>, kullanımdaki seri hale getirici sonuçları bağlıdır. Varsayılan serileştirici ile dizinin her bir bayt için tek bir giriş olarak temsil edilir. Ancak, ne zaman `XmlSerializer` seçili (kullanarak <xref:System.ServiceModel.XmlSerializerFormatAttribute> hizmet sözleşmesi üzerinde), bayt dizileri Base64 veri dizisi veya dizi olmayan öznitelikleri kullanılıp bağımsız olarak kabul edilir.  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a>İmzalama ve şifreleme iletinin bölümleri  
 İleti sözleşmesi üstbilgileri ve/veya ileti gövdesini dijital olarak İmzalanabilir ve şifrelenebilir olup olmadığını gösterebilir.  
  
 Bu ayarlayarak yapılır <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> özelliği <xref:System.ServiceModel.MessageHeaderAttribute> ve <xref:System.ServiceModel.MessageBodyMemberAttribute> öznitelikleri. Sabit listesi özelliktir <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> yazın ve ayarlanabilir <xref:System.Net.Security.ProtectionLevel.None> (şifreleme veya imza), <xref:System.Net.Security.ProtectionLevel.Sign> (dijital imza yalnızca), veya <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (şifreleme ve dijital imza). Varsayılan, <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> değeridir.  
  
 Bu güvenlik özellikleri çalışacak şekilde bağlama ve davranışları düzgün şekilde yapılandırmanız gerekir. Bu güvenlik özellikleri uygun yapılandırma olmadan (örneğin, bir ileti kimlik bilgilerinizi girmeden oturum çalışılıyor) kullanırsanız, doğrulama aynı anda özel durum oluşur.  
  
 İleti üstbilgilerini koruma düzeyi ayrı ayrı her bir üstbilgisi belirlenir.  
  
 İleti gövdesi bölümleri için koruma düzeyi, "düşük koruma düzeyi." değerlendirilebilir Gövde gövde bölümlerinin sayısını bağımsız olarak yalnızca bir koruma düzeyi vardır. Gövde koruma düzeyi yüksek tarafından belirlenir <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> tüm gövde bölümlerini özellik ayarı. Bununla birlikte, her bir gövde kısmının koruma düzeyini düzeyi gereken gerçek minimum koruma için ayarlamanız gerekir.  
  
 Aşağıdaki kod örneğinde sınıfında göz önünde bulundurun.  
  
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
  
 Bu örnekte, `recordID` üstbilgi korumalı değil, `patientName` olan `signed`, ve `SSN` imzalı ve şifrelenir. En az bir gövde bölümü `medicalHistory`, sahip <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> uygulanan ve dolayısıyla tüm ileti gövdesi şifrelenir ve imzalanmış rağmen açıklamalar ve tanılama gövde bölümlerinin daha düşük koruma düzeyleri belirtin.  
  
## <a name="soap-action"></a>SOAP eylemi  
 SOAP ve ilgili Web hizmeti standartlarını tanımlamak adlı bir özellik `Action` , olabilir gönderilen her SOAP iletisi için mevcut. İşlem <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> ve <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> denetim özelliklerini bu özelliğin değeri.  
  
## <a name="soap-header-attributes"></a>SOAP üstbilgi öznitelikleri  
 SOAP standart üstbilgi bulunabilir aşağıdaki öznitelikleri tanımlar:  
  
-   `Actor/Role` (`Actor` SOAP 1.1 `Role` SOAP 1.2)  
  
-   `MustUnderstand`  
  
-   `Relay`  
  
 `Actor` Veya `Role` özniteliği, verili bir üstbilginin amaçlanmıştır düğümü Tekdüzen Kaynak Tanımlayıcısı'nı (URI) belirtir. `MustUnderstand` Özniteliği, üst bilgi işlem düğümü, anlamak olup olmadığını belirtir. `Relay` Özniteliği, üstbilgi aşağı akış düğümlerine geçirilmesine izin olup olmadığını belirtir. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dışında bu özniteliklerin gelen iletileri üzerinde herhangi bir işlem gerçekleştirmez `MustUnderstand` özniteliği, bu konunun devamındaki "İleti sözleşmesi sürümü oluşturma" bölümünde belirtildiği gibi. Ancak, gerekirse aşağıdaki açıklama olduğu gibi bu öznitelikler okumasına ve yazmasına sağlar.  
  
 İleti gönderirken bu öznitelikler varsayılan olarak gösterilen değil. Bunu iki şekilde değiştirebilirsiniz. İlk olarak, statik olarak öznitelikleri için istenen tüm değerleri değiştirerek ayarladığınız <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, ve <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> aşağıdaki kod örneğinde gösterildiği gibi özellikler. (Unutmayın hiçbir `Role` özellik; ayarı <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> özelliği yayar `Role` SOAP 1.2 kullanıyorsanız özniteliği).  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 Bu öznitelikler denetlemek için ikinci yol dinamik olarak kodudur. Bu istenen üstbilgi türünde kaydırma tarafından elde <xref:System.ServiceModel.MessageHeader%601> türü (Bu tür genel olmayan sürümüyle karıştırır değil emin olun) ve türü ile birlikte kullanarak <xref:System.ServiceModel.MessageHeaderAttribute>. Daha sonra özellikleri kullanabileceğinizi <xref:System.ServiceModel.MessageHeader%601> aşağıdaki kod örneğinde gösterildiği gibi SOAP öznitelikleri ayarlamak için.  
  
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
  
 Dinamik ve statik denetimi düzenekleri kullanırsanız, statik ayarları varsayılan olarak kullanılır, ancak daha sonra dinamik mekanizmasını kullanarak aşağıdaki kodda gösterildiği gibi geçersiz kılınabilir.  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 Dinamik öznitelik denetimi ile yinelenen başlıkları oluşturma, aşağıdaki kodda gösterildiği olarak izin verilir.  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 Alıcı tarafında SOAP özniteliklerden okuma yalnızca varsa yapılabilir <xref:System.ServiceModel.MessageHeader%601> sınıfı türü üstbilgisinde için kullanılır. İncelemek `Actor`, `Relay`, veya `MustUnderstand` başlık özelliklerini <xref:System.ServiceModel.MessageHeader%601> alınan iletide öznitelik ayarlarını bulmak için türü.  
  
 Bir ileti alındı ve geri gönderilen zaman SOAP özniteliği ayarları yalnızca üst bilgilerinin gidiş dönüş gidin <xref:System.ServiceModel.MessageHeader%601> türü.  
  
## <a name="order-of-soap-body-parts"></a>SOAP gövdesi bölümleri sırasını  
 Bazı durumlarda, gövde bölümlerinin sırasını denetlemek gerekebilir. Gövde öğelerin sırasını varsayılan olarak alfabetik ancak tarafından denetlenen <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> özelliği. Bu özellik olarak aynı semantiklerine sahip <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> devralma senaryolarda (ileti sözleşmeleri, temel türü gövdesi üyeleri önce türetilen tür gövde üyeleri sıralanmamış) davranış dışında özelliği. Daha fazla bilgi için bkz: [veri üye sırası](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 Aşağıdaki örnekte, `amount` alfabetik olarak ilk olduğundan normal olarak ilk gelecektir. Ancak, <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> özelliği, üçüncü yerine koyar.  
  
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
 Bazen, ileti sözleşmeleri değiştirmeniz gerekebilir. Örneğin, uygulamanızın yeni bir sürümünü iletiye ek üstbilgi ekleyebilir. Ardından, gelen yeni sürümü eski gönderirken, sistem bir ek üstbilgi yanı sıra ile üstbilgisi eksik ters yönde geçerken ilgilenmeniz gerekir.  
  
 Sürüm üstbilgilerini aşağıdaki kurallar geçerli olur:  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] eksik üstbilgileri nesne değildir — varsayılan değerlerine karşılık gelen üyeleri bırakılır.  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Ayrıca beklenmeyen fazladan üstbilgiler yoksayar. Ek üstbilgi varsa bu kuralın tek özel durum olan bir `MustUnderstand` özniteliğini `true` gelen SOAP iletisi — anlaşılmalıdır bir üstbilgi işlenemediği için bu durumda, bir özel durum oluşur.  
  
 İleti gövdeleri sahip benzer sürüm oluşturma kuralları — eksik ve ek İleti gövde bölümü yok sayılır.  
  
## <a name="inheritance-considerations"></a>Devralma hakkında önemli noktalar  
 Temel türü bir ileti sözleşmesi de sahip olduğu sürece başka bir türden bir ileti sözleşmesi türü devralabilirsiniz.  
  
 Oluşturma veya diğer ileti sözleşme türlerinden devralan bir ileti sözleşmesi türü kullanarak ileti erişme, aşağıdaki kurallar geçerlidir:  
  
-   Tüm devralma hiyerarşisinde iletisi üstbilgilerinin birlikte ileti üstbilgilerini kümesini oluşturmak için toplanır.  
  
-   Tüm devralma hiyerarşisi içinde ileti gövdesi parçalarını birlikte tam ileti gövdesini form için toplanır. Gövde bölümlerinin normal sıralama kurallara göre sıralanır (tarafından <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> özelliği ve ardından alfabetik), hiçbir göreli kendi yerleştirmek için devralma hiyerarşisi. İleti gövde bölümlerinin birden çok devralma ağacında düzeylerinde gerçekleştiği ileti sözleşme devralma kullanımı kesinlikle önerilmez. Bir taban sınıf ve türetilmiş bir sınıf bir üstbilgi veya aynı ada sahip bir gövde bölümü tanımlarsanız, çoğu temel sınıfından üye Bu üstbilgi veya gövde bölümü değeri depolamak için kullanılır.  
  
 Aşağıdaki kod örneğinde sınıflarda göz önünde bulundurun.  
  
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
  
 `PatientRecord` Sınıfı açıklayan bir ileti adlı bir üstbilgiyle `ID`. Üstbilgi karşılık gelen `personID` ve `patientID` üye, temel çoğu üyesi seçilir olduğundan. Bu nedenle, `patientID` alandır gereksiz bu durumda. İleti gövdesini içeren `diagnosis` öğesi arkasından `patientName` öğesi alfabetik olduğu için. Örnek kesinlikle önerilmez bir desen gösterdiğine dikkat edin: hem temel hem de türetilmiş ileti sözleşmeleri ileti gövdesi bölümden oluşur.  
  
## <a name="wsdl-considerations"></a>WSDL konuları  
 Web Hizmetleri Açıklama Dili (WSDL) sözleşme ileti sözleşmeleri kullanan bir hizmetinden oluştururken, tüm ileti sözleşmesi özellikleri elde edilen WSDL içinde yansıtılır hatırlamak önemlidir. Aşağıdaki noktaları göz önünde bulundurun:  
  
-   WSDL üstbilgileri dizisi kavramı hızlı olamaz. İletileri kullanarak üstbilgileri bir dizi oluşturulurken <xref:System.ServiceModel.MessageHeaderArrayAttribute>, sonuçta elde edilen WSDL dizi yerine yalnızca bir üstbilgi yansıtır.  
  
-   Sonuçta elde edilen WSDL belgesinde bazı koruma düzeyi bilgileri yansıtmaz.  
  
-   WSDL içinde oluşturulan ileti türü ileti sözleşme türü sınıf adı ile aynı ada sahiptir.  
  
-   Birden çok işlemlerinde aynı iletiyi kullanarak sözleşme, birden çok ileti türlerini WSDL belgesinde üretilir. Adları "3", numaraları "2" ekleyerek ve benzeri sonraki kullanımlar için benzersiz yapılır. Geri WSDL içe aktarırken, birden çok ileti sözleşme türleri oluşturulur ve adlarını dışında aynıdır.  
  
## <a name="soap-encoding-considerations"></a>SOAP konuları kodlama  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] eski SOAP kodlama stilini XML kullanmanıza olanak tanır ancak kullanımı önerilmez. Bu stili kullanırken (ayarlayarak `Use` özelliğine `Encoded` üzerinde <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> hizmet sözleşmesini uygulanan), aşağıdaki ek maddeler geçerlidir:  
  
-   İleti üstbilgilerini desteklenmez; Bu öznitelik anlamına <xref:System.ServiceModel.MessageHeaderAttribute> ve dizi öznitelik <xref:System.ServiceModel.MessageHeaderArrayAttribute> SOAP kodlama ile uyumlu değil.  
  
-   İleti sözleşmesi, diğer bir deyişle, sarmalanmamış varsa özelliği <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> ayarlanır `false`, ileti sözleşmesi yalnızca bir gövde bölümü olabilir.  
  
-   İstek ileti sözleşmesi için sarmalayıcı öğesi adını, işlem adı eşleşmelidir. Kullanım `WrapperName` bu ileti sözleşmesi özelliği.  
  
-   Yanıt ileti sözleşmesi için kapsayıcı öğe adını 'Yanıtıyla' sonekine işlemin adı ile aynı olması gerekir. Kullanım <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> bu ileti sözleşmesi özelliği.  
  
-   SOAP kodlama nesne başvuruları korur. Örneğin, aşağıdaki kodu göz önünde bulundurun.  
  
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
  
 İletinin SOAP kodlama, kullanılarak seri hale getirme sonra `changedFrom` ve `changedTo` kendi kopyalarını içermeyen `p`, ancak bunun yerine iç kopyayı işaret `changedBy` öğesi.  
  
## <a name="performance-considerations"></a>Başarım Değerlendirmeleri  
 Her ileti başlığı ve ileti Gövde bölümünün bağımsız olarak diğer serileştirilir. Bu nedenle, aynı ad alanları yeniden her başlık ve gövde bölümü için bildirilebilir. Özellikle Tel üzerinde iletinin boyutunu bakımından performansını artırmak için birden çok üst bilgiler ve gövde bölümlerinin tek bir üstbilgi veya gövde bölümüne birleştirin. Örneğin, aşağıdaki kodu yerine:  
  
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
 Olay tabanlı zaman uyumsuz modeli için tasarım yönergeleri birden fazla değer döndürülürse, tek bir değer olarak döndürülen durum `Result` özelliği ve diğerleri döndürülür özellikleri olarak üzerinde <xref:System.EventArgs> nesnesi. Bunun bir sonucu olduğundan, bu, istemci olay tabanlı zaman uyumsuz komut seçeneklerini kullanarak meta verilerini alır ve birden fazla değer, varsayılan işlemi döndürürse <xref:System.EventArgs> nesnesi döndüren bir değer olarak `Result` özelliği ve geri kalan özelliklerini <xref:System.EventArgs> nesnesi.  
  
 İleti nesnesi olarak almak istiyorsanız `Result` özelliği ve bu nesne üzerinde özellikleri kullanma gibi döndürülen değerlere sahip `/messageContract` komut seçeneği. Bu olarak yanıt iletisi döndüren bir imza oluşturur `Result` özellikte <xref:System.EventArgs> nesnesi. Tüm iç dönüş değerleri yanıt iletisi nesnesi sonra özellikleridir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Anlaşmalarını Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Hizmetleri Tasarlama ve Uygulama](../../../../docs/framework/wcf/designing-and-implementing-services.md)
