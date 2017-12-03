---
title: "Veri Sözleşmesi Sürümü Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versioning [WCF], data contracts
- versioning [WCF]
- data contracts [WCF], versioning
ms.assetid: 4a0700cb-5f5f-4137-8705-3a3ecf06461f
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 68d9d153127f3f34c6546cef9f2b3ab5fc668899
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="data-contract-versioning"></a>Veri Sözleşmesi Sürümü Oluşturma
Uygulamaları geliştikçe, aynı zamanda değiştirmeniz gerekebilir Hizmetleri kullanım verileri sözleşme. Bu konuda açıklanmaktadır sürüm veri sözleşmeleri nasıl. Bu konuda veri sözleşmesi sürümü oluşturma mekanizmaları açıklanmaktadır. Tam genel bakış ve düzenleyici sürüm oluşturma yönergeleri için bkz: [en iyi uygulamalar: veri sözleşmesi sürümü oluşturma](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md).  
  
## <a name="breaking-vs-nonbreaking-changes"></a>VS kesiliyor. Bölünemez değişiklikleri  
 Bir veri sözleşmesi önemli değişiklikler veya bölünemez. Veri sözleşmesi bölünemez şekilde değiştirildiğinde Sözleşmesi'nin daha eski sürümünü kullanan bir uygulamayı daha yeni sürümünü kullanarak bir uygulama ile iletişim kurabilir ve Sözleşmesi'nin daha yeni sürümünü kullanan bir uygulama bir uygulamayla iletişim kurabilir eski sürümü kullanıyor. Diğer taraftan, önemli bir değişiklik bir ya da her iki yönde iletişimi engeller.  
  
 Nasıl, gönderilen ve alınan etkilemeyen tüm değişiklikler türüne bölünemez. Bu değişiklikleri veri sözleşmesi, yalnızca temel alınan tür değiştirmeyin. Ardından ayarlarsanız, örneğin, bir alanın adını bölünemez şekilde değiştirebileceğiniz <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> özelliği <xref:System.Runtime.Serialization.DataMemberAttribute> eski sürüm adı. Aşağıdaki kod, bir veri sözleşmesi 1 sürümünü gösterir.  
  
 [!code-csharp[C_DataContractVersioning#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#1)]
 [!code-vb[C_DataContractVersioning#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#1)]  
  
 Aşağıdaki kod bölünemez değişiklik gösterir.  
  
 [!code-csharp[C_DataContractVersioning#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#2)]
 [!code-vb[C_DataContractVersioning#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#2)]  
  
 Bazı değişiklikler iletilen verileri değiştirebilir, ancak olabilir veya sonu değil. Her zaman yeni aşağıdaki değişiklikler:  
  
-   Değiştirme <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> veya <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> bir veri sözleşmesi değeri.  
  
-   Veri üyeleri sırasını kullanarak değiştirme <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> özelliği <xref:System.Runtime.Serialization.DataMemberAttribute>.  
  
-   Bir veri üyesi yeniden adlandırılıyor.  
  
-   Veri sözleşmesi veri üyesi değiştirme. Örneğin, "Müşteri", "Kişi" adlı bir veri sözleşmesi ile bir türe adlı bir veri sözleşmesi ile bir dizeyi bir tamsayıya veya bir tür veri üyesi türünü değiştirme.  
  
 Aşağıdaki değişiklikleri da mümkündür.  
  
## <a name="adding-and-removing-data-members"></a>Ekleme ve kaldırma veri üyeleri  
 Kesin Şema geçerlilik (yeni örnekleri eski şemasına göre doğrulanıyor) gerektirmedikçe çoğu durumda, ekleme veya kaldırma veri üye önemli bir değişiklik değil.  
  
 Fazladan bir alan türüyle alanı eksik türüyle içine seri durumdan olduğunda, ek bilgileri göz ardı edilir. (Ayrıca olabilir depolanan gidiş amacıyla; daha fazla bilgi için bkz: [İleri uyumlu veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)).  
  
 Eksik alan türüyle fazladan bir alan türüyle içine seri durumdan olduğunda, ek alan, varsayılan değer olarak bırakılır, genellikle sıfır veya `null`. (Varsayılan değer değiştirilebilir; daha fazla bilgi için bkz: [sürüm toleranslı seri hale getirme geri çağrıları](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).)  
  
 Örneğin, kullanabilirsiniz `CarV1` sınıfı bir istemcide ve `CarV2` sınıfı bir hizmet veya kullanabilir `CarV1` bir hizmet sınıfında ve `CarV2` bir istemcide sınıfı.  
  
 [!code-csharp[C_DataContractVersioning#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#3)]
 [!code-vb[C_DataContractVersioning#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#3)]  
  
 Sürüm 2 uç noktası başarıyla sürüm 1 uç noktasına veri gönderebilir. Biçimlendiricisi sürüm 2 `Car` veri sözleşmesi XML aşağıdakine benzer verir.  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
    <HorsePower>300</HorsePower>  
</Car>  
```  
  
 V1 seri durumdan çıkarma altyapısı için eşleşen bir veri üyesi bulamazsa `HorsePower` alan ve bu verileri atar.  
  
 Ayrıca, sürüm 1 endpoint sürüm 2 uç noktasına veri gönderebilir. Biçimlendiricisi sürümü 1 `Car` veri sözleşmesi XML aşağıdakine benzer verir.  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
</Car>  
```  
  
 Sürüm 2 seri durumdan çıkarıcının ne ayarlamak bilmez `HorsePower` alanı, gelen XML içinde eşleşen verileri olduğundan. Bunun yerine, alanın 0 varsayılan değerine ayarlanır.  
  
## <a name="required-data-members"></a>Gerekli veri üyeleri  
 Bir veri üyesi ayarlayarak gerektiği olarak işaretlenmiş olabilir <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> özelliği <xref:System.Runtime.Serialization.DataMemberAttribute> için `true`. Veriler eksik kaldırılırken gerekirse, veri üyesi varsayılan değer olarak ayarlamak yerine bir özel durum.  
  
 Gerekli veri üye ekleme sonu bir değişikliktir. Diğer bir deyişle, yeni türü hala Uç noktalara eski türü, ancak şekilde geçici gönderilebilir. Olarak işaretlenmiş bir veri üyesini kaldırma gereken tüm önceki sürümü de önemli bir değişiklik ' dir.  
  
 Değiştirme <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> özellik değerinden `true` için `false` değil parçalamak, ancak ondan değiştirme `false` için `true` türü önceki tüm sürümlerini veri üyesi yoksa söz konusu çiğnemekten.  
  
> [!NOTE]
>  Ancak <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> özelliği ayarlanmış `true`, gelen veri boş olabilir veya sıfır ve bir türü olmalıdır hazırlanan bu olasılığı işlemek için. Kullanmayın <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> hatalı gelen veri karşı korumak için bir güvenlik mekanizması olarak.  
  
## <a name="omitted-default-values"></a>Belirtilmemişse varsayılan değerler  
 (Önerilmez rağmen) mümkündür ayarlamak için `EmitDefaultValue` örneğin özniteliğine özellik `false`açıklandığı gibi [veri üyesi varsayılan değerler](../../../../docs/framework/wcf/feature-details/data-member-default-values.md). Bu ayar ise `false`, varsayılan değer olarak ayarlanırsa veri üyesi yayılan değil (genellikle boş veya sıfır). Bu iki yolla farklı sürümleri gerekli veri üyeleri ile uyumlu değil:  
  
-   Bir veri sözleşmesine bir sürümünde gerekli bir veri üyesi varsayılan alamaz (null veya sıfır) farklı bir sürüm veri üyesi olan verileri `EmitDefaultValue` kümesine `false`.  
  
-   Gerekli veri üyesi olan `EmitDefaultValue` kümesine `false` varsayılan seri hale getirmek için kullanılamaz (null veya sıfır) değeri, ancak böyle bir değer seri durumdan çıkarma işleminde alabilir. Bu gidiş sorun oluşturur (veri okunabilir ancak aynı veri sonra yazılamaz). Bu nedenle, varsa `IsRequired` olan `true` ve `EmitDefaultValue` olan `false` sağlayacak şekilde herhangi bir veri sözleşmesi sürümü bir gidiş dönüş sonuçlanmaz bir değer üretmek edebilir tüm diğer sürümleri için bir sürümde aynı bileşimini uygulamalıdır.  
  
## <a name="schema-considerations"></a>Şema konuları  
 Veri sözleşmesi türleri için hangi şema üretilen açıklama için bkz: [veri sözleşmesi şema başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 Şema [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] üretir veri sözleşme türleri için sürüm oluşturma için hiç hükümleri yapar. Diğer bir deyişle, yalnızca bu sürümde mevcut veri üyeleri bir türü sürümünden dışa aktarılan bir şema içeriyor. Uygulama <xref:System.Runtime.Serialization.IExtensibleDataObject> arabirimi bir türüne ilişkin şema değiştirmez.  
  
 Veri üyeleri için şema varsayılan olarak isteğe bağlı öğeleri olarak dışarı aktarılır. Diğer bir deyişle, `minOccurs` (XML özniteliği) değerini 0 olarak ayarlayın. Gerekli veri üyeleri ile verilir `minOccurs` 1 olarak ayarlayın.  
  
 Değişikliklerin birçoğunu kabul olmasını bölünemez gerçekte şemaya katı bağlılığı gerekiyorsa sonu. Önceki örnekte, bir `CarV1` örneği yalnızca `Model` öğesi doğrulamak karşı `CarV2` şeması (her ikisi de olan `Model` ve `Horsepower`, ancak her ikisi de isteğe bağlı). Ancak, bu durumun tersi geçerli değildir: bir `CarV2` örneği karşı doğrulama başarısız olurdu `CarV1` şema.  
  
 Gidiş ayrıca bazı hususlar kapsar. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]"Şema hususlar" bölümünde [İleri uyumlu veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
### <a name="other-permitted-changes"></a>Diğer değişiklikler de izin verilir.  
 Uygulama <xref:System.Runtime.Serialization.IExtensibleDataObject> bölünemez değişikliği bir arabirimdir. Ancak, gidiş destek türü olan sürümden önceki sürümler için yok <xref:System.Runtime.Serialization.IExtensibleDataObject> uygulanmıştır. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][İleri uyumlu veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
## <a name="enumerations"></a>Numaralandırmalar  
 Kesme ekleyerek veya kaldırarak bir numaralandırma üyesine farklıdır. Bir numaralandırma üyesine adının değiştirilmesi parçalamak, sözleşme adının eski sürüm ile aynı kullanarak tutulur sürece `EnumMemberAtttribute` özniteliği. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Veri sözleşmelerinde Numaralandırma türleri](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).  
  
## <a name="collections"></a>Koleksiyonlar  
 Çoğu koleksiyonu değişiklikler bölünemez çoğu koleksiyon türü veri sözleşmesi modelinde birbirleri ile karşılıklı olduğundan. Ancak, özelleştirilmiş bir noncustomized koleksiyon yapma veya tersi önemli bir değişiklik olabilir. Ayrıca, koleksiyonun özelleştirme ayarlarını değiştirmek önemli bir değişiklik, diğer bir deyişle, kendi veri sözleşme adına ve ad alanı, yinelenen öğe adı, anahtar öğe adı ve değeri öğe adı değiştirme. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Koleksiyon özelleştirme bkz [veri sözleşmelerinde koleksiyon türleri](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md).  
Doğal olarak, koleksiyon (örneğin, bir tamsayı listesinden dizeleri listesine değiştirme) içeriğinin veri sözleşmesi değiştirmek önemli bir değişiklik.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>  
 <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>  
 <xref:System.Runtime.Serialization.SerializationException>  
 <xref:System.Runtime.Serialization.IExtensibleDataObject>  
 [Sürüm toleranslı seri hale getirme geri çağrıları](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)  
 [En iyi uygulamalar: Veri sözleşmesi sürümü oluşturma](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)  
 [Veri sözleşmelerini kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Veri sözleşmesi eşitliği](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [İleri uyumlu veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)
