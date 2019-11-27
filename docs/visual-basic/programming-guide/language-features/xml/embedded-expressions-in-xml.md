---
title: XML'de Katıştırılmış İfadeler
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: 0cdb960160457108ddf18c554dae5f5993269833
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332347"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a>XML'de Katıştırılmış İfadeler (Visual Basic)
Katıştırılmış ifadeler çalışma zamanında değerlendirilen ifadeler içeren XML sabit değerleri oluşturmanızı sağlar. Gömülü bir ifade için sözdizimi, ASP.NET içinde kullanılan sözdizimiyle aynı olan `<%=` `expression` `%>`.  
  
 Örneğin, katıştırılmış ifadeleri sabit metin içeriğiyle birleştiren bir XML öğesi değişmez değeri oluşturabilirsiniz.  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 `isbnNumber` 12345 tamsayısını içeriyorsa ve `modifiedDate` 3/5/2006 tarihini içeriyorsa, bu kod yürütüldüğünde `book` değeri şu olur:  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a>Katıştırılmış Ifade konumu ve doğrulama  
 Katıştırılmış ifadeler yalnızca XML sabit ifadeleri içindeki belirli konumlarda görünebilir. İfade konumu, ifadenin hangi türleri döndürebileceğini ve `Nothing` nasıl işleneceğini denetler. Aşağıdaki tabloda, eklenmiş ifadelerin izin verilen konumları ve türleri açıklanmaktadır.  
  
|Değişmez değer içindeki konum|İfade türü|`Nothing` işleme|  
|---|---|---|  
|XML öğesi adı|<xref:System.Xml.Linq.XName>|Hata|  
|XML öğesi içeriği|`Object` `Object` veya dizisi|Yoksayıldı|  
|XML öğesi öznitelik adı|<xref:System.Xml.Linq.XName>|Öznitelik değeri de `Nothing` olmadığı takdirde hata|  
|XML öğesi öznitelik değeri|`Object`|Öznitelik bildirimi yoksayıldı|  
|XML öğesi özniteliği|<xref:System.Xml.Linq.XAttribute> veya <xref:System.Xml.Linq.XAttribute> koleksiyonu|Yoksayıldı|  
|XML belgesi kök öğesi|<xref:System.Xml.Linq.XElement> veya bir <xref:System.Xml.Linq.XElement> nesnesi koleksiyonu ve rastgele sayıda <xref:System.Xml.Linq.XProcessingInstruction> ve <xref:System.Xml.Linq.XComment> nesnesi|Yoksayıldı|  
  
- Bir XML öğe adında katıştırılmış ifade örneği:  
  
     [!code-vb[VbXMLSamples#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#32)]  
  
- XML öğesi içeriğinde gömülü ifade örneği:  
  
     [!code-vb[VbXMLSamples#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#33)]  
  
- XML öğesi öznitelik adında gömülü ifade örneği:  
  
     [!code-vb[VbXMLSamples#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#34)]  
  
- XML öğesi öznitelik değerinde gömülü ifade örneği:  
  
     [!code-vb[VbXMLSamples#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#35)]  
  
- XML öğesi özniteliğinde gömülü ifade örneği:  
  
     [!code-vb[VbXMLSamples#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#36)]  
  
- XML belgesi kök öğesinde katıştırılmış ifade örneği:  
  
     [!code-vb[VbXMLSamples#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#37)]  
  
 `Option Strict`etkinleştirirseniz derleyici, her bir katıştırılmış ifadenin türünün gerekli türe widens olup olmadığını denetler. Tek özel durum, kod çalıştırıldığında doğrulanan bir XML belgesinin kök öğesi içindir. `Option Strict`olmadan derlerseniz, `Object` türünde ifadeler ekleyebilirsiniz ve bu tür çalışma zamanında doğrulanır.  
  
 İçeriğin isteğe bağlı olduğu konumlarda `Nothing` içeren katıştırılmış ifadeler yok sayılır. Bu, bir XML sabit değeri kullanmadan önce öğe içeriği, öznitelik değerleri ve dizi öğelerinin `Nothing` olmadığını denetlemeniz gerekmediği anlamına gelir. Öğe ve öznitelik adları gibi gerekli değerler `Nothing`olamaz.  
  
 Belirli bir sabit değer türünde gömülü bir ifade kullanma hakkında daha fazla bilgi için bkz. [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML öğesi değişmez değeri](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="scoping-rules"></a>Kapsam oluşturma kuralları  
 Derleyici, her XML sabit değerini uygun değişmez değer türü için bir Oluşturucu çağrısına dönüştürür. Bir XML sabit değerinde değişmez içerik ve katıştırılmış ifadeler, oluşturucuya bağımsız değişken olarak geçirilir. Bu, bir XML sabit değeri için kullanılabilen tüm Visual Basic programlama öğelerinin katıştırılmış ifadeler tarafından da kullanılabildiği anlamına gelir.  
  
 Bir XML sabit değeri içinde, `Imports` ifadesiyle belirtilen XML ad alanı öneklerine erişebilirsiniz. Yeni bir XML ad alanı öneki bildirebilir veya var olan bir XML ad alanı önekini, `xmlns` özniteliğini kullanarak bir öğede gölgelendirebilir. Yeni ad alanı, bu öğenin alt düğümleri için kullanılabilir ancak gömülü ifadelerde XML değişmez değerleri için kullanılamaz.  
  
> [!NOTE]
> `xmlns` ad alanı özniteliğini kullanarak bir XML ad alanı öneki bildirdiğinizde, öznitelik değeri bir sabit dize olmalıdır. Bu şekilde, `xmlns` özniteliği kullanmak bir XML ad alanı bildirmek için `Imports` bildirimini kullanmaktır. XML ad alanı değerini belirtmek için gömülü bir ifade kullanamazsınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML Belgesi Değişmez Değeri](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [XML Öğesi Değişmez Değeri](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [XML Değişmez Değerlerine Genel Bakış](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
