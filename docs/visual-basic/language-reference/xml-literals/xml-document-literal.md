---
title: XML Belgesi Değişmez Değeri (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
ms.openlocfilehash: f58c1365e145166dfe122d455854d44526300a1e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814633"
---
# <a name="xml-document-literal-visual-basic"></a>XML Belgesi Değişmez Değeri (Visual Basic)
Bir değişmez değer temsil eden bir <xref:System.Xml.Linq.XDocument> nesne.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`encoding`|İsteğe bağlı. Metin kodlama hangi belge bildirme kullanır.|  
|`standalone`|İsteğe bağlı. Değişmez değer metni. "Evet" olmalıdır veya "Hayır".|  
|`piCommentList`|İsteğe bağlı. XML işleme yönergeleri ve XML açıklamaları listesi. Aşağıdaki biçimi alır:<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> Her `piComment` aşağıdakilerden biri olabilir:<br /><br /> -   [XML işleme talimatı değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).<br />-   [XML açıklama değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).|  
|`rootElement`|Gerekli. Belgenin kök öğesi. Biçim aşağıdakilerden biridir:<br /><br /> <ul><li>[XML öğesi değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</li><li>Gömülü deyim `<%=` `elementExp` `%>`. `elementExp` Aşağıdakilerden birini döndürür:<br /><br /> <ul><li>Bir <xref:System.Xml.Linq.XElement> nesne.</li><li>Birini içeren bir koleksiyon <xref:System.Xml.Linq.XElement> nesne ve herhangi bir sayıda <xref:System.Xml.Linq.XProcessingInstruction> ve <xref:System.Xml.Linq.XComment> nesneleri.</li></ul></li></ul><br /> Daha fazla bilgi için [XML'de katıştırılmış ifadeler](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir <xref:System.Xml.Linq.XDocument> nesne.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir XML belgesi değişmez değeri, değişmez değerin başında XML bildirimi tarafından tanımlanır. Her bir XML belgesi değişmez değeri tam olarak bir kök XML öğesi var olmalıdır, ancak herhangi bir sayıda XML işleme yönergeleri ve XML açıklamaları sahip olabilir.  
  
 Bir XML belgesi değişmez değeri bir XML öğesi bulunamaz.  
  
> [!NOTE]
>  XML değişmez değer birden fazla satır, satır devamlılığı karakteri kullanmadan yayılabilir. Bu içerik bir XML belgesinden kopyalayıp bir Visual Basic programa doğrudan yapıştırın olanak sağlar.  
  
 Visual Basic derleyici çağrıları XML belgesi değişmez değeri dönüştürür <xref:System.Xml.Linq.XDocument.%23ctor%2A> ve <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> oluşturucular.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir XML bildirimi, bir işlem yönergesi, bir açıklama ve başka bir öğe içeren bir öğeyi içeren bir XML belgesi oluşturur.  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [XML İşleme Talimatı Değişmez Değeri](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)
- [XML Açıklama Değişmez Değeri](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [XML Öğesi Değişmez Değeri](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic'de XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML'de Katıştırılmış İfadeler](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
