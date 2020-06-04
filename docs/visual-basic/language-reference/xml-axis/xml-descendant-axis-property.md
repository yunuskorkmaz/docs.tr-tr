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
ms.openlocfilehash: 52544619171dbc7034baeb5feb61395d81096387
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400259"
---
# <a name="xml-descendant-axis-property-visual-basic"></a>XML Descendant Axis Özelliği (Visual Basic)

Aşağıdakilerin alt öğeleri için erişim sağlar: <xref:System.Xml.Linq.XElement> nesne, <xref:System.Xml.Linq.XDocument> nesne, nesne koleksiyonu <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesne koleksiyonu.

## <a name="syntax"></a>Sözdizimi

```vb
object...<descendant>
```

## <a name="parts"></a>Bölümler

`object`Gerekli. <xref:System.Xml.Linq.XElement>Nesne, <xref:System.Xml.Linq.XDocument> nesne, <xref:System.Xml.Linq.XElement> nesneler koleksiyonu veya nesne koleksiyonu <xref:System.Xml.Linq.XDocument> .

`...<`Gerekli. Alt eksen özelliğinin başlangıcını gösterir.

`descendant`Gerekli. Erişmek için alt düğümlerin adı, form [ `prefix:]name` .

|Bölüm|Description|
|----------|-----------------|
|`prefix`|İsteğe bağlı. Alt düğüm için XML ad alanı öneki. Bir ifade kullanılarak tanımlanmış bir genel XML ad alanı olmalıdır `Imports` .|
|`name`|Gereklidir. Alt düğümün yerel adı. [BELIRTILEN XML öğelerinin ve özniteliklerin adlarına](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)bakın.|

`>`Gerekli. Alt eksen özelliğinin sonunu belirtir.

## <a name="return-value"></a>Dönüş Değeri

<xref:System.Xml.Linq.XElement> nesneleri topluluğu.

## <a name="remarks"></a>Açıklamalar

Alt düğümlere bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XDocument> nesnesinden veya bir <xref:System.Xml.Linq.XElement> veya nesneleri koleksiyonundan bir ad ile erışmek için bir xml alt eksen özelliği kullanabilirsiniz <xref:System.Xml.Linq.XDocument> . `Value`Döndürülen koleksiyondaki ilk alt düğümün değerine erişmek IÇIN XML özelliğini kullanın. Daha fazla bilgi için bkz. [XML Value özelliği](xml-value-property.md).

Visual Basic derleyici, alt eksen özelliklerini yöntemine yapılan çağrılara dönüştürür <xref:System.Xml.Linq.XContainer.Descendants%2A> .

## <a name="xml-namespaces"></a>XML ad alanları

Alt eksen özelliğindeki ad, ifadesiyle Global olarak belirtilen yalnızca XML ad alanlarını kullanabilir `Imports` . XML öğesi değişmez değerleri içinde yerel olarak belirtilen XML ad alanlarını kullanamaz. Daha fazla bilgi için bkz. [Imports bildirisi (XML ad alanı)](../statements/imports-statement-xml-namespace.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, adlı ilk alt düğümün değerine `name` ve nesne adındaki tüm alt düğümlerin değerlerine nasıl erişegösterdiğini gösterir `phone` `contacts` .

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

Bu kod aşağıdaki metni görüntüler:

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a>Örnek

Aşağıdaki örnek `ns` BIR XML ad alanı ön eki olarak bildirir. Daha sonra bir XML sabit değeri oluşturmak için ad alanının önekini kullanır ve ilk alt düğümün değerine tam adı ile erişin `ns:name` .

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

Bu kod aşağıdaki metni görüntüler:

`Name: Patrick Hines`

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement>
- [XML Eksen Özellikleri](index.md)
- [XML Değişmez Değerleri](../xml-literals/index.md)
- [Visual Basic'de XML Oluşturma](../../programming-guide/language-features/xml/creating-xml.md)
- [Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
