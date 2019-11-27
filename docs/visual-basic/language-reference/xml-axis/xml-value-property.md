---
title: XML Değeri Özelliği
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
ms.openlocfilehash: 571d9130ef69df580bbba5d90bc8758b4b627196
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349415"
---
# <a name="xml-value-property-visual-basic"></a>XML Değeri Özelliği (Visual Basic)

Bir <xref:System.Xml.Linq.XElement> nesneleri koleksiyonunun ilk öğesinin değerine erişim sağlar.

## <a name="syntax"></a>Sözdizimi

```vb
object.Value
```

## <a name="parts"></a>Bölümler

|Terim|Tanım|  
|---|---|  
|`object`|Gerekli. <xref:System.Xml.Linq.XElement> nesneleri koleksiyonu.|  

## <a name="return-value"></a>Dönüş Değeri

 Koleksiyonun ilk öğesinin değerini içeren `String` veya koleksiyon boşsa `Nothing`.

## <a name="remarks"></a>Açıklamalar

 <xref:System.Xml.Linq.XElement.Value%2A> özelliği, bir <xref:System.Xml.Linq.XElement> nesneleri koleksiyonundaki ilk öğenin değerine erişmeyi kolaylaştırır. Bu özellik önce koleksiyonun en az bir nesne içerip içermediğini denetler. Koleksiyon boşsa, bu özellik `Nothing`döndürür. Aksi takdirde, bu özellik koleksiyondaki ilk öğenin <xref:System.Xml.Linq.XElement.Value%2A> özelliğinin değerini döndürür.

> [!NOTE]
> '\@' tanımlayıcısını kullanarak bir XML özniteliğinin değerine eriştiğinizde, öznitelik değeri bir `String` olarak döndürülür ve <xref:System.Xml.Linq.XAttribute.Value%2A> özelliğini açıkça belirtmeniz gerekmez.

 Bir koleksiyondaki diğer öğelere erişmek için XML uzantısı Indexer özelliğini kullanabilirsiniz. Daha fazla bilgi için bkz. [uzantı Dizin Oluşturucu özelliği](extension-indexer-property.md).

## <a name="inheritance"></a>Devralma

 Çoğu Kullanıcı <xref:System.Collections.Generic.IEnumerable%601>uygulamak zorunda olmaz ve bu nedenle bu bölümü yoksayabilirsiniz.

 <xref:System.Xml.Linq.XElement.Value%2A> özelliği, `IEnumerable(Of XElement)`uygulayan türler için bir uzantı özelliğidir. Bu uzantı özelliğinin bağlaması uzantı yöntemlerinin bağlaması gibidir: bir tür arabirimlerden birini uygular ve "Value" adlı bir özellik tanımlıyorsa, bu özellik uzantı özelliğine göre önceliğe sahiptir. Diğer bir deyişle, bu <xref:System.Xml.Linq.XElement.Value%2A> özelliği, `IEnumerable(Of XElement)`uygulayan bir sınıfta yeni bir özellik tanımlayarak geçersiz kılınabilir.

## <a name="example"></a>Örnek

 Aşağıdaki örnek, <xref:System.Xml.Linq.XElement.Value%2A> özelliğinin bir <xref:System.Xml.Linq.XElement> nesneleri koleksiyonundaki ilk düğüme erişmek için nasıl kullanılacağını gösterir. Örnek, `contact` nesnesindeki `phone` adlı tüm alt düğümlerin koleksiyonunu almak için alt eksen özelliğini kullanır.

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
