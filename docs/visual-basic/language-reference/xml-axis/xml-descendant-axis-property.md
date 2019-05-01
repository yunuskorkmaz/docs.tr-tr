---
title: XML Descendant Axis Özelliği (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Basic]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: bc1dff6dc3b580079087f370212b7d3acd30e4fb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938677"
---
# <a name="xml-descendant-axis-property-visual-basic"></a>XML Descendant Axis Özelliği (Visual Basic)

Aşağıdaki alt öğeleri için erişim sağlar: bir <xref:System.Xml.Linq.XElement> nesnesi bir <xref:System.Xml.Linq.XDocument> nesnesi, koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri ya da bir koleksiyonu <xref:System.Xml.Linq.XDocument> nesneleri.

## <a name="syntax"></a>Sözdizimi

```
object...<descendant>
```

## <a name="parts"></a>Bölümler

`object` Gerekli. Bir <xref:System.Xml.Linq.XElement> nesnesi bir <xref:System.Xml.Linq.XDocument> nesnesi, koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri ya da bir koleksiyonu <xref:System.Xml.Linq.XDocument> nesneleri.

`...<` Gerekli. Descendant axis özelliği başlangıcını gösterir.

`descendant` Gerekli. Adı biçiminin erişmeye alt düğümleri [`prefix:]name`.

|Bölümü|Açıklama|
|----------|-----------------|
|`prefix`|İsteğe bağlı. Alt düğümü için XML ad alanı öneki. Tarafından tanımlanan genel bir XML ad alanı olmalıdır bir `Imports` deyimi.|
|`name`|Gerekli. Alt düğümü yerel adı. Bkz: [bildirilmiş XML öğeleri ve özniteliklerinin adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|

`>` Gerekli. Descendant axis özelliği sonunu gösterir.

## <a name="return-value"></a>Dönüş Değeri

Bir koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri.

## <a name="remarks"></a>Açıklamalar

Bir XML descendant axis özelliği tarafından adından alt düğümleri erişmek için kullanabileceğiniz bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesnesi veya bir koleksiyonunu <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesneleri. XML'i `Value` özelliği döndürülen koleksiyondaki ilk alt düğümü değerine erişin. Daha fazla bilgi için [XML değeri özelliği](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).

Visual Basic derleyici çağrıları alt eksen özellikleri dönüştürür <xref:System.Xml.Linq.XContainer.Descendants%2A> yöntemi.

## <a name="xml-namespaces"></a>XML ad alanları

Descendant axis özelliği adı yalnızca XML ad alanları ile küresel olarak bildirilen kullanabilirsiniz `Imports` deyimi. XML ad alanları XML öğesi değişmez değerleri içinde yerel olarak bildirilen kullanamazsınız. Daha fazla bilgi için [Imports deyimi (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).

## <a name="example"></a>Örnek

Aşağıdaki örnekte adlı ilk alt düğüm değerine erişin gösterilmiştir `name` ve tüm alt düğümleri adlı değerlerini `phone` gelen `contacts` nesne.

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

Bu kod, aşağıdaki metni görüntüler:

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a>Örnek

Aşağıdaki örnek bildirir `ns` olarak bir XML ad alanı öneki. XML değişmez değer oluşturun ve nitelikli ada sahip ilk alt düğüm değerini erişmek için ad alanı öneki kullanır `ns:name`.

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

Bu kod, aşağıdaki metni görüntüler:

`Name: Patrick Hines`

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement>
- [XML Eksen Özellikleri](../../../visual-basic/language-reference/xml-axis/index.md)
- [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic'de XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
