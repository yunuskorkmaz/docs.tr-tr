---
title: XML Alt Axis Özelliği (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyChildAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 89a59d00-985e-4f5c-b59f-29b47bad11cb
ms.openlocfilehash: 88d0b1f315bc1bb9dc474604d222a8ebcc1e40aa
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582234"
---
# <a name="xml-child-axis-property-visual-basic"></a>XML Alt Axis Özelliği (Visual Basic)
Aşağıdakilerden birinin alt öğelerine erişim sağlar: <xref:System.Xml.Linq.XElement> nesnesi, <xref:System.Xml.Linq.XDocument> nesnesi, <xref:System.Xml.Linq.XElement> nesneleri koleksiyonu veya <xref:System.Xml.Linq.XDocument> nesneleri koleksiyonu.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
object.<child>  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`object`|Gerekli. @No__t_0 nesnesi, <xref:System.Xml.Linq.XDocument> nesnesi, <xref:System.Xml.Linq.XElement> nesneleri koleksiyonu veya <xref:System.Xml.Linq.XDocument> nesneleri koleksiyonu.|  
|. <|Gerekli. Bir alt eksen özelliğinin başlangıcını gösterir.|  
|`child`|Gerekli. [@No__t_0 biçiminde erişmek için alt düğümlerin adı.<br /><br /> -    `Prefix`-Isteğe bağlı. Alt düğüm için XML ad alanı ön eki. Bir `Imports` ifadesiyle tanımlanmış bir genel XML ad alanı olmalıdır.<br />-    `Name`-gerekli. Yerel alt düğüm adı. [BELIRTILEN XML öğelerinin ve özniteliklerin adlarına](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)bakın.|  
|>|Gerekli. Alt eksen özelliğinin sonunu belirtir.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 @No__t_0 nesneleri koleksiyonu.  
  
## <a name="remarks"></a>Açıklamalar  
 Alt düğümlere bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesnesinden veya <xref:System.Xml.Linq.XElement> ya da <xref:System.Xml.Linq.XDocument> nesnelerinden oluşan bir koleksiyondan ad ile erişmek için bir XML alt eksen özelliği kullanabilirsiniz. Döndürülen koleksiyondaki ilk alt düğümün değerine erişmek için XML `Value` özelliğini kullanın. Daha fazla bilgi için bkz. [XML Value özelliği](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
 Visual Basic Derleyicisi alt eksen özelliklerini <xref:System.Xml.Linq.XContainer.Elements%2A> yöntemine yapılan çağrılara dönüştürür.  
  
## <a name="xml-namespaces"></a>XML ad alanları  
 Bir alt eksen özelliğindeki ad, `Imports` ifadesiyle Global olarak belirtilen yalnızca XML ad alanı öneklerini kullanabilir. XML öğesi değişmez değerleri içinde yerel olarak belirtilen XML ad alanı öneklerini kullanamaz. Daha fazla bilgi için bkz. [Imports bildirisi (XML ad alanı)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `contact` nesnesinden `phone` adlı alt düğümlere nasıl erişebileceğiniz gösterilmektedir.  
  
 [!code-vb[VbXMLSamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#17)]  
  
 Bu kod aşağıdaki metni görüntüler:  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `contacts` nesnesinin `contact` alt eksen özelliği tarafından döndürülen koleksiyondan `phone` adlı alt düğümlere nasıl erişebileceğiniz gösterilmektedir.  
  
 [!code-vb[VbXMLSamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#18)]  
  
 Bu kod aşağıdaki metni görüntüler:  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `ns` bir XML ad alanı öneki olarak bildirir. Daha sonra bir XML sabit değeri oluşturmak için ad alanının önekini kullanır ve `ns:name` nitelenmiş ada sahip ilk alt düğüme erişir.  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 Bu kod aşağıdaki metni görüntüler:  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement>
- [XML Eksen Özellikleri](../../../visual-basic/language-reference/xml-axis/index.md)
- [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
