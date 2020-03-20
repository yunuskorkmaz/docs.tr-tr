---
title: Hizmet Sürümü Oluşturma
ms.date: 03/30/2017
ms.assetid: 37575ead-d820-4a67-8059-da11a2ab48e2
ms.openlocfilehash: ea5e80e33d1b29e01e6d1867c50bb3bb973b01c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183115"
---
# <a name="service-versioning"></a>Hizmet Sürümü Oluşturma
İlk dağıtımdan sonra ve kullanım ömürleri boyunca birkaç kez hizmet (ve maruz kaldıkları uç noktalar) iş gereksinimlerinin değiştirilmesi, bilgi teknolojisi gereksinimleri veya diğer Sorun. Her değişiklik, hizmetin yeni bir sürümünü sunar. Bu konu, Windows Communication Foundation 'da (WCF) sürüm konusunu nasıl değerlendireceklerini açıklar.  
  
## <a name="four-categories-of-service-changes"></a>Hizmet Değişikliklerinin Dört Kategorisi  
 Gerekli olabilecek hizmetlerdeki değişiklikler dört kategoriye ayırılabilir:  
  
- Sözleşme değişiklikleri: Örneğin, bir işlem eklenebilir veya iletideki bir veri öğesi eklenebilir veya değiştirilebilir.  
  
- Adres değişiklikleri: Örneğin, bir hizmet uç noktaların yeni adresleri olduğu farklı bir konuma taşınır.  
  
- Bağlama değişiklikleri: Örneğin, bir güvenlik mekanizması değişir veya ayarları değişir.  
  
- Uygulama değişiklikleri: Örneğin, bir iç yöntem uygulaması değiştiğinde.  
  
 Bu değişikliklerden bazıları "kırılmaz" olarak adlandırılır ve diğerleri "kırılmaz" olarak adlandırılır. Önceki sürümde başarıyla işlenmiş olan tüm iletiler yeni sürümde başarıyla işlenirse, değişiklik *kırılmaz.* Bu kriteri karşılamayan herhangi bir değişiklik *bir kırılma* değişikliktir.  
  
## <a name="service-orientation-and-versioning"></a>Hizmet Yönlendirme ve Sürüm  
 Hizmet yönlendirme ilkelerinden biri, hizmetlerin ve istemcilerin özerk (veya bağımsız) olmasıdır. Diğer şeylerin yanı sıra, bu, hizmet geliştiricilerin tüm hizmet istemcilerini denetlediklerini ve hatta bildiklerini varsayamadıkları anlamına gelir. Bu, bir hizmet sürümleri değiştirdiğinde tüm istemcileri yeniden oluşturma ve yeniden dağıtma seçeneğini ortadan kaldırır. Bu konu, hizmetin bu ilkeye uygun olduğunu varsayar ve bu nedenle istemcilerinden bağımsız olarak değiştirilmesi veya "sürülmesi" gerekir.  
  
 Bir kesme değişikliğinin beklenmeyen ve önlenemediği durumlarda, bir uygulama bu ilkeyi yoksaymayı seçebilir ve istemcilerin hizmetin yeni bir sürümüyle yeniden oluşturulmasını ve yeniden dağıtılmasını gerektirebilir.  
  
## <a name="contract-versioning"></a>Sözleşme Sürümü  
 Müşteri tarafından kullanılan sözleşmelerin hizmet tarafından kullanılan sözleşmeyle aynı olması gerekmez; sadece uyumlu olması gerekir.  
  
 Hizmet sözleşmeleri için uyumluluk, hizmetin maruz kaçtığı yeni işlemlerin eklenebileceği, ancak varolan işlemlerin anlamsal olarak kaldırılamadığı veya değiştirilemeyeceği anlamına gelir.  
  
 Veri sözleşmeleri için uyumluluk, yeni şema türü tanımlarının eklenebileceği, ancak varolan şema türü tanımlarının kırılma yollarında değiştirilemeyeceği anlamına gelir. Son dakika değişiklikleri, veri üyelerinin kaldırılmasını veya veri türünü uyumlu bir şekilde değiştirmeyi içerebilir. Bu özellik, hizmetin sözleşmelerinin sürümünü istemcileri bozmadan değiştirmede bazı enlemler sağlar. Sonraki iki bölüm, WCF verileri ve hizmet sözleşmelerinde yapılabilecek sonsyama ve bozma değişikliklerini açıklayırır.  
  
## <a name="data-contract-versioning"></a>Veri Sözleşmesi Sürümü Oluşturma  
 Bu bölümde, <xref:System.Runtime.Serialization.DataContractSerializer> sınıfları ve <xref:System.Runtime.Serialization.DataContractAttribute> bunları kullanırken veri sürümle ilgilidir.  
  
### <a name="strict-versioning"></a>Sıkı Sürümleme  
 Sürümleri değiştirme sorun olduğunda birçok senaryoda, hizmet geliştiricisi istemciler üzerinde denetimi yoktur ve bu nedenle ileti XML veya şema değişikliklere nasıl tepki vereceğini hakkında varsayımlar yapamaz. Bu gibi durumlarda, yeni iletilerin eski şema aleyhine iki nedenden dolayı doğrulaşacağını garanti emelisiniz:  
  
- Eski istemciler şema değişmez varsayımı ile geliştirilmiştir. Hiçbir zaman tasarlanamadıkları iletileri işlemeyi başaramayabilirler.  
  
- Eski istemciler, iletileri işlemeye çalışmadan önce eski şemaya karşı gerçek şema doğrulaması gerçekleştirebilir.  
  
 Bu tür senaryolarda önerilen yaklaşım, varolan veri sözleşmelerini değişmez olarak ele almak ve benzersiz XML nitelikli adlara sahip yeni lerini oluşturmaktır. Hizmet geliştiricisi daha sonra varolan bir hizmet sözleşmesine yeni yöntemler ekler veya yeni veri sözleşmesini kullanan yöntemlerle yeni bir hizmet sözleşmesi oluşturur.  
  
 Genellikle bir hizmet geliştiricisi veri sözleşmesi artı veri sözleşmesinin her sürümü için sürüm özel iş kodu tüm sürümleri içinde çalışması gereken bazı iş mantığı yazmak gerekir durumda olacaktır. Bu konunun sonundaki ekte, arabirimlerin bu ihtiyacı karşılamak için nasıl kullanılabileceğini açıklar.  
  
### <a name="lax-versioning"></a>Lax Versiyon  
 Diğer birçok senaryoda, hizmet geliştiricisi veri sözleşmesine yeni, isteğe bağlı bir üye eklemenin varolan istemcileri bozamayacağı varsayımında bulunabilir. Bu, servis geliştiricisinin varolan istemcilerin şema doğrulaması yapıp yapmamayı ve bilinmeyen veri üyelerini yoksaydığını araştırmasını gerektirir. Bu senaryolarda, yeni üyeler eklemek için veri sözleşmesi özelliklerinden kesintisiz bir şekilde yararlanmak mümkündür. Sürüm için veri sözleşmesi özellikleri hizmetin ilk sürümü için zaten kullanılmışsa, hizmet geliştiricisi bu varsayımı güvenle yapabilir.  
  
 WCF, ASP.NET Web Hizmetleri ve diğer birçok Web hizmeti yığınları *gevşek sürümü*destekler: yani, alınan verilerde yeni bilinmeyen veri üyeleri için özel durumlar atmayın.  
  
 Yanlışlıkla yeni bir üye eklemenin varolan istemcileri kırmayacağına inanmak kolaydır. Tüm istemcilerin gevşek sürümle başa çıkabileceğinden emin değilseniz, öneri katı sürüm yönergelerini kullanmak ve veri sözleşmelerini değişmez olarak ele almaktır.  
  
 Veri sözleşmelerinin hem gevşek hem de katı sürümü için ayrıntılı yönergeler için En [İyi Uygulamalar: Veri Sözleşmesi Sürümü](best-practices-data-contract-versioning.md)bölümüne bakın.  
  
### <a name="distinguishing-between-data-contract-and-net-types"></a>Veri Sözleşmesi ile .NET Türleri Arasında Ayrım  
 Bir .NET sınıfı veya yapısı, sınıfa öznitelik <xref:System.Runtime.Serialization.DataContractAttribute> uygulanarak veri sözleşmesi olarak yansıtılabilir. .NET türü ve veri sözleşmesi projeksiyonları iki farklı konudur. Aynı veri sözleşmesi projeksiyonuna sahip birden çok .NET türü olması mümkündür. Bu ayrım, özellikle öngörülen veri sözleşmesini korurken .NET türünü değiştirmenize ve böylece sözcüğün katı anlamıyla bile varolan istemcilerle uyumluluğu korumanıza olanak sağlar. .NET türü ve veri sözleşmesi arasındaki bu ayrımı korumak için her zaman yapmanız gereken iki şey vardır:  
  
- Bir <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> ve <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>. belirtin .NET türün adının ve ad alanının sözleşmede açıkolmasını önlemek için her zaman veri sözleşmenizin adını ve ad alanını belirtmeniz gerekir. Bu şekilde, .NET ad alanını veya türü adını daha sonra değiştirmeye karar verirseniz, veri sözleşmeniz aynı kalır.  
  
- <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> belirtin. .NET üye adınızın sözleşmede açıkolmasını önlemek için her zaman veri üyelerinizin adını belirtmeniz gerekir. Bu şekilde, üyenin .NET adını daha sonra değiştirmeye karar verirseniz, veri sözleşmeniz aynı kalır.  
  
### <a name="changing-or-removing-members"></a>Üyelerin Değiştirilmesi veya Kaldırılması  
 Bir üyenin adını veya veri türünü değiştirmek veya veri üyelerini kaldırmak, gevşek sürüm alınmasına izin verilse bile bir kesme değişikliğidir. Bu gerekliyse, yeni bir veri sözleşmesi oluşturun.  
  
 Hizmet uyumluluğu çok önemliyse, kodunuzda kullanılmayan veri üyelerini yoksaymayı ve yerinde bırakmayı düşünebilirsiniz. Bir veri üyesini birden çok üyeye bölüyorsanız, varolan üyeyi alt düzey istemciler (en son sürüme yükseltilmeyen istemciler) için gerekli bölme ve yeniden toplamayı gerçekleştirebilecek bir özellik olarak yerinde bırakmayı düşünebilirsiniz.  
  
 Benzer şekilde, veri sözleşmesinin adı veya ad alanında yapılan değişiklikler de değişiklikleri bozuyor.  
  
### <a name="round-trips-of-unknown-data"></a>Bilinmeyen Verilerin Gidiş-Dönüşleri  
 Bazı senaryolarda, yeni bir sürümde eklenen üyelerden gelen bilinmeyen verileri "gidiş-dönüş" olarak yapmanız gerekir. Örneğin, bir "sürümNew" hizmeti, yeni eklenen bazı üyelerle birlikte verileri "sürümOld" istemcisine gönderir. İstemci iletiyi işlerken yeni eklenen üyeleri yoksa, ancak yeni eklenen üyeler de dahil olmak üzere aynı verileri sürümYeni hizmete geri gönderir. Bunun için tipik senaryo, verilerin hizmetten alındığı, değiştirildiği ve döndürüldüğü veri güncelleştirmeleridir.  
  
 Belirli bir tür için yuvarlama özelliğini etkinleştirmek <xref:System.Runtime.Serialization.IExtensibleDataObject> için, tür arabirimi uygulamalıdır. Arabirim, <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> türü döndüren <xref:System.Runtime.Serialization.ExtensionDataObject> bir özellik içerir. Özellik, geçerli sürüm tarafından bilinmeyen veri sözleşmesinin gelecekteki sürümlerinden gelen verileri depolamak için kullanılır. Bu veriler istemciye opaktır, ancak örnek seri hale geldiğinde, <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> özelliğin içeriği diğer veri sözleşmesi üyelerinin verileriyle birlikte yazılır.  
  
 Tüm türlerinizin, gelecekteki yeni ve bilinmeyen üyeleri barındırmak için bu arabirimi uygulaması önerilir.  
  
### <a name="data-contract-libraries"></a>Veri Sözleşmesi Kitaplıkları  
 Bir sözleşmenin merkezi bir depoda yayımlandığı veri sözleşmeleri kitaplıkları olabilir ve hizmet ve tür uygulayıcıları söz konusu depodaki veri sözleşmelerini uygular ve ortaya çıkarır. Bu durumda, depoya bir veri sözleşmesi yayımladığınızda, bunu uygulayan türleri kimin oluşturduğu üzerinde hiçbir denetiminiz yoktur. Bu nedenle, yayımlandıktan sonra sözleşmeyi değiştiremezsiniz ve bu da sözleşmeyi etkin bir şekilde değişmez hale getirir.  
  
### <a name="when-using-the-xmlserializer"></a>XmlSerializer kullanırken  
 <xref:System.Xml.Serialization.XmlSerializer> Sınıfı kullanırken aynı sürüm ilkeleri geçerlidir. Sıkı sürüm gerektiğinde, veri sözleşmelerini değişmez olarak ele verin ve yeni sürümler için benzersiz, nitelikli adlarla yeni veri sözleşmeleri oluşturun. Gevşek sürüm kullanılabilir emin olduğunuzda, yeni sürümler yeni serializable üyeleri ekleyebilirsiniz, ancak değiştirmek veya varolan üyeleri kaldırmak değil.  
  
> [!NOTE]
> Bilinmeyen <xref:System.Xml.Serialization.XmlSerializer> verilerin <xref:System.Xml.Serialization.XmlAnyElementAttribute> <xref:System.Xml.Serialization.XmlAnyAttributeAttribute> yuvarlak tripping desteklemek için ve öznitelikleri kullanır.  
  
## <a name="message-contract-versioning"></a>İleti Sözleşmesi Sürümü  
 İleti sözleşmesi sürümü için yönergeler veri sözleşmelerini sürümleme çok benzer. Sıkı sürüm gerekiyorsa, ileti gövdenizi değiştirmemeli, bunun yerine benzersiz bir nitelikli ada sahip yeni bir ileti sözleşmesi oluşturmanız gerekir. Gevşek sürüm kullanabilirsiniz biliyorsanız, yeni ileti gövde parçaları ekleyebilirsiniz, ancak değiştirmek veya varolan olanları kaldırmak değil. Bu kılavuz, hem çıplak hem de sarılmış ileti sözleşmeleri için geçerlidir.  
  
 Sıkı sürüm kullanımda olsa bile ileti üstileri her zaman eklenebilir. MustUnderstand bayrağı sürümü etkileyebilir. Genel olarak, WCF başlıkları için sürüm modeli SOAP belirtiminde açıklandığı gibi.  
  
## <a name="service-contract-versioning"></a>Hizmet Sözleşmesi Sürümü  
 Veri sözleşmesi sürümüne benzer şekilde, hizmet sözleşmesi sürümü de ekleme, değiştirme ve işlemleri kaldırmayı içerir.  
  
### <a name="specifying-name-namespace-and-action"></a>Ad, Ad Alanı ve Eylem Belirtme  
 Varsayılan olarak, bir hizmet sözleşmesinin adı arabirimin adıdır. Varsayılan ad alanıhttp://tempuri.org" "dır ve her işleminhttp://tempuri.org/contractname/methodnameeylemi " "dir. Hizmet sözleşmesi için açıkça bir ad ve ad alanı ve " "http://tempuri.orgkullanmaktan kaçınmak ve arabirim ve yöntem adlarının hizmet sözleşmesinde açığa çıkarını önlemek için her işlem için bir eylem belirtmeniz önerilir.  
  
### <a name="adding-parameters-and-operations"></a>Parametreler ve İşlemler Ekleme  
 Hizmet tarafından açıkta olan hizmet işlemleri ekleme, varolan istemcilerin bu yeni işlemlerle ilgilenmesi gerekmedığından, sonuçsuz bir değişikliktir.  
  
> [!NOTE]
> Çift yönlü geri arama sözleşmesine işlem eklemek bir son işlemdir.  
  
### <a name="changing-operation-parameter-or-return-types"></a>İşlem Parametresi veya İade Türlerini Değiştirme  
 Parametre veya iade türlerini değiştirmek, yeni tür eski tür tarafından uygulanan aynı veri sözleşmesini uygulamadığı sürece genellikle bir kesme değişikliğidir. Böyle bir değişiklik yapmak için hizmet sözleşmesine yeni bir işlem ekleyin veya yeni bir hizmet sözleşmesi tanımlayın.  
  
### <a name="removing-operations"></a>İşlemleri Kaldırma  
 İşlemleri kaldırma da bir kırılma değişikliğidir. Böyle bir değişiklik yapmak için yeni bir hizmet sözleşmesi tanımlayın ve yeni bir bitiş noktasında ortaya çıkarın.  
  
### <a name="fault-contracts"></a>Arıza Sözleşmeleri  
 Öznitelik, <xref:System.ServiceModel.FaultContractAttribute> bir hizmet sözleşmesi geliştiricisinin sözleşmenin işlemlerinden döndürülebilen hatalar hakkında bilgi belirtmesini sağlar.  
  
 Bir hizmetin sözleşmesinde açıklanan hataların listesi ayrıntılı olarak kabul edilmez. Herhangi bir zamanda, bir işlem sözleşmesinde açıklanmayan hataları döndürebilir. Bu nedenle sözleşmede açıklanan hata kümesinin değiştirilmesi kırılma olarak kabul edilmez. Örneğin, varolan bir hatayı kullanarak <xref:System.ServiceModel.FaultContractAttribute> veya sözleşmeden kaldırarak sözleşmeye yeni bir hata eklemek.  
  
### <a name="service-contract-libraries"></a>Hizmet Sözleşmesi Kütüphaneleri  
 Kuruluşların, merkezi bir depoya sözleşme yayınlandığı ve hizmet uygulayıcılarının söz konusu depodan sözleşmeleri uyguladığı sözleşme kitaplıkları olabilir. Bu durumda, depoya bir hizmet sözleşmesi yayımladığınızda, bunu uygulayan hizmetleri kimin oluşturduğu üzerinde hiçbir denetiminiz yoktur. Bu nedenle, hizmet sözleşmesini yayımlandıktan sonra değiştiremezsiniz ve bu da hizmet sözleşmesini etkin bir şekilde değişmez hale getirir. WCF, varolan sözleşmeleri uzatan yeni bir sözleşme oluşturmak için kullanılabilecek sözleşme mirasını destekler. Bu özelliği kullanmak için, eski hizmet sözleşmesi arabiriminden devralınan yeni bir hizmet sözleşmesi arabirimi tanımlayın ve ardından yeni arabirime yöntemler ekleyin. Daha sonra, yeni sözleşmeyi uygulamak için eski sözleşmeyi uygulayan hizmeti değiştirir ve yeni sözleşmeyi kullanmak için "sürümOld" bitiş noktası tanımını değiştirirsiniz. "VersionOld" istemcileri için, bitiş noktası "versionOld" sözleşmesini açığa çıkarmak olarak görünmeye devam edecektir; "versionNew" istemcileri için, bitiş noktası "sürümNew" sözleşmesini ortaya çıkarmak için görünür.  
  
## <a name="address-and-binding-versioning"></a>Adres ve Ciltleme Sürümleme  
 Uç nokta adresi ve bağlama değişiklikleri, istemciler yeni uç nokta adresini dinamik olarak keşfedebilme veya bağlama yeteneğine sahip olmadığı sürece değişiklikleri bozuyor. Bu özelliği uygulamak için bir mekanizma evrensel bulma açıklama ve tümleştirme (UDDI) kayıt defteri ve UDDI Çağırma Deseni kullanarak bir istemci nin bir bitiş noktası ile iletişim kurmaya çalışır ve başarısızlık üzerine, iyi bilinen bir UDDI sorgular geçerli uç nokta meta verilerinin kayıt defteri. İstemci daha sonra bitiş noktası ile iletişim kurmak için bu meta verilerden adresi ve bağlama kullanır. Bu iletişim başarılı olursa, istemci adresi ve bağlayıcı bilgileri ileride kullanmak üzere önbelleğe alınr.  
  
## <a name="routing-service-and-versioning"></a>Yönlendirme Hizmeti ve Sürüm  
 Bir hizmette yapılan değişiklikler değişiklikleri kırıyorsa ve aynı anda çalışan bir hizmetin iki veya daha fazla farklı sürümüne sahip olmanız gerekiyorsa, iletileri uygun hizmet örneğine yönlendirmek için WCF Yönlendirme Hizmeti'ni kullanabilirsiniz. WCF Yönlendirme Hizmeti içerik tabanlı yönlendirme kullanır, başka bir deyişle, iletiyi nereye yönlendireceklerini belirlemek için ileti içindeki bilgileri kullanır. WCF Yönlendirme Hizmeti hakkında daha fazla bilgi için [Yönlendirme Hizmeti'ne](./feature-details/routing-service.md)bakın. Hizmet sürümü için WCF Yönlendirme Hizmeti'nin nasıl kullanılacağına bir örnek için [bkz.](./feature-details/how-to-service-versioning.md)  
  
## <a name="appendix"></a>Ek  
 Sıkı sürüm gerektiğinde genel veri sözleşmesi sürüm kılavuzu, veri sözleşmelerini değişmez olarak ele almak ve değişiklikler gerektiğinde yenilerini oluşturmaktır. Her yeni veri sözleşmesi için yeni bir sınıf oluşturulması gerekir, bu nedenle eski veri sözleşmesi sınıfı açısından yazılmış varolan kodu almak ve yeni veri sözleşmesi sınıfı açısından yeniden yazmak zorunda kalmaktan kaçınmak için bir mekanizma gereklidir.  
  
 Bu mekanizmalardan biri, arabirimleri uygulayan veri sözleşmesi sınıfları yerine arabirimler açısından her veri sözleşmesinin üyelerini tanımlamak ve iç uygulama kodu yazmak için arabirimleri kullanmaktır. Bir hizmetin sürüm 1 için `IPurchaseOrderV1` aşağıdaki kodu `PurchaseOrderV1`bir arabirim ve bir gösterir:  
  
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
  
 Hizmet sözleşmesinin işlemleri açısından `PurchaseOrderV1`yazılırken, asıl iş mantığı açısından `IPurchaseOrderV1`olacaktır. Daha sonra, sürüm 2'de, `IPurchaseOrderV2` aşağıdaki kodda gösterildiği gibi yeni bir arabirim ve yeni `PurchaseOrderV2` bir sınıf olacaktır:  
  
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
  
 Hizmet sözleşmesi, `PurchaseOrderV2`'' açısından yazılmış yeni işlemleri içerecek şekilde güncellenecektir. Mevcut iş mantığı açısından `IPurchaseOrderV1` yazılan lar `PurchaseOrderV2` için çalışmaya devam edecek `OrderDate` ve yeni iş `IPurchaseOrderV2`mantığı na ihtiyaç duyduğu özellik açısından yazılacak.  
  
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
- [Veri Sözleşmesi Eşitliği](./feature-details/data-contract-equivalence.md)
- [Sürüm Toleranslı Seri Hale Getirme Geri Çağrıları](./feature-details/version-tolerant-serialization-callbacks.md)
