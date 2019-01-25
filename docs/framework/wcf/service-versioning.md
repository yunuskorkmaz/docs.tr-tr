---
title: Hizmet Sürümü Oluşturma
ms.date: 03/30/2017
ms.assetid: 37575ead-d820-4a67-8059-da11a2ab48e2
ms.openlocfilehash: 62c8641e69ea461c3bf56b911c25b4894f63abe9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649251"
---
# <a name="service-versioning"></a>Hizmet Sürümü Oluşturma
İlk dağıtım ve potansiyel olarak kendi ömürlerine sırasında birkaç kez sonra Hizmetleri (ve bunlar ortaya uç noktaları) için çeşitli iş gereksinimlerini, bilgi teknolojisi gereksinimlerini değiştirme gibi nedenlerle, değiştirilmesi veya diğer adres gerekebilir sorun. Her değişikliği hizmetinin yeni bir sürümünü içeriyor. Bu konu, Windows Communication Foundation (WCF) sürüm oluşturmayı göz önünde bulundurun açıklanmaktadır.  
  
## <a name="four-categories-of-service-changes"></a>Hizmet değişikliklerini dört kategorileri  
 Gerekli hizmetlere yapılan değişiklikleri dört kategoride sınıflandırılabilir:  
  
-   Sözleşme değişiklikler: Örneğin, bir işlem eklenebilir veya bir veri öğesi içinde bir ileti eklendiğinde veya değiştirilmiş.  
  
-   Değişiklikleri adres: Örneğin, bir hizmet uç noktaları yeni adreslerine sahip olduğu farklı bir konuma taşır.  
  
-   Bağlama değişiklikler: Örneğin, bir güvenlik mekanizması değişiklikler veya ayarlarını değiştirebilirsiniz.  
  
-   Uygulama değişiklikler: Örneğin, bir iç yöntem uygulaması değiştiğinde.  
  
 Bu değişikliklerden bazıları "önemli" olarak adlandırılır ve diğerleri "bölünemez." Bir değişiklik *bölünemez* başarıyla önceki sürümde işlenen tüm iletileri yeni sürümde başarılı bir şekilde işlenir. Bu ölçütü karşılamayan herhangi bir değişiklik olup bir *bozucu* değiştirin.  
  
## <a name="service-orientation-and-versioning"></a>Hizmet yönlendirmesi ve sürüm oluşturma  
 Hizmet yönlendirmesi İlkesi hizmetler ve istemcileri otonom (veya bağımsız) biridir. Diğerlerinin yanı sıra, bu hizmet geliştiricilerin denetlemek veya bile tüm istemcilere hakkında bilmeniz varsayamazsınız anlamına gelir. Bu, yeniden ve tüm istemcilere hizmet değişiklikleri sürümleri, yeniden dağıtım seçeneğinin ortadan kaldırır. Bu konuda, hizmet için bu uyarlamanız uyar ve bu nedenle tüm istemcileri değiştirilmiş veya "tutulan" bağımsız olmalıdır varsayılır.  
  
 Burada bir değişiklik, beklenmeyen bir durumdur ve kaçınılmaz durumlarda bu uyarlamanız yoksay ve istemcilerin yeniden ve hizmetin yeni bir sürümüyle yeniden gerektiren bir uygulama tercih edebilirsiniz.  
  
## <a name="contract-versioning"></a>Sözleşmesi sürümü oluşturma  
 Sözleşmeler, bir istemci tarafından kullanılan hizmet tarafından kullanılan sözleşme ile aynı olması gerekmez; yalnızca uyumlu olması gerekir.  
  
 Hizmet sözleşmeleri için Uyumluluk hizmet tarafından sunulan yeni işlemleri anlamına gelir eklenebilir, ancak mevcut işlemleri kaldırılamıyor veya anlamsal olarak değiştirildi.  
  
 Veri sözleşmeleri, yeni şema türü tanımları eklenebilir uyumluluk anlamına gelir ancak mevcut şema türü tanımları yolu sonu değiştirilemez. Değişiklikler, veri üyeleri kaldırma veya kendi veri türü incompatibly değiştirme içerebilir. Bu özellik, sözleşme sürümü istemciler bozmadan değiştirmede bazı enlem hizmet sağlar. Sonraki iki bölümde WCF veri yapılabilir ve sözleşmeleri hizmet bölünemez ve derleyicideki en güncel değişiklikler açıklanmaktadır.  
  
## <a name="data-contract-versioning"></a>Veri Sözleşmesi Sürümü Oluşturma  
 Bu bölüm veri sürüm oluşturma kullanılırken ilgilenir <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.DataContractAttribute> sınıfları.  
  
### <a name="strict-versioning"></a>Katı sürüm oluşturma  
 Birçok senaryoda sürümleri değiştirerek bir sorun olduğunda hizmeti Geliştirici istemciler üzerinde denetime sahip değil ve bu nedenle nasıl bunlar XML veya şema yapılacak değişikliklere tepki hakkında varsayımlar yapamazsınız. Bu durumlarda, yeni iletileri iki nedenden dolayı eski şemayla, doğrulama garanti etmeniz gerekir:  
  
-   Eski istemciler, şema değişmez varsayımına ile geliştirilmiştir. Bunlar, bunlar hiç için tasarlanmış olan iletileri işlemek başarısız olabilir.  
  
-   Eski istemciler, hatta iletileri işlemek üzere çalışmadan önce gerçek şema doğrulaması eski şemayla gerçekleştirebilir.  
  
 Önerilen senaryolarda adları mevcut veri sözleşmeleri sabit olarak kabul et ve yenilerini benzersiz XML ile oluşturmak için tam bir yaklaşımdır. Hizmet Geliştirici sonra yeni yöntemler için var olan bir hizmet sözleşmesini eklemek veya yeni bir hizmet sözleşmesi yeni veri anlaşması kullanan yöntemleri ile oluşturabilirsiniz.  
  
 Bu genellikle tüm sürümlerini bir veri anlaşması yanı sıra her bir veri sözleşmesi sürümü için sürüme özgü iş kod içinde çalışması gereken bazı iş mantığı yazmak için bir hizmet geliştiricinin ihtiyaç duyduğu durumda olacaktır. Bu konunun sonunda ek arabirimleri bu ihtiyacı karşılamak için nasıl kullanılabileceğini açıklar.  
  
### <a name="lax-versioning"></a>Lax sürüm oluşturma  
 Diğer birçok senaryoda service geliştirici, veri anlaşması için yeni ve isteğe bağlı üye ekleme mevcut istemcilerini kesintiye uğratır değil varsayabilirsiniz. Bu mevcut istemcilerin şema doğrulaması gerçekleştirmiyorsanız olup olmadığını araştırmak Hizmet Geliştirici gerektirir ve bunlar bilinmeyen veri üyelerini yoksay. Bu senaryolarda, bölünemez bir biçimde yeni üyeler eklemek için veri anlaşması özelliklerden yararlanmak mümkündür. Hizmetin ilk sürümü için sürüm oluşturma için veri anlaşması özellikleri zaten kullanıldıysa service geliştirici bu varsayımı güvenle yapabilir.  
  
 WCF, ASP.NET Web Hizmetleri ve diğer birçok Web hizmeti yığınları desteği *lax sürüm*: diğer bir deyişle, bunlar yeni bilinmeyen veri üyeleri için özel durumlar alınan verilerde oluşturmayın.  
  
 Yeni bir üye ekleyerek mevcut istemcilerin kesintiye uğratacağını değil yanlışlıkla düşünüyorsanız daha kolaydır. Tüm istemcilerin lax sürüm işleyebilir, katı sürüm oluşturma yönergeleri kullanın ve veri önerilir değilseniz olarak sabit daraltır.  
  
 Veri sözleşmesi sürümü oluşturma lax ve katı ayrıntılı yönergeler için bkz: [en iyi uygulamalar: Veri sözleşmesi sürümü oluşturma](../../../docs/framework/wcf/best-practices-data-contract-versioning.md).  
  
### <a name="distinguishing-between-data-contract-and-net-types"></a>Veri sözleşmesi ve .NET türleri arasında ayrım  
 Bir .NET sınıf veya yapı bir veri anlaşması uygulayarak izlenebilir <xref:System.Runtime.Serialization.DataContractAttribute> öznitelik sınıfı. .NET türü ve onun veri sözleşme projeksiyonlar iki ayrı sorunları var. Aynı veri anlaşması projeksiyon ile birden çok .NET türleri olması mümkündür. Bu ayrım, böylece mevcut istemcilerin bile word'ün katı algılama uyum koruma tahmini veri sözleşme korurken .NET türünü değiştirmek izin verme özellikle yararlıdır. Her zaman bu birbirinden .NET type ve veri sözleşme korumak için yapmanız gereken iki şey vardır:  
  
-   Belirtin bir <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> ve <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>. Her zaman ve .NET türünün adı önlemek için veri anlaşması ad alanı sözleşmede açıklanmasını gelen ad alanı ve adını belirtmeniz gerekir. .NET ad alanını değiştirme veya adı yazın, daha sonra karar verirseniz, bu şekilde, veri sözleşme aynı kalır.  
  
-   Belirtin <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>. Her zaman .NET üye adınızı sözleşmede yararlanılmasını önlemek için veri üyeleri adını belirtmeniz gerekir. Daha sonra .NET üyenin adını değiştirmeye karar verirseniz, bu şekilde, veri sözleşme aynı kalır.  
  
### <a name="changing-or-removing-members"></a>Üyeleri kaldırma veya değiştirme  
 Lax sürüm kullanılabilir olsa bile bir üye adı ya da veri türünü değiştirme veya kaldırma veri üyeleri bölünmesi farklıdır. Gerekli değilse, yeni bir veri sözleşmesi oluşturun.  
  
 Yüksek önem derecesi hizmet uyumluluk ise kullanılmayan veri üyeleri, kodunuzda yoksayılıyor göz önünde bulundurun ve bunları yerinde bırakmayı. Bir veri üyesi birden çok üye içine'kurmak bölüyorsanız, varolan bir üye yerinde bir özellik olarak, gerekli bölme ve yeniden toplama (en son sürüme yükseltilmemiş istemciler) alt düzey istemciler için gerçekleştirilebilmesidir göz önünde bulundurabilirsiniz.  
  
 Benzer şekilde, veri sözleşme adı veya ad alanı yapılan değişiklikleri ayırırsınız.  
  
### <a name="round-trips-of-unknown-data"></a>Bilinmeyen veri gidiş dönüş  
 Bazı senaryolarda, yeni sürümde eklenen üyeler geldiği "gidiş-dönüş" Bilinmeyen veri gerek yoktur. Örneğin, bir "versionNew" hizmeti, bazı verileri "versionOld" istemciye yeni üyeler eklediyseniz gönderir. İstemci yeni eklenen üyeler iletiyi işlerken yok sayar, ancak geri versionNew hizmetine yeni eklenen Üyeler dahil olmak üzere, aynı veri beşe. Bu tipik bir senaryo burada veri hizmetinden alınır, değiştirilen ve döndürülen veri güncelleştirmesidir.  
  
 Belirli bir tür için gidiş dönüşü etkinleştirmek için tür uygulamalıdır <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi. Arabirim bir özellik içeren <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> döndüren <xref:System.Runtime.Serialization.ExtensionDataObject> türü. Özelliği, geçerli sürümü için bilinmeyen veri anlaşması'nın gelecek sürümlerinden herhangi bir veriyi depolamak için kullanılır. Bu veriler opak istemciye, ancak bir örneğini serileştirilmiş olduğunda, içeriğini <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> özelliği, veri sözleşme üyeleri veri geri kalanı ile yazılır.  
  
 Tüm türleri'nın yeni ve bilinmeyen gelecekteki üyeleri uyum sağlamak için bu arabirimi uygulayan önerilir.  
  
### <a name="data-contract-libraries"></a>Veri sözleşmesi kitaplıkları  
 Burada bir sözleşme için merkezi bir depo yayımlanır ve hizmet ve türü uygulayıcılar uygulamak ve bu depodan veri sözleşmeleri kullanıma veri sözleşmeleri kitaplıkları olabilir. Bu durumda, depoya bir veri anlaşması yayımladığınızda, kimin oluşturur, onu uygulayan türler üzerinde denetiminiz yoktur. Bu nedenle, yayımlandıktan sonra Sözleşme etkili bir şekilde sabit işleme değiştirilemiyor.  
  
### <a name="when-using-the-xmlserializer"></a>XmlSerializer kullanırken  
 Aynı sürüm ilkeler kullanılırken geçerlidir <xref:System.Xml.Serialization.XmlSerializer> sınıfı. Katı sürüm gerekli olduğunda, veri sözleşmeleri sabit olarak kabul et ve yeni sürümler için benzersiz, tam adlarıyla yeni veri sözleşmeleri oluşturun. Ne zaman lax sürüm kullanılabilir, yeni sürümlerinde yeni seri hale getirilebilir üyeler ekleyebilirsiniz emin ancak değiştiremez veya mevcut üyeleri kaldırın.  
  
> [!NOTE]
>  <xref:System.Xml.Serialization.XmlSerializer> Kullanan <xref:System.Xml.Serialization.XmlAnyElementAttribute> ve <xref:System.Xml.Serialization.XmlAnyAttributeAttribute> bilinmeyen veri gidiş dönüşü engelleyebilecek desteklemek için öznitelikler.  
  
## <a name="message-contract-versioning"></a>İleti sözleşmesi sürümü oluşturma  
 İleti sözleşmesi sürümü oluşturma için yönergeler, sürüm oluşturma veri sözleşmelerine oldukça benzerdir. Katı sürüm gerekiyorsa, ileti gövdesi değiştirilmemesi ancak bunun yerine benzersiz bir tam adla yeni bir ileti sözleşmesi oluşturun. Lax sürüm kullanabileceğiniz biliyorsanız, yeni ileti gövdesi bölümleri ekleyebilir ancak değil değiştirmek veya var olanları kaldırın. Bu kılavuz, her ikisi de tam olarak uygular ve ileti sözleşmeleri sarmalanmış.  
  
 İleti üstbilgileri, her zaman kesin sürüm kullanımda olsa bile eklenebilir. MustUnderstand bayrağı, sürüm oluşturma etkileyebilir. Genel olarak, sürüm üst bilgilerinde WCF için SOAP Belirtimi'nde açıklanan modelidir.  
  
## <a name="service-contract-versioning"></a>Hizmet sözleşmesi sürümü oluşturma  
 Benzer şekilde veri sözleşmesi sürümü oluşturma, hizmet sözleşmesi sürümü oluşturma da ekleme, değiştirme ve kaldırma işlemleri içerir.  
  
### <a name="specifying-name-namespace-and-action"></a>Eylem adı ve Namespace belirtme  
 Varsayılan olarak, hizmet sözleşmesi adı arabirim adıdır. Kendi varsayılan ad alanı "http://tempuri.org", ve her işlemin işlem "http://tempuri.org/contractname/methodname". Önerilen açıkça bir ad ve ad alanı için hizmet sözleşmesi ve kullanmaktan kaçınmak her işlem için bir eylem belirtin "http://tempuri.org" ve arabirimi ve yöntem adları hizmet sözleşmesinde yararlanılmasını önlemek için.  
  
### <a name="adding-parameters-and-operations"></a>Parametreleri ve işlem ekleme  
 Mevcut istemciler bu yeni işlemleri hakkında endişe olması gerekmez çünkü hizmet tarafından sunulan hizmet işlemleri ekleme bölünemez bir değişikliktir.  
  
> [!NOTE]
>  İşlem için çift yönlü bir geri çağırma anlaşması ekleme bölünmesi farklıdır.  
  
### <a name="changing-operation-parameter-or-return-types"></a>Değiştirme işlemi parametre veya dönüş türleri  
 Eski tür tarafından uygulanan aynı veri anlaşması yeni türün uyguladığı sürece, parametre veya dönüş türleri genellikle değiştirme bölünmesi farklıdır. Böyle bir değişiklik yapmak için hizmet sözleşmesi yeni işlem ekleyebilir veya yeni bir hizmet sözleşmesini tanımlama.  
  
### <a name="removing-operations"></a>İşlemleri kaldırılıyor  
 Kaldırma işlemleri bölünmesi farklıdır. Böyle bir değişiklik yapmak için yeni bir hizmet sözleşmesini tanımlama ve yeni bir uç nokta üzerinden kullanıma sunacaksınız.  
  
### <a name="fault-contracts"></a>Hata sözleşmeleri  
 <xref:System.ServiceModel.FaultContractAttribute> Özniteliği sözleşmenin işlemlerinden döndürülen hatalar hakkında bilgi belirtmek bir hizmet sözleşmesi Geliştirici sağlar.  
  
 Bir hizmetin sözleşmede açıklanan hataların listesi kapsamlı olarak kabul edilmez. Herhangi bir zamanda bir işlem içinde sözleşmesi açıklanmayan hataları döndürebilir. Bu nedenle sözleşmede açıklanan hataları kümesini değiştirme bozucu olarak kabul edilmez. Örneğin, sözleşme kullanarak yeni bir hata ekleme <xref:System.ServiceModel.FaultContractAttribute> veya mevcut bir hataya sözleşmeden kaldırılıyor.  
  
### <a name="service-contract-libraries"></a>Hizmet sözleşmesi kitaplıkları  
 Kuruluşların, burada bir sözleşme için merkezi bir depo yayımlanır ve bu depoyu sözleşmelerden hizmet uygulayıcılar uygulamak sözleşmeleri kitaplıkları olabilir. Bu durumda, depoya bir hizmet sözleşmesini yayımladığınızda kimin uygulamak Hizmetleri oluşturur üzerinde denetiminiz yoktur. Bu nedenle etkili bir şekilde sabit işleme yayımlandıktan sonra hizmet sözleşmesini değiştiremiyor. WCF mevcut sözleşmelerinin genişleten yeni bir sözleşme oluşturmak için kullanılan anlaşma devralma destekler. Bu özelliği kullanmak için eski hizmet sözleşme arabirimden devralan yeni bir hizmet sözleşme arabirimi tanımlayın, sonra yeni arabirimine yöntemleri ekleyin. Ardından, yeni sözleşme uygulamak ve yeni sözleşme kullanmak için "versionOld" uç nokta tanımı değiştirmek için eski sözleşme uygulayan hizmette de değiştirin. "VersionOld" istemciler için uç nokta olarak ifşa edildi "versionOld" Sözleşme görüntülenmeye devam eder; "versionNew" istemcilere "versionNew" Sözleşme kullanıma sunmak için uç nokta görünür.  
  
## <a name="address-and-binding-versioning"></a>Adres ve bağlama sürüm oluşturma  
 İstemciler yeni uç nokta adresini dinamik olarak bulmak veya bağlama yeteneğine sahip değilseniz uç nokta adresi ve bağlama yapılan değişiklikleri ayırırsınız. Bir evrensel keşif açıklaması ve tümleştirme (UDDI) kayıt defteri ve burada bir istemci bir uç nokta ile iletişim kurmaya çalışır ve iyi bilinen UDDI başarısızlık durumunda, sorgular UDDI çağırma deseni kullanarak bu özelliği uygulamak için bir mekanizma olan Geçerli uç nokta meta veriler için kayıt defteri. İstemci ardından bu meta verilerden bağlamasını ve adresini uç noktası ile iletişim kurmak için kullanır. Bu iletişim başarılı olursa, istemci gelecekte kullanım için adres ve bağlama bilgilerini önbelleğe alır.  
  
## <a name="routing-service-and-versioning"></a>Yönlendirme hizmeti ve sürüm oluşturma  
 Durumunda bir hizmette yapılan değişiklikleri değişiklikleri ve iki veya daha fazla farklı sürümlerini çalıştıran bir hizmet için aynı anda WCF yönlendirme hizmeti iletileri yönlendirmek için uygun bir hizmet örneği kullanabilirsiniz. WCF yönlendirme hizmeti, içerik tabanlı yönlendirme kullanan, diğer bir deyişle, ileti yolu yerini belirlemek için message içindeki bilgileri kullanır. WCF yönlendirme hizmeti bakın hakkında daha fazla bilgi için [yönlendirme hizmeti](../../../docs/framework/wcf/feature-details/routing-service.md). Hizmet sürümü oluşturma için yönlendirme WCF hizmetini kullanmaya ilişkin bir örnek için bkz: [nasıl yapılır: Hizmet sürümü oluşturma](../../../docs/framework/wcf/feature-details/how-to-service-versioning.md).  
  
## <a name="appendix"></a>Ek  
 Katı bir sürüm gerektiğinde genel veri sözleşmesi sürümü oluşturma kılavuzu değişiklikleri gerekli olduğunda veri sözleşmeleri sabit olarak kabul et ve yenilerini oluşturmaktır. Yeni bir sınıf her yeni bir veri anlaşması için oluşturulması gerekir, eski verileri de yazılmış varolan kod almak zorunda kalmamak için bir mekanizma gerekmez, sınıf sözleşme ve açısından yeni veri sözleşme sınıfı yeniden.  
  
 Tür mekanizmalardan biridir, her veri anlaşması üyelerini tanımlamak ve iç uygulama kodu arabirimleri uygulayan veri sözleşme sınıfları yerine arabirimleri açısından yazma arabirimleri kullanmaktır. Aşağıdaki kod, bir hizmetin sürüm 1 için gösterir bir `IPurchaseOrderV1` arabirimi ve `PurchaseOrderV1`:  
  
```  
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
  
 Hizmet sözleşme işlemleri açısından yazılması sırada `PurchaseOrderV1`, gerçek iş mantığı açısından olacaktır `IPurchaseOrderV1`. Ardından, sürüm 2'de, olacaktır yeni `IPurchaseOrderV2` arabirimi ve yeni bir `PurchaseOrderV2` aşağıdaki kodda gösterildiği gibi sınıf:  
  
```  
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
  
 Hizmet sözleşmesi açısından yazılan yeni işlemleri içerecek şekilde güncelleştirilmesi `PurchaseOrderV2`. Var olan iş mantığındaki açısından yazılan `IPurchaseOrderV1` için çalışmaya devam eder `PurchaseOrderV2` ve gereken yeni iş mantığı `OrderDate` özelliği de yazılabilir `IPurchaseOrderV2`.  
  
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
- [Veri Anlaşması Eşitliği](../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [Sürüm Toleranslı Seri Hale Getirme Geri Çağrıları](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)
