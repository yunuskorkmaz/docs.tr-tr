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
ms.openlocfilehash: 0b504a9e368e5179d5f91faf7256445d7da47b1d
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929619"
---
# <a name="xml-child-axis-property-visual-basic"></a>XML Alt Axis Özelliği (Visual Basic)
Aşağıdakilerden birinin alt öğelere erişim sağlar: bir <xref:System.Xml.Linq.XElement> nesnesi bir <xref:System.Xml.Linq.XDocument> nesnesi, koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri ya da bir koleksiyonu <xref:System.Xml.Linq.XDocument> nesneleri.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
object.<child>  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`object`|Gerekli. Bir <xref:System.Xml.Linq.XElement> nesnesi bir <xref:System.Xml.Linq.XDocument> nesnesi, koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri ya da bir koleksiyonu <xref:System.Xml.Linq.XDocument> nesneleri.|  
|.<|Gerekli. Child axis özelliği başlangıcını gösterir.|  
|`child`|Gerekli. Adı biçiminin erişmeye alt düğümleri [`prefix``:`]`name`.<br /><br /> -   `Prefix` -İsteğe bağlı. Alt düğümü için XML ad alanı öneki. Genel XML ad alanı ile tanımlanmalıdır bir `Imports` deyimi.<br />-   `Name` -Gerekli. Yerel alt düğüm adı. Bkz: [bildirilmiş XML öğeleri ve özniteliklerinin adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
|>|Gerekli. Child axis özelliği sonunu gösterir.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri.  
  
## <a name="remarks"></a>Açıklamalar  
 Adından tarafından erişim alt düğümler için bir XML alt axis özelliği kullanabilirsiniz bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesnesi veya bir koleksiyonunu <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesneleri. XML'i `Value` özelliği döndürülen koleksiyondaki ilk alt düğüm değerine erişin. Daha fazla bilgi için [XML değeri özelliği](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
 Visual Basic derleyici çağrıları alt eksen özellikleri dönüştürür <xref:System.Xml.Linq.XContainer.Elements%2A> yöntemi.  
  
## <a name="xml-namespaces"></a>XML ad alanları  
 Child axis özelliği adı ile küresel olarak bildirilen XML ad alanı öneklerini kullanabilirsiniz `Imports` deyimi. XML ad alanı öneklerini XML öğesi değişmez değerleri içinde yerel olarak bildirilen kullanamazsınız. Daha fazla bilgi için [Imports deyimi (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte adlı alt düğümleri nasıl gösterir `phone` gelen `contact` nesne.  
  
 [!code-vb[VbXMLSamples#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_1.vb)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte adlı alt düğümleri nasıl gösterir `phone` tarafından döndürülen koleksiyondan `contact` child axis özelliği, `contacts` nesne.  
  
 [!code-vb[VbXMLSamples#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_2.vb)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bildirir `ns` olarak bir XML ad alanı öneki. XML değişmez değer oluşturun ve ilk alt düğüm tam adı ile erişmek için bir ad alanı öneki kullanır `ns:name`.  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_3.vb)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Linq.XElement>  
 [XML Eksen Özellikleri](../../../visual-basic/language-reference/xml-axis/index.md)  
 [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Visual Basic'de XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
