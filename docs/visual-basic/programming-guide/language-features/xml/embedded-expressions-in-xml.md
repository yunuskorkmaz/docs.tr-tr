---
title: XML'de Katıştırılmış İfadeler (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: c02b6ea0895d8b22ac71d0cb3ea6950861de47df
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678765"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a>XML'de Katıştırılmış İfadeler (Visual Basic)
Katıştırılmış ifadeler, çalışma zamanında değerlendirilen bir ifade içeren bir XML sabit değerleri oluşturmanıza olanak sağlar. Katıştırılmış bir ifade sözdizimi `<%=` `expression` `%>`, olduğu aynı söz dizimi içinde kullanılan [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)].  
  
 Örneğin, bir XML öğesi değişmez değeri katıştırılmış ifadeler sabit metin içerikli birleştirme oluşturabilirsiniz.  
  
 [!code-vb[VbXMLSamples#27](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]  
  
 Varsa `isbnNumber` 12345 tamsayı içerir ve `modifiedDate` tarihi içeren 3/5/olduğunda bu kodu yürütür, değerini 2006 `book` olan:  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a>Gömülü deyim konumu ve doğrulama  
 XML değişmez ifadelerinde içinde belirli konumlara yalnızca katıştırılmış ifadeler görünür. İfade türleri ifade konumu denetimleri döndürebilir ve nasıl `Nothing` ele alınır. Aşağıdaki tabloda, izin verilen konumlar ve katıştırılmış ifadeler türleri açıklanmaktadır.  
  
|Konumda sabit değer|İfadenin türü|İşleme `Nothing`|  
|---|---|---|  
|XML öğesi adı|<xref:System.Xml.Linq.XName>|Hata|  
|XML öğesi içeriği|`Object` veya dizi `Object`|Yoksayıldı|  
|XML öğesi öznitelik adı|<xref:System.Xml.Linq.XName>|Hata, öznitelik değeri de olmadığı sürece `Nothing`|  
|XML öğesi öznitelik değeri|`Object`|Öznitelik bildirim yoksayıldı|  
|XML öğesi özniteliği|<xref:System.Xml.Linq.XAttribute> veya bir koleksiyonu <xref:System.Xml.Linq.XAttribute>|Yoksayıldı|  
|XML belgesi kök öğesi|<xref:System.Xml.Linq.XElement> veya bir koleksiyonu <xref:System.Xml.Linq.XElement> nesne ve tercihe bağlı sayıda <xref:System.Xml.Linq.XProcessingInstruction> ve <xref:System.Xml.Linq.XComment> nesneleri|Yoksayıldı|  
  
-   Bir XML öğesinin adındaki katıştırılmış bir ifade örneği:  
  
     [!code-vb[VbXMLSamples#32](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]  
  
-   Bir XML öğesi içeriğinde katıştırılmış bir ifade örneği:  
  
     [!code-vb[VbXMLSamples#33](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]  
  
-   Bir XML öğesi öznitelik adı bir gömülü ifade örneği:  
  
     [!code-vb[VbXMLSamples#34](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]  
  
-   Gömülü deyim bir XML öğesi öznitelik değeri örneği:  
  
     [!code-vb[VbXMLSamples#35](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]  
  
-   Bir XML öğesi özniteliği katıştırılmış bir ifadede örneği:  
  
     [!code-vb[VbXMLSamples#36](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]  
  
-   Bir XML belgesi kök öğesi içinde katıştırılmış bir ifade örneği:  
  
     [!code-vb[VbXMLSamples#37](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]  
  
 Etkinleştirirseniz `Option Strict`, derleyici her katıştırılmış ifadenin türü için gerekli tür widens denetler. Tek özel durum için kod çalıştığında doğrulanır bir XML belgesi kök öğesidir. Olmadan derlerseniz `Option Strict`, türündeki ifadeler katıştırabilirsiniz `Object` ve çalışma zamanında türlerine doğrulanır.  
  
 İçeriğin bulunduğu, isteğe bağlı konumlarda içeren ifadeler katıştırılmış `Nothing` göz ardı edilir. Bunun anlamı, öznitelik değerleri, öğe içerik denetleme gerekmez ve dizi öğesi olmayan `Nothing` önce bir XML değişmez değeri kullanın. Öğe ve öznitelik adları gibi bir değer olamaz gerekli `Nothing`.  
  
 Katıştırılmış bir ifade sabit değeri belirli bir tür kullanma hakkında daha fazla bilgi için bkz. [XML belgesi değişmez değeri](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML öğesi değişmez değeri](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="scoping-rules"></a>Kapsam kuralları  
 Derleyici uygun bir değişmez değer türü için bir oluşturucu çağrısı her XML değişmez değer dönüştürür. Katıştırılmış ifadelerde XML sabit ve değişmez değer içeriğine oluşturucusuna bağımsız değişken olarak geçirilir. Başka bir deyişle, XML değişmez değer için kullanılabilir tüm Visual Basic programlama öğeleri de kendi katıştırılmış ifadeler için kullanılabilir.  
  
 XML değişmez değer içinde XML ad alanı ön ekleri ile bildirilmiş erişebileceğiniz `Imports` deyimi. Yeni bir XML ad alanı öneki bildirin veya bir öğedeki kullanarak varolan bir XML ad alanı öneki gölge `xmlns` özniteliği. Yeni ad alanı, o öğenin alt düğümleri, ancak XML değişmez değerlerine katıştırılmış ifadeler kullanılabilir.  
  
> [!NOTE]
>  Kullanarak bir XML ad alanı öneki bildirdiğinizde `xmlns` namespace özniteliği, öznitelik değeri bir sabit dize olmalıdır. Bu bağlamda kullanarak `xmlns` özniteliktir kullanma gibi `Imports` deyimi bir XML ad alanı bildirmek için. XML ad alanı değeri belirtmek için bir katıştırılmış deyim kullanamazsınız.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Visual Basic'de XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML Belgesi Değişmez Değeri](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [XML Öğesi Değişmez Değeri](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [XML Değişmez Değerlerine Genel Bakış](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
