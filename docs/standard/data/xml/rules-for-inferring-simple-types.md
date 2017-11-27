---
title: "Basit türler çıkarımını yapma için kurallar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 394624d6-4da0-430a-8a88-46efe40f14de
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9a74d111720eb9436f0cd71fd5acef7ea10939c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="rules-for-inferring-simple-types"></a>Basit türler çıkarımını yapma için kurallar
Açıklar nasıl <xref:System.Xml.Schema.XmlSchemaInference> sınıfı öznitelikler ve öğeler için veri türünü oluşturur.  
  
 <xref:System.Xml.Schema.XmlSchemaInference> Sınıfı öznitelikler ve öğeler basit türler için veri türünü oluşturur. Birden çok farklı değerler şunlardır: tek bir türle mutabakatı ve nasıl şemasını tanımlama olası oluşturulursa türleri, bu bölümde açıklanmıştır `xsi` öznitelikleri işlenir.  
  
## <a name="inferred-types"></a>Çıkarsanan türleri  
 <xref:System.Xml.Schema.XmlSchemaInference> Sınıfı öğesi oluşturur ve öznitelik değerleri basit türler olarak ve sonuçta elde edilen şemada türü özniteliği içerir. Tüm basit türler türleridir sonuçlandı. Taban türleri ya da modelleri elde edilen şeması bir parçası olarak dahil edilir.  
  
 XML belgesinde karşılaşılan değerlerini ayrı ayrı incelenir. Türü için bir değer, incelenir zaman algılanır. Bir tür bir öznitelik veya bir öğe için ortaya çıkan ve öznitelik veya bir öğe için bir değer, şu anda çıkarılan türü eşleşmeyen karşılaştı <xref:System.Xml.Schema.XmlSchemaInference> sınıfın her bir kural kümesi için türü yükseltir. Bu kurallar tür yükseltme bölümünde, bu konunun ilerleyen bölümlerinde ele alınmıştır.  
  
 Aşağıdaki tabloda, sonuçta elde edilen şema için olası oluşturulursa türlerini listeler.  
  
|Basit tür|Açıklama|  
|-----------------|-----------------|  
|Boole değeri|TRUE, false, 0, 1.|  
|byte|Tamsayı aralığında 127 – 128 arasında yer.|  
|unsignedByte|0-255 aralığında tamsayılar.|  
|short|Tamsayı aralığında –32768 ile 32767 arasında yer.|  
|unsignedShort|0 ile 65535 aralığında tamsayılar.|  
|int|Tamsayı aralığında –2147483648 ile 2147483647 arasında yer.|  
|unsignedInt|0-4294967295 aralığında tamsayılar.|  
|long|Tamsayılar 9223372036854775807 –9223372036854775808 aralığı içinde.|  
|unsignedLong|Tamsayılar için 0 18446744073709551615 aralığı içinde.|  
|tamsayı|Büyük olasılıkla önekine sahip basamak sınırlı sayıda "-".|  
|decimal|0 ile 28 duyarlık için rakam sayısal değerleri.|  
|float|"E" veya "e üs temsil eden bir tamsayı değeri tarafından izlenen" tarafından ardından isteğe bağlı bir ondalık sayı. Ondalık değer 16777216-16777216 aralığında olabilir. Üs değerler 104 –149 aralığında olabilir.<br /><br /> Float sonsuz göstermek özel değerler ve sayısal olmayan tüm değerleri olanak sağlar. Kayan nokta özel değerler: 0, - 0, INF, -INF, NaN.|  
|çift|Kayan noktalı ondalık değerler dışında aynı 9007199254740992-9007199254740992 aralığında olabilir ve üs değerleri 970 –1075 aralığında olabilir.<br /><br /> Çift sonsuz göstermek özel değerler ve sayısal olmayan tüm değerleri olanak sağlar. Kayan nokta özel değerler: 0, - 0, INF, -INF, NaN.|  
|süre|W3C süre biçimi.|  
|tarih saat|W3C dateTime biçimi.|  
|zaman|W3C saat biçimi.|  
|Tarih|Yıl değerlerini 0001 9999 kısıtlanır.|  
|gYearMonth|W3C Gregoryen ay ve yıl biçimi.|  
|dize|Bir veya daha fazla Unicode karakter.|  
  
## <a name="type-promotion"></a>Tür Yükseltme  
 <xref:System.Xml.Schema.XmlSchemaInference> Sınıfı özniteliği ve öğesi değerlerine biri aynı anda inceler. Değerleri karşılaşılan gibi en kısıtlayıcı, imzasız türü algılanır. Bir tür bir öznitelik veya bir öğe için ortaya çıkan ve yeni bir değer, şu anda çıkarılan türü eşleşmeyen karşılaşılırsa, çıkarılan türü için şu anda çıkarılan türü ve yeni değer uygulanan yeni bir türe yükseltildi. <xref:System.Xml.Schema.XmlSchemaInference> Çıkarılan türü yükseltirken, sınıf önceki değerleri düşünün.  
  
 Örneğin, iki XML belgelerinden aşağıdaki XML parçaları göz önünde bulundurun:  
  
 `<MyElement1 attr1="12" />`  
  
 `<MyElement1 attr1="52344" />`  
  
 Zaman ilk `attr1` değeri karşılaştı, türü `attr1` olarak algılanır `unsignedByte` değere göre `12`. Zaman ikinci `attr1` olan karşılaştı, türü için yükseltilir `unsignedShort` şu anda oluşturulursa türüne göre `unsignedByte` geçerli değeri `52344`.  
  
 Şimdi, aşağıdaki iki XML belgelerini XML'den göz önünde bulundurun:  
  
 `<MyElement2 attr2="0" />`  
  
 `<MyElement2 attr2="true" />`  
  
 Zaman ilk `attr2` değeri karşılaştı, türü `attr2` olarak algılanır `unsignedByte` değere göre `0`. Zaman ikinci `attr2` olan karşılaştı, türü için yükseltilir `string` şu anda oluşturulursa türüne göre `unsignedByte` geçerli değeri `true` çünkü <xref:System.Xml.Schema.XmlSchemaInference> yükseltirken, sınıf önceki değerleri düşünün tür çıkarımı yapılan. Ancak, her iki örneği `attr2` aynı XML belgesinde yer alan ve iki farklı XML belgeleri yukarıda gösterildiği gibi karşılaşıldı `attr2` olarak ortaya `boolean`.  
  
### <a name="ignored-attributes-from-the-httpwwww3org2001xmlschema-instance-namespace"></a>Http://www.w3.org/2001/XMLSchema-instance Namespace yoksayılan öznitelikleri  
 Aşağıdaki şema tanımlama sırasında şema çıkarım göz ardı edilir öznitelikleri.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`xsi:type`|Bir öğe ile karşılaşıldığında `xsi:type` belirtilen `xsi:type` göz ardı edilir.|  
|`xsi:nil`|Bir öğe ile bir `xsi:nil` özniteliği ile karşılaşıldı, öğesi bildiriminden oluşturulursa şemasında değerine sahip `nillable="true"`. Bir öğesiyle bir `xsi:nil` özniteliğini `true` alt öğelere sahip olamaz.|  
|`xsi:schemaLocation`|Varsa `xsi:schemaLocation` olan karşılaştı, dikkate alınmaz.|  
|`xsi:noNamespaceSchemaLocation`|Varsa `xsi:noNamespaceSchemaLocation` olan karşılaştı, dikkate alınmaz.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML şema nesne modeli (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 [XML belgelerden şemaları çıkarımını yapma](../../../../docs/standard/data/xml/inferring-schemas-from-xml-documents.md)  
 [Şema düğüm türleri ve yapısı çıkarımını yapma için kurallar](../../../../docs/standard/data/xml/rules-for-inferring-schema-node-types-and-structure.md)
