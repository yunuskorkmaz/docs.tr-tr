---
title: Serileştirme ve Meta Veriler
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
ms.openlocfilehash: 7c6fe241fbf92f52abfa0eb66c37bff4d227b4e5
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81241925"
---
# <a name="serialization-and-metadata"></a>Serileştirme ve Meta Veriler

Uygulamanız nesneleri seri hale getirebilir ve deserialize ederse, gerekli meta verilerin çalışma zamanında bulunduğundan emin olmak için çalışma zamanı yönergelerinize (.rd.xml) giriş eklemeniz gerekebilir. İki serializers kategorisi vardır ve her biri çalışma zamanı yönergeleri dosyanızda farklı işleme gerektirir:  
  
- Yansıma tabanlı üçüncü taraf serileştiriciler. Bunlar çalışma zamanı yönergeleri dosyanızda değişiklik gerektirir ve bir sonraki bölümde tartışılır.  
  
- .NET Framework sınıf kitaplığında bulunan yansıma tabanlı olmayan serializers. Bunlar çalışma zamanı yönergeleri dosyanızda değişiklik yapılmasını gerektirebilir ve [Microsoft serializers](#Microsoft) bölümünde tartışılır.  
  
<a name="ThirdParty"></a>
## <a name="third-party-serializers"></a>Üçüncü taraf serileştiriciler

 Newtonsoft.JSON dahil olmak üzere üçüncü bölüm serializers, genellikle yansıma tabanlıdır. Serileştirilmiş verilerin ikili büyük nesnesi (BLOB) göz önüne alındığında, verilerdeki alanlar hedef türündeki alanlara adıyla bakarak somut bir türe atanır. En azından, bu kitaplıkları kullanarak bir <xref:System.Type> `List<Type>` koleksiyonda seri hale getirmeye veya deserialize etmeye çalıştığınız her nesne için Eksik [MetadataException](missingmetadataexception-class-net-native.md) özel durumlara neden olur.  
  
 Bu serileştiriciler için eksik meta verilerin neden olduğu sorunları gidermenin en kolay yolu, serileştirmede tek `App.Models`bir ad `Serialize` alanı altında (örneğin) kullanılacak türleri toplamak ve ona bir meta veri yönergesi uygulamaktır:  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 Örnekte kullanılan sözdizimi hakkında bilgi için Ad [ \<alanı> Öğesi'ne](namespace-element-net-native.md)bakın.  
  
<a name="Microsoft"></a>
## <a name="microsoft-serializers"></a>Microsoft serializers

 <xref:System.Runtime.Serialization.DataContractSerializer>" ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <xref:System.Xml.Serialization.XmlSerializer> sınıflar yansımaya dayanmasa da, seri hale getirilecek veya deserialized olacak nesneye dayalı olarak oluşturulacak kod gerektirir. Her serileştirici için aşırı yüklü yapıcılar, seri hale getirilecek veya deserialized türünü belirten bir <xref:System.Type> parametre içerir. Kodunuzdaki bu türü nasıl belirtdiğiniz, sonraki iki bölümde açıklanıldığı gibi, işleminizi tanımlar.  
  
### <a name="typeof-used-in-the-constructor"></a>konstrüktörde kullanılan tip

 Bu serileştirme sınıflarının bir oluşturucusu çağırır ve yöntem çağrısına C# [tipi](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) işleci **eklerseniz, ek bir iş yapmanız gerekmez.** Örneğin, aşağıdaki çağrıların her birinde bir serileştirme sınıfı `typeof` oluşturucuya, anahtar kelime oluşturucuya geçirilen ifadenin bir parçası olarak kullanılır.  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 .NET Native derleyicisi bu kodu otomatik olarak işler.  
  
### <a name="typeof-used-outside-the-constructor"></a>yapıcı dışında kullanılan tip

 Bu serileştirme sınıflarının oluşturucusu çağırır ve [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) aşağıdaki kodda olduğu gibi,.NET Native <xref:System.Type> derleyicisi aşağıdaki kodda olduğu gibi, oluşturucunun parametresine verilen ifadenin dışında C# tipi işleci kullanırsanız, .NET Native derleyicisi türü çözemez:  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 Bu durumda, aşağıdaki gibi bir giriş ekleyerek çalışma zamanı yönergeleri dosyasındaki türü belirtmeniz gerekir:  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 Benzer şekilde, aşağıdaki kodda olduğu <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29> gibi serihale <xref:System.Type> getirmek için bir dizi ek nesne çağırır ve sağlarsanız, .NET Native derleyicisi bu türleri çözemez.  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 Çalışma zamanı yönergeleri dosyasına her tür için aşağıdaki gibi girişler eklemeniz gerekir:  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 Örnekte kullanılan sözdizimi hakkında bilgi için, [ \<> Öğesi Türü'ne](type-element-net-native.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
- [\<> Öğesi Yazın](type-element-net-native.md)
- [\<Ad Alanı> Öğesi](namespace-element-net-native.md)
