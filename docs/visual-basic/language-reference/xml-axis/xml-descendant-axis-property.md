---
title: XML Descendant Axis Özelliği (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Baisc]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: 02bb87235efbdef8a5474fec9799757f75877876
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="xml-descendant-axis-property-visual-basic"></a>XML Descendant Axis Özelliği (Visual Basic)
Aşağıdaki alt öğelere erişim sağlar: bir <xref:System.Xml.Linq.XElement> nesne, bir <xref:System.Xml.Linq.XDocument> nesnesi, bir koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri veya koleksiyonu <xref:System.Xml.Linq.XDocument> nesneleri.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
object...<descendant>  
```  
  
## <a name="parts"></a>Bölümler  
 `object`  
 Gerekli. Bir <xref:System.Xml.Linq.XElement> nesne, bir <xref:System.Xml.Linq.XDocument> nesnesi, bir koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri veya koleksiyonu <xref:System.Xml.Linq.XDocument> nesneleri.  
  
 ...<  
 Gerekli. Descendant axis özelliği başlangıcını gösterir.  
  
 `descendant`  
 Gerekli. Biçiminde erişmeye alt düğümlerin adı [`prefix``:`]`name`.  
  
|Bölümü|Açıklama|  
|----------|-----------------|  
|`prefix`|İsteğe bağlı. Alt düğüm için XML ad alanı öneki. Kullanılarak tanımlanmış genel bir XML ad alanı olmalıdır bir `Imports` deyimi.|  
|`name`|Gerekli. Yerel alt düğümün adı. Bkz: [bildirilmiş XML öğeleri ve özniteliklerinin adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
  
 \>  
 Gerekli. Descendant axis özelliği sonunu gösterir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri.  
  
## <a name="remarks"></a>Açıklamalar  
 XML descendant axis özelliği adından tarafından alt düğümleri erişmek için kullanabileceğiniz bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesnesi veya bir koleksiyonundan <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesneleri. XML kullanmak `Value` döndürülen koleksiyon ilk alt düğüm değerini erişmek için özellik. Daha fazla bilgi için bkz: [XML değeri özelliği](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
 Visual Basic derleyici çağrıları alt eksen özellikleri dönüştürür <xref:System.Xml.Linq.XContainer.Descendants%2A> yöntemi.  
  
## <a name="xml-namespaces"></a>XML ad alanları  
 Descendant axis özelliği adı yalnızca XML ad alanları ile genel olarak bildirilen kullanabilirsiniz `Imports` deyimi. XML öğesi değişmez içinde yerel olarak bildirilen XML ad alanları kullanamazsınız. Daha fazla bilgi için bkz: [Imports deyimi (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl adlı ilk alt düğüm değerini erişeceğinizi gösterir `name` ve tüm alt düğümlerin adlı değerleri `phone` gelen `contacts` nesnesi.  
  
 [!code-vb[VbXMLSamples#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bildirir `ns` bir XML ad alanı öneki olarak. XML değişmez değer oluşturmak ve tam adı ile ilk alt düğüm değerini erişmek için ad alanı öneki sonra kullanan `ns:name`.  
  
 [!code-vb[VbXMLSamples#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Linq.XElement>  
 [XML Eksen Özellikleri](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Visual Basic'de XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
