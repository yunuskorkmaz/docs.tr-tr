---
title: XML Belgesi Değişmez Değeri
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
ms.openlocfilehash: 3a2182d2937827bc8dc45e22307a3668420261a2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400208"
---
# <a name="xml-document-literal-visual-basic"></a>XML Belgesi Değişmez Değeri (Visual Basic)
Bir nesneyi temsil eden sabit değer <xref:System.Xml.Linq.XDocument> .  
  
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
|`encoding`|İsteğe bağlı. Belgenin hangi kodlamayla kullandığını bildiren değişmez metin.|  
|`standalone`|İsteğe bağlı. Değişmez değer metni. "Yes" veya "No" olmalıdır.|  
|`piCommentList`|İsteğe bağlı. XML işleme yönergelerinin ve XML açıklamalarının listesi. Aşağıdaki biçimi alır:<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> Her biri `piComment` aşağıdakilerden biri olabilir:<br /><br /> -   [XML Işleme yönergesi sabit değeri](xml-processing-instruction-literal.md).<br />-   [XML açıklama değişmez değeri](xml-comment-literal.md).|  
|`rootElement`|Gereklidir. Belgenin kök öğesi. Biçim aşağıdakilerden biridir:<br /><br /> <ul><li>[XML öğesi değişmez değeri](xml-element-literal.md).</li><li>Formun katıştırılmış ifadesi `<%=` `elementExp` `%>` . , Aşağıdakilerden `elementExp` birini döndürür:<br /><br /> <ul><li>Bir <xref:System.Xml.Linq.XElement> nesnesi.</li><li>Bir <xref:System.Xml.Linq.XElement> nesne ve herhangi bir sayıda ve nesne içeren bir <xref:System.Xml.Linq.XProcessingInstruction> koleksiyon <xref:System.Xml.Linq.XComment> .</li></ul></li></ul><br /> Daha fazla bilgi için bkz. [XML 'de katıştırılmış ifadeler](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir <xref:System.Xml.Linq.XDocument> nesnesi.  
  
## <a name="remarks"></a>Açıklamalar  
 XML belgesi değişmez değeri, değişmez değerin başlangıcında XML bildirimi tarafından tanımlanır. Her XML belgesi değişmez değeri tam olarak bir kök XML öğesi içermelidir, ancak herhangi bir sayıda XML işleme yönergesi ve XML açıklaması olabilir.  
  
 XML belgesi değişmez değeri bir XML öğesinde görünemez.  
  
> [!NOTE]
> Bir XML sabit değeri, satır devamlılık karakterleri kullanmadan birden fazla satıra yayılabilir. Bu sayede bir XML belgesinden içerik kopyalayabilir ve doğrudan bir Visual Basic programına yapıştırabilirsiniz.  
  
 Visual Basic derleyici, XML belgesi değişmez değerini <xref:System.Xml.Linq.XDocument.%23ctor%2A> ve oluşturuculara çağrılarına dönüştürür <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir XML bildirimi, işleme yönergesi, açıklama ve başka bir öğesi içeren bir öğesi olan bir XML belgesi oluşturur.  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [XML İşleme Talimatı Değişmez Değeri](xml-processing-instruction-literal.md)
- [XML Açıklama Değişmez Değeri](xml-comment-literal.md)
- [XML Öğesi Değişmez Değeri](xml-element-literal.md)
- [XML Değişmez Değerleri](index.md)
- [Visual Basic'de XML Oluşturma](../../programming-guide/language-features/xml/creating-xml.md)
- [XML'de Katıştırılmış İfadeler](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
