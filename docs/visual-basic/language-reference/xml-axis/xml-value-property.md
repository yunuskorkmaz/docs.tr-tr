---
title: XML Değeri Özelliği (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
ms.openlocfilehash: 46f81e39686da30270cd67edeb4c9f2d43e048b3
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592015"
---
# <a name="xml-value-property-visual-basic"></a>XML Değeri Özelliği (Visual Basic)

@No__t-0 nesnelerinin bir koleksiyonunun ilk öğesinin değerine erişim sağlar.

## <a name="syntax"></a>Sözdizimi

```vb
object.Value
```

## <a name="parts"></a>Bölümler

|Terim|Tanım|  
|---|---|  
|`object`|Gerekli. @No__t-0 nesnelerinin koleksiyonu.|  

## <a name="return-value"></a>Dönüş Değeri

 Koleksiyonun ilk öğesinin değerini içeren `String` veya koleksiyon boşsa, `Nothing`.

## <a name="remarks"></a>Açıklamalar

 @No__t-0 özelliği, bir <xref:System.Xml.Linq.XElement> nesneleri koleksiyonundaki ilk öğenin değerine erişmeyi kolaylaştırır. Bu özellik önce koleksiyonun en az bir nesne içerip içermediğini denetler. Koleksiyon boşsa, bu özellik `Nothing` değerini döndürür. Aksi takdirde, bu özellik koleksiyondaki ilk öğenin <xref:System.Xml.Linq.XElement.Value%2A> özelliğinin değerini döndürür.

> [!NOTE]
> ' @No__t-0 ' tanımlayıcısını kullanarak bir XML özniteliğinin değerine eriştiğinizde, öznitelik değeri bir `String` olarak döndürülür ve <xref:System.Xml.Linq.XAttribute.Value%2A> özelliğini açıkça belirtmeniz gerekmez.

 Bir koleksiyondaki diğer öğelere erişmek için XML uzantısı Indexer özelliğini kullanabilirsiniz. Daha fazla bilgi için bkz. [uzantı Dizin Oluşturucu özelliği](extension-indexer-property.md).

## <a name="inheritance"></a>Devralma

 Çoğu Kullanıcı <xref:System.Collections.Generic.IEnumerable%601> ' ı uygulamak zorunda olmaz ve bu nedenle bu bölümü yoksayabilirsiniz.

 @No__t-0 özelliği, `IEnumerable(Of XElement)` ' i uygulayan türler için bir uzantı özelliğidir. Bu uzantı özelliğinin bağlaması uzantı yöntemlerinin bağlaması gibidir: bir tür arabirimlerden birini uygular ve "Value" adlı bir özellik tanımlıyorsa, bu özellik uzantı özelliğine göre önceliğe sahiptir. Diğer bir deyişle, bu <xref:System.Xml.Linq.XElement.Value%2A> özelliği, `IEnumerable(Of XElement)` uygulayan bir sınıfta yeni bir özellik tanımlayarak geçersiz kılınabilir.

## <a name="example"></a>Örnek

 Aşağıdaki örnek, <xref:System.Xml.Linq.XElement.Value%2A> özelliğinin, bir <xref:System.Xml.Linq.XElement> nesneleri koleksiyonundaki ilk düğüme erişmek için nasıl kullanılacağını gösterir. Örnek, `contact` nesnesindeki `phone` adlı tüm alt düğümlerin koleksiyonunu almak için alt eksen özelliğini kullanır.

 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]

 Bu kod aşağıdaki metni görüntüler:

 `Phone number: 206-555-0144`

## <a name="example"></a>Örnek

 Aşağıdaki örnek, bir <xref:System.Xml.Linq.XAttribute> nesneleri koleksiyonundan bir XML özniteliği değerinin nasıl alınacağını gösterir. Örnek, tüm `phone` öğeleri için `type` özniteliğinin değerini göstermek için öznitelik ekseni özelliğini kullanır.

 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]

 Bu kod aşağıdaki metni görüntüler:

 ```console
 home
 work
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [XML Eksen Özellikleri](index.md)
- [XML Değişmez Değerleri](../xml-literals/index.md)
- [Visual Basic XML oluşturma](../../programming-guide/language-features/xml/creating-xml.md)
- [Genişletme Yöntemleri](../../programming-guide/language-features/procedures/extension-methods.md)
- [Extension Indexer Özelliği](extension-indexer-property.md)
- [XML Alt Axis Özelliği](xml-child-axis-property.md)
- [XML Özniteliği Axis Özelliği](xml-attribute-axis-property.md)
