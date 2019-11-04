---
title: Hizmet Sürümü Oluşturma
ms.date: 03/30/2017
ms.assetid: 37575ead-d820-4a67-8059-da11a2ab48e2
ms.openlocfilehash: 3f9fd87eacf67a1b23568dcf87df086e935879ba
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423680"
---
# <a name="service-versioning"></a>Hizmet Sürümü Oluşturma
İlk dağıtımdan sonra ve yaşam süreleri (ve sergiledikleri uç noktalar) sırasında, iş ihtiyaçlarını değiştirme, bilgi teknolojisi gereksinimleri gibi çeşitli nedenlerle değişiklik yapılması veya diğer sorunları ele almanız gerekebilir çıkışları. Her değişiklik, hizmetin yeni bir sürümünü kullanıma sunar. Bu konu, Windows Communication Foundation (WCF) sürümünde sürüm oluşturmayı nasıl düşüntireceğinizi açıklamaktadır.  
  
## <a name="four-categories-of-service-changes"></a>Dört hizmet kategorisi değişikliği  
 Gerekebilecek hizmetlerde yapılan değişiklikler dört kategoride sınıflandırılabilir:  
  
- Sözleşme değişiklikleri: Örneğin, bir işlem eklenebilir veya bir iletideki veri öğesi eklenebilir veya değiştirilebilir.  
  
- Adres değişiklikleri: Örneğin, bir hizmet, uç noktaların yeni adreslere sahip olduğu farklı bir konuma geçer.  
  
- Bağlantı değişiklikleri: Örneğin, bir güvenlik mekanizması değişir veya ayarları değişir.  
  
- Uygulama değişiklikleri: Örneğin, bir iç Yöntem uygulamasında değişiklik yapıldığında.  
  
 Bu değişikliklerden bazıları "kırın" olarak, diğerleri ise "bölünemez" olarak adlandırılır. Önceki sürümde başarıyla işlenen tüm iletiler yeni sürümde başarıyla işlenirse bir değişiklik *bölünemez* . Bu ölçütü karşılamayan herhangi bir değişiklik, bir *son* değişiklik olur.  
  
## <a name="service-orientation-and-versioning"></a>Hizmet yönü ve sürüm oluşturma  
 Hizmet yönünün her biri, hizmetlerin ve istemcilerin otonom (veya bağımsız) olduğu bir hizmettir. Diğer şeyler arasında bu, Service Developers 'ın tüm hizmet istemcileri hakkında kontrol ettikleri veya bunlara yönelik olduğunu varsaymayacağı anlamına gelir. Bu, bir hizmet sürümleri değiştirdiğinde tüm istemcilerin yeniden oluşturulması ve yeniden dağıtılması seçeneklerini ortadan kaldırır. Bu konu, hizmetin bu temel 'e ait olduğunu varsayar ve bu nedenle, istemcilerinden bağımsız olarak değiştirilmesi veya "sürümlenmiş" olması gerekir.  
  
 Önemli bir değişikliğin beklenmiyorsa ve kaçınılmaz durumda, bir uygulama bu temel 'i yok saymayı seçebilir ve istemcilerin yeniden oluşturulmasını ve hizmetin yeni bir sürümü ile yeniden dağıtılmasını gerektirebilir.  
  
## <a name="contract-versioning"></a>Sözleşme sürümü oluşturma  
 İstemci tarafından kullanılan sözleşmelerin, hizmet tarafından kullanılan sözleşmeyle aynı olması gerekmez; yalnızca uyumlu olmaları gerekir.  
  
 Hizmet sözleşmeleri için uyumluluk, hizmet tarafından kullanıma sunulan yeni işlemler eklenebilir, ancak mevcut işlemler kaldırılabilir veya anlamsal olarak değiştirilemez.  
  
 Veri sözleşmeleri için uyumluluk, yeni şema türü tanımlarının eklenebileceği, ancak var olan şema türü tanımlarının de kırılmaya karşı değiştirimeyeceği anlamına gelir. Son değişiklikler veri üyelerini kaldırmayı veya incompatibly veri türünü değiştirmeyi içerebilir. Bu özellik, hizmetin istemcileri bozmadan sözleşmelerinin sürümünü değiştirme konusunda bazı Enlem sağlar. Sonraki iki bölüm, WCF verileri ve hizmet sözleşmeleri üzerinde yapılabilecek bölünemez ve son değişiklikleri açıklamaktadır.  
  
## <a name="data-contract-versioning"></a>Veri Sözleşmesi Sürümü Oluşturma  
 Bu bölüm <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.DataContractAttribute> sınıfları kullanılırken veri sürümü oluşturma ile ilgilidir.  
  
### <a name="strict-versioning"></a>Katı sürüm oluşturma  
 Birçok senaryoda, sürümleri değiştirirken bir sorun olduğunda, hizmet geliştiricisi istemciler üzerinde denetime sahip değildir ve bu nedenle ileti XML veya şemadaki değişikliklere nasıl tepki verdikleri hakkında varsayımlar yapamaz. Bu durumlarda, yeni iletilerin iki nedenden dolayı eski şemaya göre doğrulanabileceğini garanti etmeniz gerekir:  
  
- Eski istemciler şemanın değişmeyecek varsayımıyla geliştirilmiştir. Şimdiye kadar tasarlandıkları iletileri işleyemeyebilir.  
  
- Eski istemciler, iletileri işlemeye çalışmadan önce eski şemaya göre gerçek şema doğrulaması gerçekleştirebilir.  
  
 Bu senaryolarda önerilen yaklaşım, var olan veri sözleşmelerini sabit olarak değerlendirmek ve benzersiz XML nitelikli adlarıyla yenilerini oluşturmak için kullanılır. Hizmet geliştiricisi daha sonra mevcut bir hizmet sözleşmesine yeni yöntemler ekler ya da yeni veri sözleşmesini kullanan yöntemlerle yeni bir hizmet sözleşmesi oluşturur.  
  
 Genellikle bir hizmet geliştiricisinin, veri sözleşmesinin tüm sürümlerinde çalışması gereken bir iş mantığı yazması ve veri sözleşmesinin her sürümü için sürüme özgü iş kodu olması gerekir. Bu konunun sonundaki ek, arabirimlerin bu gereksinimi karşılamak için nasıl kullanılabileceğini açıklar.  
  
### <a name="lax-versioning"></a>LAX sürümü oluşturma  
 Diğer birçok senaryoda, hizmet geliştiricisi, veri sözleşmesine yeni ve isteğe bağlı bir üyenin eklenmesinin mevcut istemcileri bozmayacak şekilde varsayımını yapabilir. Bu, hizmet geliştiricisi 'nin mevcut istemcilerin şema doğrulaması yapıp gerçekleştirmediğini ve bilinmeyen veri üyelerini yoksaymalarını araştırmasını gerektirir. Bu senaryolarda, yeni üyeleri bölünemez bir şekilde eklemek için veri sözleşmesi özelliklerinden faydalanmak mümkündür. Hizmet geliştiricisi, sürüm için veri sözleşmesi özelliklerinin hizmetin ilk sürümü için zaten kullanılmış olması durumunda bu varsayımını güvenle yapabilir.  
  
 WCF, ASP.NET Web Hizmetleri ve diğer birçok Web hizmeti yığını *LAX sürüm oluşturmayı*destekler: Yani, alınan verilerdeki yeni bilinmeyen veri üyeleri için özel durumlar oluşturmaz.  
  
 Yeni bir üyenin eklenmesi, var olan istemcileri bozmayacak şekilde çok daha kolay bir şekilde inanacaktır. Tüm istemcilerin LAX sürümü oluşturma işlemi yaptığından emin değilseniz, katı sürüm oluşturma yönergelerini kullanmak ve veri sözleşmelerini sabit olarak değerlendirmek için öneri önerilir.  
  
 Veri sözleşmelerinin hem LAX hem de katı sürümü oluşturma hakkında ayrıntılı yönergeler için bkz. [En Iyi uygulamalar: veri sözleşmesi sürümü oluşturma](best-practices-data-contract-versioning.md).  
  
### <a name="distinguishing-between-data-contract-and-net-types"></a>Veri sözleşmesi ve .NET türleri arasında ayrım  
 Bir .NET sınıfı veya yapısı, sınıfa <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği uygulanarak veri sözleşmesi olarak yansıtılyabilirler. .NET türü ve veri sözleşmesi projeksiyonları iki ayrı önemlidir. Aynı veri anlaşması projeksiyonu ile birden çok .NET türü olması mümkündür. Bu ayrım özellikle, tasarlanan veri sözleşmesini koruyarak .NET türünü değiştirmenize olanak tanıyan yararlı olur ve böylece sözcüğün katı anlamda bile mevcut istemcilerle uyumluluğu sürdürmenize yardımcı olur. .NET türü ve veri sözleşmesi arasında bu ayrımı sürdürmek için her zaman yapmanız gereken iki şey vardır:  
  
- Bir <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> ve <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>belirtin. .NET türünün adının ve ad alanının sözleşmede gösterilmesini engellemek için, her zaman veri sözleşmeniz adını ve ad alanını belirtmeniz gerekir. Bu şekilde, daha sonra .NET ad alanı veya tür adı değiştirmeye karar verirseniz, veri sözleşmeniz aynı kalır.  
  
- <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>belirtin. .NET üye adınızın sözleşmede gösterilmesini engellemek için, her zaman veri üyelerinizin adını belirtmeniz gerekir. Bu şekilde, üyenin .NET adını daha sonra değiştirmeye karar verirseniz, veri sözleşmeniz aynı kalır.  
  
### <a name="changing-or-removing-members"></a>Üyeleri değiştirme veya kaldırma  
 Bir üyenin adını veya veri türünü değiştirmek ya da veri üyelerini kaldırmak, LAX sürümliğine izin verilse bile Son değişiklik olur. Bu gerekliyse, yeni bir veri sözleşmesi oluşturun.  
  
 Hizmet uyumluluğu yüksek öneme sahip ise, kodunuzda kullanılmayan veri üyelerini yoksaymayı ve bunları yerinde bırakmayı düşünebilirsiniz. Bir veri üyesini birden çok üyeye bölebiliyorsanız, alt düzey istemciler (en son sürüme yükseltilmeyen istemciler) için gerekli bölme ve yeniden toplamayı gerçekleştirebilecek bir özellik olarak var olan üyeyi yerinde bırakmayı düşünebilirsiniz.  
  
 Benzer şekilde, veri sözleşmesinin adı veya ad alanındaki değişiklikler de büyük değişikliklerdir.  
  
### <a name="round-trips-of-unknown-data"></a>Bilinmeyen verilerin gidiş dönüşleri  
 Bazı senaryolarda, yeni bir sürüme eklenen üyelerden gelen bilinmeyen veriler "gidiş dönüş" için bir gereksinim vardır. Örneğin, "versionNew" hizmeti, yeni eklenen bazı üyelere "versionOld" istemcisine veri gönderir. İstemci, iletiyi işlerken yeni eklenen üyeleri yoksayar, ancak yeni eklenen üyeler de dahil olmak üzere aynı verileri versionNew hizmetine geri gönderir. Bunun için tipik senaryo, verilerin hizmetten alındığı, değiştirildiği ve döndürüldüğü veri güncelleştirmeleridir.  
  
 Belirli bir tür için gidiş-dönüşü etkinleştirmek üzere, türün <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimini uygulaması gerekir. Arabirim bir özellik içerir, <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> <xref:System.Runtime.Serialization.ExtensionDataObject> türünü döndürür. Özelliği, geçerli sürüme bilinmeyen veri sözleşmesinin gelecekteki sürümlerindeki verileri depolamak için kullanılır. Bu veriler istemci için opaktır, ancak örnek serileştirildiğinde <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> özelliğinin içeriği, veri sözleşmesinin üyelerinin verileri ile yazılır.  
  
 Tüm türlerinizin, yeni ve bilinmeyen gelecekteki üyelere uyum sağlaması için bu arabirimi uygulaması önerilir.  
  
### <a name="data-contract-libraries"></a>Veri sözleşmesi kitaplıkları  
 Bir sözleşmenin merkezi bir depoya yayımlandığı veri sözleşmeleri kitaplıkları olabilir ve hizmet ve tür uygulayıcıları, bu depodan veri sözleşmeleri uygular ve kullanıma sunar. Bu durumda, depoya bir veri sözleşmesi yayımladığınızda, kendisini uygulayan türler oluşturan herhangi bir denetiminiz yoktur. Bu nedenle, sözleşmeyi yayımlandıktan sonra değiştiremezsiniz ve etkili bir şekilde sabit hale gelir.  
  
### <a name="when-using-the-xmlserializer"></a>XmlSerializer kullanılırken  
 <xref:System.Xml.Serialization.XmlSerializer> sınıfı kullanılırken aynı sürüm oluşturma ilkeleri uygulanır. Katı sürüm oluşturma gerektiğinde, veri sözleşmelerini sabit olarak değerlendirin ve yeni sürümler için benzersiz ve nitelikli adlarla yeni veri sözleşmeleri oluşturun. LAX sürümü oluşturma 'nın kullanılabilir olduğundan emin olduğunuzda, yeni sürümlere yeni seri hale getirilebilir Üyeler ekleyebilirsiniz, ancak var olan üyeleri değiştirmez veya kaldıramazsınız.  
  
> [!NOTE]
> <xref:System.Xml.Serialization.XmlSerializer>, bilinmeyen verilerin gidiş dönüşü desteklemek için <xref:System.Xml.Serialization.XmlAnyElementAttribute> ve <xref:System.Xml.Serialization.XmlAnyAttributeAttribute> özniteliklerini kullanır.  
  
## <a name="message-contract-versioning"></a>İleti sözleşmesi sürümü oluşturma  
 İleti sözleşmesi sürümü oluşturma yönergeleri, veri sözleşmelerinin sürümü oluşturma konusunda çok benzer. Katı sürüm oluşturma gerekliyse, ileti gövdesini değiştirmemelisiniz, bunun yerine benzersiz bir nitelenmiş ada sahip yeni bir ileti sözleşmesi oluşturmalısınız. LAX sürümü oluşturmayı biliyorsanız, yeni ileti gövdesi parçalarını ekleyebilir, ancak varolanları değiştirmez veya kaldırabilirsiniz. Bu kılavuz, hem çıplak hem de Sarmalanan ileti sözleşmeleri için geçerlidir.  
  
 Katı sürüm oluşturma kullanımda olsa bile ileti üstbilgileri her zaman eklenebilir. MustUnderstand bayrağı sürümü oluşturmayı etkileyebilir. Genel olarak, WCF 'deki üst bilgiler için sürüm oluşturma modeli SOAP belirtiminde açıklanacaktır.  
  
## <a name="service-contract-versioning"></a>Hizmet sözleşmesi sürümü oluşturma  
 Veri sözleşmesi sürümü oluşturma ile benzer şekilde, hizmet sözleşmesi sürümü oluşturma işlemi ekleme, değiştirme ve kaldırma işlemlerini de kapsar.  
  
### <a name="specifying-name-namespace-and-action"></a>Ad, ad alanı ve eylem belirtme  
 Varsayılan olarak, bir hizmet sözleşmesinin adı arabirimin adıdır. Varsayılan ad alanı "http://tempuri.org" ve her bir işlemin eylemi "http://tempuri.org/contractname/methodname". Hizmet sözleşmesi için bir ad ve ad alanı ve "http://tempuri.org" kullanmaktan kaçınmak ve arabirim ve yöntem adlarının hizmetin sözleşmesinde gösterilmesini önlemek için her işlem için bir eylem belirlemeniz önerilir.  
  
### <a name="adding-parameters-and-operations"></a>Parametreleri ve Işlemleri ekleme  
 Hizmet tarafından sunulan hizmet işlemlerinin eklenmesi, var olan istemcilerin bu yeni işlemler konusunda endişe duymadığı için bölünemez bir değişiklik.  
  
> [!NOTE]
> Bir çift yönlü geri çağırma sözleşmesine işlemler eklemek, önemli bir değişiklik olur.  
  
### <a name="changing-operation-parameter-or-return-types"></a>Işlem parametresini veya dönüş türlerini değiştirme  
 Yeni tür, eski tür tarafından uygulanan aynı veri sözleşmesini uygularsa, parametre veya dönüş türlerinin genel olarak değiştirilmesi genellikle bir son değişiklik olur. Böyle bir değişiklik yapmak için, hizmet sözleşmesine yeni bir işlem ekleyin veya yeni bir hizmet sözleşmesi tanımlayın.  
  
### <a name="removing-operations"></a>Işlemleri kaldırma  
 İşlemleri kaldırma işlemi de son değişiklik olur. Böyle bir değişiklik yapmak için yeni bir hizmet sözleşmesi tanımlayın ve yeni bir uç noktada kullanıma sunun.  
  
### <a name="fault-contracts"></a>Hata sözleşmeleri  
 <xref:System.ServiceModel.FaultContractAttribute> özniteliği, bir hizmet sözleşmesi geliştiricisinin, sözleşmenin işlemlerinden döndürülebilecek hatalar hakkında bilgi belirtmesini sağlar.  
  
 Bir hizmetin sözleşmesinde açıklanan hataların listesi ayrıntılı olarak değerlendirilmez. Herhangi bir zamanda, bir işlem sözleşmede açıklanmayan hatalar döndürebilir. Bu nedenle, sözleşmede açıklanan hata kümesini değiştirmenin bölünmesi düşünülmez. Örneğin, <xref:System.ServiceModel.FaultContractAttribute> kullanarak sözleşmeye yeni bir hata ekleme veya mevcut bir hatayı sözleşmeden kaldırma.  
  
### <a name="service-contract-libraries"></a>Hizmet sözleşmesi kitaplıkları  
 Kuruluşların, bir sözleşmenin merkezi bir depoya yayımlandığı ve hizmet uygulayıcıları bu depodan sözleşme uygulayan sözleşmeler kitaplıkları olabilir. Bu durumda, depoya bir hizmet sözleşmesi yayımladığınızda, kendisini uygulayan hizmetler oluşturan herhangi bir denetiminiz yoktur. Bu nedenle, hizmet sözleşmesini yayımlandıktan sonra değiştirilemez, böylece etkili bir şekilde işleme alabilirsiniz. WCF, mevcut sözleşmeleri genişleten yeni bir sözleşme oluşturmak için kullanılabilecek sözleşme devralmayı destekler. Bu özelliği kullanmak için eski hizmet sözleşmesi arabiriminden devralan yeni bir hizmet sözleşmesi arabirimi tanımlayın ve ardından yeni arabirime Yöntemler ekleyin. Daha sonra, yeni sözleşmeyi uygulamak için eski sözleşmeyi uygulayan hizmeti değiştirirsiniz ve "versionOld" uç nokta tanımını yeni sözleşmeyi kullanacak şekilde değiştirebilirsiniz. "VersionOld" istemcileri için uç nokta, "versionOld" sözleşmesini açığa çıkarmasına devam edecektir; "versionNew" istemcileri için uç nokta "versionNew" sözleşmesini kullanıma sunacaktır.  
  
## <a name="address-and-binding-versioning"></a>Adres ve bağlama sürümü oluşturma  
 İstemcilerin yeni uç nokta adresini veya bağlamayı dinamik olarak bulamadığı durumlar, uç nokta adresi ve bağlamadaki değişiklikler ortadan kaldırılır. Bu özelliği uygulamaya yönelik bir mekanizma, bir evrensel keşif açıklaması ve Tümleştirme (UDDI) kayıt defteri ve istemcinin bir uç noktayla iletişim kurmayı denediği ve hata durumunda iyi bilinen bir UDDI 'yı sorgulayan bir UDDI çağırma modelini kullanmaktır geçerli uç nokta meta verileri için kayıt defteri. İstemci daha sonra uç noktayla iletişim kurmak için bu meta verilerden adresi ve bağlamayı kullanır. Bu iletişim başarılı olursa istemci, daha sonra kullanmak üzere adresi ve bağlama bilgilerini önbelleğe alır.  
  
## <a name="routing-service-and-versioning"></a>Yönlendirme hizmeti ve sürümü oluşturma  
 Bir hizmette yapılan değişiklikler önemli değişiklikler olduğunda ve hizmetin iki veya daha fazla farklı sürümünü aynı anda çalıştıran bir hizmete sahip olmanız gerekiyorsa, iletileri uygun hizmet örneğine yönlendirmek için WCF yönlendirme hizmetini kullanabilirsiniz. WCF yönlendirme hizmeti, içerik tabanlı yönlendirme kullanır, diğer bir deyişle, iletinin nereye yönlendirileceğini anlamak için ileti içindeki bilgileri kullanır. WCF yönlendirme hizmeti hakkında daha fazla bilgi için bkz. [yönlendirme hizmeti](./feature-details/routing-service.md). Hizmet sürümü oluşturma için WCF yönlendirme hizmetini nasıl kullanacağınızı gösteren bir örnek için bkz. [nasıl yapılır: hizmet sürümü oluşturma](./feature-details/how-to-service-versioning.md).  
  
## <a name="appendix"></a>Yer  
 Katı sürüm oluşturma gerektiğinde genel veri anlaşması sürüm oluşturma kılavuzu, veri sözleşmelerini sabit olarak değerlendirmek ve değişiklikler gerektiğinde yenilerini oluşturmak için kullanılır. Her yeni veri sözleşmesi için yeni bir sınıf oluşturulması gerekir. bu nedenle, eski veri sözleşmesi sınıfına göre yazılmış olan kodu almak zorunda kalmamak ve yeni veri sözleşmesi sınıfına yeniden yazmak için bir mekanizma gereklidir.  
  
 Bu tür bir mekanizma, her bir veri sözleşmesinin üyelerini tanımlamak ve arabirimleri uygulayan veri sözleşmesi sınıfları yerine iç uygulama kodu yazmak için arabirimler kullanmaktır. Bir hizmetin 1. sürümü için aşağıdaki kod `IPurchaseOrderV1` arabirimini ve `PurchaseOrderV1` ' i gösterir:  
  
```csharp  
public interface IPurchaseOrderV1  
{  
    string OrderId { get; set; }  
    string CustomerId { get; set; }  
}  
  
[DataContract(  
Name = "PurchaseOrder",  
Namespace = "http://examples.microsoft.com/WCF/2005/10/PurchaseOrder")]  
public class PurchaseOrderV1 : IPurchaseOrderV1  
{  
    [DataMember(...)]  
    public string OrderId {...}  
    [DataMember(...)]  
    public string CustomerId {...}  
}  
```  
  
 Hizmet sözleşmesinin işlemleri `PurchaseOrderV1` ' da yazıldığında, gerçek iş mantığı `IPurchaseOrderV1` ' de olabilir. Ardından, sürüm 2 ' de, aşağıdaki kodda gösterildiği gibi yeni bir `IPurchaseOrderV2` arabirimi ve yeni bir `PurchaseOrderV2` sınıfı vardır:  
  
```csharp
public interface IPurchaseOrderV2  
{  
    DateTime OrderDate { get; set; }  
}

[DataContract(   
Name = "PurchaseOrder",  
Namespace = "http://examples.microsoft.com/WCF/2006/02/PurchaseOrder")]  
public class PurchaseOrderV2 : IPurchaseOrderV1, IPurchaseOrderV2  
{  
    [DataMember(...)]  
    public string OrderId {...}  
    [DataMember(...)]  
    public string CustomerId {...}  
    [DataMember(...)]  
    public DateTime OrderDate { ... }  
}  
```  
  
 Hizmet sözleşmesi, `PurchaseOrderV2` ' da yazılı yeni işlemleri içerecek şekilde güncelleştirilecektir. `IPurchaseOrderV1` olarak yazılan mevcut iş mantığı `PurchaseOrderV2` ve `OrderDate` özelliğin `IPurchaseOrderV2`açısından yazılması gereken yeni iş mantığı için çalışmaya devam edecektir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>
- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- <xref:System.Runtime.Serialization.ExtensionDataObject>
- <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A>
- <xref:System.Xml.Serialization.XmlSerializer>
- [Veri Anlaşması Eşitliği](./feature-details/data-contract-equivalence.md)
- [Sürüm Toleranslı Seri Hale Getirme Geri Çağrıları](./feature-details/version-tolerant-serialization-callbacks.md)
