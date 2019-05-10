---
title: 'En İyi Yöntemler: Veri Sözleşmesi Sürümü Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- service contracts
- best practices [WCF], data contract versioning
- Windows Communication Foundation, data contracts
ms.assetid: bf0ab338-4d36-4e12-8002-8ebfdeb346cb
ms.openlocfilehash: a56111796b1e301862dcbd9e76a6294c709ea06f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64652150"
---
# <a name="best-practices-data-contract-versioning"></a>En İyi Yöntemler: Veri Sözleşmesi Sürümü Oluşturma
Bu konu, zaman içinde kolayca geliştirebilirsiniz veri sözleşmeleri oluşturmak için en iyi uygulamaları listeler. Veri sözleşmeleri hakkında daha fazla bilgi için bkz: konularındaki [kullanarak veri sözleşmeleri](../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
## <a name="note-on-schema-validation"></a>Şema doğrulaması ilgili not  
 Veri sözleşmesi sürümü oluşturma görüştükten içinde Windows Communication Foundation (WCF) tarafından verilen veri sözleşmesi şema öğeleri varsayılan olarak isteğe bağlı olarak işaretlenmiş olgu dışındaki herhangi bir sürüm oluşturma desteği sahip olmadığını unutmayın.  
  
 Başka bir deyişle, yeni bir veri üyesi ekleme gibi bile en yaygın sürüm oluşturma senaryosu, bir şema ile ilgili sorunsuz bir şekilde uygulanamaz. Bir veri anlaşması (ile yeni veri üyesi, örneğin) daha yeni sürümleri eski şemayı kullanarak doğrulamaz.  
  
 Ancak, katı şema uyumluluk gerekli değil birçok senaryo vardır. ASP.NET kullanılarak oluşturulan WCF ve XML Web Hizmetleri gibi birçok Web Hizmetleri platformları değil şema doğrulaması varsayılan olarak gerçekleştirin ve bu nedenle şema tarafından açıklanmayan ekstra öğeler tolerans. Böyle platformları ile çalışırken, birçok sürüm oluşturma senaryoları uygulamak daha kolaydır.  
  
 Bu nedenle, var olan iki veri kümesi sözleşmesi sürümü oluşturma yönergeleri: Burada katı şema geçerlilik önemlidir ve başka ayarlayın senaryoları için olmadığında senaryolar için ayarlayın.  
  
## <a name="versioning-when-schema-validation-is-required"></a>Şema doğrulaması gerektiğinde sürüm oluşturma  
 Veri sözleşmeleri katı şema geçerlilik tüm yönde (eski yeni ve eski yeni) gerekiyorsa, sabit düşünülmelidir. Sürüm oluşturma gerekiyorsa, yeni bir veri sözleşmesi, farklı bir ad veya ad alanı ile oluşturulmalıdır ve veri türü kullanan bir hizmet sözleşmesini uygun şekilde tutulan olmalıdır.  
  
 Örneğin, hizmet sözleşmesi adlı işleme satınalma siparişi `PoProcessing` ile bir `PostPurchaseOrder` işlemi uyan bir parametre alır bir `PurchaseOrder` veri anlaşması. Varsa `PurchaseOrder` sözleşme sahip değiştirmek, diğer bir deyişle, yeni bir veri anlaşması oluşturmalısınız `PurchaseOrder2`, değişiklikler içerir. Ardından, hizmet sözleşmesi düzeyinde sürüm işlemesi gerekir. Oluşturarak Örneğin, bir `PostPurchaseOrder2` alan işlemi `PurchaseOrder2` parametresi veya oluşturarak bir `PoProcessing2` hizmet sözleşmesini nereden `PostPurchaseOrder` işlemi alır bir `PurchaseOrder2` veri anlaşması.  
  
 Diğer veri sözleşmeleri tarafından başvurulan veri anlaşmalarında değişiklikler de için hizmet modeli katmanını genişletme unutmayın. Örneğin, önceki senaryoda `PurchaseOrder` veri anlaşması değiştirmeniz gerekmez. Ancak, veri üyesi içerdiği bir `Customer` sırayla veri üyesi bulunan veri anlaşması `Address` değiştirilmesi gereken veri sözleşmesi,. Bu durumda, oluşturmanız gerekecektir bir `Address2` gerekli değişiklikleri ile veri anlaşması bir `Customer2` içeren veri anlaşması `Address2` veri üyesi ve `PurchaseOrder2` içeren veri anlaşması bir `Customer2` veri üyesi. Önceki örnekte olduğu gibi hizmet sözleşmesi de tutulan olması gerekir.  
  
 Bu örneklerde ("2" ekleyerek) adları değiştirildi olsa da, yeni ad alanları bir sürüm numarası veya bir tarih ile ekleyerek adları yerine ad alanlarını değiştirmek için kullanılması önerilir. Örneğin, `http://schemas.contoso.com/2005/05/21/PurchaseOrder` veri anlaşması değiştirmek `http://schemas.contoso.com/2005/10/14/PurchaseOrder` veri anlaşması.  
  
 Daha fazla bilgi için bkz: [Hizmet sürümü oluşturma](../../../docs/framework/wcf/service-versioning.md).  
  
 Bazen, uygulamanız tarafından gönderilen iletiler için katı şema uyumluluğu garanti gerekir ancak kesinlikle şema uyumlu olması için gelen iletiler güvenemezsiniz. Bu durumda, gelen ileti fazlalık veri içerebilir bir olma tehlikesi yoktur. Fazlalık değerler depolanabilir ve WCF tarafından döndürülen ve bu nedenle gönderilen iletileri şema geçersiz olur. Bu sorunu önlemek için gidiş dönüşü özellik kapatılmalıdır. Bunu yapmanın iki yolu vardır.  
  
- Uygulamayın <xref:System.Runtime.Serialization.IExtensibleDataObject> tüm türleri arabirimi.  
  
- Geçerli bir <xref:System.ServiceModel.ServiceBehaviorAttribute> öznitelik, hizmet sözleşmesi ile <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> özelliğini `true`.  
  
 Gidiş dönüşü hakkında daha fazla bilgi için bkz: [İleri uyumlu veri sözleşmeleri](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
## <a name="versioning-when-schema-validation-is-not-required"></a>Şema doğrulaması gerekmediğinde sürüm oluşturma  
 Katı şema uyumluluk nadiren gereklidir. Birçok platformda bir şema tarafından açıklanmayan ekstra öğeler tolerans. Bu izin sürece, özelliklerin tamamı açıklanan [veri sözleşmesi sürümü oluşturma](../../../docs/framework/wcf/feature-details/data-contract-versioning.md) ve [İleri uyumlu veri sözleşmeleri](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md) kullanılabilir. Aşağıdaki yönergeler önerilir.  
  
 Bazı yönergeler daha eski beklenirken yeni sürümleri bir türün tam olarak göndermek için izlenmesi gereken veya yeni bir tane beklenirken eski bir gönderin. Diğer yönergeleri kati şekilde gerekli değildir, ancak şema sürümü geleceği tarafından etkilenebilir, çünkü burada listelenir.  
  
1. Sürüm veri sözleşmelerine göre türü devralma çalışmayın. Sonraki sürümler oluşturmak için var olan bir türü veri anlaşması değiştirin veya yeni ilişkisiz türü oluşturun.  
  
2. Devralma, sürüm oluşturma mekanizması olarak kullanılmaz ve belirli kuralları takip koşuluyla devralma veri sözleşmeleri ile birlikte kullanımı verilmez. Bir tür belirli temel türünden türer ise, gelecek sürümlerinden farklı bir temel tür türetilir yapmayın (aynı verilere sahip olmadığı sürece sözleşme). Bunun tek istisnası vardır: bir veri anlaşması türü kendi temel türü arasındaki hiyerarşi içine bir tür ekleyebilirsiniz, ancak yalnızca veri üyeleri ile içermiyorsa hiyerarşideki diğer türleri olası tüm sürümlerini diğer üyelerin aynı adları. Genel olarak, farklı düzeylerde aynı aynı ada sahip veri üyeleri kullanarak Devralma Hiyerarşisi sürüm ciddi sorunlara yol açabilir ve kaçınılmalıdır.  
  
3. Bir veri sözleşmesi ilk sürümünden itibaren her zaman uygulama <xref:System.Runtime.Serialization.IExtensibleDataObject> gidiş dönüşü etkinleştirmek için. Daha fazla bilgi için [İleri uyumlu veri sözleşmeleri](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md). Bu arabirim uygulamadan bir veya daha fazla sürümleri bir türün yayımlandı, türü bir sonraki sürümünde uygulayın.  
  
4. Sonraki sürümlerde, veri anlaşması adına veya ad alanı değiştirmeyin. Adını veya temel alınan veri anlaşması türünün ad alanını değiştirme, ad alanı ve veri anlaşması adına gibi uygun mekanizmaları kullanarak doğru yazdığınızdan emin <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> özelliği <xref:System.Runtime.Serialization.DataContractAttribute>. Adlandırma hakkında daha fazla bilgi için bkz. [veri sözleşmesi adları](../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
5. Sonraki sürümlerde, tüm veri üyelerinin adları değiştirmeyin. Alan, özelliği veya veri üyesi temel olay adının değiştirilmesi kullanırsanız `Name` özelliği <xref:System.Runtime.Serialization.DataMemberAttribute> mevcut veri üye adına korumak için.  
  
6. Sonraki sürümlerde, herhangi bir alan, özelliği veya sağlayacak şekilde ilgili veri üye değişiklikleri için ortaya çıkan veri anlaşması veri üyesi temel olay türünü değiştirmeyin. Arabirim türleri etkilenebileceğini eşdeğer <xref:System.Object> beklenen veri anlaşması belirleme amacıyla.  
  
7. Sonraki sürümlerde, mevcut veri üyelerinin sırasını ayarlayarak değiştirmeyin <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> özelliği <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği.  
  
8. Sonraki sürümlerde, yeni veri üyeleri eklenebilir. Bunlar, her zaman bu kuralları izlemelidir:  
  
    1. <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> Özelliği her zaman sol varsayılan değerine `false`.  
  
    2. Varsayılan değeri, `null` veya üye için sıfır kabul edilemez, bir geri çağırma yöntemi kullanarak sağlanmalıdır <xref:System.Runtime.Serialization.OnDeserializingAttribute> üye gelen akışta mevcut değilse, makul bir varsayılan değer sağlamak için. Geri çağırma hakkında daha fazla bilgi için bkz: [sürüme dayanıklı serileştirme geri çağırmaları](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).  
  
    3. <xref:System.Runtime.Serialization.DataMemberAttribute.Order?displayProperty=nameWithType> Özelliği, tüm yeni eklenen veri üyelerinin sonra var olan veri üyeleri göründüğünden emin olmak için kullanılmalıdır. Bu önerilen yöntem aşağıdaki gibidir: İlk veri sözleşmesi sürümü veri üyeleri hiçbiri olmalıdır, `Order` özellik kümesi. Tüm veri anlaşması 2 sürümünde eklenen veri üyelerinin olması gerekir, `Order` özelliği 2 olarak ayarlayın. Tüm veri anlaşması 3. sürümüne eklenen veri üyelerinin olması gerekir, `Order` 3 olarak ayarlayın ve benzeri. Birden fazla veri üyesi aynı ayarlamak için izin verilen `Order` sayı.  
  
9. Veri üyeleri, sonraki sürümlerde kaldırmayın bile <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> özelliği, varsayılan özellik sol `false` önceki sürümlerinde.  
  
10. Değişmez `IsRequired` tüm var olan sürüm veri üyelerinin sürümünden özelliği.  
  
11. Gerekli veri üyeleri için (burada `IsRequired` olduğu `true`), değiştirmeyin `EmitDefaultValue` sürüm özelliğine sürümü.  
  
12. Dallı sürüm hiyerarşileri oluşturmaya çalışmayın. Diğer bir deyişle, her zaman olmalıdır bir yolu yalnızca bu yönergeleri tarafından izin verilen değişiklikleri kullanarak başka bir sürüm için herhangi bir sürümünden en az bir yönde.  
  
     Bir kişi veri sözleşmesi sürümü 1 yalnızca adı veri üyesi içeriyorsa, örneğin, yalnızca yaş üye ve sürüm 2b ekleme Sözleşme sürümü 2a oluşturmamalısınız adresi üyesi ekleniyor. 2a gitmeyi 2b yaş kaldırarak ve eklemenin içerir; diğer yönde giderek kaldırma adresi ve ekleme yaş gerektirdiği. Bu yönergelere göre üyeler kaldırılırken izin verilmez.  
  
13. Genellikle, uygulamanızın yeni bir sürümünde var olan veri anlaşması türleri yeni subtypes oluşturmamalısınız. Benzer şekilde, veri üyeleri yerine nesnesi veya arabirim türleri olarak kullanılan yeni veri sözleşmeleri oluşturmamalısınız. Yeni türleri, eski uygulamanın tüm örneklerini bilinen türler listesine ekleyebilirsiniz bildiğinizde, bu yeni sınıflar oluşturma izin verilir. Örneğin, sürümünde uygulamanızı 1 LibraryItem veri sözleşme türü Defterinizle ve subtypes sözleşme gazete veri olabilir. LibraryItem ardından kitap ve gazete içeren bilinen türleri listesi gerekir. Bir alt LibraryItem olan sürüm 2 şimdi Magazine türü ekleyin varsayalım. Sürüm 2 ' sürüm 1 Magazine örneği gönderirseniz, dergi veri sözleşme bilinen türleri listesinde bulunamadı ve bir özel durum oluşturulur.  
  
14. Değil ekleyin veya sürümleri arasında numaralandırma üyelerini kaldırmanız gerekir. Name özelliği kullanmıyorsanız, ayrıca numaralandırma üyelerini değiştirmemeniz gerekir `EnumMemberAttribute` adlarını aynı veri anlaşması modelinde tutmak için özniteliği.  
  
15. Koleksiyonları açıklanan veri sözleşme modelinde birbirinin yerine [veri anlaşmalarında koleksiyon türleri](../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md). Bu işlem için önemli ölçüde esneklik sağlar. Ancak, yanlışlıkla bir olmayan-birbirinin yerine bir koleksiyon türü şekilde sürümü sürümü değiştirmemenizi emin olun. Örneğin, özelleştirilmiş olmayan bir koleksiyondan değiştirme (olmadan, diğer bir deyişle, `CollectionDataContractAttribute` özniteliği) özelleştirilmiş bir ya da özelleştirilmiş olmayan bir özelleştirilmiş bir koleksiyon. Ayrıca, özelliklerini değiştirmeyin `CollectionDataContractAttribute` sürümü başka bir sürümü. İzin verilen tek değişiklik bir Name ya da Namespace özelliği temel alınan koleksiyon türün adı veya ad alanı değişmişse ve verilerini yapmanız ekliyor ve ad alanına sözleşme önceki bir sürümü ile aynıdır.  
  
 Burada listelenen yönergeleri bazı özel durumlar uygulandığında güvenle yoksayılabilir. Seri hale getirme, seri durumundan çıkarma ve şema mekanizmaları ilgili yönergeleri'ndeki deviating önce tam olarak anladığınızdan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>
- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- <xref:System.ServiceModel.ServiceBehaviorAttribute>
- <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A>
- <xref:System.Runtime.Serialization.ExtensionDataObject>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- [Veri Anlaşmalarını Kullanma](../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Veri Anlaşması Sürümü Oluşturma](../../../docs/framework/wcf/feature-details/data-contract-versioning.md)
- [Veri Anlaşması Adları](../../../docs/framework/wcf/feature-details/data-contract-names.md)
- [İleri Uyumlu Veri Anlaşmaları](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)
- [Sürüm Toleranslı Seri Hale Getirme Geri Çağrıları](../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)
