---
title: "Hizmet Sürümü Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37575ead-d820-4a67-8059-da11a2ab48e2
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 73b7fd7564fea065167978deaad21bb533dbef0c
ms.sourcegitcommit: 425524461530f020f9747492b42f8cd72b011ae7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2017
---
# <a name="service-versioning"></a>Hizmet Sürümü Oluşturma
İlk dağıtım ve olası birkaç kez kendi ömürleri sırasında sonra Hizmetleri (ve bunların kullanıma uç noktaları) çeşitli değişen işletme gereksinimlerine göre bilgi teknolojisi gereksinimleri gibi nedenlerle, değiştirilecek veya diğer gidermenin gerekebilir sorunları. Her değişiklik hizmeti yeni bir sürümünü kullanıma sunmaktadır. Bu konuda, sürüm oluşturma dikkate alınması gereken açıklanmaktadır [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].  
  
## <a name="four-categories-of-service-changes"></a>Hizmet değişikliklerini dört kategorisi  
 Gerekli hizmetler değişiklikleri dört kategoriye sınıflandırılabilir:  
  
-   Sözleşme değişiklikleri: Örneğin, bir işlem eklenebilir veya bir veri öğesi iletide eklenen veya değiştirilen.  
  
-   Adres değişiklikleri: Örneğin, bir hizmet uç noktaları yeni adresleri olduğu farklı bir konuma taşır.  
  
-   Değişiklikleri bağlama: Örneğin, bir güvenlik mekanizması değiştirir veya ayarlarını değiştirebilirsiniz.  
  
-   Uygulama değişiklikleri: Örneğin, bir iç yöntem uygulaması değiştiğinde.  
  
 Bu değişikliklerden bazıları "sonu" olarak adlandırılır ve diğerleri "bölünemez." Bir değişiklik *bölünemez* başarıyla yeni sürümde işlenen başarılı bir şekilde bir önceki sürümde işlenen tüm iletileri. Bu ölçütü karşılamayan herhangi bir değişiklik olup bir *sonu* değiştirin.  
  
## <a name="service-orientation-and-versioning"></a>Hizmet yönlendirmesi ve sürüm oluşturma  
 Hizmet yönlendirmesi tenets hizmetler ve istemcileri otonom (veya bağımsız) biridir. Bunun yanı sıra, bu hizmet geliştiricileri denetlemek veya hatta tüm hizmeti istemcileri hakkında bilmeniz varsayın olamaz anlamına gelir. Bu, yeniden oluşturma ve tüm istemcilere hizmet değişiklikleri sürümleri zaman dağıtarak seçeneğinin ortadan kaldırır. Bu konu, hizmet için bu tenet aynılarını ve bu nedenle, istemcileri değiştirilmiş veya "sürümlü" bağımsız olmalıdır varsayar.  
  
 Önemli bir değişiklik, beklenmeyen bir durumdur ve kaçınılmaz olduğu durumlarda, bir uygulama bu tenet yoksay ve istemcilerin yeniden ve hizmetin yeni bir sürümü ile imzalanmasını gerektirir seçebilirsiniz.  
  
## <a name="contract-versioning"></a>Sözleşmesi sürümü oluşturma  
 Bir istemci tarafından kullanılan sözleşmeleri hizmeti tarafından kullanılan sözleşme ile aynı olması gerekmez; yalnızca uyumlu olması gerekir.  
  
 Hizmet sözleşmeleri için Uyumluluk anlamına gelir yeni işlem hizmeti tarafından sunulan eklenebilir, ancak mevcut işlemleri kaldırılamıyor veya anlamsal olarak değiştirildi.  
  
 Veri sözleşmeleri için Uyumluluk tanımları eklenen yeni şema türü anlamına gelir ancak yolları bölme varolan şema türü tanımları değiştirilemez. Yeni değişiklikler veri üyeleri kaldırma veya kendi veri türü incompatibly değiştirme içerebilir. Bu özellik, istemcilerin bozmadan kendi sözleşmeleri sürümü değiştirmede bazı enlem hizmet sağlar. Sonraki iki bölümde bölünemez ve için yapılan önemli değişiklikler açıklayan [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] veri ve hizmet sözleşmeleri.  
  
## <a name="data-contract-versioning"></a>Veri Sözleşmesi Sürümü Oluşturma  
 Bu bölüm veri sürüm oluşturma kullanırken ilgilenir <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.DataContractAttribute> sınıfları.  
  
### <a name="strict-versioning"></a>Katı sürüm oluşturma  
 Çoğu senaryoda sürümleri değiştirme bir sorun olduğunda service Geliştirici istemciler üzerinde denetim sahibi değildir ve bu nedenle nasıl bunlar ileti XML veya şema değişiklikleri tepki hakkında varsayımlar yapamazsınız. Bu durumlarda, yeni iletiler iki nedenden dolayı eski şemasına göre doğrulayacak etmeleri gerekir:  
  
-   Eski istemciler şema değişmez varsayımına ile geliştirilmiştir. Bunlar hiçbir zaman için tasarlanmış iletileri işlemek başarısız.  
  
-   Eski istemciler iletileri işlemek bile denemeden önce eski şemasına karşılık gerçek şema doğrulamasını gerçekleştirebilir.  
  
 Önerilen senaryolarda adları mevcut veri sözleşmeleri değişmez olarak kabul eder ve benzersiz XML ile yeni bir tane oluşturmak için tam bir yaklaşımdır. Hizmet Geliştirici ardından var olan bir hizmet sözleşmeyi yeni yöntemleri ekleyin ya da yeni bir hizmet sözleşmesi yeni veri sözleşmesi kullanan yöntemleri ile oluşturun.  
  
 Bu genellikle bir veri sözleşmesi yanı sıra her bir veri sözleşmesi sürümü için sürüme özgü iş kodu tüm sürümleri içinde çalışması gereken bazı iş mantığı yazmak için bir hizmet geliştiricinin ihtiyacı durumda olacaktır. Bu konunun sonundaki ek arabirimleri bu gereksinimi karşılamak için nasıl kullanılabileceği açıklanır.  
  
### <a name="lax-versioning"></a>Belirsiz sürüm oluşturma  
 Birçok diğer senaryolarda, hizmet geliştirici, yeni, isteğe bağlı bir üye veri sözleşmesi ekleme mevcut istemcilerin sonu olmayan varsayabilirsiniz. Bu, mevcut istemciler şema doğrulaması gerçekleştirmiyorsanız olup araştırmak Hizmet Geliştirici gerektirir ve bilinmeyen veri üyelerini yoksay. Bu senaryolarda, bölünemez şekilde yeni üye eklemek için veri sözleşmesi özelliklerden yararlanmak mümkündür. Sürüm oluşturma için veri sözleşmesi özellikleri zaten hizmet ilk sürüm için kullanıldıysa service geliştirici bu güvenle varsayabilirsiniz.  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], ASP.NET Web Hizmetleri ve birçok diğer Web hizmeti yığınları desteği *belirsiz sürüm*: başka bir deyişle, bunlar yeni bilinmeyen veri üyeleri için özel durumlar alınan verileri oluşturmayın.  
  
 Yeni bir üye ekleme mevcut istemcilerin kesintiye uğrar değil, yanlışlıkla düşünüyorsanız kolaydır. Tüm istemcilerin belirsiz sürüm işleyebilir, katı sürüm oluşturma yönergelerini kullanın ve veri önerilir değilseniz olarak değişmez sözleşme.  
  
 Veri sözleşmeleri belirsiz ve katı sürüm oluşturma için ayrıntılı yönergeler için bkz: [en iyi uygulamalar: veri sözleşmesi sürümü oluşturma](../../../docs/framework/wcf/best-practices-data-contract-versioning.md).  
  
### <a name="distinguishing-between-data-contract-and-net-types"></a>Veri sözleşmesi ve .NET türleri arasında ayrım  
 .NET sınıf veya yapı bir veri sözleşmesi uygulayarak izlenebilir <xref:System.Runtime.Serialization.DataContractAttribute> öznitelik sınıfı. .NET türü ve kendi veri sözleşmesi tahminleri iki ayrı önemlidir markalarıdır. Aynı veri sözleşmesi projeksiyon birden çok .NET tür olması mümkündür. Bu ayrım .NET türü böylece bile Word katı algılama mevcut istemcilerin uyumluluğunu koruma tahmini veri sözleşmesi korurken değiştirmenize olanak tanır özellikle yararlı olur. Bu ayrım .NET türü ve veri sözleşmesi arasındaki korumak için her zaman yapmanız gereken iki şey vardır:  
  
-   Belirtin bir <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> ve <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>. Her zaman adını ve ad alanı .NET türünün adı önlemek için veri sözleşmesi olarak açık hale gelen ad belirtmeniz gerekir. Daha sonra .NET ad alanı değiştirme veya adı yazın karar verirseniz, bu şekilde, veri sözleşmesi aynı kalır.  
  
-   Belirtin <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>. Her zaman .NET üye adı olarak gösterilen önlemek için veri üyelerinin adını belirtmeniz gerekir. Daha sonra üye .NET adını değiştirmeye karar verirseniz, bu şekilde, veri sözleşmesi aynı kalır.  
  
### <a name="changing-or-removing-members"></a>Değiştirme veya üyeleri kaldırma  
 Belirsiz sürüm izin üye adı veya veri türünü değiştirme veya veri üyeleri kaldırma önemli bir değişiklik olsa dahi. Bu gerekli ise, yeni bir veri sözleşmesi oluşturun.  
  
 Hizmet uyumluluk yüksek önem düzeyi ise kullanılmayan veri üyeleri kodunuzda yoksayılıyor göz önünde bulundurun ve yerinde bırakın. Bir veri üyesi birden çok üye içine yukarı bölme, varolan bir üye yerinde bir özellik olarak, gerekli bölme ve yeniden toplama alt düzey istemciler (en son sürüme yükseltilmemiş istemciler) için gerçekleştirilebilmesidir düşünebilirsiniz.  
  
 Benzer şekilde, veri sözleşmenin adı veya ad alanı değişiklikleri değişiklikleri ayırırsınız.  
  
### <a name="round-trips-of-unknown-data"></a>Gidiş dönüş bilinmeyen veri  
 Bazı senaryolarda, yeni sürümde eklenen üyeler geldiği "gidiş dönüş" Bilinmeyen veri gerek yoktur. Örneğin, "versionNew" hizmeti bazı verilerle üyeleri "versionOld" istemcisi için yeni eklenen gönderir. İleti işleme sırasında istemci yeni eklenen üyeler yoksayar, ancak geri versionNew hizmetine yeni eklenen üyeleri de dahil olmak üzere bu aynı verileri yeniden gönderir. Tipik senaryo burada veri hizmetinden alınan, değiştirilen ve döndürülen veri güncelleştirmesidir.  
  
 Belirli bir tür için gidiş etkinleştirmek için türü uygulamalıdır <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi. Bir özellik arabirimi içerir <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> döndüren <xref:System.Runtime.Serialization.ExtensionDataObject> türü. Özelliği için geçerli sürümü bilinmiyor veri sözleşmesi gelecek sürümlerinden herhangi bir veriyi depolamak için kullanılır. Bu veriler opak istemciye, ancak örnek serileştirildiğinde, içeriği <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> özelliği, veri sözleşmesi üyeleri veri geri kalanı ile yazılır.  
  
 Tüm türleri yeni ve bilinmeyen gelecekteki üyeleri uyum sağlamak için bu arabirimi uygulayan önerilir.  
  
### <a name="data-contract-libraries"></a>Veri sözleşmesi kitaplıkları  
 Burada bir sözleşme merkezi bir depoya yayımlanır ve hizmeti ve türü Implementers uygulamak ve bu depodan veri sözleşmeleri kullanıma veri sözleşmeleri kitaplıklarının olabilir. Bu durumda, bir veri sözleşmesi depoya yayımladığınızda, kimin uyguladıktan türleri oluşturur üzerinde denetiminiz yoktur. Bu nedenle, yayımlandıktan sonra etkili bir şekilde değişmez işleme sözleşme değiştiremezsiniz.  
  
### <a name="when-using-the-xmlserializer"></a>XmlSerializer kullanırken  
 Aynı sürüm oluşturma ilkeleri kullanırken geçerlidir <xref:System.Xml.Serialization.XmlSerializer> sınıfı. Katı sürüm gerekli olduğunda, veri sözleşmeleri değişmez olarak kabul eder ve yeni sürümler için benzersiz, tam adlarıyla yeni veri sözleşmeleri oluşturun. Ne zaman belirsiz sürüm kullanılabilir, yeni sürümlerde yeni seri hale getirilebilir üye ekleyebilir eminseniz ancak değiştirme veya var olan üyeleri kaldırın.  
  
> [!NOTE]
>  <xref:System.Xml.Serialization.XmlSerializer> Kullanan <xref:System.Xml.Serialization.XmlAnyElementAttribute> ve <xref:System.Xml.Serialization.XmlAnyAttributeAttribute> bilinmeyen veri gidiş desteklemek için öznitelikler.  
  
## <a name="message-contract-versioning"></a>İleti sözleşmesi sürümü oluşturma  
 İleti sözleşmesi sürümü oluşturma için yönergeler sürüm veri sözleşmelerine çok benzer. Katı sürüm gerekiyorsa, ileti gövdesi değiştirilmemesi ancak bunun yerine benzersiz bir tam adı ile yeni bir ileti sözleşmesi oluşturun. Belirsiz sürüm kullanabileceğiniz biliyorsanız, yeni ileti gövdesi bölümleri ekleyebilir ancak değil değiştirmek veya var olanları kaldırın. Bu kılavuz, hem tam uygular ve ileti sözleşmeleri Sarmalanan.  
  
 İleti üstbilgilerini, her zaman katı sürüm kullanımda olsa bile eklenebilir. MustUnderstand bayrağı sürüm etkileyebilir. Sürüm oluşturma genel olarak, model üstbilgilerinde için [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] SOAP belirtimi içinde açıklandığı gibi.  
  
## <a name="service-contract-versioning"></a>Hizmet sözleşmesi sürümü oluşturma  
 Benzer şekilde veri sözleşmesi sürümü oluşturma, hizmet sözleşmesi sürümü oluşturma da ekleme, değiştirme ve kaldırma işlemlerini içerir.  
  
### <a name="specifying-name-namespace-and-action"></a>Ad, Namespace ve eylem belirtme  
 Varsayılan olarak, hizmet sözleşmesi adı arabirimi adıdır. Kendi varsayılan ad alanı "http://tempuri.org" ve "http://tempuri.org/contractname/methodname" her işlemin eylemdir. Açıkça bir ad ve hizmet sözleşmesi için ad alanı ve her bir işlemin "http://tempuri.org" kullanmaktan kaçının ve hizmetin sözleşmede gösterilen arabirim ve yöntem adları önlemek için bir eylem belirtin önerilir.  
  
### <a name="adding-parameters-and-operations"></a>Parametreler ve işlemler ekleme  
 Mevcut istemciler bu yeni işlemleri hakkında endişe olması gerekmez çünkü hizmeti tarafından sunulan hizmet işlemleri ekleme bölünemez bir değişikliktir.  
  
> [!NOTE]
>  Çift yönlü geri çağırma sözleşmeye işlemleri eklenmesi sonu bir değişikliktir.  
  
### <a name="changing-operation-parameter-or-return-types"></a>Değiştirme işlemi parametresi veya dönüş türleri  
 Yeni türü eski türü tarafından uygulanan aynı veri sözleşmesi uygulayan sürece parametresi veya return türlerini genellikle değiştirme sonu farklıdır. Bu tür bir değişiklik yapmak için yeni bir işlem için hizmet sözleşmesini eklemek veya yeni bir hizmet sözleşmesi tanımlayın.  
  
### <a name="removing-operations"></a>İşlemleri kaldırma  
 İşlemleri kaldırma, önemli bir değişiklik değil. Bu tür bir değişiklik yapmak için yeni bir hizmet sözleşmesini tanımlama ve yeni bir uç noktada kullanıma sunar.  
  
### <a name="fault-contracts"></a>Hataya sözleşmeleri  
 <xref:System.ServiceModel.FaultContractAttribute> Özniteliği sözleşmenin işlemlerinden döndürülen hatalar hakkında bilgi belirtmek bir hizmet sözleşmesi Geliştirici sağlar.  
  
 Bir hizmet sözleşmesinde açıklanan hatalarının listesini, kapsamlı sayılmaz. Herhangi bir anda bir işlem, sözleşmede açıklanmayan hataları döndürebilir. Bu yüzden sözleşmede açıklanan hataları kümesini değiştirme yeni olarak kabul edilmez. Örneğin, yeni bir arıza sözleşme kullanmaya ekleme <xref:System.ServiceModel.FaultContractAttribute> veya varolan bir hataya sözleşmeden kaldırma.  
  
### <a name="service-contract-libraries"></a>Hizmet sözleşmesi kitaplıkları  
 Kuruluşlar, burada bir sözleşme merkezi bir depoya yayımlanır ve bu depoyu sözleşmelerinden hizmet Implementers uygulamak sözleşmeleri kitaplıklarının olabilir. Bu durumda, bir hizmet sözleşmesini depoya yayımladığınızda, kimin uyguladıktan Hizmetleri oluşturur üzerinde denetiminiz yoktur. Bu nedenle, etkili bir şekilde değişmez işleme yayımlandıktan sonra hizmet sözleşmesini değiştiremiyor. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]destekler varolan sözleşmeleri genişleten yeni bir sözleşme oluşturmak için kullanılan devralma sözleşme. Bu özelliği kullanmak için eski hizmet sözleşmesi arabirimden devralan yeni bir hizmet sözleşme arabirimi tanımlayın, sonra yeni arabirim yöntemleri ekleyin. Ardından, yeni sözleşme uygulamak ve yeni sözleşme kullanmak için "versionOld" uç nokta tanımı değiştirmek için eski sözleşme uygulayan hizmeti de değiştirin. "VersionOld" istemcilere uç nokta olarak sunan "versionOld" Sözleşme görünmeye devam edecek; "versionNew" istemcilere endpoint "versionNew" Sözleşme kullanıma sunmak için görüntülenir.  
  
## <a name="address-and-binding-versioning"></a>Adres ve bağlama sürüm oluşturma  
 İstemcileri yeni uç nokta adresi dinamik olarak bulma veya bağlama yeteneğine sahip olmadığınız sürece uç noktası adresi ve bağlama değişiklikler değişiklikleri ayırırsınız. Bu özelliği uygulamak için bir kayıt defterine Evrensel bulma açıklama ve tümleştirme (UDDI) ve UDDI çağırma olduğu bir istemci bir uç nokta ile iletişim kurmaya çalışır ve, başarısızlık durumunda, iyi bilinen UDDI sorgular düzeni kullanarak mekanizmadır Geçerli uç nokta meta veriler için kayıt defteri. İstemci ardından adresi ve bu meta verilerden bağlama bitiş noktası ile iletişim kurmak için kullanır. Bu iletişim başarılı olursa, istemci gelecekte kullanım için adres ve bağlama bilgilerini önbelleğe alır.  
  
## <a name="routing-service-and-versioning"></a>Yönlendirme hizmeti ve sürüm oluşturma  
 Değişiklikleri ve yeni bir hizmet için yapılan değişiklikler, iki veya daha fazla farklı sürümlerini çalıştıran bir hizmet sağlamak için aynı anda WCF yönlendirme hizmeti iletileri yönlendirmek için uygun hizmet örneği için kullanabileceğiniz. Yönlendirme WCF hizmeti içerik tabanlı yönlendirme kullanıyor, diğer bir deyişle, ileti yönlendirmek nereye belirlemek için ileti içindeki bilgileri kullanır. [!INCLUDE[crabout](../../../includes/crabout-md.md)]WCF yönlendirme hizmeti Bkz: [yönlendirme hizmeti](../../../docs/framework/wcf/feature-details/routing-service.md). Hizmet sürümü oluşturma için yönlendirme WCF hizmetini kullanma örneği için bkz: [nasıl yapılır: Hizmet sürümü oluşturma](../../../docs/framework/wcf/feature-details/how-to-service-versioning.md).  
  
## <a name="appendix"></a>Ek  
 Veri sözleşmeleri değişmez olarak kabul eder ve değişikliklerin gerekli olduğunda yeni kampanya oluşturmak için katı sürüm gerektiğinde genel veri sözleşmesi sürümü oluşturma yönergeler verilmiştir. Yeni bir sınıf için her yeni veri sözleşmesi oluşturulmalıdır, bir mekanizma cinsinden yazılmış varolan kodun almak zorunda kalmamak için gerektiği şekilde eski verileri sınıfı sözleşme ve yeni veri sözleşme sınıfı bakımından yeniden yazma.  
  
 Bu tür bir mekanizma, her veri sözleşmesi üyelerini tanımlamak ve iç uygulama kodu arabirimlerini veri sözleşmesi sınıfları yerine arabirimler açısından yazma arabirimleri kullanmaktır. Aşağıdaki kod, bir hizmetin sürüm 1 için gösterir bir `IPurchaseOrderV1` arabirimi ve `PurchaseOrderV1`:  
  
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
  
 Hizmet sözleşmenin işlemleri cinsinden yazılacak sırada `PurchaseOrderV1`, gerçek iş mantığı cinsinden olacaktır `IPurchaseOrderV1`. Ardından, sürüm 2'de, olurdu yeni bir `IPurchaseOrderV2` arabirimi ve yeni bir `PurchaseOrderV2` sınıfı aşağıdaki kodda gösterildiği gibi:  
  
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
  
 Hizmet sözleşmesi cinsinden yazılan yeni işlem içerecek şekilde güncelleştirilmesi `PurchaseOrderV2`. Cinsinden yazılan var olan iş mantığı `IPurchaseOrderV1` için çalışmaya devam edeceği `PurchaseOrderV2` ve gereken yeni iş mantığı `OrderDate` özelliği cinsinden yazılması `IPurchaseOrderV2`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>  
 <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>  
 <xref:System.Runtime.Serialization.IExtensibleDataObject>  
 <xref:System.Runtime.Serialization.ExtensionDataObject>  
 <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [Veri sözleşmesi eşitliği](../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [Sürüm toleranslı seri hale getirme geri çağrıları](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)
