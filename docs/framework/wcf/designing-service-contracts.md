---
title: Hizmet Sözleşmeleri Tasarlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF]
ms.assetid: 8e89cbb9-ac84-4f0d-85ef-0eb6be0022fd
ms.openlocfilehash: 37723011d69e8ea2ead3f7a30a30898dede054cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176688"
---
# <a name="designing-service-contracts"></a>Hizmet Sözleşmeleri Tasarlama
Bu konu, hizmet sözleşmelerinin ne olduğunu, nasıl tanımlandığını, hangi işlemlerin kullanılabilir olduğunu (ve temel ileti alışverişinin etkileri), hangi veri türlerinin kullanıldığını ve senaryonuzun gereksinimleri.  
  
## <a name="creating-a-service-contract"></a>Hizmet Sözleşmesi Oluşturma  
 Hizmetler bir dizi işlemi ortaya çıkarır. Windows Communication Foundation (WCF) uygulamalarında, bir yöntem oluşturarak ve <xref:System.ServiceModel.OperationContractAttribute> öznitelik ile işaretleyerek işlemleri tanımlayın. Ardından, bir hizmet sözleşmesi oluşturmak için, işlemlerinizi öznitelikile <xref:System.ServiceModel.ServiceContractAttribute> işaretlenmiş bir arabirim içinde beyan ederek veya aynı öznitelikile işaretlenmiş bir sınıfta tanımlayarak gruplayın. (Temel bir örnek için [bkz: Hizmet Sözleşmesi](how-to-define-a-wcf-service-contract.md)Tanımla.)  
  
 <xref:System.ServiceModel.OperationContractAttribute> Özniteliği olmayan tüm yöntemler hizmet işlemleri değildir ve WCF hizmetleri tarafından açıklanmaz.  
  
 Bu konu, bir hizmet sözleşmesi tasarlarken aşağıdaki karar noktalarını açıklar:  
  
- Sınıfları veya arayüzleri kullanmak ister.  
  
- Alışverişi yapmak istediğiniz veri türlerini nasıl belirtirsiniz.  
  
- Kullanabileceğiniz değişim desenleri türleri.  
  
- Açık güvenlik gereksinimlerini sözleşmenin bir parçası yapıp yapamazsınız.  
  
- Çalışma giriş ve çıkışları için kısıtlamalar.  
  
## <a name="classes-or-interfaces"></a>Sınıflar veya Arayüzler  
 Hem sınıflar hem de arabirimler işlevsellik grubunu temsil eder ve bu nedenle her ikisi de bir WCF hizmet sözleşmesi tanımlamak için kullanılabilir. Ancak, doğrudan hizmet sözleşmelerini modellediği için arabirimleri kullanmanız önerilir. Bir uygulama olmadan, arabirimler, belirli imzalarla birlikte yöntemlerin gruplandırması tanımlamaktan başka bir şey yapmaz. Bir hizmet sözleşmesi arabirimi uygulayın ve bir WCF hizmeti uyguladınız.  
  
 Yönetilen arabirimlerin tüm avantajları hizmet sözleşmesi arabirimleri için geçerlidir:  
  
- Hizmet sözleşmesi arabirimleri, diğer hizmet sözleşmesi arabirimlerinin herhangi bir sayısını genişletebilir.  
  
- Tek bir sınıf, bu hizmet sözleşmesi arabirimlerini uygulayarak herhangi bir sayıda hizmet sözleşmesi uygulayabilir.  
  
- Hizmet sözleşmesi aynı kalırken, arabirim uygulamasını değiştirerek bir hizmet sözleşmesinin uygulamasını değiştirebilirsiniz.  
  
- Eski arabirimi ve yenisini uygulayarak hizmetinizi sürüm leyebilirsiniz. Eski istemciler özgün sürüme bağlanırken, yeni istemciler yeni sürüme bağlanabilir.  
  
> [!NOTE]
> Diğer hizmet sözleşmesi arabirimlerinden devralma yaparken, ad veya ad alanı gibi işlem özelliklerini geçersiz kılamazsınız. Bunu yapmaya çalışırsanız, geçerli hizmet sözleşmesinde yeni bir işlem oluşturursunuz.  
  
 Bir hizmet sözleşmesi oluşturmak için arabirim kullanma örneği için [bkz.](./feature-details/how-to-create-a-service-with-a-contract-interface.md)  
  
 Ancak, bir hizmet sözleşmesi tanımlamak ve aynı anda bu sözleşmeyi uygulamak için bir sınıf kullanabilirsiniz. Sınıfa ve <xref:System.ServiceModel.OperationContractAttribute> sınıfa uygulanan <xref:System.ServiceModel.ServiceContractAttribute> yöntemlere doğrudan uygulayarak hizmetlerinizi oluşturmanın avantajı, sırasıyla hız ve basitliktir. Dezavantajları yönetilen sınıflar birden çok devralma desteklemez ve sonuç olarak bir seferde sadece bir hizmet sözleşmesi uygulayabilirsiniz. Buna ek olarak, sınıf veya yöntem imzalarında yapılan herhangi bir değişiklik, değiştirilmemiş istemcilerin hizmetinizi kullanmasını engelleyebilen bu hizmetin ortak sözleşmesini değiştirir. Daha fazla bilgi için [bkz.](implementing-service-contracts.md)  
  
 Bir hizmet sözleşmesi oluşturmak için bir sınıf kullanan ve aynı anda uygulayan bir örnek [için bkz.](./feature-details/how-to-create-a-wcf-contract-with-a-class.md)  
  
 Bu noktada, bir arabirim kullanarak ve bir sınıf kullanarak hizmet sözleşmenizi tanımlama arasındaki farkı anlamanız gerekir. Bir sonraki adım, bir hizmet ve istemcileri arasında hangi verilerin ileri geri aktarılacağına karar vermektir.  
  
## <a name="parameters-and-return-values"></a>Parametreler ve İade Değerleri  
 Her işlemin bir geri dönüş değeri ve bir `void`parametresi vardır, bunlar . Ancak, bir nesneden diğerine nesnelere başvuru geçirebileceğiniz yerel bir yöntemin aksine, hizmet işlemleri nesnelere başvuru geçmez. Bunun yerine, nesnelerin kopyalarını geçirirler.  
  
 Parametre veya iade değeri kullanılan her tür serileştirilebilir olmalıdır, çünkü bu önemli; diğer bir zamanda, bu tür bir nesneyi bayt akışına ve bayt akışından bir nesneye dönüştürmek mümkün olmalıdır.  
  
 İlkel türler, .NET Framework'deki birçok tür gibi varsayılan olarak serileştirilebilir.  
  
> [!NOTE]
> İşlem imzasındaki parametre adlarının değeri sözleşmenin bir parçasıdır ve büyük/küçük harf duyarlıdır. Aynı parametre adını yerel olarak kullanmak ancak yayımlanmış meta verilerdeki adı <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>değiştirmek istiyorsanız, bkz.  
  
#### <a name="data-contracts"></a>Veri Sözleşmeleri  
 Windows Communication Foundation (WCF) uygulamaları gibi hizmet odaklı uygulamalar, hem Microsoft hem de Microsoft dışı platformlarda mümkün olan en geniş istemci uygulamasıyla birlikte çalışacak şekilde tasarlanmıştır. Mümkün olan en geniş birlikte çalışabilirlik için, hizmet işlemişlemlerinizin değiş tokuş ettiği verileri açıklayan hizmet sözleşmesinin bir bölümü olan bir veri sözleşmesi oluşturmak için türlerinizi <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliklerinizi işaretlemeniz önerilir.  
  
 Veri sözleşmeleri tercih tarzı sözleşmelerdir: Veri sözleşmesi özniteliğini açıkça uygulamadığınız sürece hiçbir tür veya veri üyesi serihale getirilmez. Veri sözleşmeleri yönetilen kodun erişim kapsamıyla ilgili değildir: Özel veri üyeleri seri hale getirilebilir ve genel olarak erişilebilmek üzere başka bir yere gönderilebilir. (Veri sözleşmesinin temel bir örneği için [bkz: Bir Sınıf veya Yapı için Temel Veri Sözleşmesi Oluşturma](./feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md).) WCF, işlemin işlevselliğini sağlayan temel SOAP iletilerinin tanımını ve veri tiplerinizin iletilerin gövdesine girip çıkarılmasını sağlar. Veri türleriniz seri leştirilebilir olduğu sürece, işlemlerinizi tasarlarken temel ileti alışverişi altyapısını düşünmeniz gerekmez.  
  
 Tipik WCF uygulaması, <xref:System.Runtime.Serialization.DataContractAttribute> işlemler <xref:System.Runtime.Serialization.DataMemberAttribute> için veri sözleşmeleri oluşturmak için öznitelikleri ve öznitelikleri kullansa da, diğer serileştirme mekanizmalarını kullanabilirsiniz. Standart <xref:System.Runtime.Serialization.ISerializable>ve <xref:System.SerializableAttribute> <xref:System.Xml.Serialization.IXmlSerializable> mekanizmalar tüm veri türlerinin bir uygulamadan diğerine bunları taşıyan altta yatan SOAP iletileri içine serileştirme işlemek için çalışır. Veri türleriniz özel destek gerektiriyorsa daha fazla serileştirme stratejileri kullanabilirsiniz. WCF uygulamalarında veri türlerinin serileştirilmesi seçenekleri hakkında daha fazla bilgi için [bkz.](./feature-details/specifying-data-transfer-in-service-contracts.md)  
  
#### <a name="mapping-parameters-and-return-values-to-message-exchanges"></a>Parametreleri Eşleme ve İleti Alışverişine İade Değerleri  
 Hizmet işlemleri, uygulama verilerini ileri geri aktaran SOAP iletilerinin temel değişimi yle ve uygulamanın belirli standart güvenliği, işlemi ve oturumla ilgili özellikleri desteklemek için gerektirdiği verilere ek olarak desteklenir. Bu durumda, bir hizmet işleminin imzası, veri aktarımını ve bir işlemin gerektirdiği özellikleri destekleyebilen belirli bir temel *ileti alışverişi deseni* (MEP) belirler. WCF programlama modelinde üç desen belirtebilirsiniz: istek/yanıt, tek yönlü ve çift yönlü ileti desenleri.  
  
##### <a name="requestreply"></a>İstek/Yanıtla  
 İstek/yanıt deseni, istek gönderenin (istemci uygulaması) isteğin ilişkili olduğu bir yanıt aldığı desendir. Bu varsayılan MEP'dir, çünkü bir veya daha fazla parametrenin operasyona aktarıldığı ve geri dönüş değerinin arayana geri aktarıldığı bir işlemi destekler. Örneğin, aşağıdaki C# kodu örneği, bir dize alan ve bir dize döndüren temel bir hizmet işlemini gösterir.  
  
```csharp  
[OperationContractAttribute]  
string Hello(string greeting);  
```  
  
 Aşağıda eşdeğer Visual Basic kodu verem.  
  
```vb  
<OperationContractAttribute()>  
Function Hello (ByVal greeting As String) As String  
```  
  
 Bu işlem imzası, temel ileti alışverişi biçimini belirler. Korelasyon yoksa, WCF iade değerinin hangi işlem için amaçlandığını belirleyemez.  
  
 Farklı bir temel ileti deseni belirtmediğiniz sürece, `void` `Nothing` (Visual Basic'te) dönen hizmet işlemleri bile istek/yanıt iletisi alışverişidir. İşleminizin sonucu, istemci işlemi eş senkronize olarak çağırmadığı sürece, ileti normal durumda boş olsa bile, istemcinin iade iletisi alınana kadar işlemeyi durdurmasıdır. Aşağıdaki C# kodu örneği, istemci yanıt olarak boş bir ileti alana kadar geri dönmeyen bir işlemi gösterir.  
  
```csharp  
[OperationContractAttribute]  
void Hello(string greeting);  
```  
  
 Aşağıda eşdeğer Visual Basic kodu verem.  
  
```vb  
<OperationContractAttribute()>  
Sub Hello (ByVal greeting As String)  
```  
  
 Önceki örnek, işlemin gerçekleştirilmesi uzun zaman alıyorsa istemci performansını `void`ve yanıt verme gücünü yavaşlatabilir, ancak geri dönüşettiklerinde bile söz leme/yanıtlama için avantajlar var. En belirgin olanı, SOAP hatalarının yanıt iletisinde döndürülebildiğidir, bu da ister iletişim de ister işleme de olsun, hizmetle ilgili bazı hata koşullarının oluştuğunu gösterir. Hizmet sözleşmesinde belirtilen SOAP hataları, hizmet sözleşmesinde belirtilen <xref:System.ServiceModel.FaultException%601> tür parametresi türü olduğu bir nesne olarak istemci uygulamasına geçirilir. Bu, istemcileri WCF hizmetlerindeki hata koşulları hakkında bilgilendirmeyi kolaylaştırır. İstisnalar, SOAP hataları ve hata işleme hakkında daha fazla bilgi için [bkz.](specifying-and-handling-faults-in-contracts-and-services.md) İstek/yanıt hizmeti ve istemci örneğini görmek [için bkz.](./feature-details/how-to-create-a-request-reply-contract.md) İstek-yanıt deseniyle ilgili sorunlar hakkında daha fazla bilgi [için, İstek-Yanıt Hizmetleri'ne](./feature-details/request-reply-services.md)bakın.  
  
##### <a name="one-way"></a>Tek yönlü  
 Bir WCF hizmet uygulamasının istemcisi işlemin tamamlanmasını beklememeli ve SOAP hatalarını işlemiyorsa, işlem tek yönlü bir ileti deseni belirtebilir. Tek yönlü işlem, istemcinin bir işlemi çağırdığı ve WCF iletiyi ağa yazdıktan sonra işleme devam ettiği işlemdir. Genellikle bu, giden iletide gönderilen veriler son derece büyük olmadığı sürece istemcinin hemen çalışmaya devam ettiği anlamına gelir (veri göndermede bir hata olmadığı sürece). Bu tür ileti alışverişi deseni, istemciden hizmet uygulamasına olay benzeri davranışı destekler.  
  
 Bir iletinin gönderildiği ve hiçbirinin alınmadığı bir ileti alışverişi, geri dönüş `void`değeri dışında bir hizmet işlemini destekleyemez; Bu durumda <xref:System.InvalidOperationException> bir özel durum atılır.  
  
 İade iletisi yok, aynı zamanda işleme veya iletişimdeki hataları belirtmek için iade edilen SOAP hatası nın olmadığı anlamına da gelir. (İşlemler tek yönlü işlemler olduğunda hata bilgilerinin iletilmesi çift yönlü ileti alışverişi deseni gerektirir.)  
  
 Döndüren `void`bir işlem için tek yönlü ileti <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> alışverişi `true`belirtmek için, aşağıdaki C# kodu örneğinde olduğu gibi özelliği " olarak ayarlayın.  
  
```csharp  
[OperationContractAttribute(IsOneWay=true)]  
void Hello(string greeting);  
```  
  
 Aşağıda eşdeğer Visual Basic kodu verem.  
  
```vb  
<OperationContractAttribute(IsOneWay := True)>  
Sub Hello (ByVal greeting As String)  
```  
  
 Bu yöntem önceki istek/yanıt örneğiyle aynıdır, <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> ancak `true` özelliği ayarlamak, yöntem aynı olmasına rağmen, hizmet işleminin bir iade iletisi göndermediği ve giden ileti kanal katmanına teslim edildikten hemen sonra istemcilerin geri döndüğü anlamına gelir. Örneğin, [bkz.](./feature-details/how-to-create-a-one-way-contract.md) Tek yönlü desen hakkında daha fazla bilgi için [Tek Yönlü Hizmetler'e](./feature-details/one-way-services.md)bakın.  
  
##### <a name="duplex"></a>Çift Yönlü  
 Çift yönlü desen, tek yönlü veya istek/yanıt iletisi kullanarak bağımsız olarak birbirlerine ileti gönderme yeteneği ile karakterizedir. Bu iki yönlü iletişim biçimi, doğrudan istemciyle iletişim kurması gereken hizmetler veya olay benzeri davranışlar da dahil olmak üzere ileti alışverişinin her iki tarafına da eşzamanlı bir deneyim sağlamak için yararlıdır.  
  
 Çift yönlü desen, istemciyle iletişim kurmak için ek mekanizma nedeniyle istek/yanıt veya tek yönlü desenlerden biraz daha karmaşıktır.  
  
 Çift yönlü bir sözleşme tasarlamak için, bir geri arama sözleşmesi tasarlamanız ve <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> hizmet sözleşmenizi işaretleyen öznitelik özelliğine bu geri arama sözleşmesinin <xref:System.ServiceModel.ServiceContractAttribute> türünü atamanız gerekir.  
  
 Çift yönlü desen uygulamak için istemcide çağrılan yöntem bildirimlerini içeren ikinci bir arabirim oluşturmanız gerekir.  
  
 Bir hizmet oluşturma örneği ve bu hizmete erişen bir istemci için [bkz: Çift Taraflı Sözleşme Oluşturma](./feature-details/how-to-create-a-duplex-contract.md) ve Nasıl [İşletilir: Çift Taraflı Sözleşme ile Hizmetlere Erişim.](./feature-details/how-to-access-services-with-a-duplex-contract.md) Çalışan bir örnek için [Çift Yönlü'ye](./samples/duplex.md)bakın. Çift yönlü sözleşmeleri kullanan sorunlar hakkında daha fazla bilgi için [Bkz. Çift Yönlü Hizmetler.](./feature-details/duplex-services.md)  
  
> [!CAUTION]
> Bir hizmet çift yönlü ileti aldığında, `ReplyTo` yanıtı nereye göndereceğini belirlemek için gelen iletideki öğeye bakar. İletiyi almak için kullanılan kanal güvenli değilse, güvenilmeyen bir istemci hedef makinenin kiile kötü `ReplyTo`amaçlı bir ileti gönderebilir ve bu da hedef makinenin hizmet reddine (DOS) yol açabilir.  
  
##### <a name="out-and-ref-parameters"></a>Çıkış ve Ref Parametreleri  
 Çoğu durumda, parametreleri `in` (Visual`ByVal` Basic'te) `ref` ve`ByRef` `out` (Visual Basic'te) kullanabilirsiniz. Hem `out` de `ref` parametreler verilerin bir işlemden döndürüldünden geldiğini gösterdiğinden, aşağıdaki gibi bir işlem imzası, işlem `void`imzası dönse bile bir istek/yanıt işlemi nin gerekli olduğunu belirtir.  
  
```csharp  
[ServiceContractAttribute]  
public interface IMyContract  
{  
  [OperationContractAttribute]  
  public void PopulateData(ref CustomDataType data);  
}  
```  
  
 Aşağıda eşdeğer Visual Basic kodu verem.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface IMyContract  
  <OperationContractAttribute()> _  
  Public Sub PopulateData(ByRef data As CustomDataType)  
End Interface  
```  
  
 Bunun tek istisnası, imzanızın belirli bir yapıya sahip olduğu durumlardır. Örneğin, bağlamayı <xref:System.ServiceModel.NetMsmqBinding> yalnızca bir işlemi bildirmek için kullanılan yöntem geri `void`döndüğünde istemcilerle iletişim kurmak için kullanabilirsiniz; bir dönüş değeri `ref`veya `out` parametre olsun, hiçbir çıkış değeri olabilir.  
  
 Buna ek `out` olarak, kullanma veya `ref` parametreler, değiştirilen nesneyi geri taşımak için işlemin altta yatan bir yanıt iletisi olmasını gerektirir. İşleminiz tek yönlü bir işlemse, çalışma zamanında bir <xref:System.InvalidOperationException> özel durum atılır.  
  
### <a name="specify-message-protection-level-on-the-contract"></a>Sözleşmede İleti Koruma Düzeyini Belirt  
 Sözleşmenizi tasarlarken, sözleşmenizi uygulayan hizmetlerin ileti koruma düzeyine de karar vermeniz gerekir. Bu, yalnızca ileti güvenliği sözleşmenin bitiş noktasındaki bağlamaya uygulanırsa gereklidir. Bağlama güvenliği kapalıysa (diğer bir şekilde, sistem tarafından <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> sağlanan bağlama <xref:System.ServiceModel.SecurityMode.None?displayProperty=nameWithType>değeri ayarlamıyorsa) sözleşmenin ileti koruma düzeyine karar vermeniz gerekmez. Çoğu durumda, ileti düzeyi güvenliği uygulanan sistem tarafından sağlanan bağlamalar yeterli bir koruma düzeyi sağlar ve her işlem veya her ileti için koruma düzeyini göz önünde bulundurmanız gerekmez.  
  
 Koruma düzeyi, bir hizmeti destekleyen iletilerin (veya ileti parçalarının) imzalanıp imzalanıp imzalanmadığını, şifrelenip şifrelenmediğini veya imza veya şifreleme olmadan gönderilip gönderilmediğini belirten bir değerdir. Koruma düzeyi çeşitli kapsamlarda ayarlanabilir: Hizmet düzeyinde, belirli bir işlem için, bu işlem içindeki bir ileti veya ileti parçası için. Bir kapsamda ayarlanan değerler, açıkça geçersiz kılınmadığı sürece daha küçük kapsamlar için varsayılan değer haline gelir. Bağlayıcı bir yapılandırma sözleşme için gerekli minimum koruma düzeyini sağlayamıyorsa, bir özel durum atılır. Sözleşmede açıkça koruma düzeyi değerleri ayarlanmazsa, bağlamada ileti güvenliği varsa bağlama yapılandırması tüm iletilerin koruma düzeyini denetler. Bu varsayılan davranıştır.  
  
> [!IMPORTANT]
> Bir sözleşmenin çeşitli kapsamlarını tam koruma düzeyinin <xref:System.Net.Security.ProtectionLevel.EncryptAndSign?displayProperty=nameWithType> daha düşük bir seviyeye ayarlayıp ayarlamamaya karar vermek genellikle artan performans için bir dereceye kadar güvenlik sağlayan bir karardır. Bu gibi durumlarda, kararlarınız işlemleriniz ve değiş tokuş ettikleri verilerin değeri etrafında dönmelidir. Daha fazla bilgi için [Bkz. Güvenlik Hizmetleri.](securing-services.md)  
  
 Örneğin, aşağıdaki kod örneği sözleşmedeki <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> özelliği veya özelliği belirlemez.  
  
```csharp  
[ServiceContract]  
public interface ISampleService  
{  
  [OperationContractAttribute]  
  public string GetString();  
  
  [OperationContractAttribute]  
  public int GetInt();
}  
```  
  
 Aşağıda eşdeğer Visual Basic kodu verem.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface ISampleService  
  
  <OperationContractAttribute()> _  
  Public Function GetString()As String  
  
  <OperationContractAttribute()> _  
  Public Function GetData() As Integer  
  
End Interface  
```  
  
 `ISampleService` Varsayılan <xref:System.ServiceModel.WSHttpBinding> (varsayılan , varsayılan <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, olan) ile bir uygulama <xref:System.ServiceModel.SecurityMode.Message>ile etkileşimde bulunduğunda, tüm iletiler şifrelenir ve imzalanır, çünkü bu varsayılan koruma düzeyidir. Ancak, bir `ISampleService` hizmet varsayılan <xref:System.ServiceModel.BasicHttpBinding> olarak kullanıldığında <xref:System.ServiceModel.SecurityMode>(varsayılan <xref:System.ServiceModel.SecurityMode.None>, yani), bu bağlama için güvenlik olmadığından tüm iletiler metin olarak gönderilir ve böylece koruma düzeyi yoksayılır (diğer bir şekilde, iletiler ne şifrelenir ne de imzalanır). <xref:System.ServiceModel.SecurityMode> Değiştirilirse, bu iletiler şifrelenir ve imzalanır (çünkü bu artık bağlamanın varsayılan koruma düzeyi <xref:System.ServiceModel.SecurityMode.Message>olacaktır).  
  
 Sözleşmenizin koruma gereksinimlerini açıkça belirtmek veya ayarlamak istiyorsanız, <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> mülkü (veya `ProtectionLevel` daha küçük kapsamdaki özelliklerden herhangi birini) hizmet sözleşmenizin gerektirdiği düzeye ayarlayın. Bu durumda, açık bir ayar kullanarak kullanılan kapsam için en az bu ayarı desteklemek için bağlama gerektirir. Örneğin, aşağıdaki kod <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> `GetGuid` örneği, işlem için açıkça bir değer belirtir.  
  
```csharp  
[ServiceContract]  
public interface IExplicitProtectionLevelSampleService  
{  
  [OperationContractAttribute]  
  public string GetString();  
  
  [OperationContractAttribute(ProtectionLevel=ProtectionLevel.None)]  
  public int GetInt();
  [OperationContractAttribute(ProtectionLevel=ProtectionLevel.EncryptAndSign)]  
  public int GetGuid();
}  
```  
  
 Aşağıda eşdeğer Visual Basic kodu verem.  
  
```vb  
<ServiceContract()> _
Public Interface IExplicitProtectionLevelSampleService
    <OperationContract()> _
    Public Function GetString() As String
    End Function
  
    <OperationContract(ProtectionLevel := ProtectionLevel.None)> _
    Public Function GetInt() As Integer
    End Function
  
    <OperationContractAttribute(ProtectionLevel := ProtectionLevel.EncryptAndSign)> _
    Public Function GetGuid() As Integer
    End Function
  
End Interface  
```  
  
 Bu `IExplicitProtectionLevelSampleService` sözleşmeyi uygulayan ve <xref:System.ServiceModel.WSHttpBinding> varsayılanı (varsayılan <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, <xref:System.ServiceModel.SecurityMode.Message>olan) kullanan bir bitiş noktası olan bir hizmet aşağıdaki davranışa sahiptir:  
  
- İşlem `GetString` iletileri şifrelenir ve imzalanır.  
  
- İşlem `GetInt` iletileri şifrelenmemiş ve imzalanmamış (yani düz) metin olarak gönderilir.  
  
- `GetGuid` İşlem, <xref:System.Guid?displayProperty=nameWithType> şifrelenmiş ve imzalanmış bir iletide döndürülür.  
  
 Koruma düzeyleri ve bunların nasıl kullanılacağı hakkında daha fazla bilgi için [Bkz.](understanding-protection-level.md) Güvenlik hakkında daha fazla bilgi için Güvenlik [Hizmetleri'ne](securing-services.md)bakın.  
  
##### <a name="other-operation-signature-requirements"></a>Diğer İşlem İmza Gereksinimleri  
 Bazı uygulama özellikleri belirli bir tür işlem imzası gerektirir. Örneğin, <xref:System.ServiceModel.NetMsmqBinding> bağlama, bir uygulamanın iletişimin ortasında yeniden başlatılabildiği ve hiçbir iletiyi kaçırmadan kaldığı yerden devam edebileceği dayanıklı hizmetleri ve istemcileri destekler. (Daha fazla bilgi için [WCF'deki Kuyruklar'a](./feature-details/queues-in-wcf.md)bakın.) Ancak, dayanıklı işlemler yalnızca `in` bir parametre almalıdır ve iade değeri yoktur.  
  
 Başka bir örnek, <xref:System.IO.Stream> operasyonlarda türlerin kullanımıdır. Parametre <xref:System.IO.Stream> tüm ileti gövdesini içerdiğinden, bir giriş veya çıktı `ref` (yani `out` parametre, parametre veya <xref:System.IO.Stream>iade değeri) türdeyse, işleminizde belirtilen tek giriş veya çıktı olmalıdır. Buna ek olarak, parametre veya <xref:System.IO.Stream>iade <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>türü <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>, , veya . Akışlar hakkında daha fazla bilgi için [Bkz. Büyük Veri ve Akış.](./feature-details/large-data-and-streaming.md)  
  
##### <a name="names-namespaces-and-obfuscation"></a>Adlar, Ad Alanları ve Gizleme  
 Sözleşmeler wsdl dönüştürüldüğünde ve sözleşme iletileri oluşturulup gönderildiğinde, .NET türlerinin sözleşme ve işlem tanımındaki adları ve ad alanları önemlidir. Bu nedenle, hizmet sözleşmesi adlarının ve ad alanlarının, `Name` `Namespace` <xref:System.ServiceModel.ServiceContractAttribute>, , <xref:System.ServiceModel.OperationContractAttribute>, <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute>, ve diğer sözleşme öznitelikleri gibi tüm destekleyici sözleşme özniteliklerinin ve özelliklerini kullanarak açıkça ayarlanması önerilir.  
  
 Bunun bir sonucu, adlar ve ad alanları açıkça ayarlanmazise, montajda IL gizleme kullanımı sözleşme türü adlarını ve ad alanlarını değiştirir ve genellikle başarısız olan değiştirilmiş WSDL ve tel alışverişi ile sonuçlanır. Sözleşme adlarını ve ad alanlarını açıkça ayarlamaz, ancak gizleme kullanmayı planlıyorsanız, sözleşme türü adlarının ve ad alanlarının değiştirilmesini önlemek için bu <xref:System.Reflection.ObfuscationAttribute> ve <xref:System.Reflection.ObfuscateAssemblyAttribute> öznitelikleri kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: İstek-Yanıt Sözleşmesi Oluşturma](./feature-details/how-to-create-a-request-reply-contract.md)
- [Nasıl yapılır: Tek Yönlü Sözleşme Oluşturma](./feature-details/how-to-create-a-one-way-contract.md)
- [Nasıl yapılır: Çift Yönlü Sözleşme Oluşturma](./feature-details/how-to-create-a-duplex-contract.md)
- [Hizmet Anlaşmalarında Veri Aktarımını Belirtme](./feature-details/specifying-data-transfer-in-service-contracts.md)
- [Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme](specifying-and-handling-faults-in-contracts-and-services.md)
- [Oturumları Kullanma](using-sessions.md)
- [Zaman Uyumlu ve Zaman Uyumsuz İşlemler](synchronous-and-asynchronous-operations.md)
- [Reliable Services](reliable-services.md)
- [Hizmetler ve İşlemler](services-and-transactions.md)
