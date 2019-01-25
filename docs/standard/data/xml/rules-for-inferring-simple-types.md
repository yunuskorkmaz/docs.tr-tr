---
title: Basit türlerin çıkarımını yapma kuralları
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 394624d6-4da0-430a-8a88-46efe40f14de
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15e7692abfe06ec9e9f91a3b229bf99971eaecc1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550506"
---
# <a name="rules-for-inferring-simple-types"></a>Basit türlerin çıkarımını yapma kuralları
Açıklayan nasıl <xref:System.Xml.Schema.XmlSchemaInference> sınıfı öznitelikler ve öğeler için veri türünü çıkarsar.  
  
 <xref:System.Xml.Schema.XmlSchemaInference> Sınıfı öznitelikler ve öğeler basit türler için veri türünü çıkarsar. Bu bölümde birden çok farklı değerler şunlardır: tek bir tür için mutabık ve nasıl şema tanımlama olası çıkarsanan türleri açıklanmaktadır `xsi` öznitelikleri işlenir.  
  
## <a name="inferred-types"></a>Çıkarsanan türleri  
 <xref:System.Xml.Schema.XmlSchemaInference> Sınıfı çıkarsar öğe ve öznitelik değerleri basit türler olarak ve sonuçta elde edilen şemada type özniteliği içerir. Tüm basit türler türleridir sonuçlandı. Temel türleri ya da modelleri elde edilen şemasını bir parçası olarak dahil edilir.  
  
 XML belgesinde karşılaştığından değerleri ayrı ayrı incelenir. Türü için bir değer, incelenir zamanında algılanır. Bir tür bir öznitelik veya öğenin için ortaya çıkan ve bir öznitelik veya öğenin değeri, şu anda çıkarsanan tür eşleşmeyen karşılaşılanaa <xref:System.Xml.Schema.XmlSchemaInference> sınıfı her bir kural kümesi için tür yükseltir. Bu kurallar, tür yükseltme bölümünde, bu konunun ilerleyen bölümlerinde ele alınmıştır.  
  
 Aşağıdaki tabloda, elde edilen şema için olası çıkarsanan türleri listelenmektedir.  
  
|Basit tür|Açıklama|  
|-----------------|-----------------|  
|Boole değeri|TRUE, false, 0, 1.|  
|byte|– 128 arasında 127 aralığında tamsayı.|  
|unsignedByte|0-255 aralığında tamsayı.|  
|short|İle 32767 –32768 aralığındaki tam sayılar.|  
|unsignedShort|0 ile 65535 aralığındaki tam sayılar.|  
|int|İle 2147483647 arasında –2147483648 aralığındaki tam sayılar.|  
|unsignedInt|0-4294967295 aralığındaki tam sayılar.|  
|long|Tamsayı aralığında –9223372036854775808 9223372036854775807 için.|  
|unsignedLong|0 için 18446744073709551615 aralığındaki tam sayılar.|  
|tamsayı|Sınırlı sayıda basamak büyük olasılıkla ön eki "-".|  
|decimal|0 ile 28 kesinliği basamak içeren sayısal değerler.|  
|float|"E" veya "e" üs temsil eden bir tamsayı değeri tarafından izlenen isteğe bağlı olarak arkasından bir ondalık sayı. Ondalık değerler için 16777216-16777216 aralığında olabilir. Üstel değerleri için 104 –149 aralığında olabilir.<br /><br /> Kayan noktalı sayı sonsuza göstermek özel değerler ve sayısal olmayan değerleri olanak sağlar. Kayan nokta için özel değerler şunlardır: 0, - 0, INF, -INF, NaN.|  
|çift|Kayan noktalı sayı ondalık değerler dışında aynı-9007199254740992 9007199254740992 için aralığında olabilir ve üstel değerleri için 970 –1075 aralığında olabilir.<br /><br /> Sonsuza göstermek özel değerler ve sayısal olmayan değerleri çift olanak sağlar. Kayan nokta için özel değerler şunlardır: 0, - 0, INF, -INF, NaN.|  
|süre|W3C süre biçimi.|  
|tarih saat|W3C tarih/saat biçimi.|  
|zaman|W3C saat biçimi.|  
|Tarih|Yıl değerlerini 0001 9999 kısıtlanır.|  
|gYearMonth|W3C Gregoryen ayı ve yılı biçimi.|  
|dize|Bir veya daha fazla Unicode karakteri.|  
  
## <a name="type-promotion"></a>Tür Yükseltme  
 <xref:System.Xml.Schema.XmlSchemaInference> Sınıfı özniteliği ve öğesi değerlerine bir anda inceler. Değerleri karşılaştığından, en kısıtlayıcı, işaretsiz tür algılanır. Bir tür bir öznitelik veya öğenin için ortaya çıkan ve yeni bir değer şu anda çıkarsanan tür eşleşmeyen karşılaştı, şu anda çıkarsanan tür ve yeni bir değer için geçerli yeni bir tür için çıkarsanan tür yükseltilir. <xref:System.Xml.Schema.XmlSchemaInference> Çıkarsanan tür yükseltilirken, sınıfı önceki değerleri düşünün.  
  
 Örneğin, aşağıdaki parçalarını iki XML belgelerinden göz önünde bulundurun:  
  
 `<MyElement1 attr1="12" />`  
  
 `<MyElement1 attr1="52344" />`  
  
 Zaman ilk `attr1` değeri karşılaştı, türü `attr1` olarak çıkarılan `unsignedByte` değerine göre `12`. Zaman ikinci `attr1` olduğu ile karşılaşıldı, türüne yükseltilir `unsignedShort` şu anda gösterilen türüne göre `unsignedByte` geçerli değeri `52344`.  
  
 Şimdi iki XML belgelerinden aşağıdaki XML göz önünde bulundurun:  
  
 `<MyElement2 attr2="0" />`  
  
 `<MyElement2 attr2="true" />`  
  
 Zaman ilk `attr2` değeri karşılaştı, türü `attr2` olarak çıkarılan `unsignedByte` değerine göre `0`. Zaman ikinci `attr2` olduğu ile karşılaşıldı, türüne yükseltilir `string` şu anda gösterilen türüne göre `unsignedByte` geçerli değeri `true` çünkü <xref:System.Xml.Schema.XmlSchemaInference> yükseltilirken, sınıfı önceki değerleri düşünün türün gösterilmesi. Ancak, her iki `attr2` aynı XML belgesi ve iki farklı XML belgeleri, yukarıda gösterildiği gibi karşılaşılan `attr2` olarak ortaya çıkan `boolean`.  
  
### <a name="ignored-attributes-from-the-httpswwww3org2001xmlschema-instance-namespace"></a>Öznitelikleri yoksayıldı <https://www.w3.org/2001/XMLSchema-instance> ad alanı

Aşağıdaki şema tanımlama öznitelikleri şema çıkarımı sırasında yok sayılır.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`xsi:type`|Bir öğe ile karşılaşılırsa `xsi:type` belirtilen `xsi:type` göz ardı edilir.|  
|`xsi:nil`|Bir öğe ile bir `xsi:nil` öznitelik karşılaşıldığında, çıkarsanan şema öğesi bildiriminde sahip `nillable="true"`. Bir öğe ile bir `xsi:nil` özniteliğini `true` alt öğeleri olamaz.|  
|`xsi:schemaLocation`|Varsa `xsi:schemaLocation` olan karşılaştı, göz ardı edilir.|  
|`xsi:noNamespaceSchemaLocation`|Varsa `xsi:noNamespaceSchemaLocation` olan karşılaştı, göz ardı edilir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Şema Nesne Modeli (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)
- [XML Belgelerinden Şema Çıkarımı Yapma](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)
- [Şema Düğüm Türleri ve Yapısını Çıkarma Kuralları](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)
