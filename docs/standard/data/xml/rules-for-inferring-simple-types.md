---
title: Basit Türlerin Çıkarımını Yapma Kuralları
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 394624d6-4da0-430a-8a88-46efe40f14de
ms.openlocfilehash: 17429e77f7764873e607a8feaa62da1cc6e014a4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710238"
---
# <a name="rules-for-inferring-simple-types"></a>Basit Türlerin Çıkarımını Yapma Kuralları
<xref:System.Xml.Schema.XmlSchemaInference> sınıfının öznitelikler ve öğeler için veri türünü nasıl kullandığını açıklar.  
  
 <xref:System.Xml.Schema.XmlSchemaInference> sınıfı, öznitelikler ve öğeler için veri türünü basit türler olarak anlar. Bu bölümde, birden çok farklı değerin tek bir türe göre nasıl uzlanalındığı ve şema tanımlama `xsi` özniteliklerinin nasıl işlendiği açıklanmaktadır.  
  
## <a name="inferred-types"></a>Çıkartılan türler  
 <xref:System.Xml.Schema.XmlSchemaInference> sınıfı, öğe ve öznitelik değerlerini basit türler olarak barındırır ve sonuç şemasında bir tür özniteliği içerir. Tüm çıkartılan türler basit türlerdir. Ortaya çıkan şemanın bir parçası olarak hiçbir temel tür veya model dahil değildir.  
  
 Değerler, XML belgesinde karşılaştığı şekilde ayrı ayrı incelenir. Tür, İncelenme sırasında bir değer için algılanır. Bir öznitelik veya öğe için bir tür çıkarsanmışsa ve şu anda çıkartılan türle eşleşmeyen öznitelik veya öğe için bir değer ile karşılaşılırsa, <xref:System.Xml.Schema.XmlSchemaInference> sınıfı her bir kural kümesinin türünü yükseltir. Bu kurallar, bu konunun ilerleyen kısımlarında bulunan yükseltme türü bölümünde ele alınmıştır.  
  
 Aşağıdaki tabloda, sonuçta elde edilen şema için olası çıkartılan türler listelenmektedir.  
  
|Basit tür|Açıklama|  
|-----------------|-----------------|  
|Boole değeri|True, false, 0, 1.|  
|byte|-128 ile 127 arasında tamsayılar.|  
|unsignedByte|0 ile 255 arasında tamsayılar.|  
|short|-32768 ile 32767 arasında tamsayılar.|  
|unsignedShort|0 ile 65535 arasında tamsayılar.|  
|int|-2147483648 ile 2147483647 arasında tamsayılar.|  
|unsignedInt|0 ile 4294967295 arasında tamsayılar.|  
|long|– 9223372036854775808 ile 9223372036854775807 arasında tamsayılar.|  
|unsignedLong|0 ile 18446744073709551615 aralığındaki tamsayılar.|  
|tamsayı|"-" Önekli sınırlı sayıda basamak olabilir.|  
|decimal|0 ile 28 basamak arasındaki sayısal değerler.|  
|float|, İsteğe bağlı olarak "E" veya "e" ve ardından üs değerini temsil eden bir tamsayı değeri gelir. Ondalık değerler-16777216 ile 16777216 arasında olabilir. Üs değerleri – 149 ile 104 arasında olabilir.<br /><br /> Float, özel değerlerin sonsuz ve sayısal olmayan değerleri göstermesini sağlar. Float için özel değerler şunlardır: 0,-0, INF,-INF, NaN.|  
|çift|Ondalık değerler dışında float ile aynı değeri-9007199254740992 9007199254740992 aralığında olabilir ve üs değerleri – 1075-970 aralığında olabilir.<br /><br /> Double, özel değerlerin sonsuz ve sayısal olmayan değerleri göstermesini sağlar. Float için özel değerler şunlardır: 0,-0, INF,-INF, NaN.|  
|süre|W3C süre biçimi.|  
|tarih saat|W3C dateTime biçimi.|  
|zaman|W3C saat biçimi.|  
|Tarih|Yıl değerleri 0001 ile 9999 arasında kısıtlanmıştır.|  
|Gyearayı|W3C Gregoryen ay ve yıl biçimi.|  
|dize|Bir veya daha fazla Unicode karakteri.|  
  
## <a name="type-promotion"></a>Tür Yükseltme  
 <xref:System.Xml.Schema.XmlSchemaInference> sınıfı özniteliği ve öğe değerlerini tek seferde inceler. Değerlerle karşılaşıldığında, en kısıtlayıcı, imzasız tür algılanır. Bir tür öznitelik veya öğe için çıkarsanmışsa ve şu anda çıkartılan türle eşleşmeyen yeni bir değerle karşılaşılırsa, çıkartılan tür, şu anda çıkartılan tür ve yeni değer için geçerli olan yeni bir türe yükseltilir. <xref:System.Xml.Schema.XmlSchemaInference> sınıfı, çıkartılan türü yükseltirken önceki değerleri dikkate almaz.  
  
 Örneğin, iki XML belgelerinden aşağıdaki XML parçalarını göz önünde bulundurun:  
  
 `<MyElement1 attr1="12" />`  
  
 `<MyElement1 attr1="52344" />`  
  
 İlk `attr1` değeri ile karşılaşıldığında, `attr1` türü `12`göre `unsignedByte` olarak algılanır. İkinci `attr1` karşılaşıldığında, tür şu anda çıkartılan `unsignedByte` türüne ve geçerli değer `52344`göre `unsignedShort` yükseltilir.  
  
 Şimdi iki XML belgelerinden aşağıdaki XML 'i göz önünde bulundurun:  
  
 `<MyElement2 attr2="0" />`  
  
 `<MyElement2 attr2="true" />`  
  
 İlk `attr2` değeri ile karşılaşıldığında, `attr2` türü `0`göre `unsignedByte` olarak algılanır. İkinci `attr2` karşılaşıldığında, türü şu anda çıkartılan `unsignedByte` türüne ve geçerli değere göre `string` yükseltilir `true`, <xref:System.Xml.Schema.XmlSchemaInference> sınıfı, çıkartılan türü yükseltirken önceki değerleri dikkate alır. Ancak, yukarıda gösterildiği gibi iki farklı XML belgesinde değil aynı XML belgesinde `attr2` her iki örneğe de karşılaşılırsa, `attr2` `boolean`olarak algılanır.  
  
### <a name="ignored-attributes-from-the-httpswwww3org2001xmlschema-instance-namespace"></a><https://www.w3.org/2001/XMLSchema-instance> ad alanındaki öznitelikler yoksayıldı

Şema, şema çıkarımı sırasında yoksayılan öznitelikleri tanımlar.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`xsi:type`|`xsi:type` belirtilen bir öğeyle karşılaşılırsa, `xsi:type` yok sayılır.|  
|`xsi:nil`|`xsi:nil` özniteliğine sahip bir öğe ile karşılaşılırsa, çıkarılan şemadaki öğe bildiriminin `nillable="true"`değeri vardır. `true` olarak ayarlanmış `xsi:nil` özniteliği olan bir öğenin alt öğeleri olamaz.|  
|`xsi:schemaLocation`|`xsi:schemaLocation` karşılaşılırsa, yok sayılır.|  
|`xsi:noNamespaceSchemaLocation`|`xsi:noNamespaceSchemaLocation` karşılaşılırsa, yok sayılır.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şema Nesne Modeli (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)
- [XML Belgelerinden Şema Çıkarımı Yapma](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)
- [Şema Düğüm Türleri ve Yapısını Çıkarma Kuralları](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)
