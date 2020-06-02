---
title: Basit Türlerin Çıkarımını Yapma Kuralları
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 394624d6-4da0-430a-8a88-46efe40f14de
ms.openlocfilehash: 571019d13433312a5d31f581c3527aae901bbba7
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289076"
---
# <a name="rules-for-inferring-simple-types"></a>Basit Türlerin Çıkarımını Yapma Kuralları
<xref:System.Xml.Schema.XmlSchemaInference>Sınıfının öznitelikler ve öğeler için veri türünü nasıl kullandığını açıklar.  
  
 <xref:System.Xml.Schema.XmlSchemaInference>Sınıfı, öznitelikler ve öğeler için veri türünü basit türler olarak anlar. Bu bölümde, birden çok farklı değerin tek bir türe göre nasıl mutabık kılınmasıyla ve şema tanımlama `xsi` özniteliklerinin nasıl işlendiği açıklanmaktadır.  
  
## <a name="inferred-types"></a>Çıkartılan türler  
 <xref:System.Xml.Schema.XmlSchemaInference>Sınıfı, öğe ve öznitelik değerlerini basit türler olarak anlar ve sonuç şemasında bir tür özniteliği içerir. Tüm çıkartılan türler basit türlerdir. Ortaya çıkan şemanın bir parçası olarak hiçbir temel tür veya model dahil değildir.  
  
 Değerler, XML belgesinde karşılaştığı şekilde ayrı ayrı incelenir. Tür, İncelenme sırasında bir değer için algılanır. Bir öznitelik veya öğe için bir tür çıkarsanmışsa ve şu anda çıkartılan türle eşleşmeyen öznitelik veya öğe için bir değer ile karşılaşılırsa, <xref:System.Xml.Schema.XmlSchemaInference> sınıf her bir kural kümesinin türünü yükseltir. Bu kurallar, bu konunun ilerleyen kısımlarında bulunan yükseltme türü bölümünde ele alınmıştır.  
  
 Aşağıdaki tabloda, sonuçta elde edilen şema için olası çıkartılan türler listelenmektedir.  
  
|Basit tür|Description|  
|-----------------|-----------------|  
|boole|True, false, 0, 1.|  
|byte|-128 ile 127 arasında tamsayılar.|  
|unsignedByte|0 ile 255 arasında tamsayılar.|  
|short|-32768 ile 32767 arasında tamsayılar.|  
|unsignedShort|0 ile 65535 arasında tamsayılar.|  
|int|-2147483648 ile 2147483647 arasında tamsayılar.|  
|unsignedInt|0 ile 4294967295 arasında tamsayılar.|  
|long|– 9223372036854775808 ile 9223372036854775807 arasında tamsayılar.|  
|unsignedLong|0 ile 18446744073709551615 aralığındaki tamsayılar.|  
|integer|"-" Önekli sınırlı sayıda basamak olabilir.|  
|decimal|0 ile 28 basamak arasındaki sayısal değerler.|  
|float|, İsteğe bağlı olarak "E" veya "e" ve ardından üs değerini temsil eden bir tamsayı değeri gelir. Ondalık değerler-16777216 ile 16777216 arasında olabilir. Üs değerleri – 149 ile 104 arasında olabilir.<br /><br /> Float, özel değerlerin sonsuz ve sayısal olmayan değerleri göstermesini sağlar. Float için özel değerler şunlardır: 0,-0, INF,-INF, NaN.|  
|double|Ondalık değerler dışında float ile aynı değeri-9007199254740992 9007199254740992 aralığında olabilir ve üs değerleri – 1075-970 aralığında olabilir.<br /><br /> Double, özel değerlerin sonsuz ve sayısal olmayan değerleri göstermesini sağlar. Float için özel değerler şunlardır: 0,-0, INF,-INF, NaN.|  
|süre|W3C süre biçimi.|  
|tarih saat|W3C dateTime biçimi.|  
|time|W3C saat biçimi.|  
|date|Yıl değerleri 0001 ile 9999 arasında kısıtlanmıştır.|  
|Gyearayı|W3C Gregoryen ay ve yıl biçimi.|  
|string|Bir veya daha fazla Unicode karakteri.|  
  
## <a name="type-promotion"></a>Tür Yükseltme  
 <xref:System.Xml.Schema.XmlSchemaInference>Sınıfı özniteliği ve öğe değerlerini tek seferde inceler. Değerlerle karşılaşıldığında, en kısıtlayıcı, imzasız tür algılanır. Bir tür öznitelik veya öğe için çıkarsanmışsa ve şu anda çıkartılan türle eşleşmeyen yeni bir değerle karşılaşılırsa, çıkartılan tür, şu anda çıkartılan tür ve yeni değer için geçerli olan yeni bir türe yükseltilir. <xref:System.Xml.Schema.XmlSchemaInference>Sınıfı, çıkartılan türü yükseltirken önceki değerleri dikkate almaz.  
  
 Örneğin, iki XML belgelerinden aşağıdaki XML parçalarını göz önünde bulundurun:  
  
 `<MyElement1 attr1="12" />`  
  
 `<MyElement1 attr1="52344" />`  
  
 İlk `attr1` değer ile karşılaşıldığında, türü `attr1` `unsignedByte` değerine göre çıkarılır `12` . İkinciden `attr1` karşılaşıldığında, türü `unsignedShort` Şu anda çıkartılan tür ve geçerli değer temel alınarak öğesine yükseltilir `unsignedByte` `52344` .  
  
 Şimdi iki XML belgelerinden aşağıdaki XML 'i göz önünde bulundurun:  
  
 `<MyElement2 attr2="0" />`  
  
 `<MyElement2 attr2="true" />`  
  
 İlk `attr2` değer ile karşılaşıldığında, türü `attr2` `unsignedByte` değerine göre çıkarılır `0` . İkinciden `attr2` karşılaşıldığında, türü `string` Şu anda çıkartılan türe `unsignedByte` ve geçerli değere göre yükseltilir `true` çünkü <xref:System.Xml.Schema.XmlSchemaInference> sınıf, çıkartılan türü yükseltirken önceki değerleri dikkate alır. Ancak, `attr2` aynı XML belgesinde ve yukarıda gösterildiği gibi iki farklı XML belgesinde olmayan her iki örneğe de karşılaşılırsa, `attr2` olarak çıkarılırdı `boolean` .  
  
### <a name="ignored-attributes-from-the-httpswwww3org2001xmlschema-instance-namespace"></a>Ad alanından yoksayılan öznitelikler <https://www.w3.org/2001/XMLSchema-instance>

Şema, şema çıkarımı sırasında yoksayılan öznitelikleri tanımlar.  
  
|Öznitelik|Description|  
|---------------|-----------------|  
|`xsi:type`|Belirtilen bir öğeyle karşılaşılırsa, yok `xsi:type` `xsi:type` sayılır.|  
|`xsi:nil`|Özniteliği olan bir öğe ile `xsi:nil` karşılaşılırsa, çıkarılan şemadaki öğe bildiriminin değeri olur `nillable="true"` . `xsi:nil`Özniteliği olarak ayarlanmış bir öğenin `true` alt öğeleri olamaz.|  
|`xsi:schemaLocation`|`xsi:schemaLocation`Karşılaşılırsa, yok sayılır.|  
|`xsi:noNamespaceSchemaLocation`|`xsi:noNamespaceSchemaLocation`Karşılaşılırsa, yok sayılır.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şema Nesne Modeli (SOM)](xml-schema-object-model-som.md)
- [XML Belgelerinden Şema Çıkarımı Yapma](inferring-schemas-from-xml-documents.md)
- [Şema Düğüm Türleri ve Yapısını Çıkarma Kuralları](rules-for-inferring-schema-node-types-and-structure.md)
