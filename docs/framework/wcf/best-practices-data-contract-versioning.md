---
title: 'En İyi Uygulamalar: Veri Sözleşmesi Sürümü Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- service contracts
- best practices [WCF], data contract versioning
- Windows Communication Foundation, data contracts
ms.assetid: bf0ab338-4d36-4e12-8002-8ebfdeb346cb
ms.openlocfilehash: 33db8749656a8bb001f0a1797c77451476a126f2
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33808542"
---
# <a name="best-practices-data-contract-versioning"></a>En İyi Uygulamalar: Veri Sözleşmesi Sürümü Oluşturma
Bu konu, zaman içinde kolayca gelişmesi veri sözleşmeleri oluşturmak için en iyi uygulamaları listeler. Veri sözleşmeleri hakkında daha fazla bilgi için konulara bakın [kullanarak veri sözleşmeleri](../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
## <a name="note-on-schema-validation"></a>Şema doğrulaması göz önünde bulundurun  
 Veri sözleşmesi sürümü oluşturma ele de, Windows Communication Foundation (WCF) tarafından verilen veri sözleşmesi şema öğeleri varsayılan olarak isteğe bağlı olarak işaretlenmiş olgu dışındaki herhangi bir sürüm destek yok dikkate almak önemlidir.  
  
 Bu, yeni bir veri üye ekleme gibi bile en yaygın sürüm senaryo, belirli bir şema ile sorunsuz bir şekilde uygulanamayacağını anlamına gelir. Bir veri sözleşmesine (yeni bir veri üyesi, örneğin) daha yeni sürümleri eski Şeması'nı kullanarak doğrulamaz.  
  
 Ancak, kesin şema uyumluluk gerekli değil birçok senaryo vardır. ASP.NET kullanılarak oluşturulan WCF ve XML Web Hizmetleri dahil olmak üzere birçok Web Hizmetleri platformda değil şema doğrulaması varsayılan olarak gerçekleştirmek ve bu nedenle şema tarafından açıklanmayan ekstra öğeler tolerans. Bu tür platformları ile çalışırken, çok sayıda sürüm oluşturma senaryoları uygulamak daha kolaydır.  
  
 Bu nedenle, var olan iki veri kümesi sözleşme sürüm oluşturma yönergelerini: Burada kesin şema geçerlilik önemlidir ve başka ayarlayın senaryoları için olmadığında senaryolar için ayarlayın.  
  
## <a name="versioning-when-schema-validation-is-required"></a>Şema doğrulaması gerekli olduğunda sürüm oluşturma  
 Kesin Şema geçerlilik tüm yönlerde (eski yeni ve eski yeni) gerekirse, veri sözleşmeleri değişmez dikkate alınmalıdır. Sürüm oluşturma gerekiyorsa, yeni bir veri sözleşmesi, farklı bir ad veya ad alanı, ile oluşturulmalıdır ve veri türünü kullanarak hizmet sözleşmesini uygun şekilde sürümlü olmalıdır.  
  
 Örneğin, hizmet sözleşmesini adlı işleme bir satın alma siparişi `PoProcessing` ile bir `PostPurchaseOrder` işlem için uyumlu bir parametre alan bir `PurchaseOrder` veri sözleşme. Varsa `PurchaseOrder` sözleşme sahip değiştirmek, diğer bir deyişle, yeni bir veri sözleşmesi oluşturmalısınız `PurchaseOrder2`, değişiklikler içerir. Ardından hizmet sözleşmesi düzeyinde sürüm işlemesi gerekir. Oluşturarak Örneğin, bir `PostPurchaseOrder2` alır işlemi `PurchaseOrder2` parametresi veya oluşturarak bir `PoProcessing2` hizmet sözleşmesini nerede `PostPurchaseOrder` işlemi alır bir `PurchaseOrder2` veri sözleşme.  
  
 Diğer veri sözleşmeleri tarafından başvurulan veri sözleşmelerinde değişiklikleri Ayrıca hizmet modeli katmanını genişletme unutmayın. Örneğin, önceki senaryoda `PurchaseOrder` veri sözleşmesi değiştirmeniz gerekmez. Ancak, bir veri üyesi içeren bir `Customer` sırayla veri üyesi yer alan veri sözleşmesi `Address` değiştirilmesi gereken veri sözleşme. Bu durumda, oluşturmanız gerekecek bir `Address2` veri sözleşmesi gerekli değişiklikleri bir `Customer2` içeren veri sözleşmesi `Address2` veri üyesi ve `PurchaseOrder2` içeren veri sözleşmesi bir `Customer2` veri üyesi. Önceki durumda olduğu gibi hizmet sözleşmesi de sürümlü olması gerekir.  
  
 ("2" ekleyerek) adlarının değiştirilmesi bu örneklerde rağmen yeni ad alanları bir sürüm numarası veya bir tarih ile ekleyerek adları yerine ad alanlarını değiştirmek için önerilir. Örneğin, `http://schemas.contoso.com/2005/05/21/PurchaseOrder` veri sözleşmesi değiştirmek için `http://schemas.contoso.com/2005/10/14/PurchaseOrder` veri sözleşme.  
  
 En iyi yöntemleri daha fazla bilgi için bkz: [hizmet sürümü oluşturma](../../../docs/framework/wcf/service-versioning.md).  
  
 Bazen, uygulamanız tarafından gönderilen iletiler için kesin şema uyumluluğu güvence altına almalıdır ancak kesinlikle şeması uyumlu olacak şekilde gelen iletileri bağlı olamaz. Bu durumda, gelen iletiyi gereksiz veriler içerebilir tehlike yoktur. Yabancı değerler depolanabilir ve WCF tarafından döndürülen ve böylece gönderilen şema geçersiz iletilerinde sonuçlanır. Bu sorunu önlemek için gidiş özelliği kapatılması. Bunu yapmanın iki yolu vardır.  
  
-   Uygulamayan <xref:System.Runtime.Serialization.IExtensibleDataObject> türlerinizi hiçbirinde arabirimi.  
  
-   Geçerli bir <xref:System.ServiceModel.ServiceBehaviorAttribute> öznitelik, hizmet sözleşmesi ile <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> özelliğini `true`.  
  
 Gidiş hakkında daha fazla bilgi için bkz: [İleri uyumlu veri sözleşmeleri](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
## <a name="versioning-when-schema-validation-is-not-required"></a>Şema doğrulama gerekli olmadığında sürüm oluşturma  
 Kesin şema uyumluluk nadiren gereklidir. Birçok platformda şeması tarafından açıklanmayan ekstra öğeler tolerans. Bu izin sürece, özellikleri, tamamını açıklanan [veri sözleşmesi sürümü oluşturma](../../../docs/framework/wcf/feature-details/data-contract-versioning.md) ve [İleri uyumlu veri sözleşmeleri](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md) kullanılabilir. Aşağıdaki yönergeler tavsiye edilir.  
  
 Bazı kılavuzları tam olarak bir tür yeni sürümleri daha eski bir beklenirken göndermek için izlenmesi gereken veya yeni bir beklenirken eski bir gönderin. Diğer yönergeleri kesinlikle gerekli değildir, ancak şema sürüm gelecekteki tarafından etkilenebilir çünkü burada listelenir.  
  
1.  Sürüm veri sözleşmelerine göre tür devralma çalışmayın. Daha yeni sürümlerini oluşturmak için mevcut bir türle veri sözleşme değiştirin veya yeni ilişkisiz türü oluşturun.  
  
2.  Veri sözleşmeleri birlikte devralma kullanımını, devralma sürüm oluşturma mekanizması olarak kullanılmaz ve belirli kurallar ardından koşuluyla izin verilir. Bazı temel türünden bir türü türetilen varsa, onu farklı bir taban türü gelecek bir sürümünde öğesinden türetilen yapmayın (aynı verilere sahip olmadığı sürece sözleşme). Bu bir istisna vardır: bir veri sözleşmesi türünün temel türü arasındaki hiyerarşi içine bir türü ekleyebilirsiniz, ancak yalnızca veri üyeleriyle içermiyorsa, aynı diğer üyeleri hiyerarşideki diğer türleri olası tüm sürümlerini adları. Genel olarak, veri üyeleri aynı farklı düzeylerde aynı adlarıyla kullanarak Devralma Hiyerarşisi ciddi sürüm sorunlara yol açabilir ve kaçınılmalıdır.  
  
3.  İlk veri sözleşmesi sürümü ile başlayarak, her zaman uygulamak <xref:System.Runtime.Serialization.IExtensibleDataObject> gidiş etkinleştirmek için. Daha fazla bilgi için bkz: [İleri uyumlu veri sözleşmeleri](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md). Bu arabirim uygulamadan bir türü bir veya daha fazla sürümleri yayımlandı durumunda türü bir sonraki sürümde uygulayın.  
  
4.  Sonraki sürümlerde, veri sözleşme adı veya ad alanı değiştirmeyin. Adı veya temel veri sözleşmesi türünün ad alanını değiştirme, uygun mekanizmaları gibi kullanarak ad alanı ve veri sözleşmesi adını doğru yazdığınızdan emin <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> özelliği <xref:System.Runtime.Serialization.DataContractAttribute>. Adlandırma hakkında daha fazla bilgi için bkz: [veri sözleşmesi adları](../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
5.  Sonraki sürümlerde, herhangi bir veri üyesi adlarını değiştirmeyin. Alan, özelliği veya veri üyesi temel olay adının değiştirilmesi kullanırsanız `Name` özelliği <xref:System.Runtime.Serialization.DataMemberAttribute> mevcut veri üye adı korumak için.  
  
6.  Sonraki sürümlerde, herhangi bir alan, özelliği veya bu veri üye değişiklikleri için ortaya çıkan veri sözleşmesi şekilde veri üyesi temel olay türünü değiştirmeyin. Arabirim türleri unutmayın eşdeğer <xref:System.Object> , beklenen veri sözleşmesi belirlemek amacıyla.  
  
7.  Sonraki sürümlerde, var olan verileri üyeleri sırasını ayarlayarak değiştirmeyin <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> özelliğinin <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği.  
  
8.  Sonraki sürümlerde, yeni veri üyeleri eklenebilir. Her zaman bu kurallara uygun olmalıdır:  
  
    1.  <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> Özelliği her zaman sol varsayılan değerinde `false`.  
  
    2.  Varsayılan değer olarak, `null` veya sıfır üye için kabul edilemez ise, bir geri çağırma yöntemi kullanılarak sağlanmalıdır <xref:System.Runtime.Serialization.OnDeserializingAttribute> makul varsayılan bir durumda gelen akışını üye yok sağlamak için. Geri çağırma hakkında daha fazla bilgi için bkz: [sürüm toleranslı seri hale getirme geri çağrıları](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).  
  
    3.  `Order` Özellikte `DataMemberAttribute` tüm yeni eklenen veri üyelerinin sonra varolan veri üyeleri göründüğünden emin olmak için kullanılmalıdır. İçin önerilen yol bunu yaparsanız, bu şu şekildedir: veri sözleşmesi ilk sürümünde veri üyeleri hiçbiri olmalıdır kendi `Order` özellik kümesi. Tüm veri sözleşmesi 2 sürümünde eklenen veri üyeleri olmalıdır kendi `Order` özelliği 2 olarak ayarlanmış. Sürüm veri sözleşmesi 3 eklenen veri üyelerin tümünü olmalıdır kendi `Order` 3'e ayarlayın ve benzeri. Birden fazla veri üyesi aynı ayarlamak için izin verilen `Order` sayısı.  
  
9. Veri üyeleri sonraki sürümlerde kaldırmayın olsa bile <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> özelliği, varsayılan özelliğinin sol `false` önceki sürümlerinde.  
  
10. Değiştirmeyin `IsRequired` herhangi varolan bir veri üyesi sürümünden sürümüne özelliği.  
  
11. Gerekli verileri üyeler için (burada `IsRequired` olan `true`), değiştirmeyin `EmitDefaultValue` sürüm sürümünden özelliğine.  
  
12. Dallı sürüm oluşturma hiyerarşileri oluşturmaya çalışmayın. Diğer bir deyişle, her zaman olmamalıdır bir yolu yalnızca bu yönergeleri tarafından izin verilen değişiklikleri kullanarak başka bir sürüm için herhangi bir sürümünden en az bir yönde.  
  
     Sürüm 1 bir kişi veri sözleşmesi yalnızca adı veri üyesi içeriyorsa, örneğin, sürüm 2a yalnızca yaş üye ve sürüm 2b ekleme sözleşmesinin oluşturmamalısınız yalnızca adres üye ekleme. 2a gitmeyi 2b yaş kaldırarak ve adres ekleyerek içerir; başka bir yöne giderek kaldırma adresi ve ekleme yaş gerektirdiği. Bu yönergeleri üyeleri kaldırma izin verilmiyor.  
  
13. Genellikle, uygulamanızın yeni sürümde mevcut veri sözleşmesi türlerinin yeni alt oluşturmamalısınız. Benzer şekilde, yerine üyeleri olarak bildirilen veri nesnesi veya arabirim türleri olarak kullanılan yeni veri sözleşmeleri oluşturmamalısınız. Eski uygulamasının tüm örneklerini bilinen türleri listesine yeni türleri ekleyebilirsiniz biliyorsanız, bu yeni sınıflar oluşturma izin verilir. Örneğin, sürümünde uygulamanızı 1 gazete veri türlerinde sözleşme ve kitap türüyle sözleşme LibraryItem veri olabilir. LibraryItem sonra kitap veya gazete içeren bir bilinen türleri listesini gerekir. Alt LibraryItem türünün olan sürüm 2 şimdi dergisi türü eklemek varsayalım. Sürüm 2 ' sürüm 1 dergisi örneği gönderirseniz, dergi veri sözleşmesi bilinen türler listesinde bulunamadı ve bir özel durum.  
  
14. Değil ekleyin veya sürümleri arasında numaralandırma üyeleri kaldırmanız gerekir. Name özelliği üzerinde kullanmadığınız sürece, aynı zamanda numaralandırma üyeleri değiştirmemeniz gerekir `EnumMemberAttribute` adlarını veri sözleşmesi modelinde aynı kalmasını özniteliği.  
  
15. Koleksiyonları açıklandığı gibi veri sözleşmesi modelindeki birbirinin yerine [veri sözleşmelerinde koleksiyon türleri](../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md). Bu harika dereceli bir esneklik sağlar. Ancak, farkında olmadan bir olmayan-birbirinin yerine bir koleksiyon türü şekilde sürümden sürüme değiştirmemenizi emin olun. Örneğin, özelleştirilmiş olmayan bir koleksiyondan değiştirmeyin (diğer bir deyişle, olmadan `CollectionDataContractAttribute` özniteliği) özelleştirilmiş bir ya da özelleştirilmiş olmayan bir özelleştirilmiş bir koleksiyona. Ayrıca, özellikleri değiştirmeyin `CollectionDataContractAttribute` sürümü başka bir sürümü. Yalnızca izin verilen değişiklik Name ya da Namespace özelliği temel alınan koleksiyon tür adı veya ad alanı değişti ve verilerini yapmanız ekleme Sözleşme ve ad alanına önceki bir sürümü ile aynı.  
  
 Özel durumlar uyguladığınızda, burada listelenen yönergeleri bazıları güvenle yoksayılabilir. Seri hale getirme, seri durumdan çıkarma ve şema mekanizmaları yönergeleri deviating önce söz konusu tam olarak anladığınızdan emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>  
 <xref:System.Runtime.Serialization.IExtensibleDataObject>  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>  
 <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A>  
 <xref:System.Runtime.Serialization.ExtensionDataObject>  
 <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
 [Veri Anlaşmalarını Kullanma](../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Veri Anlaşması Sürümü Oluşturma](../../../docs/framework/wcf/feature-details/data-contract-versioning.md)  
 [Veri Anlaşması Adları](../../../docs/framework/wcf/feature-details/data-contract-names.md)  
 [İleri Uyumlu Veri Anlaşmaları](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)  
 [Sürüm Toleranslı Seri Hale Getirme Geri Çağrıları](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)
