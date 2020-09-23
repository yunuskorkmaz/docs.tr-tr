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
ms.openlocfilehash: 44a6c3408b57fa7f89e2834aa677fe8801ef21f3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058319"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a>XML'de Katıştırılmış İfadeler (Visual Basic)

Katıştırılmış ifadeler çalışma zamanında değerlendirilen ifadeler içeren XML sabit değerleri oluşturmanızı sağlar. Gömülü ifade için sözdizimi `<%=` `expression` `%>` , ASP.NET içinde kullanılan söz dizimi ile aynıdır.  
  
 Örneğin, katıştırılmış ifadeleri sabit metin içeriğiyle birleştiren bir XML öğesi değişmez değeri oluşturabilirsiniz.  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 Eğer `isbnNumber` 12345 tamsayısını içeriyorsa ve `modifiedDate` 3/5/2006 tarihini içeriyorsa, değeri `book` Şu şekilde olur:  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a>Katıştırılmış Ifade konumu ve doğrulama  

 Katıştırılmış ifadeler yalnızca XML sabit ifadeleri içindeki belirli konumlarda görünebilir. İfade konumu, ifadenin hangi türleri döndürebileceğini ve nasıl işlendiğini denetler `Nothing` . Aşağıdaki tabloda, eklenmiş ifadelerin izin verilen konumları ve türleri açıklanmaktadır.  
  
|Değişmez değer içindeki konum|İfade türü|İşleme `Nothing`|  
|---|---|---|  
|XML öğesi adı|<xref:System.Xml.Linq.XName>|Hata|  
|XML öğesi içeriği|`Object` veya dizisi `Object`|Yoksayıldı|  
|XML öğesi öznitelik adı|<xref:System.Xml.Linq.XName>|Öznitelik değeri de yoksa, hata `Nothing`|  
|XML öğesi öznitelik değeri|`Object`|Öznitelik bildirimi yoksayıldı|  
|XML öğesi özniteliği|<xref:System.Xml.Linq.XAttribute> veya bir koleksiyonu <xref:System.Xml.Linq.XAttribute>|Yoksayıldı|  
|XML belgesi kök öğesi|<xref:System.Xml.Linq.XElement> ya da bir <xref:System.Xml.Linq.XElement> nesne ve rastgele sayıda <xref:System.Xml.Linq.XProcessingInstruction> ve <xref:System.Xml.Linq.XComment> nesne koleksiyonu|Yoksayıldı|  
  
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
  
 `Option Strict`' I etkinleştirirseniz, derleyici her bir katıştırılmış ifadenin türünün gerekli türe widens olup olmadığını denetler. Tek özel durum, kod çalıştırıldığında doğrulanan bir XML belgesinin kök öğesi içindir. Olmadan derlerseniz `Option Strict` , türünde ifadeler ekleyebilirsiniz `Object` ve bunların türleri çalışma zamanında doğrulanır.  
  
 İçeriğin isteğe bağlı olduğu konumlarda, içeren katıştırılmış ifadeler `Nothing` yok sayılır. Bu, `Nothing` BIR XML sabit değeri kullanmadan önce öğe içeriği, öznitelik değerleri ve dizi öğelerinin olmadığını denetlemeniz gerekmediği anlamına gelir. Öğe ve öznitelik adları gibi gerekli değerler olamaz `Nothing` .  
  
 Belirli bir sabit değer türünde gömülü bir ifade kullanma hakkında daha fazla bilgi için bkz. [XML Document Literal](../../../language-reference/xml-literals/xml-document-literal.md), [XML öğesi değişmez değeri](../../../language-reference/xml-literals/xml-element-literal.md).  
  
## <a name="scoping-rules"></a>Kapsam oluşturma kuralları  

 Derleyici, her XML sabit değerini uygun değişmez değer türü için bir Oluşturucu çağrısına dönüştürür. Bir XML sabit değerinde değişmez içerik ve katıştırılmış ifadeler, oluşturucuya bağımsız değişken olarak geçirilir. Bu, bir XML sabit değeri için kullanılabilen tüm Visual Basic programlama öğelerinin katıştırılmış ifadeler tarafından da kullanılabildiği anlamına gelir.  
  
 Bir XML sabit değeri içinde, ifadesiyle belirtilen XML ad alanı öneklerine erişebilirsiniz `Imports` . Özniteliğini kullanarak bir öğesinde yeni bir XML ad alanı ön eki veya var olan bir XML ad alanı ön ekini gölgelendirebilmeniz gerekir `xmlns` . Yeni ad alanı, bu öğenin alt düğümleri için kullanılabilir ancak gömülü ifadelerde XML değişmez değerleri için kullanılamaz.  
  
> [!NOTE]
> Ad alanı özniteliğini kullanarak bir XML ad alanı öneki bildirdiğinizde `xmlns` , öznitelik değeri bir sabit dize olmalıdır. Bu şekilde, `xmlns` özniteliği kullanmak `Imports` bir XML ad alanı bildirmek için ifadesini kullanmak gibidir. XML ad alanı değerini belirtmek için gömülü bir ifade kullanamazsınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de XML Oluşturma](creating-xml.md)
- [XML Belgesi Değişmez Değeri](../../../language-reference/xml-literals/xml-document-literal.md)
- [XML Öğesi Değişmez Değeri](../../../language-reference/xml-literals/xml-element-literal.md)
- [Option Strict Deyimi](../../../language-reference/statements/option-strict-statement.md)
- [Imports Deyimi (.NET Ad Alanı ve Türü)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [XML Değişmez Değerlerine Genel Bakış](xml-literals-overview.md)
