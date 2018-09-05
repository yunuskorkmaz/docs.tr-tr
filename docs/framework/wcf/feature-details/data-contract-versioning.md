---
title: Veri Sözleşmesi Sürümü Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versioning [WCF], data contracts
- versioning [WCF]
- data contracts [WCF], versioning
ms.assetid: 4a0700cb-5f5f-4137-8705-3a3ecf06461f
ms.openlocfilehash: 0e91bf597e344dd09e80bee5787e92383065b654
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520204"
---
# <a name="data-contract-versioning"></a>Veri Sözleşmesi Sürümü Oluşturma
Uygulamaları değiştikçe, ayrıca değiştirmek zorunda kalabilirsiniz veri sözleşmeleri Hizmetleri kullanın. Bu konu açıklar nasıl sürüm veri anlaşmaları. Bu konuda, veri sözleşmesi sürümü oluşturma mekanizmaları açıklanmaktadır. Eksiksiz bir genel bakış ve öngörücü sürüm oluşturma yönergeleri için bkz: [en iyi uygulamalar: veri sözleşmesi sürümü oluşturma](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md).  
  
## <a name="breaking-vs-nonbreaking-changes"></a>VS kesiliyor. Bölünemez değişiklikleri  
 Bir veri sözleşmesi önemli değişiklikler veya bölünemez. Bir veri anlaşması bölünemez şekilde değiştirildiğinde, Sözleşme'nin eski sürümünü kullanan bir uygulamanın daha yeni sürümünü kullanarak bir uygulama ile iletişim kurabilir ve sözleşmenin daha yeni sürümünü kullanarak bir uygulama bir uygulamayla iletişim kurabilir eski sürümü kullanıyor. Öte yandan, bir değişiklik, bir veya iki yönlü iletişimi engeller.  
  
 Nasıl, gönderilen ve alınan etkilemeyen herhangi bir tür değişiklikler bölünemez. Bu tür değişiklikler yalnızca temel alınan türü veri anlaşması değiştirmeyin. Ardından ayarlarsanız, örneğin, bir alanın adı bölünemez şekilde değiştirebileceğiniz <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> özelliği <xref:System.Runtime.Serialization.DataMemberAttribute> eski sürüm adı. Aşağıdaki kod, bir veri anlaşması 1 sürümünü gösterir.  
  
 [!code-csharp[C_DataContractVersioning#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#1)]
 [!code-vb[C_DataContractVersioning#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#1)]  
  
 Aşağıdaki kod, bölünemez değişiklik gösterir.  
  
 [!code-csharp[C_DataContractVersioning#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#2)]
 [!code-vb[C_DataContractVersioning#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#2)]  
  
 Bazı değişiklikler iletilen verileri değiştirebilir ancak olabilir veya bozucu değildir. Aşağıdaki değişiklikleri her zaman ayırırsınız:  
  
-   Değiştirme <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> veya <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> veri anlaşması değeri.  
  
-   Kullanarak veri üyelerinin sırasını değiştirme <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> özelliği <xref:System.Runtime.Serialization.DataMemberAttribute>.  
  
-   Bir veri üyesi yeniden adlandırma.  
  
-   Veri anlaşması bir veri üyesinin değiştiriliyor. Örneğin, "Müşteri" bir türe sahip "Kişi" adlı bir veri sözleşmesi adlı bir veri sözleşmesi ile bir dizeyi bir tamsayıya veya bir tür veri üyesi türünün değiştirilmesi.  
  
 Aşağıdaki değişiklikleri de mümkündür.  
  
## <a name="adding-and-removing-data-members"></a>Ekleme ve kaldırma veri üyesi  
 (Yeni örnekler eski şemasına göre doğrulanıyor) katı şema geçerlilik gerektirmedikçe çoğu durumda, ekleme veya kaldırma veri üyesi bozucu bir değişiklik değil.  
  
 Fazladan bir alan türüyle eksik alan bir türle içine seri durumdan, ek bilgilerin göz ardı edilir. (Ayrıca olabilir depolanan gidiş dönüşü amacıyla; daha fazla bilgi için bkz: [İleri uyumlu veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)).  
  
 Eksik alan türüyle fazladan bir alan bir türle içine seri durumdan ek alan varsayılan değerinde bırakılır, genellikle sıfır veya `null`. (Varsayılan değer değişebilir; daha fazla bilgi için [sürüme dayanıklı serileştirme geri çağırmaları](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).)  
  
 Gibi kullanabilirsiniz `CarV1` sınıfı bir istemcide ve `CarV2` sınıfı bir hizmet veya kullanabilir `CarV1` hizmet sınıfı ve `CarV2` istemci sınıfı.  
  
 [!code-csharp[C_DataContractVersioning#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#3)]
 [!code-vb[C_DataContractVersioning#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#3)]  
  
 Sürüm 2 uç nokta, başarılı bir şekilde sürüm 1 uç noktasına veri gönderebilir. Serileştirmek sürüm 2 `Car` aşağıdakine benzer XML veri anlaşması verir.  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
    <HorsePower>300</HorsePower>  
</Car>  
```  
  
 V1 seri durumundan çıkarma altyapısında eşleşen veri üyesi bulamazsa `HorsePower` alan ve bu veriyi atar.  
  
 Ayrıca, sürüm 1 uç noktası, sürüm 2 uç noktasına veri gönderebilir. Serileştirmek sürümü 1 `Car` aşağıdakine benzer XML veri anlaşması verir.  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
</Car>  
```  
  
 Sürüm 2 seri durumdan çıkarıcı ne ayarlanacak bilmez `HorsePower` gelen XML dosyasında eşleşen veri yok olduğundan alan için. Bunun yerine, alanın varsayılan değeri 0 olarak ayarlanır.  
  
## <a name="required-data-members"></a>Gerekli veri üyeleri  
 Bir veri üyesi ayarlayarak gerektiği olarak işaretlenmiş olabilir <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> özelliği <xref:System.Runtime.Serialization.DataMemberAttribute> için `true`. Seri durumdan çıkarılırken veriler eksik gerekli olursa, veri üyesi varsayılan değerine ayarlamak yerine bir özel durum oluşturulur.  
  
 Gerekli veri üyesi ekleme bölünmesi farklıdır. Diğer bir deyişle, yeni türü yine de uç noktalar için eski tür ancak dönüştürülemeyeceği geçici olarak gönderilebilir. Olarak işaretlenmiş bir veri üyesini kaldırma herhangi bir önceki sürümünde de bir değişiklik gereklidir.  
  
 Değiştirme <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> özellik değerinden `true` için `false` bozucu değildir, ancak ondan değiştirme `false` için `true` türü önceki tüm sürümlerini veri üyesi yoksa söz konusu parçalamak.  
  
> [!NOTE]
>  Ancak <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> özelliği `true`, gelen verileri null veya sıfır ve türü gerekir hazırlanan bu olasılığı işlemek için. Kullanmayın <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> hatalı gelen veri karşı korumak için bir güvenlik mekanizması olarak.  
  
## <a name="omitted-default-values"></a>Belirtilmemişse varsayılan değerler  
 (Önerilmez olsa da) mümkündür ayarlanacak `EmitDefaultValue` DataMemberAttribute özniteliğine özellik `false`anlatılan şekilde [veri üyesi varsayılan değerler](../../../../docs/framework/wcf/feature-details/data-member-default-values.md). Bu ayar `false`, varsayılan değerine ayarlanırsa veri üyesi yayılan değil (genellikle null ya da sıfır). Bu iki yolla farklı sürümleri gerekli veri üyeleri ile uyumlu değil:  
  
-   Bir veri sözleşmesi ile bir sürüm gerekli bir veri üyesi varsayılan alamaz (boş veya sıfır) veri üyesi olan farklı bir sürümünden verileri `EmitDefaultValue` kümesine `false`.  
  
-   Gerekli veri üyesine sahip `EmitDefaultValue` kümesine `false` varsayılan seri hale getirmek için kullanılamaz (boş veya sıfır) değeri, ancak seri durumundan çıkarma böyle bir değeri alabilir. Bu bir gidiş dönüşü sorun oluşturur (veri okunabilir ancak aynı verileri sonra yazılamaz). Bu nedenle, `IsRequired` olduğu `true` ve `EmitDefaultValue` olduğu `false` herhangi bir veri sözleşmesi sürümü gidiş dönüş içinde sonuçlanmaz bir değer üretmek için, bir sürüm, diğer tüm sürümler için aynı bileşimini uygulamalıdır.  
  
## <a name="schema-considerations"></a>Şema konuları  
 Hangi şema veri anlaşması türleri için üretilen açıklaması için bkz [veri sözleşmesi şema başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 Veri sözleşmesi türleri yapar için sürüm oluşturma için hiçbir hükümlerine WCF şema oluşturur. Diğer bir deyişle, bir türü sürümünden dışa aktarılan şema yalnızca bu sürümde mevcut veri üyeleri içerir. Uygulama <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi bir türü için şema değiştirmez.  
  
 Veri üyeleri, varsayılan isteğe bağlı öğeler şemaya dışarı aktarılır. Diğer bir deyişle, `minOccurs` (XML özniteliği) değerini 0 olarak ayarlayın. Gerekli veri üyeleri dışa aktarılır `minOccurs` 1 olarak ayarlayın.  
  
 Değişikliklerin birçoğu kabul edilecek katı şema uyulması gerekiyorsa, bölünemez bozucu gerçekten. Yukarıdaki örnekte, bir `CarV1` ile örnek yalnızca `Model` öğesi karşı doğrulamak `CarV2` şeması (her ikisi de sahip `Model` ve `Horsepower`, ancak her ikisi de isteğe bağlı). Ancak tersi doğru değildir: bir `CarV2` örneğine karşı doğrulama başarısız olurdu `CarV1` şema.  
  
 Gidiş dönüşü ayrıca bazı ek hususlar kapsar. Daha fazla bilgi için bkz: "Şema dikkat edilmesi gerekenler" bölümünde [İleri uyumlu veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
### <a name="other-permitted-changes"></a>Diğer değişikliklere izin  
 Uygulama <xref:System.Runtime.Serialization.IExtensibleDataObject> bölünemez değişiklik arabirimidir. Ancak, gidiş dönüşü destek türü olan sürümden önceki sürümler için yok <xref:System.Runtime.Serialization.IExtensibleDataObject> uygulanmıştır. Daha fazla bilgi için [İleri uyumlu veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
## <a name="enumerations"></a>Numaralandırmalar  
 Ekleyerek veya kaldırarak bir numaralandırma üyesine bölünmesi farklıdır. Bir numaralandırma üyesine adının değiştirilmesi bölme, sözleşme adı eski sürümü ile aynı kullanarak tutulur sürece `EnumMemberAttribute` özniteliği. Daha fazla bilgi için [veri sözleşmelerinde Numaralandırma türleri](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).  
  
## <a name="collections"></a>Koleksiyonlar  
 Çoğu koleksiyonu değişiklikler bölünemez çünkü çoğu koleksiyon türü veri anlaşması modelinde birbirleri ile değiştirilebilir. Ancak, özelleştirilmiş bir noncustomized koleksiyon yapma veya tam tersi bölünmesi farklıdır. Ayrıca, koleksiyonun özelleştirme ayarlarını değiştirme bölünmesi farklıdır; diğer bir deyişle, ad alanı, öğe adı, anahtar öğe adı ve değeri öğe adı yinelenen ve veri anlaşması adına değiştiriliyor. Koleksiyon özelleştirme hakkında daha fazla bilgi için bkz. [veri anlaşmalarında koleksiyon türleri](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md).  
Doğal olarak, içeriğinin (örneğin, bir dize listesi tamsayılar listesinden değiştirme) bir koleksiyon veri anlaşması değiştirme bölünmesi farklıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>  
 <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>  
 <xref:System.Runtime.Serialization.SerializationException>  
 <xref:System.Runtime.Serialization.IExtensibleDataObject>  
 [Sürüm Toleranslı Seri Hale Getirme Geri Çağrıları](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)  
 [En İyi Uygulamalar: Veri Sözleşmesi Sürümü Oluşturma](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)  
 [Veri Anlaşmalarını Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Veri Anlaşması Eşitliği](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [İleri Uyumlu Veri Anlaşmaları](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)
