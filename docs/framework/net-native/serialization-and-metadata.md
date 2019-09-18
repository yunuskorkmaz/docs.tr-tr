---
title: Serileştirme ve Meta Veriler
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec8180da9637ec2b2c4e1b432773b4f9f1ac908b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049181"
---
# <a name="serialization-and-metadata"></a>Serileştirme ve Meta Veriler

Uygulamanız nesneleri serileştirir ve onları yeniden ayırır, gerekli meta verilerin çalışma zamanında mevcut olduğundan emin olmak için çalışma zamanı yönergeleri (. RD. xml) dosyasına girişler eklemeniz gerekebilir. Serileştiricilerin iki kategorisi vardır ve her biri çalışma zamanı yönergeleri dosyasında farklı işleme gerektirir:  
  
- Yansıma tabanlı üçüncü taraf serileştiriciler. Bunlar, çalışma zamanı yönergeleri dosyasında değişiklik yapılmasını gerektirir ve sonraki bölümde ele alınmıştır.  
  
- .NET Framework sınıfı kitaplığında yansıma tabanlı olmayan serileştiriciler bulundu. Bunlar, çalışma zamanı yönergeleri dosyasında değişiklikler yapılmasını gerektirebilir ve [Microsoft serileştiriciler](#Microsoft) bölümünde ele alınmıştır.  
  
<a name="ThirdParty"></a>
## <a name="third-party-serializers"></a>Üçüncü taraf serileştiriciler

 Newtonsoft. JSON dahil olmak üzere üçüncü bölümden oluşan serileştiriciler, genellikle yansıma tabanlıdır. Seri hale getirilmiş verilerin ikili büyük nesne (BLOB) verildiğinde, verilerdeki alanlar, hedef türdeki alanlara ada göre bakılarak somut bir türe atanır. Bu kitaplıkların kullanılması en azından, bir `List<Type>` koleksiyonda serileştirmek veya seri durumdan çıkarmak <xref:System.Type> istediğiniz her nesne için [MissingMetadataException](missingmetadataexception-class-net-native.md) özel durumlarına neden olur.  
  
 Bu serileştiriciler için eksik meta verilerin neden olduğu sorunları ele almanın en kolay yolu, tek bir ad alanı (gibi `App.Models`) altında serileştirme içinde kullanılacak türleri toplamaktır ve buna bir `Serialize` meta veri yönergesi uygular:  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 Örnekte kullanılan sözdizimi hakkında daha fazla bilgi için bkz [ \<. Namespace > element](namespace-element-net-native.md).  
  
<a name="Microsoft"></a>
## <a name="microsoft-serializers"></a>Microsoft serileştiriciler

 <xref:System.Runtime.Serialization.DataContractSerializer>, ,<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Ve<xref:System.Xml.Serialization.XmlSerializer> sınıfları yansımayla güvenmese de, seri hale getirilecek veya seri durumdan çıkarılacak nesne temel alınarak kodun oluşturulmasını gerektirir. Her seri hale getirici için aşırı yüklenmiş oluşturucular <xref:System.Type> , seri hale getirilecek veya seri durumdan çıkarılacak türü belirten bir parametre içerir. Kodunuzda bu tür bir sonraki iki bölümde anlatıldığı gibi uygulamanız gereken eylemi tanımlar.  
  
### <a name="typeof-used-in-the-constructor"></a>oluşturucuda kullanılan typeof

 Bu serileştirme sınıflarının bir oluşturucusunu çağırır ve yöntem çağrısına C# [typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) işlecini eklerseniz, **ek bir iş yapmanız**gerekmez. Örneğin, bir serileştirme sınıfı oluşturucusuna yapılan aşağıdaki çağrıların her birinde, `typeof` oluşturucuya geçirilen ifadenin bir parçası olarak anahtar sözcüğü kullanılır.  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 .NET Native derleyici bu kodu otomatik olarak işleymeyecektir.  
  
### <a name="typeof-used-outside-the-constructor"></a>Oluşturucu dışında kullanılan typeof

 Bu serileştirme sınıflarının bir oluşturucusunu çağırır ve aşağıdaki kodda olduğu gibi oluşturucunun C# [](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator) <xref:System.Type> parametresine sağlanan ifadenin dışında typeof işlecini kullanırsanız, .NET Native derleyicisi türü çözemez:  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 Bu durumda, aşağıdaki gibi bir giriş ekleyerek çalışma zamanı yönergeleri dosyasında türü belirtmeniz gerekir:  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 Benzer şekilde, gibi bir Oluşturucu <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType> çağırırsanız ve seri hale getirmek için bir dizi ek <xref:System.Type> nesne sağlarsanız, aşağıdaki kodda olduğu gibi .NET Native derleyici bu türleri çözemez.  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 Her tür için aşağıdaki gibi girdileri çalışma zamanı yönergeleri dosyasına eklemeniz gerekir:  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 Örnekte kullanılan sözdizimi hakkında daha fazla bilgi için bkz [ \<. Type > element](type-element-net-native.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
- [Çalışma Zamanı Yönerge Öğeleri](runtime-directive-elements.md)
- [\<> Öğesi yazın](type-element-net-native.md)
- [\<Ad alanı > öğesi](namespace-element-net-native.md)
