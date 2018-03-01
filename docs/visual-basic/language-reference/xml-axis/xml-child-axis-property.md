---
title: "XML Alt Axis Özelliği (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyChildAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 89a59d00-985e-4f5c-b59f-29b47bad11cb
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ea4db763bbed651a01845b49395255586cb60113
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-child-axis-property-visual-basic"></a>XML Alt Axis Özelliği (Visual Basic)
Aşağıdaki alt erişim sağlar: bir <xref:System.Xml.Linq.XElement> nesne, bir <xref:System.Xml.Linq.XDocument> nesnesi, bir koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri veya koleksiyonu <xref:System.Xml.Linq.XDocument> nesneleri.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
object.<child>  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`object`|Gerekli. Bir <xref:System.Xml.Linq.XElement> nesne, bir <xref:System.Xml.Linq.XDocument> nesnesi, bir koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri veya koleksiyonu <xref:System.Xml.Linq.XDocument> nesneleri.|  
|.<|Gerekli. Child axis özelliği başlangıcını gösterir.|  
|`child`|Gerekli. Biçiminde erişmeye alt düğümlerin adı [`prefix``:`]`name`.<br /><br /> -   `Prefix`-İsteğe bağlı. Alt düğüm için XML ad alanı öneki. Genel bir XML ad alanı ile tanımlanmalıdır bir `Imports` deyimi.<br />-   `Name`-Gerekli. Yerel alt düğüm adı. Bkz: [bildirilmiş XML öğeleri ve özniteliklerinin adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
|>|Gerekli. Child axis özelliği sonunu gösterir.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri.  
  
## <a name="remarks"></a>Açıklamalar  
 Adından tarafından erişim alt düğümler için bir XML alt axis özelliği kullanabilirsiniz bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesnesi veya bir koleksiyonundan <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesneleri. XML kullanmak `Value` döndürülen koleksiyon ilk alt düğüm değerini erişmek için özellik. Daha fazla bilgi için bkz: [XML değeri özelliği](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Derleyici çağrıları alt eksen özellikleri dönüştürür <xref:System.Xml.Linq.XContainer.Elements%2A> yöntemi.  
  
## <a name="xml-namespaces"></a>XML ad alanları  
 Child axis özelliği adı ile genel olarak bildirilen XML ad alanı önekleri kullanabilirsiniz `Imports` deyimi. XML ad alanı önekleri XML öğesi değişmez içinde yerel olarak bildirilen kullanamazsınız. Daha fazla bilgi için bkz: [Imports deyimi (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl adlı alt düğümleri erişeceğinizi gösterir `phone` gelen `contact` nesnesi.  
  
 [!code-vb[VbXMLSamples#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_1.vb)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl adlı alt düğümleri erişeceğinizi gösterir `phone` tarafından döndürülen koleksiyonundan `contact` child axis özelliği, `contacts` nesnesi.  
  
 [!code-vb[VbXMLSamples#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_2.vb)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bildirir `ns` bir XML ad alanı öneki olarak. XML değişmez değer oluşturmak ve ilk alt düğüm tam adı ile erişmek için ad alanı öneki sonra kullanan `ns:name`.  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_3.vb)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Linq.XElement>  
 [XML eksen özellikleri](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [XML değişmez değerleri](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Visual Basic'de XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Bildirilmiş XML öğeleri ve özniteliklerinin adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
