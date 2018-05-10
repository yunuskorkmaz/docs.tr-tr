---
title: Hizmet Sözleşmeleri Tasarlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF]
ms.assetid: 8e89cbb9-ac84-4f0d-85ef-0eb6be0022fd
ms.openlocfilehash: 163c551103a68ac320e482b1daa0a0c19b2b8fed
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="designing-service-contracts"></a>Hizmet Sözleşmeleri Tasarlama
Bu konuda açıklanmaktadır olan, nasıl tanımlanır, hangi işlemleri kullanılabilir (ve temel alınan ileti alışverişlerinde etkilerini) hangi hizmetin sözleşme, hangi veri türleri olan yardımcı kullanılan ve diğer tasarım sorunları karşılamak işlemleri Senaryonuz gereksinimleri.  
  
## <a name="creating-a-service-contract"></a>Hizmet sözleşmesi oluşturma  
 Hizmetleri işlemleri sayısını kullanıma sunar. Windows Communication Foundation (WCF) uygulamalarında bir yöntem oluşturarak ve onunla işaretleme işlemleri tanımlayan <xref:System.ServiceModel.OperationContractAttribute> özniteliği. Ardından, bir hizmet sözleşmesini oluşturmak için işlemleri, bunları ile işaretli bir arabirim içinde bildirme ya da gruplamak <xref:System.ServiceModel.ServiceContractAttribute> özniteliği ya da göre tanımlama bunları aynı özniteliğiyle işaretlenmiş bir sınıf. (Temel bir örnek için bkz: [nasıl yapılır: bir hizmet sözleşmesini tanımlama](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).)  
  
 Olmayan herhangi bir yöntem bir <xref:System.ServiceModel.OperationContractAttribute> özniteliği hizmet işlemleri değildir ve WCF hizmetleri tarafından açık değildir.  
  
 Bu konuda, bir hizmet sözleşmesini tasarlarken aşağıdaki karar noktalarının açıklanmaktadır:  
  
-   Sınıfları veya arabirimleri kullanılıp kullanılmayacağını belirtir.  
  
-   Exchange istediğiniz veri türlerini belirleme.  
  
-   Kullanabileceğiniz exchange desenleri türleri.  
  
-   Açık güvenlik gereksinimleri sözleşmesinin bir parçası olup olmadığını yapabilirsiniz.  
  
-   İşlem girişleri ve çıkışları kısıtlamaları.  
  
## <a name="classes-or-interfaces"></a>Sınıfları veya arabirimleri  
 Sınıflar ve arabirimler işlevselliği gruplandırması temsil eder ve bu nedenle, her ikisi de bir WCF Hizmeti sözleşmesi tanımlamak için kullanılabilir. Ancak, bunlar doğrudan Hizmet sözleşmeleri model çünkü arabirimleri kullanmanız önerilir. Bir uygulama arabirimler en fazla belirli imzaları yöntemleriyle gruplandırması tanımlar. Bir hizmet sözleşme arabirimi uygulamak ve bir WCF Hizmeti uyguladık.  
  
 Yönetilen arabirimleri tüm avantajlarını hizmet sözleşmesi arabirimleri için geçerlidir:  
  
-   Hizmet sözleşmesi arabirimleri, diğer hizmet sözleşmesi arabirimleri herhangi bir sayıda genişletebilirsiniz.  
  
-   Tek bir sınıf herhangi bir sayıda hizmet sözleşmeleri bu hizmet sözleşmesi arabirimleri uygulayarak uygulayabilirsiniz.  
  
-   Bir hizmet sözleşmesini uygulama, hizmet sözleşmesi aynı kalırken arabirim uygulamasına değiştirerek değiştirebilirsiniz.  
  
-   Eski arabirimi ve yeni bir uygulama tarafından hizmetinizi sürümüyle yapabilirsiniz. Yeni istemciler yeni sürüme bağlanabilirken eski istemciler özgün sürüme bağlanırsınız.  
  
> [!NOTE]
>  Diğer hizmet sözleşmesi arabirimlerinden devralırken adı veya ad alanı gibi işlem özellikleri geçersiz kılamaz. Bunu yapmak çalışırsanız, geçerli hizmet sözleşmesinde yeni işlem oluşturun.  
  
 Bir hizmet sözleşmesini oluşturmak için bir arabirimi kullanarak bir örnek için bkz: [nasıl yapılır: sözleşme arabirimi ile bir hizmet oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md).  
  
 Ancak, bir hizmet sözleşmesini tanımlama ve aynı zamanda bu sözleşmeyi uygulamak için bir sınıf kullanabilirsiniz. Hizmetlerinizin uygulayarak oluşturma avantajı <xref:System.ServiceModel.ServiceContractAttribute> ve <xref:System.ServiceModel.OperationContractAttribute> doğrudan sınıfı ve sınıfı yöntemleri, sırasıyla hızı ve Basitlik sağlamaktır. Olumsuz yönleri şunlardır: yönetilen sınıflar birden çok devralma desteklemez ve sonuç olarak, yalnızca bir hizmet sözleşmesini aynı anda uygulayabilirsiniz. Ayrıca, sınıf veya yöntemin imzaları kendilerine herhangi bir değişiklik değiştirilmemiş istemcilerin hizmetinizi kullanmalarına engel bu hizmet için ortak sözleşme değiştirir. Daha fazla bilgi için bkz: [hizmet sözleşmelerini uygulama](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
 Bir hizmet sözleşmesini oluşturmak için bir sınıf kullanır ve aynı anda uygulayan bir örnek için bkz: [nasıl yapılır: Sözleşme sınıfı ile hizmet oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md).  
  
 Bu noktada, bir arabirim kullanarak ve bir sınıf kullanarak, hizmet sözleşmesini tanımlama arasındaki farkı anlamanız gerekir. Sonraki adım, hangi verilerin geri ve ileri bir hizmet ve istemcileri arasında geçirilebilir karar vermektir.  
  
## <a name="parameters-and-return-values"></a>Parametreler ve dönüş değerleri  
 Bunlar olsa bile, her bir işlemin dönüş değeri ve bir parametre sahip `void`. Ancak, hangi nesnelerin referansları bir nesneden diğerine geçirebilirsiniz yerel bir yöntemini aksine hizmet işlemleri nesnelerin referansları geçmeyin. Bunun yerine, nesnelerin kopyalarını geçirirler.  
  
 Her tür kullanılan bir parametre veya dönüş değeri seri hale getirilebilir önemli olmasıdır; diğer bir deyişle, bu türdeki bir nesneyi bir akışa bayt ve bir nesne içinde bayt akıştan dönüştürmek olası olmalıdır.  
  
 İlkel türler, .NET Framework'teki birçok türleri gibi varsayılan olarak, seri hale getirilebilir.  
  
> [!NOTE]
>  İşlemi imza parametre adlarında değerini sözleşmenin parçası olan ve büyük/küçük harfe duyarlıdır. İstiyorsanız, yerel olarak aynı parametre adı kullanın, ancak yayımlanan meta verilerde adını değiştirebilir, bakın <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>.  
  
#### <a name="data-contracts"></a>Veri Sözleşmeleri  
 Hizmet odaklı uygulamalar Windows Communication Foundation (WCF) uygulamaları gibi istemci uygulamalarını hem Microsoft hem de Microsoft olmayan platformları geniş olası sayısı ile birlikte çalışmak üzere tasarlanmıştır. Geniş olası birlikte çalışabilirlik için türleri ile işaretle önerilir <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> verileri tanımlayan hizmet sözleşmesi kısmı bir veri sözleşmesi oluşturmak için öznitelikleri, hizmet işlemleri Exchange.  
  
 Veri sözleşmeleri olan katılımı stili sözleşmeleri: açıkça veri sözleşmesi özniteliği uyguladığınız sürece hiçbir tür veya veri üyesi seri değildir. Veri sözleşmeleri yönetilen kod erişim kapsamını ilgisiz: özel veri üyeleri serileştirilmiş ve genel olarak erişilebilmesi için başka bir gönderilir. (Bir veri sözleşmesi temel bir örnek için bkz: [nasıl yapılır: bir sınıf veya yapı için temel veri sözleşmesi oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md).) WCF içine ve dışına ileti gövdesini serileştirme, veri türlerinin yanı sıra, işlem işlevselliğini etkinleştirmek temel alınan SOAP iletilerine tanımını işler. Veri türleri seri hale getirilebilir sürece işlemlerinizin tasarlarken, temel alınan ileti exchange altyapı hakkında düşünmek gerekmez.  
  
 Tipik WCF uygulaması kullansa <xref:System.Runtime.Serialization.DataContractAttribute> ve <xref:System.Runtime.Serialization.DataMemberAttribute> işlemleri için veri sözleşmeleri oluşturmak için öznitelikleri diğer serileştirme mekanizmaları kullanabilirsiniz. Standart <xref:System.Runtime.Serialization.ISerializable>, <xref:System.SerializableAttribute> ve <xref:System.Xml.Serialization.IXmlSerializable> mekanizmaları tüm iş veri türlerinizi serileştirme bunları bir uygulamadan diğerine taşımak temel alınan SOAP iletilerine işlemek için. Veri türlerinizi özel destek gerekiyorsa daha fazla seri hale getirme stratejileri tercih edebilirsiniz. WCF uygulamalarda veri türlerini serileştirmek için seçenekler hakkında daha fazla bilgi için bkz: [hizmet sözleşmelerinde veri aktarımı belirtme](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).  
  
#### <a name="mapping-parameters-and-return-values-to-message-exchanges"></a>Parametreler ve dönüş değerleri için ileti alışverişlerinde eşleme  
 Hizmet işlemleri belirli standart güvenlik, işlem ve oturum ilgili özellikleri desteklemek için uygulama tarafından gerekli olan veriler yanı sıra uygulama verilerini geri ve İleri aktarım SOAP iletilerinin temel alınan bir exchange tarafından desteklenir. Bu durumda olduğundan, bir bazı temel bir hizmet işlemi imza belirleyen *ileti değişim deseni* (MEP) veri aktarımı ve bir işlem gerektiren özellikleri destekleyebilir. WCF programlama modelinde üç desenleri belirtebilirsiniz: istek/yanıt, tek yönlü ve çift yönlü ileti desenleri.  
  
##### <a name="requestreply"></a>İstek/yanıt  
 Bir istek/yanıt düzeni isteği gönderen (istemci uygulaması) isteği ile ilişkili bir yanıt alır biridir. Bir veya daha fazla parametre çalışması için geçirilen ve çağırana geri dönüş değeri geçirilen bir işlem desteklediğinden, bu MEP varsayılandır. Örneğin, aşağıdaki C# kod örneğinde bir dize alır ve bir dize döndüren bir temel hizmet işlemi gösterilmektedir.  
  
```csharp  
[OperationContractAttribute]  
string Hello(string greeting);  
```  
  
 Eşdeğer Visual Basic kodu verilmiştir.  
  
```vb  
<OperationContractAttribute()>  
Function Hello (ByVal greeting As String) As String  
```  
  
 Bu işlemi imza formun temel alınan ileti değişimi belirler. Hiçbir bağıntı varsa, WCF işlemi için dönüş değerini yöneliktir belirleyemiyor.  
  
 Bir farklı temel alınan ileti deseni belirtmediğiniz sürece, dönüş hizmet işlemleri bile Not `void` (`Nothing` Visual Basic'te) istek/yanıt ileti alışverişlerinde şunlardır. İşlemi için bir istemci işlemini zaman uyumsuz olarak çağırır sürece, istemci Dönüş iletisinin alınana kadar bu iletiyi normal durumda boş olsa bile işlemeyi durdurur sonucudur. Aşağıdaki C# kod örneği, istemci yanıt olarak boş bir ileti aldı kadar döndürmeyen bir işlem gösterir.  
  
```csharp  
[OperationContractAttribute]  
void Hello(string greeting);  
```  
  
 Eşdeğer Visual Basic kodu verilmiştir.  
  
```vb  
<OperationContractAttribute()>  
Sub Hello (ByVal greeting As String)  
```  
  
 Önceki örnekte istemci performans ve yanıt verme işlemi gerçekleştirmek için çok uzun sürüyor ancak faydası vardır istek/yanıt işlemleri bile döndürmeleri zaman yavaşlatabilir `void`. SOAP hataları iletişimi veya işlem bazı hizmet ile ilgili hata koşulu oluştuğunu gösterir Yanıt iletisindeki döndürülebilecek en bariz adrestir. Bir hizmet sözleşmesinde belirtilen SOAP hataları, istemci uygulamasına olarak geçirilir bir <xref:System.ServiceModel.FaultException%601> nesnesi, burada hizmet sözleşmesinde belirtilen tür, tür parametresi. Bu hata koşulları hakkında bildirimde bulunan istemciler WCF hizmetlerinde kolaylaştırır. Özel durumlar, SOAP hataları ve hata işleme hakkında daha fazla bilgi için bkz: [belirtme ve işleme hataları sözleşme ve hizmetlerde](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md). Bir istek/yanıt hizmet ve istemci bir örnek için bkz [nasıl yapılır: istek-yanıt sözleşmesi oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). İstek-yanıt desen ile ilgili sorunlar hakkında daha fazla bilgi için bkz: [istek-yanıt Hizmetleri](../../../docs/framework/wcf/feature-details/request-reply-services.md).  
  
##### <a name="one-way"></a>Tek yönlü  
 Bir WCF Hizmeti uygulamasının istemci işlemin tamamlanmasını bekleme ve SOAP hataları işlemez işlemi, bir tek yönlü ileti deseni belirtebilirsiniz. Bir tek yönlü işlemi bir istemci bir işlemini çağırır ve WCF ileti ağa yazdırdıktan sonra işleme devam ediyor. Genellikle bu Giden iletiye gönderilen tüm veriler son derece büyük olmadığı sürece istemci hemen çalıştıran devam anlamına gelir (veri gönderilirken bir hata olmadıkça). Bu tür bir ileti değişim deseni bir hizmet uygulaması için bir istemciden olay benzeri davranışını destekler.  
  
 Bir ileti gönderilir ve hiçbir alınan ileti exchange dışındaki bir dönüş değeri belirten bir hizmet işlemi destekleyemiyor `void`; bu durumda bir <xref:System.InvalidOperationException> özel durumu oluşur.  
  
 Dönüş ileti işleme ya da iletişim hatalarını göstermek için döndürülen bir SOAP hatası olabilir anlamına gelir. (İşlemler tek yönlü işlemler olduğunda hata bilgileri iletişim kurulurken bir çift yönlü ileti değişim deseni gerektirir.)  
  
 Tek yönlü ileti değişimi döndüren bir işlem için belirtmek için `void`ayarlayın <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliğine `true`, aşağıdaki C# kod örneğindeki gibi.  
  
```csharp  
[OperationContractAttribute(IsOneWay=true)]  
void Hello(string greeting);  
```  
  
 Eşdeğer Visual Basic kodu verilmiştir.  
  
```vb  
<OperationContractAttribute(IsOneWay := True)>  
Sub Hello (ByVal greeting As String)  
```  
  
 Bu yöntem önceki istek/yanıt örnek, ancak ayarı için aynı olan <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> özelliğine `true` yöntemi aynı olsa da, hizmet işlemi dönen bir ileti göndermek ve istemcilerin dönüş hemen bir kez anlamına gelir Giden message kanal katmana karmalayan. Bir örnek için bkz: [nasıl yapılır: bir One-Way sözleşmesi oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md). Tek yönlü desen hakkında daha fazla bilgi için bkz: [One-Way Hizmetleri](../../../docs/framework/wcf/feature-details/one-way-services.md).  
  
##### <a name="duplex"></a>Çift Yönlü  
 Çift yönlü bir desen iletileri birbirlerine bağımsız olarak kullanarak olup olmadığını tek yönlü gönderme olanağı hem hizmet hem de istemci tarafından belirlenir veya istek/yanıt iletileri. İki yönlü iletişim, bu formu, doğrudan istemciye iletişim kurması gereken hizmetleri veya olay benzeri davranışı dahil olmak üzere bir ileti exchange ya da tarafına zaman uyumsuz bir deneyim sağlamak için kullanışlıdır.  
  
 Çift yönlü düzeni istemcisi ile iletişim kurmak için ek mekanizması nedeniyle istek/yanıt ya da tek yönlü desenleri biraz daha karmaşıktır.  
  
 Çift yönlü sözleşme tasarlamak için de bir geri çağırma sözleşme tasarım ve bu geri çağırma sözleşme türü atamanız gerekir <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> özelliği <xref:System.ServiceModel.ServiceContractAttribute> , hizmet sözleşmesini işaretler özniteliği.  
  
 Çift yönlü bir desen uygulamak için istemcide adlı yöntem bildirimlerini içeren ikinci bir arabirim oluşturmanız gerekir.  
  
 Bir hizmet ve bu hizmete erişen bir istemci oluşturma örneği için bkz: [nasıl yapılır: çift yönlü sözleşme oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md) ve [nasıl yapılır: çift yönlü sözleşme ile Erişim Hizmetleri](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md). Çalışma örnek için bkz: [çift yönlü](../../../docs/framework/wcf/samples/duplex.md). Çift yönlü sözleşmeler kullanarak sorunları hakkında daha fazla bilgi için bkz: [çift yönlü Hizmetler](../../../docs/framework/wcf/feature-details/duplex-services.md).  
  
> [!CAUTION]
>  Bir hizmet çift yönlü bir ileti aldığında bakar `ReplyTo` yanıt gönderileceği yeri belirlemek için bu gelen ileti öğesinde. İleti almak için kullanılan kanalını güvenli hale getirilmemiş sonra güvenilmeyen bir istemci bir hedef makinenin ile kötü amaçlı bir ileti gönderebilir `ReplyTo`, bu hedef makinenin (DOS) hizmet reddine başında.  
  
##### <a name="out-and-ref-parameters"></a>Out ve Ref parametreleri  
 Çoğu durumda, kullandığınız `in` parametreleri (`ByVal` Visual Basic'te) ve `out` ve `ref` parametreleri (`ByRef` Visual Basic'te). Çünkü her ikisi de `out` ve `ref` parametreleri belirtmek veri döndürülen bir işlemi, aşağıdaki gibi bir işlem imza işlemi imza döndürürolsabilebiristek/yanıtişlemigerekliolduğunubelirtir`void`.  
  
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
  
 Yalnızca imzanız özel bir yapı olduğu durumlarda özel durumlardır. Örneğin, kullanabileceğiniz <xref:System.ServiceModel.NetMsmqBinding> bir işlem bildirmek için kullanılan yöntem istemcileri eksikse ile iletişim kurmak için bağlama döndürür `void`; bir dönüş değeri olup hiçbir çıkış değerini olabilir `ref`, veya `out` parametresi.  
  
 Ayrıca, kullanarak `out` veya `ref` parametreleri gerektirir işlemi geri değiştirilmiş nesne taşımak için temel bir yanıt iletisi vardır. İşlemi tek yönlü bir işlem ise bir <xref:System.InvalidOperationException> çalışma zamanında özel durum.  
  
### <a name="specify-message-protection-level-on-the-contract"></a>Sözleşme ileti koruma düzeyi belirtin  
 Sizin tasarlarken, sözleşmesini uygulama hizmetleri ileti koruma düzeyini karar vermeniz gerekir. İleti güvenliği bağlama sözleşmenin uç noktada yalnızca uygulandıysa, bu gereklidir. Bağlama kapalı güvenlik varsa (diğer bir deyişle, sistem tarafından sağlanan bir bağlamayı ayarlarsa <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> değerine <xref:System.ServiceModel.SecurityMode.None?displayProperty=nameWithType>) ileti koruma düzeyi sözleşmesi için karar sahip değil. Çoğu durumda, uygulanan ileti düzeyinde güvenliği olan sistem tarafından sağlanan bağlamalar yeterli bir koruma düzeyi sağlar ve her işlem için veya her ileti için koruma düzeyi göz önünde bulundurmanız gereken değil.  
  
 Koruma düzeyi iletileri (ileti bölümleri) bir hizmet oturumunuz destekleyen imzalanmış ve şifrelenmiş veya imza veya şifreleme gönderilen olup olmadığını belirten bir değerdir. Koruma düzeyi çeşitli kapsamların ayarlanabilir: Bu işlem ya da bir ileti bölümü içindeki bir ileti için belirli bir işlem için hizmet düzeyinde. Bir kapsamda ayarladığınız değerlerini küçük kapsamlar için varsayılan değer açıkça geçersiz kılınmadığı sürece haline gelir. Bağlama yapılandırması sözleşme için gerekli minimum koruma düzeyi sağlayamaz, özel durum oluşur. Ve hiçbir koruma düzeyi değerleri açıkça sözleşme ayarlandığında, ileti güvenliği bağlama varsa, bağlama yapılandırması tüm iletiler için koruma düzeyini denetler. Bu varsayılan davranıştır.  
  
> [!IMPORTANT]
>  Açıkça sözleşmenin çeşitli kapsamlar tam koruma düzeyini çok daha az ayarlanıp ayarlanmayacağını karar <xref:System.Net.Security.ProtectionLevel.EncryptAndSign?displayProperty=nameWithType> genellikle, performansı artırmak için güvenlik bazı derecesini trades bir karardır. Bu durumlarda, kararlarınızı işlemlerinizin ve bunlar exchange verilerin değerini etrafında Uzayda Döndür gerekir. Daha fazla bilgi için bkz: [Hizmetleri güvenli hale getirme](../../../docs/framework/wcf/securing-services.md).  
  
 Örneğin, aşağıdaki kod örneğinde ya da ayarlamaz <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> veya <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> sözleşme özelliği.  
  
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
  
 İle kullanılırken bir `ISampleService` varsayılan bir uç nokta uygulamasında <xref:System.ServiceModel.WSHttpBinding> (varsayılan <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, olduğu <xref:System.ServiceModel.SecurityMode.Message>), tüm iletileri şifrelenir ve bu varsayılan koruma düzeyini olduğundan imzalanmış. Ancak, bir `ISampleService` hizmeti varsayılan olarak kullanılan <xref:System.ServiceModel.BasicHttpBinding> (varsayılan <xref:System.ServiceModel.SecurityMode>, olduğu <xref:System.ServiceModel.SecurityMode.None>), tüm iletileri metin olarak gönderilir, çünkü bu bağlama için güvenlik ve koruma düzeyi göz ardı edilir (diğer bir deyişle, iletileri şifrelenmiş imzalı ne). Varsa <xref:System.ServiceModel.SecurityMode> şekilde değiştirilmiştir <xref:System.ServiceModel.SecurityMode.Message>, bu iletiler şifrelenir ve (, şimdi bağlamanın varsayılan koruma düzeyini olacağından) imzalı sonra.  
  
 Açıkça belirtin veya sizin için koruma gereksinimlerini ayarlamak istiyorsanız, <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> özelliği (ya da herhangi bir `ProtectionLevel` özellikleri daha küçük bir kapsamda), hizmet sözleşmesini düzeyini gerektirir. Bu durumda, açık bir ayarı kullanarak bu ayarı en az kullanılan kapsamın desteklemek bağlama gerektirir. Örneğin, aşağıdaki kod örneğinde bir belirtir <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> değeri açıkça için `GetGuid` işlemi.  
  
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
  
 Bu uygulayan bir hizmet `IExplicitProtectionLevelSampleService` sözleşme ve sahip varsayılan bir uç nokta <xref:System.ServiceModel.WSHttpBinding> (varsayılan <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, olduğu <xref:System.ServiceModel.SecurityMode.Message>) şu davranışa sahiptir:  
  
-   `GetString` İşlemi iletileri şifrelenir ve imzalanmış.  
  
-   `GetInt` Olarak gönderilen iletileri işlemi şifrelenmemiş ve imzalanmamış (diğer bir deyişle, düz) metin.  
  
-   `GetGuid` İşlemi <xref:System.Guid?displayProperty=nameWithType> şifrelenen ve imzalanmış bir ileti döndürdü.  
  
 Koruma düzeyleri ve bunların nasıl kullanılacağını hakkında daha fazla bilgi için bkz: [anlama koruma düzeyi](../../../docs/framework/wcf/understanding-protection-level.md). Güvenlik hakkında daha fazla bilgi için bkz: [Hizmetleri güvenli hale getirme](../../../docs/framework/wcf/securing-services.md).  
  
##### <a name="other-operation-signature-requirements"></a>Diğer işlem imza gereksinimleri  
 Bazı uygulama özellikleri, belirli bir işlemi imza türünü gerektirir. Örneğin, <xref:System.ServiceModel.NetMsmqBinding> bağlama, dayanıklı hizmetler ve bir uygulama ortasında iletişimi yeniden başlatın ve herhangi bir ileti eksik olmadan kaldığı yerden alması istemcileri destekler. (Daha fazla bilgi için bkz: [wcf'de kuyruklar](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).) Dayanıklı işlemleri yalnızca bir ancak almalıdır `in` parametre ve dönüş değeri yok.  
  
 Başka bir örneği kullanımıdır <xref:System.IO.Stream> işlemlerinde türleri. Çünkü <xref:System.IO.Stream> parametresi içeriyorsa tüm ileti gövdesi bir giriş veya çıkış (diğer bir deyişle, `ref` parametresi `out` parametresi veya dönüş değeri) türü <xref:System.IO.Stream>, yalnızca giriş sonra olmalıdır veya çıkış belirtilen, işlem. Ayrıca, parametre veya dönüş türü ya da olması gerekir <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>, veya <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>. Akışları hakkında daha fazla bilgi için bkz: [büyük veriler ve akış](../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
##### <a name="names-namespaces-and-obfuscation"></a>Adları, ad alanları ve gizleme  
 Ad alanları sözleşmeleri ve işlemlerin tanımında .NET türleri ve adları sözleşmeleri WSDL dönüştürüldüğünde ve sözleşme iletileri oluşturduğunuzda ve gönderilen önemlidir. Bu nedenle, hizmet sözleşmesi adları ve ad alanları açıkça kullanarak ayarlandığını önerilir `Name` ve `Namespace` tüm destekleyici özellikleri sözleşme öznitelikleri gibi <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, <xref:System.Runtime.Serialization.DataContractAttribute>,  <xref:System.Runtime.Serialization.DataMemberAttribute>ve diğer sözleşme öznitelikleri.  
  
 Bunun bir sonucu, adları ve ad alanları açıkça ayarlanmazsa, derleme üzerinde IL gizleme kullanımını sözleşme tür adları ad alanlarını ve değiştirilen WSDL ve genellikle başarısız kablo alışverişleri sonuçlarında değiştirir ' dir. Ad alanları ve sözleşme adlarını açıkça ayarlı değil, ancak gizleme kullanmak istiyorsanız, kullanmak <xref:System.Reflection.ObfuscationAttribute> ve <xref:System.Reflection.ObfuscateAssemblyAttribute> sözleşme değiştirilmesini engellemek için öznitelik adları ve ad alanları yazın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: İstek-Yanıt Anlaşması Oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)  
 [Nasıl yapılır: Tek Yönlü Anlaşma Oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md)  
 [Nasıl yapılır: Çift Yönlü Anlaşma Oluşturma](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [Hizmet Anlaşmalarında Veri Aktarımını Belirtme](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 [Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)  
 [Oturumları Kullanma](../../../docs/framework/wcf/using-sessions.md)  
 [Zaman Uyumlu ve Zaman Uyumsuz İşlemler](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)  
 [Güvenilir Hizmetler](../../../docs/framework/wcf/reliable-services.md)  
 [Hizmetler ve İşlemler](../../../docs/framework/wcf/services-and-transactions.md)
