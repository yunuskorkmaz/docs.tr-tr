---
title: XML Descendant Axis Özelliği
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
ms.openlocfilehash: b2bf524214fa8ecca215d50c198b23d127e3b400
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349440"
---
# <a name="xml-descendant-axis-property-visual-basic"></a>XML Descendant Axis Özelliği (Visual Basic)

Aşağıdakilerin alt öğeleri için erişim sağlar: <xref:System.Xml.Linq.XElement> nesnesi, <xref:System.Xml.Linq.XDocument> nesnesi, <xref:System.Xml.Linq.XElement> nesneleri koleksiyonu veya <xref:System.Xml.Linq.XDocument> nesneleri koleksiyonu.

## <a name="syntax"></a>Sözdizimi

```vb
object...<descendant>
```

## <a name="parts"></a>Bölümler

`object` gerekiyor. <xref:System.Xml.Linq.XElement> nesnesi, <xref:System.Xml.Linq.XDocument> nesnesi, <xref:System.Xml.Linq.XElement> nesneleri koleksiyonu veya <xref:System.Xml.Linq.XDocument> nesneleri koleksiyonu.

`...<` gerekiyor. Alt eksen özelliğinin başlangıcını gösterir.

`descendant` gerekiyor. [`prefix:]name`biçiminde erişmek için alt düğümlerin adı.

|Bölümüyle|Açıklama|
|----------|-----------------|
|`prefix`|İsteğe bağlı. Alt düğüm için XML ad alanı öneki. Bir `Imports` ekstresi kullanılarak tanımlanmış bir genel XML ad alanı olmalıdır.|
|`name`|Gerekli. Alt düğümün yerel adı. [BELIRTILEN XML öğelerinin ve özniteliklerin adlarına](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)bakın.|

`>` gerekiyor. Alt eksen özelliğinin sonunu belirtir.

## <a name="return-value"></a>Dönüş Değeri

<xref:System.Xml.Linq.XElement> nesneleri koleksiyonu.

## <a name="remarks"></a>Açıklamalar

Alt düğümlere bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesnesinden veya <xref:System.Xml.Linq.XElement> ya da <xref:System.Xml.Linq.XDocument> nesnelerinden oluşan bir koleksiyondan ad ile erişmek için bir XML alt eksen özelliği kullanabilirsiniz. Döndürülen koleksiyondaki ilk alt düğümün değerine erişmek için XML `Value` özelliğini kullanın. Daha fazla bilgi için bkz. [XML Value özelliği](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).

Visual Basic derleyici, alt eksen özelliklerini <xref:System.Xml.Linq.XContainer.Descendants%2A> yöntemine yapılan çağrılara dönüştürür.

## <a name="xml-namespaces"></a>XML ad alanları

Alt eksen özelliğindeki ad, `Imports` ifadesiyle Global olarak belirtilen yalnızca XML ad alanlarını kullanabilir. XML öğesi değişmez değerleri içinde yerel olarak belirtilen XML ad alanlarını kullanamaz. Daha fazla bilgi için bkz. [Imports bildirisi (XML ad alanı)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, `name` adlı ilk alt düğümün değerine ve `contacts` nesnesinden `phone` adlı tüm alt düğümlerin değerlerine nasıl erişebileceğini gösterir.

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

Bu kod aşağıdaki metni görüntüler:

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a>Örnek

Aşağıdaki örnek, `ns` bir XML ad alanı öneki olarak bildirir. Daha sonra bir XML sabit değeri oluşturmak için ad alanının önekini kullanır ve `ns:name`nitelenmiş ada sahip ilk alt düğümün değerine erişir.

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

Bu kod aşağıdaki metni görüntüler:

`Name: Patrick Hines`

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement>
- [XML Eksen Özellikleri](../../../visual-basic/language-reference/xml-axis/index.md)
- [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
