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
ms.openlocfilehash: 525fa04db86a299d88e1612aac76d014f35124eb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922627"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a>XML'de Katıştırılmış İfadeler (Visual Basic)
Katıştırılmış ifadeler çalışma zamanında değerlendirilen ifadeler içeren XML sabit değerleri oluşturmanızı sağlar. Gömülü ifade `<%=` `expression` içinsözdizimi,ASP.NETiçindekullanılansöz`%>`dizimi ile aynıdır.  
  
 Örneğin, katıştırılmış ifadeleri sabit metin içeriğiyle birleştiren bir XML öğesi değişmez değeri oluşturabilirsiniz.  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 Eğer `isbnNumber` 12345 tamsayısını içeriyorsa ve `modifiedDate` 3/5/2006 tarihini içeriyorsa, değeri `book` şu şekilde olur:  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a>Katıştırılmış Ifade konumu ve doğrulama  
 Katıştırılmış ifadeler yalnızca XML sabit ifadeleri içindeki belirli konumlarda görünebilir. İfade konumu, ifadenin hangi türleri döndürebileceğini ve nasıl `Nothing` işlendiğini denetler. Aşağıdaki tabloda, eklenmiş ifadelerin izin verilen konumları ve türleri açıklanmaktadır.  
  
|Değişmez değer içindeki konum|İfade türü|İşleme`Nothing`|  
|---|---|---|  
|XML öğesi adı|<xref:System.Xml.Linq.XName>|Hata|  
|XML öğesi içeriği|`Object`veya dizisi`Object`|Yoksayıldı|  
|XML öğesi öznitelik adı|<xref:System.Xml.Linq.XName>|Öznitelik değeri de yoksa, hata`Nothing`|  
|XML öğesi öznitelik değeri|`Object`|Öznitelik bildirimi yoksayıldı|  
|XML öğesi özniteliği|<xref:System.Xml.Linq.XAttribute>veya bir koleksiyonu<xref:System.Xml.Linq.XAttribute>|Yoksayıldı|  
|XML belgesi kök öğesi|<xref:System.Xml.Linq.XElement>ya da bir <xref:System.Xml.Linq.XElement> nesne ve rastgele <xref:System.Xml.Linq.XProcessingInstruction> sayıda ve <xref:System.Xml.Linq.XComment> nesne koleksiyonu|Yoksayıldı|  
  
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
  
 ' I etkinleştirirseniz `Option Strict`, derleyici her bir katıştırılmış ifadenin türünün gerekli türe widens olup olmadığını denetler. Tek özel durum, kod çalıştırıldığında doğrulanan bir XML belgesinin kök öğesi içindir. Olmadan `Option Strict`derlerseniz, türünde `Object` ifadeler ekleyebilirsiniz ve bunların türleri çalışma zamanında doğrulanır.  
  
 İçeriğin isteğe bağlı olduğu konumlarda, içeren katıştırılmış ifadeler `Nothing` yok sayılır. Bu, bir XML sabit değeri kullanmadan `Nothing` önce öğe içeriği, öznitelik değerleri ve dizi öğelerinin olmadığını denetlemeniz gerekmediği anlamına gelir. Öğe ve öznitelik adları `Nothing`gibi gerekli değerler olamaz.  
  
 Belirli bir sabit değer türünde gömülü bir ifade kullanma hakkında daha fazla bilgi için bkz. [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md), [XML öğesi değişmez değeri](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="scoping-rules"></a>Kapsam oluşturma kuralları  
 Derleyici, her XML sabit değerini uygun değişmez değer türü için bir Oluşturucu çağrısına dönüştürür. Bir XML sabit değerinde değişmez içerik ve katıştırılmış ifadeler, oluşturucuya bağımsız değişken olarak geçirilir. Bu, bir XML sabit değeri için kullanılabilen tüm Visual Basic programlama öğelerinin katıştırılmış ifadeler tarafından da kullanılabildiği anlamına gelir.  
  
 Bir XML sabit değeri içinde, `Imports` ifadesiyle belirtilen xml ad alanı öneklerine erişebilirsiniz. `xmlns` Özniteliğini kullanarak bir öğesinde yeni bir XML ad alanı ön eki veya var olan bir XML ad alanı ön ekini gölgelendirebilmeniz gerekir. Yeni ad alanı, bu öğenin alt düğümleri için kullanılabilir ancak gömülü ifadelerde XML değişmez değerleri için kullanılamaz.  
  
> [!NOTE]
> `xmlns` Ad alanı özniteliğini kullanarak bir XML ad alanı öneki bildirdiğinizde, öznitelik değeri bir sabit dize olmalıdır. Bu şekilde, `xmlns` özniteliği kullanmak bir XML ad alanı bildirmek için `Imports` ifadesini kullanmak gibidir. XML ad alanı değerini belirtmek için gömülü bir ifade kullanamazsınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML Belgesi Değişmez Değeri](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [XML Öğesi Değişmez Değeri](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [XML Değişmez Değerlerine Genel Bakış](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
