---
title: Hizmet Sözleşmeleri Tasarlama
description: Hizmet sözleşmeleri hakkında bilgi edinin, bunların nasıl oluşturulacağı, kullanılabilir işlemlerin ve veri türlerinin yanı sıra WCF programlamasında hizmet sözleşmelerinin diğer yönlerini öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF]
ms.assetid: 8e89cbb9-ac84-4f0d-85ef-0eb6be0022fd
ms.openlocfilehash: 366157b86ed7c420aed9a3a70838b4d6cd1e451f
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245394"
---
# <a name="designing-service-contracts"></a>Hizmet Sözleşmeleri Tasarlama
Bu konu başlığı altında, hizmet sözleşmelerinin ne olduğu, nasıl tanımlandığı, hangi işlemlerin kullanılabildiği (ve temel alınan ileti değişimlerinin etkileri), hangi veri türlerinin kullanıldığı ve senaryolarınızın gereksinimlerini karşılayan işlemler tasarlamanızı sağlayan diğer sorunlar açıklanmaktadır.  
  
## <a name="creating-a-service-contract"></a>Hizmet sözleşmesi oluşturma  
 Hizmetler çok sayıda işlem sunar. Windows Communication Foundation (WCF) uygulamalarında, bir yöntem oluşturup özniteliği ile işaretleyerek işlemleri tanımlayın <xref:System.ServiceModel.OperationContractAttribute> . Ardından, bir hizmet sözleşmesi oluşturmak için, özniteliğiyle işaretlenmiş bir arabirim içinde bildirerek <xref:System.ServiceModel.ServiceContractAttribute> veya aynı özniteliğiyle işaretlenmiş bir sınıfta tanımlayarak işlemlerinizi birlikte gruplandırın. (Temel bir örnek için bkz. [nasıl yapılır: bir hizmet sözleşmesi tanımlama](how-to-define-a-wcf-service-contract.md).)  
  
 Özniteliği olmayan yöntemler <xref:System.ServiceModel.OperationContractAttribute> hizmet işlemleri değildir ve WCF Hizmetleri tarafından gösterilmez.  
  
 Bu konuda, bir hizmet sözleşmesi tasarlarken aşağıdaki karar noktaları açıklanmaktadır:  
  
- Sınıfların veya arabirimlerin kullanılıp kullanılmayacağını belirtir.  
  
- Exchange 'de kullanmak istediğiniz veri türlerini belirtme.  
  
- Kullanabileceğiniz Exchange desenlerinin türleri.  
  
- Açık güvenlik gereksinimlerini sözleşmenin bir parçası yapıp yapamayacağı.  
  
- İşlem girişleri ve çıkışları için kısıtlamalar.  
  
## <a name="classes-or-interfaces"></a>Sınıflar veya arabirimler  
 Her iki sınıf ve arabirim de bir işlev gruplandırmasını temsil eder ve bu nedenle, her ikisi de bir WCF hizmeti sözleşmesi tanımlamak için kullanılabilir. Ancak, hizmet sözleşmelerini doğrudan modellerse, arabirimleri kullanmanız önerilir. Bir uygulama olmadan, arabirimler belirli imzalara sahip bir yöntem gruplandırması tanımlamaktan daha fazla olmaz. Bir hizmet sözleşmesi arabirimi uygulayın ve bir WCF hizmeti uyguladık.  
  
 Yönetilen arabirimlerin tüm avantajları hizmet sözleşmesi arabirimleri için geçerlidir:  
  
- Hizmet sözleşmesi arabirimleri, herhangi bir sayıda diğer hizmet sözleşmesi arabirimini genişletebilir.  
  
- Tek bir sınıf, bu hizmet sözleşmesi arabirimlerini uygulayarak herhangi bir sayıda hizmet sözleşmesi uygulayabilir.  
  
- Hizmet sözleşmesi aynı olmaya devam ederken, bir hizmet sözleşmesinin uygulanmasını, arabirim uygulamasını değiştirerek değiştirebilirsiniz.  
  
- Eski arabirimi ve yenisini uygulayarak hizmetinizi sürüm sürümüne ekleyebilirsiniz. Eski istemciler özgün sürüme bağlanır, daha yeni istemciler yeni sürüme bağlanabilir.  
  
> [!NOTE]
> Diğer hizmet sözleşmesi arabirimlerinden devralma sırasında, ad veya ad alanı gibi işlem özelliklerini geçersiz kılamazsınız. Bunu yapmayı denerseniz, geçerli hizmet sözleşmesinde yeni bir işlem oluşturursunuz.  
  
 Bir hizmet sözleşmesi oluşturmak için arabirim kullanmanın bir örneği için bkz. [nasıl yapılır: sözleşme arabirimi Ile hizmet oluşturma](./feature-details/how-to-create-a-service-with-a-contract-interface.md).  
  
 Bununla birlikte, bir hizmet sözleşmesi tanımlamak ve bu sözleşmeyi aynı anda uygulamak için bir sınıfı kullanabilirsiniz. , <xref:System.ServiceModel.ServiceContractAttribute> Ve sırasıyla sınıfına ve <xref:System.ServiceModel.OperationContractAttribute> sınıf üzerindeki yöntemlere uygulama yaparak ve doğrudan, hız ve kolaylık sağlar. Dezavantajları, yönetilen sınıfların birden çok devralmayı desteklememe ve sonuç olarak yalnızca bir hizmet sözleşmesini tek seferde uygulayabilecekleri bir dezavantajlardır. Ayrıca, sınıf veya yöntem imzalarında yapılan herhangi bir değişiklik söz konusu hizmet için genel sözleşmeyi değiştirir ve bu da, değiştirilmemiş istemcilerin hizmetinizi kullanmasını engelleyebilir. Daha fazla bilgi için bkz. [hizmet sözleşmelerini uygulama](implementing-service-contracts.md).  
  
 Bir hizmet sözleşmesi oluşturmak için bir sınıf kullanan ve aynı anda uygulayan bir örnek için bkz. [nasıl yapılır: bir sözleşme sınıfı Ile hizmet oluşturma](./feature-details/how-to-create-a-wcf-contract-with-a-class.md).  
  
 Bu noktada, bir arabirim kullanarak ve bir sınıfı kullanarak hizmet sözleşmenizi tanımlama arasındaki farkı anlamalısınız. Bir sonraki adım, bir hizmet ve istemcileri arasında hangi verilerin geri geçirilebileceğini saptarken.  
  
## <a name="parameters-and-return-values"></a>Parametreler ve dönüş değerleri  
 Her işlemin bir dönüş değeri ve parametresi vardır, ancak bunlar da vardır `void` . Ancak, bir yerel yöntemin aksine, bir nesneden diğerine başvuruları geçirebilmeniz için, hizmet işlemleri nesnelere başvuruları geçirmez. Bunun yerine, nesnelerin kopyalarını iletir.  
  
 Bu çok önemlidir çünkü bir parametre veya dönüş değerinde kullanılan her tür seri hale getirilebilir olmalıdır; diğer bir deyişle, bu türdeki bir nesneyi bayt akışına ve bayt akışından bir nesneye dönüştürmek mümkün olmalıdır.  
  
 Temel türler, .NET Framework birçok tür olduğu gibi varsayılan olarak seri hale getirilebilir.  
  
> [!NOTE]
> İşlem imzasında parametre adlarının değeri sözleşmenin bir parçasıdır ve büyük/küçük harfe duyarlıdır. Aynı parametre adını yerel olarak kullanmak ancak yayımlanan meta verilerde adı değiştirmek istiyorsanız, bkz <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType> ..  
  
#### <a name="data-contracts"></a>Veri Sözleşmeleri  
 Windows Communication Foundation (WCF) uygulamaları gibi hizmet odaklı uygulamalar, hem Microsoft hem de Microsoft dışı platformlarda en yüksek sayıda istemci uygulaması ile birlikte çalışmak üzere tasarlanmıştır. Mümkün olan en iyi birlikte çalışabilirlik için, hizmet <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> sözleşmesinin, hizmet işlem alışverişi yaptığınız verileri açıklayan bölümü olan bir veri sözleşmesi oluşturmak için türlerinizi ve öznitelikleriyle işaretlemeniz önerilir.  
  
 Veri sözleşmeleri, kabul etme stil sözleşmeleri: veri sözleşmesi özniteliğini açıkça uygulamadığınız takdirde hiçbir tür veya veri üyesi serileştirilmez. Veri sözleşmeleri, yönetilen kodun erişim kapsamıyla ilişkili değildir: özel veri üyeleri seri hale getirilebilir ve başka bir yere erişilebilmesi adına gönderilebilir. (Bir veri sözleşmesinin temel bir örneği için bkz. [nasıl yapılır: bir sınıf veya yapı Için temel veri sözleşmesi oluşturma](./feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md).) WCF, işlemin işlevselliğini etkinleştiren temel SOAP iletilerinin tanımını ve iletilerin gövdesine ve veri türlerinizi serileştirmesini sağlar. Veri türlerinizin seri hale getirilebilir olduğu sürece, işlemlerinizi tasarlarken temeldeki ileti değişim altyapısı hakkında düşünmeniz gerekmez.  
  
 Tipik WCF uygulaması, <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> işlemler için veri sözleşmeleri oluşturmak üzere ve özniteliklerini kullansa da, diğer serileştirme mekanizmalarını kullanabilirsiniz. Standart <xref:System.Runtime.Serialization.ISerializable> , <xref:System.SerializableAttribute> ve mekanizmaları, <xref:System.Xml.Serialization.IXmlSerializable> veri türlerinizin serileştirmesini bir uygulamadan diğerine taşıyan temel alınan SOAP iletilerine işlemek için çalışır. Veri türlerinizin özel destek gerektirmesi durumunda daha fazla serileştirme stratejileri kullanabilirsiniz. WCF uygulamalarında veri türlerini serileştirme seçimleri hakkında daha fazla bilgi için bkz. [hizmet sözleşmeleri içinde veri aktarımı belirtme](./feature-details/specifying-data-transfer-in-service-contracts.md).  
  
#### <a name="mapping-parameters-and-return-values-to-message-exchanges"></a>Parametreleri eşleme ve dönüş değerleri Ileti alışverişlerine  
 Hizmet işlemleri, uygulamanın belirli standart güvenlik, işlem ve oturumla ilgili özelliklerini desteklemesi için gereken verilere ek olarak, uygulama verilerini geri ve geriye doğru bir şekilde veren bir dizi SOAP iletisi tarafından desteklenir. Bu durum, bir hizmet işleminin imzası, veri aktarımını destekleyebilen belirli bir temel *ileti değişim modelini* (MEP) ve bir işlemin gerektirdiği özellikleri belirler. WCF programlama modelinde üç desen belirtebilirsiniz: istek/yanıt, tek yönlü ve çift yönlü ileti desenleri.  
  
##### <a name="requestreply"></a>İstek/yanıt  
 İstek/yanıt deseninin bir istek gönderici (istemci uygulaması), isteğin bağıntılı olduğu bir yanıt aldığı bir yanıt alır. Bu varsayılan MEP 'dir çünkü bir veya daha fazla parametrenin işleme geçirildiği bir işlemi desteklediğinden ve dönüş değeri çağırana geri geçirilir. Örneğin, aşağıdaki C# kod örneği, bir dize alan ve bir dize döndüren temel bir hizmet işlemini gösterir.  
  
```csharp  
[OperationContractAttribute]  
string Hello(string greeting);  
```  
  
 Eşdeğer Visual Basic kodu aşağıda verilmiştir.  
  
```vb  
<OperationContractAttribute()>  
Function Hello (ByVal greeting As String) As String  
```  
  
 Bu işlem imzası, temeldeki ileti değişimi formunu belirler. Hiçbir bağıntı yoksa, WCF döndürülen değeri hangi işlemin amaçladığı belirlenemiyor.  
  
 Farklı bir temel alınan ileti deseninin belirtilmediği, hatta (Visual Basic) döndürülen hizmet işlemlerinin `void` `Nothing` istek/yanıt iletisi değişimlerinin olduğunu unutmayın. İşlem için sonuç, bir istemci işlemi zaman uyumsuz olarak çağırmadığı sürece istemci, normal durumda bu ileti boş olsa bile, döndürülen ileti alınana kadar işlemeyi durduruyor. Aşağıdaki C# kod örneği, istemciye yanıt olarak boş bir ileti alınana kadar döndürmeyen bir işlemi gösterir.  
  
```csharp  
[OperationContractAttribute]  
void Hello(string greeting);  
```  
  
 Eşdeğer Visual Basic kodu aşağıda verilmiştir.  
  
```vb  
<OperationContractAttribute()>  
Sub Hello (ByVal greeting As String)  
```  
  
 Yukarıdaki örnek, işlemin gerçekleştirmesi uzun sürerse istemci performansını ve yanıt hızını yavaşlatabilir, ancak geri dönseler bile istek/yanıt işlemlerinin avantajları vardır `void` . En belirgin bir tane, yanıt iletisinde SOAP hatalarının döndürülmesinin, iletişim veya işleme durumunda, hizmetle ilgili bir hata koşulunun oluştuğunu belirten bir durumdur. Bir hizmet sözleşmesinde belirtilen SOAP hataları istemci uygulamasına bir nesne olarak geçirilir <xref:System.ServiceModel.FaultException%601> , burada tür parametresi hizmet sözleşmesinde belirtilen türdür. Bu, istemcilerin WCF hizmetlerindeki hata koşullarını kolay bir şekilde bildirmesini sağlar. Özel durumlar, SOAP hataları ve hata işleme hakkında daha fazla bilgi için bkz. [anlaşmalar ve hizmetlerde hataları belirtme ve işleme](specifying-and-handling-faults-in-contracts-and-services.md). İstek/yanıt hizmeti ve istemcisinin bir örneğini görmek için bkz. [nasıl yapılır: istek-yanıt sözleşmesi oluşturma](./feature-details/how-to-create-a-request-reply-contract.md). İstek-yanıt düzeniyle ilgili sorunlar hakkında daha fazla bilgi için bkz. [istek-yanıt Hizmetleri](./feature-details/request-reply-services.md).  
  
##### <a name="one-way"></a>Tek yönlü  
 Bir WCF hizmet uygulamasının istemcisi işlemin tamamlanmasını bekleyemez ve SOAP hatalarını işlemezse, işlem tek yönlü bir ileti kalıbı belirtebilir. Tek yönlü bir işlem, istemcinin bir işlemi çağırdığı ve WCF iletiyi ağa yazdığında işleme devam eden bir işlemdir. Genellikle bu, giden mesajda gönderilen verilerin son derece büyük olması durumunda istemcinin neredeyse hemen çalışmaya devam ettiğinden (verileri gönderirken bir hata olmadığı anlamına gelir.) Bu tür bir ileti değişimi stili istemciden bir hizmet uygulamasına olay benzeri davranışı destekler.  
  
 Bir iletinin gönderildiği ve hiçbirinin alındığı bir ileti değişimi, dışında bir dönüş değeri belirten bir hizmet işlemini desteklemez `void` ; Bu durumda bir <xref:System.InvalidOperationException> özel durum oluşturulur.  
  
 Dönüş iletisi yok, işleme veya iletişimdeki hataları göstermek için hiçbir SOAP hatası döndürülmeyeceği anlamına gelir. (İşlemler tek yönlü işlemler olduğunda hata bilgilerini iletişim kurmak bir çift yönlü ileti değişimi deseninin olması gerekir.)  
  
 Döndüren bir işlem için tek yönlü bir ileti değişimi belirtmek için, `void` <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> `true` Aşağıdaki C# kod örneğinde olduğu gibi özelliğini olarak ayarlayın.  
  
```csharp  
[OperationContractAttribute(IsOneWay=true)]  
void Hello(string greeting);  
```  
  
 Eşdeğer Visual Basic kodu aşağıda verilmiştir.  
  
```vb  
<OperationContractAttribute(IsOneWay := True)>  
Sub Hello (ByVal greeting As String)  
```  
  
 Bu yöntem, önceki istek/yanıt örneği ile aynıdır, ancak <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliğinin olarak ayarlanması, `true` Yöntem özdeş olsa da, hizmet işlemi bir dönüş iletisi göndermese ve giden ileti Kanal katmanına alındıktan sonra istemcilerin hemen geri döndürdüğü anlamına gelir. Bir örnek için bkz. [nasıl yapılır: tek yönlü sözleşme oluşturma](./feature-details/how-to-create-a-one-way-contract.md). Tek yönlü bir model hakkında daha fazla bilgi için bkz. [tek yönlü hizmetler](./feature-details/one-way-services.md).  
  
##### <a name="duplex"></a>Çift Yönlü  
 Çift yönlü bir model, tek yönlü veya istek/yanıt mesajlaşması gibi, her iki hizmetin ve istemcinin birbirlerine ayrı ayrı ileti gönderebilme özelliği tarafından belirlenir. Bu iki yönlü iletişim biçimi, istemci ile doğrudan iletişim kurması gereken veya olay benzeri davranışlar da dahil olmak üzere ileti değişimi 'nin her tarafında zaman uyumsuz bir deneyim sağlamaya yönelik hizmetler için yararlıdır.  
  
 İstemci ile iletişim kurmak için ek mekanizma nedeniyle, çift yönlü deseni istek/yanıt veya tek yönlü desenlerden biraz daha karmaşıktır.  
  
 Bir çift yönlü sözleşme tasarlamak için, bir geri çağırma anlaşması tasarlaması ve bu geri çağırma sözleşmesinin türünü, <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> <xref:System.ServiceModel.ServiceContractAttribute> hizmet sözleşmenizi işaretleyen özniteliğin özelliğine atamanız gerekir.  
  
 Çift yönlü bir model uygulamak için, istemcisinde çağrılan yöntem bildirimlerini içeren ikinci bir arabirim oluşturmanız gerekir.  
  
 Bir hizmet ve bu hizmete erişen bir istemci oluşturma örneği için bkz. [nasıl yapılır: çift yönlü sözleşme oluşturma](./feature-details/how-to-create-a-duplex-contract.md) ve [nasıl yapılır: çift yönlü sözleşme ile hizmetlere erişme](./feature-details/how-to-access-services-with-a-duplex-contract.md). Çalışan bir örnek için bkz. [çift yönlü](./samples/duplex.md). Çift yönlü sözleşmeleri kullanma sorunları hakkında daha fazla bilgi için bkz. [çift yönlü hizmetler](./feature-details/duplex-services.md).  
  
> [!CAUTION]
> Bir hizmet çift yönlü bir ileti aldığında, `ReplyTo` yanıtın nereye gönderileceğini belirlemede bu gelen iletideki öğesine bakar. İletiyi almak için kullanılan kanal güvenli değilse, güvenilmeyen bir istemci, hedef makinenin bir `ReplyTo` hizmet reddi (DOS) için önde gelen kötü amaçlı bir ileti gönderebilir.  
  
##### <a name="out-and-ref-parameters"></a>Out ve ref parametreleri  
 Çoğu durumda, `in` parametreleri ( `ByVal` Visual Basic) ve `out` `ref` parametrelerini ve parametrelerini ( `ByRef` Visual Basic) kullanabilirsiniz. Hem hem `out` de `ref` parametreleri verilerin bir işlemden döndürüldüğünü belirttiğinden, aşağıdaki gibi bir işlem imzası, işlem imzası dönüşmesine rağmen bir istek/yanıt işleminin gerekli olduğunu belirtir `void` .  
  
```csharp  
[ServiceContractAttribute]  
public interface IMyContract  
{  
  [OperationContractAttribute]  
  public void PopulateData(ref CustomDataType data);  
}  
```  
  
 Eşdeğer Visual Basic kodu aşağıda verilmiştir.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface IMyContract  
  <OperationContractAttribute()> _  
  Public Sub PopulateData(ByRef data As CustomDataType)  
End Interface  
```  
  
 Tek özel durumlar, imzanızın belirli bir yapıya sahip olduğu durumlardır. Örneğin, <xref:System.ServiceModel.NetMsmqBinding> yalnızca bir işlemi bildirmek için kullanılan yöntem geri dönerse istemcilerle iletişim kurmak için bağlamayı kullanabilirsiniz `void` ; bir dönüş değeri, veya parametresi olup olmadığı, çıkış değeri olamaz `ref` `out` .  
  
 Ayrıca, `out` veya parametrelerinin kullanılması, `ref` değiştirilen nesneyi geri almak için işlemin temeldeki bir yanıt iletisine sahip olmasını gerektirir. İşlem tek yönlü bir işlem ise, <xref:System.InvalidOperationException> çalışma zamanında bir özel durum oluşturulur.  
  
### <a name="specify-message-protection-level-on-the-contract"></a>Sözleşmede Ileti koruma düzeyini belirtin  
 Sözleşmenizi tasarlarken, sözleşmenizi uygulayan hizmetlerin ileti koruma düzeyine de karar vermelisiniz. Bu yalnızca, Sözleşmenin uç noktasındaki bağlamaya ileti güvenliği uygulanırsa gereklidir. Bağlamanın güvenliği kapalıysa (yani, sistem tarafından sağlanmış bağlama <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> değerini değerine ayarlarsa <xref:System.ServiceModel.SecurityMode.None?displayProperty=nameWithType> ), sözleşmenin ileti koruma düzeyine karar vermeniz gerekmez. Çoğu durumda, ileti düzeyinde güvenlik uygulanmış sistem tarafından sunulan bağlamalar yeterli bir koruma düzeyi sağlar ve her bir işlemin veya her ileti için koruma düzeyini dikkate almanız gerekmez.  
  
 Koruma düzeyi, bir hizmeti destekleyen mesajların (veya ileti bölümlerinin) imzalı, imzalanmış ve şifrelenmiş olduğunu veya imza ya da şifreleme olmadan gönderilip gönderilmeyeceğini belirten bir değerdir. Koruma düzeyi çeşitli kapsamlara ayarlanabilir: hizmet düzeyinde belirli bir işlem için, söz konusu işlem içindeki bir ileti veya bir ileti bölümü. Açık olarak geçersiz kılınmadıkça, bir kapsamda ayarlanan değerler daha küçük kapsamlar için varsayılan değer olur. Bir bağlama yapılandırması, sözleşme için gereken en düşük koruma düzeyini sağlayabilirse, bir özel durum oluşturulur. Anlaşma üzerinde hiçbir koruma düzeyi değeri açıkça ayarlanmamışsa bağlama yapılandırması, bağlamada ileti güvenliği varsa tüm iletiler için koruma düzeyini denetler. Bu, varsayılan davranıştır.  
  
> [!IMPORTANT]
> Bir sözleşmenin tam koruma düzeyinden daha düşük bir şekilde farklı bir şekilde bir şekilde ayarlanması gerektiğine karar vermek <xref:System.Net.Security.ProtectionLevel.EncryptAndSign?displayProperty=nameWithType> , daha fazla performans elde etmek için bir ölçüde güvenlik artışı sağlayan bir karardır. Bu durumlarda kararlarınız, işlemlerinizin yanı sıra, değişdikleri verilerin değerini döndürmelidir. Daha fazla bilgi için bkz. [hizmetleri güvenli hale getirme](securing-services.md).  
  
 Örneğin, aşağıdaki kod örneği sözleşmede ya da <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> özelliğini ayarlamayın.  
  
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
  
 Eşdeğer Visual Basic kodu aşağıda verilmiştir.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface ISampleService  
  
  <OperationContractAttribute()> _  
  Public Function GetString()As String  
  
  <OperationContractAttribute()> _  
  Public Function GetData() As Integer  
  
End Interface  
```  
  
 Bir `ISampleService` uç noktada varsayılan olan bir uygulamayla etkileşim kurarken <xref:System.ServiceModel.WSHttpBinding> (varsayılan <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> olan <xref:System.ServiceModel.SecurityMode.Message> ), bu varsayılan koruma düzeyi olduğundan tüm iletiler şifrelenir ve imzalanır. Bununla birlikte, bir `ISampleService` hizmet varsayılan <xref:System.ServiceModel.BasicHttpBinding> olarak kullanıldığında (varsayılan olarak <xref:System.ServiceModel.SecurityMode> <xref:System.ServiceModel.SecurityMode.None> ), bu bağlama için güvenlik olmadığı ve koruma düzeyi yok sayılacak (yani, iletiler şifrelenmez veya imzalanmamışsa) tüm iletiler metin olarak gönderilir. <xref:System.ServiceModel.SecurityMode>Olarak değiştirilmişse <xref:System.ServiceModel.SecurityMode.Message> , bu iletiler şifrelenir ve imzalanır (Bu, şimdi bağlamanın varsayılan koruma düzeyi olacağından).  
  
 Sözleşmeniz için koruma gereksinimlerini açıkça belirtmek veya ayarlamak istiyorsanız, <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> Özelliği (veya `ProtectionLevel` daha küçük bir kapsamdaki özelliklerden herhangi biri), hizmet sözleşmeniz için gereken düzeye ayarlayın. Bu durumda, bir açık ayarı kullanmak için bağlama, kullanılan kapsamda en düşük düzeyde bu ayarı desteklemek için gereklidir. Örneğin, aşağıdaki kod örneği <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> işlem için açıkça bir değeri belirtir `GetGuid` .  
  
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
  
 Eşdeğer Visual Basic kodu aşağıda verilmiştir.  
  
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
  
 Bu `IExplicitProtectionLevelSampleService` sözleşmeyi uygulayan ve varsayılan olan (varsayılan olan) bir uç noktaya sahip bir hizmet <xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> <xref:System.ServiceModel.SecurityMode.Message> aşağıdaki davranışa sahiptir:  
  
- `GetString`İşlem iletileri şifrelenir ve imzalanır.  
  
- `GetInt`İşlem iletileri şifrelenmemiş ve işaretsiz (yani düz) metin olarak gönderilir.  
  
- `GetGuid`İşlem <xref:System.Guid?displayProperty=nameWithType> şifrelenmiş ve imzalı bir ileti ile döndürülür.  
  
 Koruma düzeyleri ve bunların nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [koruma düzeyini anlama](understanding-protection-level.md). Güvenlik hakkında daha fazla bilgi için bkz. [hizmetleri güvenli hale getirme](securing-services.md).  
  
##### <a name="other-operation-signature-requirements"></a>Diğer Işlem Imzası gereksinimleri  
 Bazı uygulama özellikleri belirli bir işlem imzası türü gerektirir. Örneğin, <xref:System.ServiceModel.NetMsmqBinding> bağlama sürekli Hizmetleri ve istemcileri destekler, bu da bir uygulamanın iletişimin ortasında yeniden başlatabileceği ve herhangi bir ileti olmadan kaldığınız yerden çekilebildiği durumlarda. (Daha fazla bilgi için bkz. [WCF 'de kuyruklar](./feature-details/queues-in-wcf.md).) Ancak, dayanıklı işlemler yalnızca bir parametre almalıdır `in` ve dönüş değeri içermemelidir.  
  
 İşlemler içindeki türlerin kullanımı başka bir örnektir <xref:System.IO.Stream> . <xref:System.IO.Stream>Parametresi tüm ileti gövdesini içerdiğinden, bir giriş veya çıkış (bir `ref` parametre, `out` parametre veya dönüş değeri) türünde ise <xref:System.IO.Stream> , bu, işlem sırasında belirtilen tek giriş veya çıkış olmalıdır. Ayrıca, parametre veya dönüş türü, ya da olmalıdır <xref:System.IO.Stream> <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType> . Akışlar hakkında daha fazla bilgi için bkz. [büyük veri ve akış](./feature-details/large-data-and-streaming.md).  
  
##### <a name="names-namespaces-and-obfuscation"></a>Adlar, ad alanları ve gizleme  
 Sözleşmelerin ve işlemlerin tanımındaki .NET türlerinin adları ve ad alanları, sözleşmeler WSDL 'ye dönüştürüldüğünde ve sözleşme iletileri oluşturulup gönderildiğinde önemlidir. Bu nedenle, hizmet sözleşmesi adları ve ad alanlarının,,,, `Name` `Namespace` <xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.OperationContractAttribute> <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> ve diğer sözleşme öznitelikleri gibi tüm destekleyici anlaşma özniteliklerinin ve özelliklerinin kullanılarak açıkça ayarlanması önemle önerilir.  
  
 Bunun bir sonucu olarak, adlar ve ad alanları açıkça ayarlanmamışsa, derlemede Il gizleme kullanımı, anlaşma türü adlarını ve ad alanlarını değiştirir ve genellikle başarısız olan değiştirilmiş WSDL ve tel değişimleriyle sonuçlanır. Anlaşma adlarını ve ad alanlarını açıkça ayarlamazsanız ancak gizleme kullanmayı planlıyorsanız, <xref:System.Reflection.ObfuscationAttribute> <xref:System.Reflection.ObfuscateAssemblyAttribute> sözleşme türü adlarının ve ad alanlarının değiştirilmesini engellemek için ve özniteliklerini kullanın.  
  
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
