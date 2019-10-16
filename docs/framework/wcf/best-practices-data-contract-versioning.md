---
title: 'En İyi Uygulamalar: Veri Sözleşmesi Sürümü Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- service contracts
- best practices [WCF], data contract versioning
- Windows Communication Foundation, data contracts
ms.assetid: bf0ab338-4d36-4e12-8002-8ebfdeb346cb
ms.openlocfilehash: 4d500c37efa4a90e24b06cd2e886147e1f159d4e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320786"
---
# <a name="best-practices-data-contract-versioning"></a>En İyi Uygulamalar: Veri Sözleşmesi Sürümü Oluşturma
Bu konuda, zaman içinde kolayca gelişelebilen veri sözleşmeleri oluşturmak için en iyi yöntemler listelenmiştir. Veri sözleşmeleri hakkında daha fazla bilgi için bkz. [veri sözleşmeleri kullanma](./feature-details/using-data-contracts.md)konuları.  
  
## <a name="note-on-schema-validation"></a>Şema doğrulamasında göz önünde  
 Veri anlaşması sürümü oluşturma bölümünde, Windows Communication Foundation (WCF) tarafından dışarıya alınan veri sözleşmesi şemasının, öğelerin varsayılan olarak isteğe bağlı olarak işaretlenmesinden başka bir sürüm desteği olmadığından emin olmanız önemlidir.  
  
 Bu, yeni bir veri üyesi ekleme gibi en yaygın sürüm oluşturma senaryosunun belirli bir şemaya göre sorunsuz şekilde uygulanamamasıdır. Bir veri sözleşmesinin daha yeni sürümleri (örneğin, yeni bir veri üyesi ile) eski şemayı kullanarak doğrulamaz.  
  
 Ancak, kesin şema uyumluluğuna gerek duyulmayan birçok senaryo vardır. ASP.NET kullanılarak oluşturulan WCF ve XML Web Hizmetleri gibi birçok Web hizmeti platformu, varsayılan olarak şema doğrulaması gerçekleştirmez ve bu nedenle şema tarafından açıklanmayan ek öğeleri kabul etmez. Bu tür platformlar ile çalışırken birçok sürüm oluşturma senaryosunun uygulanması daha kolay olur.  
  
 Bu nedenle, iki veri anlaşması oluşturma kılavuzu kümesi vardır: katı şema geçerliliği önemli olan senaryolar için bir küme ve ne zaman olmadığında farklı senaryolar için bir küme.  
  
## <a name="versioning-when-schema-validation-is-required"></a>Şema doğrulaması gerektiğinde sürüm oluşturma  
 Tüm yönlerdeki kesin şema geçerliliği gerekliyse (yeni-eski ve eski-yeni) veri sözleşmeleri sabit kabul edilmelidir. Sürüm oluşturma gerekliyse, farklı bir ad veya ad alanı ile yeni bir veri sözleşmesinin oluşturulması gerekir ve veri türünü kullanan hizmet sözleşmesinin sürümü buna uygun olmalıdır.  
  
 Örneğin, `PostPurchaseOrder` ile `PoProcessing` adlı bir satın alma siparişi işleme hizmeti sözleşmesi @no__t 2 bir veri sözleşmesine uygun bir parametre alır. @No__t-0 sözleşmesinin değiştirilmesi gerekiyorsa, yeni bir veri sözleşmesi oluşturmanız gerekir, diğer bir deyişle, değişiklikleri içeren `PurchaseOrder2`. Daha sonra hizmet sözleşmesi düzeyinde sürüm oluşturmayı işlemeniz gerekir. Örneğin, `PurchaseOrder2` parametresini alan `PostPurchaseOrder2` bir işlem oluşturarak veya `PostPurchaseOrder` işleminin `PurchaseOrder2` veri sözleşmesi aldığı `PoProcessing2` hizmet sözleşmesi oluşturarak.  
  
 Diğer veri sözleşmeleri tarafından başvurulan veri sözleşmeleri değişikliklerinin de hizmet modeli katmanına genişlediğine unutmayın. Örneğin, önceki senaryoda `PurchaseOrder` veri sözleşmesinin değişiklik yapması gerekmez. Ancak, `Customer` veri sözleşmesinin bir veri üyesini içerir ve bu da değiştirilmesi gereken `Address` veri sözleşmesinin bir veri üyesini kapsar. Bu durumda, gerekli değişikliklerle `Address2` veri sözleşmesi oluşturmanız, `Address2` veri üyesini içeren bir `Customer2` veri sözleşmesi ve @no__t 4 veri üyesi içeren @no__t 3 veri sözleşmesi oluşturmanız gerekir. Önceki durumda olduğu gibi, hizmet sözleşmesinin da sürümü oluşturulması gerekir.  
  
 Bu örneklerin adları değiştirilse de (bir "2" eklenerek), bir sürüm numarası veya tarih ile yeni ad alanları ekleyerek adlar yerine ad alanlarını değiştirmelerdir. Örneğin, `http://schemas.contoso.com/2005/05/21/PurchaseOrder` veri sözleşmesi `http://schemas.contoso.com/2005/10/14/PurchaseOrder` veri sözleşmesine değişir.  
  
 Daha fazla bilgi için bkz. En Iyi uygulamalar: [hizmet sürümü oluşturma](service-versioning.md).  
  
 Bazen, uygulamanız tarafından gönderilen iletiler için katı şema uyumluluğunu güvence altına almanız gerekir, ancak gelen iletilere tamamen şemaya uyumlu olacak şekilde güvenemezsiniz. Bu durumda, gelen bir iletinin gereksiz veriler içerebileceğini belirten bir tehlike vardır. Gereksiz değerler WCF tarafından depolanır ve döndürülür ve bu nedenle, şemaya geçersiz iletiler gönderilmesine neden olur. Bu sorundan kaçınmak için, gidiş-dönüşü özelliğinin kapalı olması gerekir. Bunu iki şekilde yapabilirsiniz.  
  
- @No__t-0 arabirimini türlerinizin hiçbirinde uygulamayın.  
  
- @No__t-1 özelliği `true` olarak ayarlanan hizmet sözleşmeniz için <xref:System.ServiceModel.ServiceBehaviorAttribute> özniteliği uygulayın.  
  
 Gidiş dönüşü hakkında daha fazla bilgi için bkz. [Forward-uyumlu veri sözleşmeleri](./feature-details/forward-compatible-data-contracts.md).  
  
## <a name="versioning-when-schema-validation-is-not-required"></a>Şema doğrulaması gerekli olmadığında sürüm oluşturma  
 Katı şema uyumluluğu nadiren gereklidir. Birçok platform, bir şema tarafından açıklanmayan ek öğelere tolerans. Bu toleranslı olduğu sürece, [veri anlaşması sürümü oluşturma](./feature-details/data-contract-versioning.md) ve [Ileri uyumlu veri sözleşmeleri](./feature-details/forward-compatible-data-contracts.md) ' nde açıklanan özelliklerin tam kümesi kullanılabilir. Aşağıdaki kılavuzlar önerilir.  
  
 Daha eski bir türün beklenildiği bir türün yeni sürümlerini gönderebilmesi veya yeni bir tane beklendiğinde eski bir tane gönderilmesi için bazı yönergelerin tam olarak izlenmesi gerekir. Diğer yönergeler kesinlikle gerekli değildir, ancak şema sürümü oluşturma işleminden etkilenmedikleri için burada listelenir.  
  
1. Veri Sözleşmelerini tür devralmayla aynı sürüme denemeyin. Sonraki sürümler oluşturmak için, mevcut bir türdeki veri sözleşmesini değiştirin veya yeni bir ilişkisiz tür oluşturun.  
  
2. Devralma bir sürüm oluşturma mekanizması olarak kullanılmadığından ve belirli kuralların izlendiði için, veri sözleşmeleri ile birlikte devralma kullanılmasına izin verilir. Bir tür belirli bir temel türden türetildiğinden, daha sonraki bir sürümde (aynı veri sözleşmesine sahip olmadığı takdirde) farklı bir temel türden türemez. Bunun için bir özel durum vardır: bir veri anlaşması türü ve temel türü arasında hiyerarşiye bir tür ekleyebilirsiniz, ancak bu, hiyerarşideki diğer türlerin olası sürümlerindeki diğer üyelerle aynı ada sahip veri üyeleri içermiyorsa. Genel olarak, aynı ada sahip veri üyelerini aynı devralma hiyerarşisinin farklı düzeylerinde kullanmak önemli sürüm sorunlarına yol açabilir ve kaçınılmalıdır.  
  
3. Bir veri sözleşmesinin ilk sürümünden itibaren, gidiş dönüşü sağlamak için her zaman <xref:System.Runtime.Serialization.IExtensibleDataObject> ' ı uygulayın. Daha fazla bilgi için bkz. [Ileri uyumlu veri sözleşmeleri](./feature-details/forward-compatible-data-contracts.md). Bu arabirimi uygulamadan bir veya daha fazla tür sürümü yayımladıysanız, bunu türün bir sonraki sürümünde uygulayın.  
  
4. Sonraki sürümlerde, veri sözleşmesi adını veya ad alanını değiştirmeyin. Veri sözleşmesini temel alan türün adını veya ad alanını değiştiriyorsanız, <xref:System.Runtime.Serialization.DataContractAttribute> ' in <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> özelliği gibi uygun mekanizmaları kullanarak veri sözleşmesi adını ve ad alanını koruduğunuzdan emin olun. Adlandırma hakkında daha fazla bilgi için bkz. [veri sözleşmesi adları](./feature-details/data-contract-names.md).  
  
5. Sonraki sürümlerde, herhangi bir veri üyesinin adlarını değiştirmeyin. Veri üyesini temel alan alanın, özelliğin veya olayın adını değiştiriyorsanız, var olan veri üyesi adını korumak için <xref:System.Runtime.Serialization.DataMemberAttribute> ' in `Name` özelliğini kullanın.  
  
6. Sonraki sürümlerde, bir veri üyesini temel alan herhangi bir alanın, özelliğin veya olayın türünü, bu veri üyesine yönelik sonuç veri sözleşmesinin değiştiği şekilde değiştirmeyin. Beklenen veri sözleşmesinin belirlenmesi amacıyla arabirim türlerinin <xref:System.Object> ' a eşit olduğunu aklınızda bulundurun.  
  
7. Sonraki sürümlerde, <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliğinin <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> özelliğini ayarlayarak mevcut veri üyelerinin sırasını değiştirmeyin.  
  
8. Sonraki sürümlerde yeni veri üyeleri eklenebilir. Her zaman bu kurallara uymalıdır:  
  
    1. @No__t-0 özelliği her zaman varsayılan `false` değerinde bırakılmalıdır.  
  
    2. Üye için `null` veya sıfır olan varsayılan bir değer kabul edilemez ise, üyenin gelen akışta olmaması durumunda makul bir varsayılan sağlamak için <xref:System.Runtime.Serialization.OnDeserializingAttribute> kullanılarak bir geri çağırma yöntemi sağlanmalıdır. Geri çağırma hakkında daha fazla bilgi için bkz. [Sürüm dayanıklı serileştirme geri çağırmaları](./feature-details/version-tolerant-serialization-callbacks.md).  
  
    3. @No__t-0 özelliği, yeni eklenen tüm veri üyelerinin, varolan veri üyelerinden sonra göründüğünden emin olmak için kullanılmalıdır. Bunu yapmanın önerilen yolu şu şekildedir: veri sözleşmesinin ilk sürümündeki veri üyelerinin hiçbirinin `Order` özelliği ayarlanmış olmalıdır. Veri sözleşmesinin 2. sürümünde eklenen tüm veri üyelerinin, `Order` özelliği 2 olarak ayarlanmış olmalıdır. Veri sözleşmesinin 3. sürümü içinde eklenen tüm veri üyelerinin `Order` ' ı 3 ' e ayarlanmış olması gerekir. Aynı `Order` numarasına ayarlanmış birden fazla veri üyesine sahip olmak için izin verilir.  
  
9. @No__t-0 özelliği önceki sürümlerde `false` ' in varsayılan özelliğinde bırakılmış olsa bile, sonraki sürümlerde veri üyelerini kaldırmayın.  
  
10. Var olan herhangi bir veri üyesinin sürümünden sürümüne `IsRequired` özelliğini değiştirmeyin.  
  
11. Gerekli veri üyeleri için (`IsRequired` `true` ' dir), `EmitDefaultValue` özelliğini sürümden sürümüne değiştirmeyin.  
  
12. Dallandırılmış sürüm hiyerarşileri oluşturmayı denemeyin. Yani, her zaman yalnızca bu yönergelerin izin verdiği değişiklikler kullanılarak herhangi bir sürümden diğer bir sürüme en az bir yönde yol olmalıdır.  
  
     Örneğin, bir kişi veri sözleşmesinin sürüm 1 ' i yalnızca ad veri üyesini içeriyorsa, yalnızca yaş üyesini ve sürüm 2B yalnızca adres üyesini ekleyerek sözleşmenin sürüm 2A 'yı oluşturmamalıdır. 2A 'dan 2B 'ye geçmek, yaşı kaldırmak ve adres eklemek içerir; diğer yönden sonra, adresi kaldırma ve yaş ekleme sıraya alındı. Bu yönergeler tarafından üyelerin kaldırılmasına izin verilmez.  
  
13. Uygulamanızın yeni bir sürümünde, var olan veri sözleşme türlerinin yeni alt türlerini genellikle oluşturmamalıdır. Benzer şekilde, nesne veya arabirim türleri olarak belirtilen veri üyeleri yerine kullanılan yeni veri sözleşmeleri oluşturmamalısınız. Bu yeni sınıfların oluşturulmasına yalnızca, eski uygulamanızın tüm örneklerinin bilinen türler listesine yeni türleri ekleyebileceğinizi bildiğiniz durumlarda izin verilir. Örneğin, uygulamanızın 1. sürümünde, kitap ve gazete veri sözleşmesi alt türleri ile LibraryItem veri sözleşme türüne sahip olabilirsiniz. Daha sonra LibraryItem, kitap ve gazete içeren bilinen bir türler listesine sahip olur. Artık LibraryItem öğesinin bir alt türü olan sürüm 2 ' de bir dergi türü eklediğinizi varsayalım. Sürüm 2 ' den sürüm 1 ' e bir dergi örneği gönderirseniz, dergi veri sözleşmesi bilinen türler listesinde bulunmadı ve bir özel durum oluşturulur.  
  
14. Sürümler arasında numaralandırma üyesi eklememelisiniz veya kaldırmamalıdır. Ayrıca, ad özelliğini, `EnumMemberAttribute` özniteliğinde kullanmadığınız müddetçe, adlarını veri sözleşmesi modelinde aynı tutmak için aynı zamanda sabit listesi üyelerini yeniden adlandırmalısınız.  
  
15. Koleksiyonlar, veri [sözleşmeleri Içindeki koleksiyon türleri](./feature-details/collection-types-in-data-contracts.md)bölümünde açıklandığı gibi veri sözleşmesi modelinde değiştirilebilir. Bu, büyük ölçüde esneklik sağlar. Bununla birlikte, bir koleksiyon türünü yanlışlıkla sürümden sürüme, farklı olmayan bir şekilde değiştirmeyin. Örneğin, özelleştirilmeyen bir koleksiyondan (yani `CollectionDataContractAttribute` özniteliği olmadan) özelleştirilmiş bir koleksiyonun veya özelleştirilmiş bir koleksiyonun özelleştirilmemiş bir koleksiyon olarak değiştirmeyin. Ayrıca, `CollectionDataContractAttribute` ' deki özellikleri sürümden sürüme değiştirmeyin. İzin verilen tek değişiklik, temeldeki koleksiyon türünün adı veya ad alanı değiştiyse ve veri sözleşmesi adını ve ad alanını önceki bir sürümde aynı şekilde yapmanız gerekiyorsa ad veya ad alanı özelliği ekliyor.  
  
 Burada listelenen yönergelerin bazıları, özel koşullar uygulandığı zaman güvenle yoksayılabilir. Kılavuzlardan sapmadan önce dahil olan serileştirme, seri durumdan çıkarma ve şema mekanizmalarını tam olarak anladığınızdan emin olun.  
  
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
- [Veri Anlaşmalarını Kullanma](./feature-details/using-data-contracts.md)
- [Veri Anlaşması Sürümü Oluşturma](./feature-details/data-contract-versioning.md)
- [Veri Anlaşması Adları](./feature-details/data-contract-names.md)
- [İleri Uyumlu Veri Anlaşmaları](./feature-details/forward-compatible-data-contracts.md)
- [Sürüm Toleranslı Seri Hale Getirme Geri Çağrıları](./feature-details/version-tolerant-serialization-callbacks.md)
