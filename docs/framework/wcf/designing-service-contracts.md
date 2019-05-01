---
title: Hizmet Sözleşmeleri Tasarlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF]
ms.assetid: 8e89cbb9-ac84-4f0d-85ef-0eb6be0022fd
ms.openlocfilehash: 68ea866b736350b8a393d1f4788e4b08754e5ab4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785040"
---
# <a name="designing-service-contracts"></a>Hizmet Sözleşmeleri Tasarlama
Bu konu başlığı altında açıklanır tanımladığınıza göre nasıl tanımlandığını, hangi işlemleri kullanılabilir (ve temel alınan ileti alışverişlerinde etkilerini) hangi hizmet sözleşmeleri, hangi veri türlerini olan yardımcı kullanılan ve diğer sorunları tasarım karşılayan işlemleri Senaryonuz gereksinimleri.  
  
## <a name="creating-a-service-contract"></a>Bir servis sözleşmesi oluşturma  
 Hizmetleri işlemlerinin sayısını kullanıma sunar. Windows Communication Foundation (WCF) uygulamalar, bir yöntem oluşturarak ve kendisiyle işaretlemek işlemleri tanımlayan <xref:System.ServiceModel.OperationContractAttribute> özniteliği. Ardından, hizmet sözleşmesini oluşturmak için operations, bunları ile işaretlenen arabirim içinde bildirme ya da gruplamak <xref:System.ServiceModel.ServiceContractAttribute> özniteliği ya da göre tanımlayarak bunları aynı özniteliği ile işaretlenmiş bir sınıf içinde. (Temel bir örnek için bkz: [nasıl yapılır: Bir hizmet sözleşmesini tanımlama](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).)  
  
 Sahip olmayan herhangi bir yöntem bir <xref:System.ServiceModel.OperationContractAttribute> özniteliği hizmet işlemler ve WCF hizmetleri tarafından açık değildir.  
  
 Bu konu, bir hizmet sözleşmesini tasarlarken aşağıdaki karar noktaları açıklar:  
  
- Sınıf veya arabirim kullanılıp kullanılmayacağını belirtir.  
  
- Değiştirmek istediğiniz veri türlerini belirleme.  
  
- Exchange desenleri kullanabilirsiniz türleri.  
  
- Olup açık güvenlik gereksinimleri sözleşmesinin bir parçası olun.  
  
- İşlem giriş ve çıkışları için kısıtlamaları.  
  
## <a name="classes-or-interfaces"></a>Sınıf veya arabirim  
 Sınıflar ve arabirimler işlevlerin bir gruplandırma temsil eder ve bu nedenle, her ikisi de bir WCF hizmet sözleşmesini tanımlama için kullanılabilir. Ancak, çünkü bunlar Hizmet sözleşmeleri doğrudan model arabirimleri kullanmanız önerilir. Bir uygulama arabirimler en fazla bir gruplandırma belirli imzalarla yöntemlerin tanımlar. Hizmet sözleşmesi arabirimini uygulayan ve bir WCF Hizmeti uyguladıysanız.  
  
 Yönetilen arabirimleri tüm avantajlarını hizmet sözleşme arayüzlere uygulanır:  
  
- Hizmet sözleşmesi arabirimleri, diğer hizmet sözleşme arabirimleri herhangi bir sayıda genişletebilirsiniz.  
  
- Tek bir sınıf herhangi bir sayıda hizmet sözleşmeleri, bu hizmet sözleşmesi arabirimleri uygulayarak uygulayabilirsiniz.  
  
- Bir hizmet sözleşmesini uygulama, arabirim uygulamasına hizmet sözleşmesi aynı kalırken değiştirerek değiştirebilirsiniz.  
  
- Hizmetinizin sürümü eski arabirimi ve yeni bir uygulama tarafından kullanabilirsiniz. En yeni sürüme yeni istemcilerden bağlanabilirsiniz buna karşın eski istemciler, özgün sürümüne bağlanır.  
  
> [!NOTE]
>  Diğer hizmet sözleşme arabirimlerden devralınırken adı veya ad alanı gibi işlem özelliklerini geçersiz kılamazsınız. Bunu yapmayı denerseniz, geçerli hizmet sözleşmesi içerisinde yeni bir işlem oluşturun.  
  
 Bir hizmet sözleşmesini oluşturmak için bir arabirim kullanarak bir örnek için bkz: [nasıl yapılır: Bir sözleşme arabirimi ile hizmet oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md).  
  
 Ancak, bir hizmet sözleşmesini tanımlama ve aynı zamanda bu sözleşmeyi uygulamak için bir sınıf kullanabilirsiniz. Hizmetlerinizi uygulayarak oluşturmanın avantajı <xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> doğrudan sınıf ve sınıftaki yöntemleri, sırasıyla, hız ve kolaylık sağlamaktır. Dezavantajları şunlardır: yönetilen sınıflar birden çok devralmayı desteklemez ve sonuç olarak, yalnızca bir hizmet sözleşmesini aynı anda uygulayabilirsiniz. Ayrıca, sınıf veya yöntem imzaları değişiklik değiştirilmemiş istemciler hizmetinizi kullanılmasını önleyebilir aydaki hizmet için genel sözleşme değiştirir. Daha fazla bilgi için [hizmet sözleşmelerini uygulama](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
 Bir hizmet sözleşmesini oluşturmak için bir sınıf kullanır ve aynı anda uygulayan bir örnek için bkz. [nasıl yapılır: Bir sözleşme sınıfı ile hizmet oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md).  
  
 Bu noktada, bir arabirim kullanarak ve bir sınıf kullanarak, hizmet sözleşmesini tanımlama arasındaki farkı anlamanız gerekir. Sonraki adım, hangi verilerin sürekli hizmet ve istemcileri arasında geçirilebilir karar vermektir.  
  
## <a name="parameters-and-return-values"></a>Parametreler ve dönüş değerleri  
 Bunlar olsa bile, her bir işlemin dönüş değeri ve bir parametre vardır. `void`. Ancak, aksine, nesnelere başvurular bir nesneden diğerine geçirebilirsiniz, yerel bir yöntem hizmet işlemleri nesnelere başvurular kodum'a geçirmez. Bunun yerine, nesneleri kopyalarını geçirin.  
  
 Bu önemlidir, çünkü her türü kullanılan bir parametre veya dönüş değeri seri hale getirilebilir olması gerekir; diğer bir deyişle, bir nesne türü bir nesneye bayt akışı gelen ve Giden bayt akışı dönüştürmek olası olmalıdır.  
  
 Çoğu .NET Framework türleri gibi ilkel türler varsayılan olarak, seri hale getirilebilir.  
  
> [!NOTE]
>  Parametre adları işlemi imzasında değerini sözleşmenin bir parçası olan ve büyük/küçük harfe duyarlıdır. İsterseniz aynı parametre adı yerel olarak kullanmak ancak yayımlanan meta veri adı değiştirmek üzere <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>.  
  
#### <a name="data-contracts"></a>Veri Sözleşmeleri  
 Windows Communication Foundation (WCF) uygulamaları gibi hizmet odaklı uygulamalar, hem Microsoft hem de Microsoft dışındaki platformlar üzerinde istemci uygulamalarının geniş olası sayısı ile çalışmak için tasarlanmıştır. Geniş olası birlikte çalışabilirlik için türlerinizi ile işaretle önerilir <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> bölümüdür verileri tanımlar hizmet sözleşmesinin bir veri anlaşması oluşturmak için öznitelikleri, hizmet işlemlerinizi Exchange.  
  
 Veri sözleşmeleri kabul etme stili sözleşmeleri şunlardır: Veri sözleşmesi öznitelik açıkça uygulamadığınız sürece herhangi bir türü veya veri üyesi seri hale getirilir. Veri sözleşmeleri, yönetilen kod için erişim kapsamı ilgisiz şunlardır: Özel veri üyeleri, serileştirilmiş ve halka açık bir şekilde erişilmesini başka bir yerde gönderilir. (Bir veri anlaşması temel bir örnek için bkz: [nasıl yapılır: Bir sınıf veya yapı için temel veri anlaşması oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md).) WCF içine ve dışına ileti gövdesi, veri türleri serileştirmek yanı sıra tanımını işlemin işlevselliği sağlayan temel SOAP iletilerini işler. Veri türleri, seri hale getirilebilir olduğu sürece, işlemlerinizin tasarlarken temel alınan ileti exchange altyapı konusunda düşünmek gerekmez.  
  
 Genel WCF uygulama kullansa <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> işlemler için veri sözleşmeleri oluşturmak için öznitelikleri diğer serileştirme mekanizmalarını kullanabilirsiniz. Standart <xref:System.Runtime.Serialization.ISerializable>, <xref:System.SerializableAttribute> ve <xref:System.Xml.Serialization.IXmlSerializable> mekanizmaları tüm iş, veri türleri serileştirmek halinde bunları bir uygulamadan diğerine taşımak temel alınan bir SOAP iletilerini işlemek için. Veri türlerinizi özel destek gerekiyorsa daha fazla seri hale getirme stratejileri tercih edebilirsiniz. WCF uygulamaları veri türleri serileştirmek için seçenekler hakkında daha fazla bilgi için bkz. [hizmet sözleşmelerinde veri aktarımı belirtme](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).  
  
#### <a name="mapping-parameters-and-return-values-to-message-exchanges"></a>Parametreler ve dönüş değerleri için ileti alışverişlerinde eşleme  
 Hizmet işlemleri uygulama tarafından belirli bir standart güvenlik, işlem ve oturum güvenlikle ilgili özellikler desteklemek için gerekli olan veriler yanı sıra uygulama verilerinin geri ve İleri aktarım SOAP iletilerinin temel alınan bir exchange tarafından desteklenir. Bu durumda olduğundan, bir hizmet işlemi imzası bir belirli temel belirleyen *ileti değişim deseni* (MEP) veri aktarımı ve bir işlem gerektiren özellikleri destekleyebilir. WCF programlama modeli üç desenleri belirtebilirsiniz: istek/yanıt, tek yönlü ve çift yönlü ileti modeller.  
  
##### <a name="requestreply"></a>İstek/yanıt  
 İstek/yanıt düzeni isteği gönderen (bir istemci uygulaması) ile istek bağıntılı yanıt aldığı biridir. İşlem için geçirilen bir veya daha fazla parametre ve dönüş değeri çağırana geri geçirilen bir işlem desteklediğinden MEP varsayılan değer budur. Örneğin, aşağıdaki C# kod örneğinde, bir dize alır ve bir dize döndüren bir temel hizmet işlemi gösterilmektedir.  
  
```csharp  
[OperationContractAttribute]  
string Hello(string greeting);  
```  
  
 Eşdeğer Visual Basic kodu verilmiştir.  
  
```vb  
<OperationContractAttribute()>  
Function Hello (ByVal greeting As String) As String  
```  
  
 Bu işlemi imza formu, temel alınan ileti değişimi belirler. Hiçbir bağıntı var, WCF işlemi için dönüş değeri kullanılmaya belirlenemiyor.  
  
 Farklı temel alınan ileti desen, belirtmediğiniz sürece, iade hizmet işlemleri bile Not `void` (`Nothing` Visual Basic'te) istek/yanıt ileti alışverişlerinde olan. İşleminiz için bir istemci işlemi zaman uyumsuz olarak çağırır sürece istemci dönüş iletisi alınana kadar ileti normal durumda boş olsa bile işlemeyi durdurur sonucudur. Aşağıdaki C# kod örneği, istemci yanıt olarak boş bir ileti aldı kadar döndürmeyen bir işlem gösterir.  
  
```csharp  
[OperationContractAttribute]  
void Hello(string greeting);  
```  
  
 Eşdeğer Visual Basic kodu verilmiştir.  
  
```vb  
<OperationContractAttribute()>  
Sub Hello (ByVal greeting As String)  
```  
  
 Yukarıdaki örnekte istemci performans ve yanıt verme işlemi gerçekleştirmek için uzun bir süre sürer, ancak avantajları vardır istek/yanıt işlemleri için bile, iade ettiğinizde yavaşlatabilir `void`. SOAP hataları iletişim veya işleme hizmeti ile ilgili hata koşulu oluştuğunu gösterir Yanıt iletisindeki döndürülebilir en belirgin bir bileşendir. Hizmet sözleşmesi içerisinde belirtilen SOAP hataları istemci uygulamasına geçirilir bir <xref:System.ServiceModel.FaultException%601> nesnesi, tür parametresi, hizmet sözleşmesi içerisinde belirtilen tür olduğu. Bu hata durumları hakkında bildirimde bulunan istemciler WCF hizmetlerinde kolaylaştırır. Özel durumlar, SOAP hataları ve hata işleme hakkında daha fazla bilgi için bkz. [belirtme ve işleme hataları sözleşme ve hizmetlerde](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md). Bir istek/yanıt hizmeti ve istemcisine bir örneğini görmek için bkz: [nasıl yapılır: İstek-yanıt anlaşması oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). İstek-yanıt desen ile ilgili sorunlar hakkında daha fazla bilgi için bkz. [istek-yanıt Hizmetleri](../../../docs/framework/wcf/feature-details/request-reply-services.md).  
  
##### <a name="one-way"></a>Tek yönlü  
 Bir WCF hizmeti uygulaması istemci, işlemin tamamlanmasını bekleyin değil ve SOAP hataları işlemez işlemi, tek yönlü mesaj düzeni belirtebilirsiniz. İşlem geri alınamaz bir istemci bir işlem başlatır ve WCF ileti ağa yazdıktan sonra işlemeye devam eder olan biridir. Genellikle bu giden iletide gönderilen tüm veriler son derece büyük olmadığı sürece istemci hemen çalışmaya devam eder, anlamına gelir (veri gönderilirken bir hata olmadıkça). Bu tür bir ileti değişim deseni, bir hizmet uygulaması için bir istemciden olay benzeri davranışını destekler.  
  
 Bir ileti gönderilir ve hiçbiri alınan ileti değişimi dışındaki bir dönüş değeri belirten bir hizmet işlemi destekleyemiyor `void`; bu durumda bir <xref:System.InvalidOperationException> özel durumu oluşturulur.  
  
 Dönüş ileti herhangi bir hata işleme ya da iletişim belirtmek için döndürülen bir SOAP hatası olabilir anlamına gelir. (İşlemler tek yönlü işlem olduğunda hata bilgilerini iletişim kurulurken bir çift yönlü ileti değişim deseni gerektirir.)  
  
 Döndüren bir işlem için bir tek yönlü mesaj exchange belirtmek için `void`ayarlayın <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliğini `true`, aşağıdaki gibi C# kod örneği.  
  
```csharp  
[OperationContractAttribute(IsOneWay=true)]  
void Hello(string greeting);  
```  
  
 Eşdeğer Visual Basic kodu verilmiştir.  
  
```vb  
<OperationContractAttribute(IsOneWay := True)>  
Sub Hello (ByVal greeting As String)  
```  
  
 Bu yöntem, önceki örnek istek/yanıt, ancak ayarı kullanmasıdır <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliğini `true` yöntemi aynı olsa da, hizmet işlemi dönen bir ileti göndermek ve istemcilerin dönüş hemen bir kez anlamına gelir Giden ileti için kanal katmanını teslim. Bir örnek için bkz [nasıl yapılır: Tek yönlü anlaşma oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md). Tek yönlü düzeni hakkında daha fazla bilgi için bkz: [One-Way Hizmetleri](../../../docs/framework/wcf/feature-details/one-way-services.md).  
  
##### <a name="duplex"></a>Çift Yönlü  
 Çift yönlü bir desen iletileri birbirine bağımsız olarak olup olmadığını tek yönlü gönderme olanağı hem hizmet hem de istemci tarafından belirlenir veya istek/yanıt mesajlaşması. Bu tür bir iki yönlü iletişim, istemciye doğrudan iletişim kurması gereken hizmetleri veya her iki tarafında olay benzeri davranış da dahil olmak üzere bir ileti değişimi için zaman uyumsuz bir deneyim sağlamak için kullanışlıdır.  
  
 Çift yönlü istemci ile iletişim kurmak için ek mekanizması nedeniyle istek/yanıt veya tek yönlü desenleri biraz daha karmaşık modelidir.  
  
 Çift yönlü sözleşme tasarlamak için ayrıca bir geri çağırma anlaşması tasarlayın ve için geri çağırma anlaşması türü atamanız gerekir <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> özelliği <xref:System.ServiceModel.ServiceContractAttribute> hizmet sözleşmeniz işaretleyen bir özniteliği.  
  
 Çift yönlü bir desen uygulamak için istemcide çağrılan yöntem bildirimleri içeren ikinci bir arabirim oluşturmanız gerekir.  
  
 Bir hizmet ve bu hizmete erişen bir istemci oluşturma örneği için bkz: [nasıl yapılır: Çift yönlü sözleşme oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md) ve [nasıl yapılır: Çift yönlü sözleşme ile hizmetlere erişme](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md). Çalışma örnek için bkz: [çift yönlü](../../../docs/framework/wcf/samples/duplex.md). Çift yönlü sözleşmeler kullanarak sorunları hakkında daha fazla bilgi için bkz. [çift yönlü Hizmetler](../../../docs/framework/wcf/feature-details/duplex-services.md).  
  
> [!CAUTION]
>  Bir hizmeti çift yönlü bir ileti aldığında bakar `ReplyTo` gelen bu iletide yanıt göndermesi yerini belirlemek için öğesi. İleti almak için kullanılan kanal güvenli sonra güvenilmeyen bir istemci, bir hedef makine ile bir kötü amaçlı iletisi gönderebilir `ReplyTo`, hizmet (DOS) bu hedef makinenin için önde gelen.  
  
##### <a name="out-and-ref-parameters"></a>Out ve Ref parametreleri  
 Çoğu durumda, kullandığınız `in` parametreleri (`ByVal` Visual Basic'te) ve `out` ve `ref` parametreleri (`ByRef` Visual Basic'te). Çünkü her ikisi de `out` ve `ref` parametreleri belirtmek veri dönen bir işlemden bir işlemi aşağıdaki gibi signatura işlemi imza döndürürolsabilebiristek/yanıtişlemigereklidir`void`.  
  
```csharp  
[ServiceContractAttribute]  
public interface IMyContract  
{  
  [OperationContractAttribute]  
  public void PopulateData(ref CustomDataType data);  
}  
```  
  
 Eşdeğer Visual Basic kodu verilmiştir.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface IMyContract  
  <OperationContractAttribute()> _  
  Public Sub PopulateData(ByRef data As CustomDataType)  
End Interface  
```  
  
 Yalnızca imzanızı belirli bir yapı olduğu durumlarda özel durumlardır. Örneğin, kullanabileceğiniz <xref:System.ServiceModel.NetMsmqBinding> bir işlem bildirmek için kullanılan yöntemi yalnızca şu durumlarda istemcileri ile iletişim kurmak için bağlama döndürür `void`; bir dönüş değeri olup olmadığını hiç çıkış değeri olabilir `ref`, veya `out` parametresi.  
  
 Ayrıca, kullanarak `out` veya `ref` parametrelerine gereksinim duyar işlemi değiştirilmiş nesne geri getirmek için temel alınan bir yanıt iletisi vardır. Tek yönlü bir işlem işlemi ise bir <xref:System.InvalidOperationException> çalışma zamanında özel durum harekete geçirilir.  
  
### <a name="specify-message-protection-level-on-the-contract"></a>Sözleşme iletisi koruma düzeyini belirtin  
 Sözleşmeniz tasarlarken, ileti koruma düzeyi sözleşmeniz uygulayan hizmetlerin karar vermeniz gerekir. İleti güvenliği bağlama sözleşmenin uç noktasını yalnızca uygulandıysa, bu gereklidir. Bağlama kapalı güvenlik varsa (diğer bir deyişle, sistem tarafından sağlanan bir bağlamayı ayarlarsa <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> değerine <xref:System.ServiceModel.SecurityMode.None?displayProperty=nameWithType>) ileti koruma düzeyi sözleşmesi için karar vermek üzere yerinizden. Çoğu durumda, sistem tarafından sağlanan bağlamaları uygulanan ileti düzeyi güvenlik ile yeterli bir koruma düzeyi sağlar ve her işlem için veya her ileti için koruma düzeyi düşünmek zorunda değildir.  
  
 Koruma düzeyi iletileri (ileti bölümlerini) bir hizmet oturumunuz destekleyen imzalanmış ve şifrelenmiş veya imza veya şifreleme gönderilen olup olmadığını belirten bir değerdir. Koruma düzeyi, çeşitli kapsamların ayarlanabilir: Hizmet düzeyinde bu işlemi ya da bir ileti bölümü içinde bir ileti için belirli bir işlem için. Bir kapsamda ayarlanmış değerleri daha küçük kapsam için varsayılan değeri açıkça geçersiz kılınmadığı sürece haline gelir. Bir bağlama yapılandırmasını sözleşme için gerekli en düşük koruma düzeyi sağlayamazsa, bir özel durum oluşturulur. Ve hiçbir koruma düzeyi değerleri sözleşme açıkça ayarlandığında, ileti güvenliği bağlama varsa bağlama yapılandırması tüm iletiler için koruma düzeyini denetler. Bu varsayılan davranıştır.  
  
> [!IMPORTANT]
>  Açıkça çeşitli kapsamı sözleşmenin tam koruma düzeyi çok daha az Ayarla karar <xref:System.Net.Security.ProtectionLevel.EncryptAndSign?displayProperty=nameWithType> genel olarak, bazı daha yüksek performans için güvenlik düzeyi arasında denge kurar bir karardır. Bu gibi durumlarda, işlemlerinizin ve bunlar exchange verinin değerinin etrafında kararlarınızı çalışmalarınızı gerekir. Daha fazla bilgi için [Hizmetleri güvenli hale getirme](../../../docs/framework/wcf/securing-services.md).  
  
 Örneğin, aşağıdaki kod örneği ya da ayarlamaz <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> veya <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> sözleşme özelliği.  
  
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
  
 Eşdeğer Visual Basic kodu verilmiştir.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface ISampleService  
  
  <OperationContractAttribute()> _  
  Public Function GetString()As String  
  
  <OperationContractAttribute()> _  
  Public Function GetData() As Integer  
  
End Interface  
```  
  
 İle etkileşimde bulunurken bir `ISampleService` varsayılan bir uç nokta uygulamasında <xref:System.ServiceModel.WSHttpBinding> (varsayılan <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, olduğu <xref:System.ServiceModel.SecurityMode.Message>), tüm iletileri şifrelenir ve varsayılan koruma düzeyini çünkü imzalanmış. Ancak, bir `ISampleService` hizmeti ile bir varsayılan kullanılan <xref:System.ServiceModel.BasicHttpBinding> (varsayılan <xref:System.ServiceModel.SecurityMode>, olduğu <xref:System.ServiceModel.SecurityMode.None>), tüm iletileri metin olarak gönderilir, çünkü bu bağlama için güvenlik ve koruma düzeyi göz ardı edilir (diğer bir deyişle, iletileri şifrelenmiş imzalı ne). Varsa <xref:System.ServiceModel.SecurityMode> değiştirilmiştir <xref:System.ServiceModel.SecurityMode.Message>, bu iletileri şifrelenir ve (Bu artık bağlamanın varsayılan koruma düzeyini olacağından) imzalı sonra.  
  
 Açıkça belirtin veya anlaşmanızda koruma gereksinimleri ayarlamak istiyorsanız, <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> özelliği (veya herhangi bir `ProtectionLevel` özellikleri daha küçük bir kapsamda), hizmet sözleşmesini düzeyini gerektirir. Bu durumda, açık bir ayarı kullanmak için bu ayarı en az kullanılan kapsamın desteklemek bağlama gerekir. Örneğin, aşağıdaki kod örneği bir belirtir <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> değeri açıkça için `GetGuid` işlemi.  
  
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
  
 Eşdeğer Visual Basic kodu verilmiştir.  
  
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
  
 Bu uygulayan bir hizmette `IExplicitProtectionLevelSampleService` sözleşme ve varsayılan bir uç noktaya sahip <xref:System.ServiceModel.WSHttpBinding> (varsayılan <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, olduğu <xref:System.ServiceModel.SecurityMode.Message>) şu davranışa sahiptir:  
  
- `GetString` İşlem iletileri şifrelenir ve imzalanmış.  
  
- `GetInt` İşlemi olarak gönderilen iletileri şifrelenmemiş ve imzalanmamış (diğer bir deyişle, düz) metin.  
  
- `GetGuid` İşlemi <xref:System.Guid?displayProperty=nameWithType> şifrelenmiş ve imzalanmış bir ileti döndürdü.  
  
 Koruma düzeyleri ve bunların nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [anlama koruma düzeyi](../../../docs/framework/wcf/understanding-protection-level.md). Güvenlik hakkında daha fazla bilgi için bkz: [Hizmetleri güvenli hale getirme](../../../docs/framework/wcf/securing-services.md).  
  
##### <a name="other-operation-signature-requirements"></a>Diğer işlem imza gereksinimleri  
 Bazı uygulama özellikleri, belirli bir işlemi imza türünü gerektirir. Örneğin, <xref:System.ServiceModel.NetMsmqBinding> dayanıklı hizmetler ve istemcileri, uygulamanın ortasında iletişim yeniden başlatın ve herhangi bir ileti kaçırmadan kaldığı yerden devam edebiliyorduk bağlamayı destekler. (Daha fazla bilgi için [wcf'de kuyruklar](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).) Dayanıklı işlemler tek ancak almalıdır `in` parametre ve dönüş değeri yoktur.  
  
 Başka bir örnek kullanımıdır <xref:System.IO.Stream> işlemlerinde türleri. Çünkü <xref:System.IO.Stream> bir giriş veya çıkış parametresi içeren tüm ileti gövdesi (diğer bir deyişle, `ref` parametresi `out` parametre veya dönüş değeri) türünde <xref:System.IO.Stream>, ardından yalnızca giriş olmalıdır veya çıkış belirtilmiş, işlem. Ayrıca, parametre veya dönüş türü olmalıdır <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>, veya <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>. Akışlar hakkında daha fazla bilgi için bkz: [büyük veriler ve akış](../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
##### <a name="names-namespaces-and-obfuscation"></a>Ad, ad alanları ve gizleme  
 Ad ve ad alanları sözleşmeler ve işlemler tanımında .NET türleri sözleşmeler WSDL dönüştürülür ve sözleşme iletileri oluşturulan ve gönderilen önemlidir. Bu nedenle, hizmet sözleşmesi adları ve ad alanları açıkça kullanarak ayarlandığını önerilir `Name` ve `Namespace` sözleşme öznitelikleri gibi tüm destekleyici Özellikler <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, <xref:System.Runtime.Serialization.DataContractAttribute>,  <xref:System.Runtime.Serialization.DataMemberAttribute>ve diğer sözleşme öznitelikleri.  
  
 Ad ve ad alanları açıkça ayarlanmazsa, derleme üzerinde IL karartma kullanımını sözleşme türü adları ve ad alanları ve değiştirilen WSDL ve genellikle başarısız bir kablo değişimleri sonuçları değiştirir bunun bir sonucu var. Sözleşme ad ve ad alanları açıkça ayarlamayın ancak karartma kullanmayı planlıyorsanız, kullanmak <xref:System.Reflection.ObfuscationAttribute> ve <xref:System.Reflection.ObfuscateAssemblyAttribute> sözleşme değiştirilmesini önlemek için öznitelik, adları ve ad alanlarını yazın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: İstek-yanıt sözleşmesi oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)
- [Nasıl yapılır: Tek yönlü anlaşma oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md)
- [Nasıl yapılır: Çift yönlü sözleşme oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
- [Hizmet Anlaşmalarında Veri Aktarımını Belirtme](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
- [Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
- [Oturumları Kullanma](../../../docs/framework/wcf/using-sessions.md)
- [Zaman Uyumlu ve Zaman Uyumsuz İşlemler](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
- [Güvenilir Hizmetler](../../../docs/framework/wcf/reliable-services.md)
- [Hizmetler ve İşlemler](../../../docs/framework/wcf/services-and-transactions.md)
