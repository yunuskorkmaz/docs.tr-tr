---
title: XML Belgesi Değişmez Değeri (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d5c84fecbb035c229cc3576bc556db6ecb6f3934
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="xml-document-literal-visual-basic"></a>XML Belgesi Değişmez Değeri (Visual Basic)
Değişmez değer gösteren bir <xref:System.Xml.Linq.XDocument> nesnesi.  
  
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
|`standalone`|İsteğe bağlı. Düz metin. "Evet" olması gerekir veya "Hayır".|  
|`piCommentList`|İsteğe bağlı. XML işleme yönergeleri ve XML açıklamaları listesi. Şu biçimi alır:<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> Her `piComment` şunlardan biri olabilir:<br /><br /> -   [XML işleme talimatı değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).<br />-   [XML açıklama değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).|  
|`rootElement`|Gerekli. Belgenin kök öğesi. Aşağıdakilerden birini biçimdedir:<br /><br /> <ul><li>[XML öğesi değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md).</li><li>İfade biçiminde katıştırılmış `<%=` `elementExp` `%>`. `elementExp` Aşağıdakilerden birini döndürür:<br /><br /> <ul><li>Bir <xref:System.Xml.Linq.XElement> nesnesi.</li><li>Birini içeren bir koleksiyon <xref:System.Xml.Linq.XElement> nesne ve herhangi bir sayıda <xref:System.Xml.Linq.XProcessingInstruction> ve <xref:System.Xml.Linq.XComment> nesneleri.</li></ul></li></ul><br /> Daha fazla bilgi için bkz: [XML'de katıştırılmış ifadeler](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir <xref:System.Xml.Linq.XDocument> nesnesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Değişmez değer bir XML belgesi değişmez değeri başlangıç XML bildirimi tarafından tanımlanır. Her bir XML belgesi değişmez değeri tam olarak bir kök XML öğesi sahip olmanız gerekir, ancak herhangi bir sayıda XML işleme yönergeleri ve XML açıklamaları olabilir.  
  
 Bir XML belgesi değişmez değeri bir XML öğesi yer alamaz.  
  
> [!NOTE]
>  XML değişmez değer, satır devamlılığı karakterleri kullanmadan birden fazla satır yayılabilir. Bu, bir XML belgesinden içeriği Kopyala ve doğrudan bir Visual Basic programa yapıştırmasını sağlar.  
  
 Visual Basic derleyici çağrıları XML belgesi değişmez değeri dönüştürür <xref:System.Xml.Linq.XDocument.%23ctor%2A> ve <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> oluşturucular.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir XML bildirimi, bir işleme yönergesi, açıklama ve başka bir öğe içeren bir öğeyi içeren bir XML belgesi oluşturur.  
  
 [!code-vb[VbXMLSamples#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-document-literal_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Linq.XElement>  
 <xref:System.Xml.Linq.XProcessingInstruction>  
 <xref:System.Xml.Linq.XComment>  
 <xref:System.Xml.Linq.XDocument>  
 [XML İşleme Talimatı Değişmez Değeri](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)  
 [XML Açıklama Değişmez Değeri](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)  
 [XML Öğesi Değişmez Değeri](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Visual Basic'de XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [XML'de Katıştırılmış İfadeler](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
