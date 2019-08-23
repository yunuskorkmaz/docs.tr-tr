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
ms.openlocfilehash: 309cd891fd2d764314060e49a401bd1d8f7b8d32
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963262"
---
# <a name="data-contract-versioning"></a>Veri Sözleşmesi Sürümü Oluşturma
Uygulamalar geliştikçe, hizmetler tarafından kullanılan veri sözleşmelerini da değiştirmeniz gerekebilir. Bu konuda, veri sözleşmelerinin nasıl kullanılacağı açıklanmaktadır. Bu konuda, veri sözleşmesi sürüm oluşturma mekanizmaları açıklanmaktadır. Kapsamlı bir genel bakış ve güvenlik sürümü oluşturma kılavuzu için bkz [. en iyi uygulamalar: Veri sözleşmesi sürümü](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)oluşturma.  
  
## <a name="breaking-vs-nonbreaking-changes"></a>Kırılmaya karşı Bölünemez değişiklikler  
 Bir veri sözleşmesindeki değişiklikler kırır veya bölünemez olabilir. Bir veri anlaşması bölünemez bir şekilde değiştirildiğinde, sözleşmenin eski sürümünü kullanan bir uygulama, yeni sürümü kullanarak bir uygulamayla iletişim kurabilir ve sözleşmenin daha yeni bir sürümünü kullanan bir uygulama bir uygulamayla iletişim kurabilir eski sürümü kullanma. Öte yandan, bir değişiklik bir veya her iki yönde iletişime engel olur.  
  
 Bir türe yapılan tüm değişiklikler, nasıl iletildiğini ve alındığını etkilemeyen bir tür için bölünmez. Bu gibi değişiklikler veri sözleşmesini değiştirmez, yalnızca temeldeki tür. Örneğin, <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> <xref:System.Runtime.Serialization.DataMemberAttribute> öğesinin özelliğini daha eski sürüm adına ayarlarsanız, bir alanın adını bölünemez bir şekilde değiştirebilirsiniz. Aşağıdaki kod, bir veri sözleşmesinin 1. sürümünü gösterir.  
  
 [!code-csharp[C_DataContractVersioning#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#1)]
 [!code-vb[C_DataContractVersioning#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#1)]  
  
 Aşağıdaki kod, Bölünemez bir değişikliği gösterir.  
  
 [!code-csharp[C_DataContractVersioning#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#2)]
 [!code-vb[C_DataContractVersioning#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#2)]  
  
 Bazı değişiklikler iletilen verileri değiştirir, ancak bunları bozmayabilir veya olmayabilir. Aşağıdaki değişiklikler her zaman en kesiliyor:  
  
- Veri sözleşmesinin <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>veyadeğerinideğiştirme. <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>  
  
- Öğesinin özelliğini<xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> kullanarak veri üyelerinin sırasını değiştirme. <xref:System.Runtime.Serialization.DataMemberAttribute>  
  
- Veri üyesini yeniden adlandırma.  
  
- Bir veri üyesinin veri sözleşmesini değiştirme. Örneğin, veri üyesinin türünü bir dizeden bir dizeye veya "Customer" adlı bir veri sözleşmesine sahip bir türden "Person" adlı bir veri sözleşmesine sahip bir türe değiştirme.  
  
 Aşağıdaki değişiklikler de mümkündür.  
  
## <a name="adding-and-removing-data-members"></a>Veri üyeleri ekleme ve kaldırma  
 Çoğu durumda, kesin şema geçerliliği gerekmedikçe bir veri üyesini eklemek veya kaldırmak, Son değişiklik değildir (eski şemaya göre yeni örnekler doğrulanıyor).  
  
 Ek alan içeren bir tür, eksik alan içeren bir türe seri durumdan çıkarılacağından, ek bilgiler yok sayılır. (Ayrıca, gidiş dönüşü için de depolanabilir; daha fazla bilgi için bkz. [Ileri uyumlu veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)).  
  
 Eksik alan içeren bir tür, ek alan içeren bir türe seri durumdan çıkarılacağından, ek alan varsayılan değerinde (genellikle sıfır veya `null`) bırakılır. (Varsayılan değer değişebilir; daha fazla bilgi için bkz. [Sürüm dayanıklı serileştirme geri çağırmaları](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).)  
  
 Örneğin, `CarV1` sınıfını bir istemcideki bir hizmette `CarV2` ve sınıfı üzerinde kullanabilir `CarV1` veya bir hizmette ve `CarV2` bir istemcide sınıfını kullanabilirsiniz.  
  
 [!code-csharp[C_DataContractVersioning#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#3)]
 [!code-vb[C_DataContractVersioning#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#3)]  
  
 Sürüm 2 uç noktası, sürüm 1 uç noktasına başarıyla veri gönderebilir. `Car` Veri sözleşmesinin sürüm 2 ' nin serileştirilmesi, XML 'e benzer şekilde XML verir.  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
    <HorsePower>300</HorsePower>  
</Car>  
```  
  
 V1 'deki seri kaldırma altyapısı, `HorsePower` alan için eşleşen bir veri üyesi bulamaz ve bu verileri atar.  
  
 Ayrıca, sürüm 1 uç noktası sürüm 2 uç noktasına veri gönderebilir. `Car` Veri sözleşmesinin seri hale getirilmesi, XML 'e benzer bir XML verir.  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
</Car>  
```  
  
 Sürüm 2 seri hale getirici, gelen XML 'de eşleşen veri bulunmadığından `HorsePower` alanın ne ayarlanacağını bilmez. Bunun yerine, alan varsayılan değeri olan 0 ' dır.  
  
## <a name="required-data-members"></a>Gerekli veri üyeleri  
 Bir veri üyesi <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> <xref:System.Runtime.Serialization.DataMemberAttribute>,öğesinin özelliği olarak ayarlanarak gerekli olarak işaretlenebilir. `true` Seri durumdan çıkarma sırasında gerekli veriler eksikse, veri üyesini varsayılan değerine ayarlamak yerine bir özel durum oluşturulur.  
  
 Gerekli bir veri üyesini eklemek, bir son değişiklik olur. Diğer bir deyişle, daha yeni tür, daha eski tür olan uç noktalara yine de başka bir şekilde gönderilebilir. Önceki bir sürümde gerekli olarak işaretlenmiş bir veri üyesini kaldırmak da aynı zamanda bir değişiklik olur.  
  
 `false` `false` `true` Özellik değerinin ' den ' `true` den ' ye değiştirilmesi, ancak türün önceki sürümlerinden biri söz konusu veri üyesine sahip değilse, ' dan ' ı ' den ' a değiştirme işlemi bozulabilir. <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>  
  
> [!NOTE]
> <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> Özelliği olarak`true`ayarlanmış olsa da, gelen veriler null veya sıfır olabilir ve bu olasılığa yönelik olarak bir tür hazırlanmalıdır. Hatalı gelen verilere <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> karşı korumak için bir güvenlik mekanizması olarak kullanmayın.  
  
## <a name="omitted-default-values"></a>Atlanan varsayılan değerler  
 `EmitDefaultValue` DataMemberAttribute`false`özniteliğinde özelliği, [veri üyesi varsayılan değerleri](../../../../docs/framework/wcf/feature-details/data-member-default-values.md)bölümünde açıklandığı gibi olarak ayarlamak için mümkündür (önerilmese de önerilmez). Bu ayar ise `false`, veri üyesi varsayılan değerine ayarlandıysa (genellikle null veya sıfır) yayınlanmaz. Bu, farklı sürümlerdeki gerekli veri üyeleriyle iki şekilde uyumlu değildir:  
  
- Bir sürümde gerekli olan veri üyesine sahip bir veri sözleşmesi, veri üyesinin `EmitDefaultValue` `false`ayarlandığı farklı bir sürümden varsayılan (null veya sıfır) veri alamaz.  
  
- `EmitDefaultValue` Olarak`false` ayarlanmış gerekli bir veri üyesi, varsayılan (null veya sıfır) değerini seri hale getirmek için kullanılamaz, ancak serisini kaldırma sırasında böyle bir değer alabilir. Bu, gidiş-dönüşü bir sorun oluşturur (veriler okunabilir, ancak aynı veriler daha sonra yazılamaz). Bu nedenle ,`EmitDefaultValue` ve tek bir sürümlerdeise,aynıbirleşim,hiçbirverisözleşmesininhiçbirsürümü,gidişdönüşsonucuolmayanbirdeğerüretmeyecekşekildediğertümsürümlereuygulanmalıdır.`false` `true` `IsRequired`  
  
## <a name="schema-considerations"></a>Şema konuları  
 Veri anlaşması türleri için hangi şemanın üretildiğinin açıklaması için bkz. [veri sözleşmesi şema başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 Veri anlaşması türleri için şema WCF, sürüm oluşturma için hiçbir anlaşma yapmaz. Diğer bir deyişle, bir türün belirli bir sürümünden aktarılmış olan şema yalnızca o sürümde bulunan veri üyelerini içerir. <xref:System.Runtime.Serialization.IExtensibleDataObject> Arabirimi uygulamak bir tür için şemayı değiştirmez.  
  
 Veri üyeleri varsayılan olarak isteğe bağlı öğeler olarak şemaya verilir. Diğer bir deyişle, `minOccurs` (XML özniteliği) değeri 0 olarak ayarlanır. Gerekli veri üyeleri, 1 olarak `minOccurs` ayarlanan ile birlikte verilir.  
  
 Şemaya sıkı bir şekilde gerek duyulduğundan, Bölünemez olarak değerlendirilen değişikliklerin çoğu aslında kırmadır. `CarV1` Önceki örnekte, `Model` yalnızca `Model` `Horsepower`öğesi olan bir örnek şemayagöre(ve'asahiptir,ancakherikisideisteğebağlıdır)doğrulanır.`CarV2` Ancak, tersi doğru değildir: bir `CarV2` örnek, `CarV1` şemaya karşı doğrulama başarısız olur.  
  
 Ayrıca, gidiş dönüşü bazı ek hususlar de kapsar. Daha fazla bilgi için, [Ileriye dönük olarak uyumlu veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)Içindeki "şema değerlendirmeleri" bölümüne bakın.  
  
### <a name="other-permitted-changes"></a>Izin verilen diğer değişiklikler  
 Arabirimi uygulamak <xref:System.Runtime.Serialization.IExtensibleDataObject> , Bölünemez bir değişiklik. Ancak, uygulanan sürümden <xref:System.Runtime.Serialization.IExtensibleDataObject> önceki türdeki sürümler için gidiş-dönüşü desteği yoktur. Daha fazla bilgi için bkz. [Ileri uyumlu veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
## <a name="enumerations"></a>Numaralandırmalar  
 Sabit Listesi üyesini ekleme veya kaldırma, bir son değişiklik. Bir numaralandırma üyesinin adının değiştirilmesi, sözleşme adı `EnumMemberAttribute` özniteliğini kullanarak eski sürümdeki ile aynı tutulmadığı sürece bir parçadır. Daha fazla bilgi için bkz. [veri sözleşmeleri Içindeki numaralandırma türleri](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).  
  
## <a name="collections"></a>Koleksiyonlar  
 Çoğu koleksiyon değişikliği, veri anlaşması modelinde birbirleriyle aynı şekilde değiştirilebilecek için bölünemez. Bununla birlikte, özelleştirilmeyen bir koleksiyonun özelleştirilme veya tam tersi de bir son değişiklik haline gelmemiştir. Ayrıca, koleksiyonun özelleştirme ayarlarının değiştirilmesi de bir son değişiklik olur; diğer bir deyişle, veri anlaşması adı ve ad alanı, yinelenen öğe adı, anahtar öğesi adı ve değer öğesi adı değiştiriliyor. Koleksiyon özelleştirmesi hakkında daha fazla bilgi için bkz. [veri sözleşmeleri Içindeki koleksiyon türleri](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md).  
Doğal olarak, bir koleksiyonun içeriği (örneğin, bir tamsayı listesinden bir dizeler listesine değiştirme), bir son değişiklik olarak değişir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>
- <xref:System.Runtime.Serialization.SerializationException>
- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- [Sürüm Toleranslı Seri Hale Getirme Geri Çağrıları](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)
- [En iyi uygulamalar: Veri sözleşmesi sürümü oluşturma](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)
- [Veri Anlaşmalarını Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Veri Anlaşması Eşitliği](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [İleri Uyumlu Veri Anlaşmaları](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)
