---
description: 'Daha fazla bilgi edinin: XML değeri özelliği (Visual Basic)'
title: XML Value Özelliği
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
ms.openlocfilehash: 49762c1fcc0059472a5be11726aa344a001807ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768772"
---
# <a name="xml-value-property-visual-basic"></a>XML Değeri Özelliği (Visual Basic)

Bir nesne koleksiyonunun ilk öğesinin değerine erişim sağlar <xref:System.Xml.Linq.XElement> .

## <a name="syntax"></a>Syntax

```vb
object.Value
```

## <a name="parts"></a>Bölümler

|Süre|Tanım|  
|---|---|  
|`object`|Gereklidir. Nesne koleksiyonu <xref:System.Xml.Linq.XElement> .|  

## <a name="return-value"></a>Dönüş Değeri

 `String`Koleksiyonun ilk öğesinin değerini içeren bir veya `Nothing` Koleksiyon boşsa.

## <a name="remarks"></a>Açıklamalar

 <xref:System.Xml.Linq.XElement.Value%2A>Özelliği, bir nesne koleksiyonundaki ilk öğenin değerine erişmeyi kolaylaştırır <xref:System.Xml.Linq.XElement> . Bu özellik önce koleksiyonun en az bir nesne içerip içermediğini denetler. Koleksiyon boşsa, bu özellik döndürür `Nothing` . Aksi takdirde, bu özellik <xref:System.Xml.Linq.XElement.Value%2A> koleksiyondaki ilk öğenin özelliğinin değerini döndürür.

> [!NOTE]
> Bir XML özniteliğinin değerine ' \@ ' tanımlayıcısını kullanarak eriştiğinizde, öznitelik değeri bir olarak döndürülür `String` ve özelliği açıkça belirtmeniz gerekmez <xref:System.Xml.Linq.XAttribute.Value%2A> .

 Bir koleksiyondaki diğer öğelere erişmek için XML uzantısı Indexer özelliğini kullanabilirsiniz. Daha fazla bilgi için bkz. [uzantı Dizin Oluşturucu özelliği](extension-indexer-property.md).

## <a name="inheritance"></a>Devralma

 Çoğu kullanıcının uygulaması <xref:System.Collections.Generic.IEnumerable%601> ve bu bölümü yoksayması gerekmez.

 <xref:System.Xml.Linq.XElement.Value%2A>Özelliği, uygulayan türler için bir genişletme özelliğidir `IEnumerable(Of XElement)` . Bu uzantı özelliğinin bağlaması uzantı yöntemlerinin bağlaması gibidir: bir tür arabirimlerden birini uygular ve "Value" adlı bir özellik tanımlıyorsa, bu özellik uzantı özelliğine göre önceliğe sahiptir. Diğer bir deyişle, bu <xref:System.Xml.Linq.XElement.Value%2A> özellik, uygulayan bir sınıfta yeni bir özellik tanımlayarak geçersiz kılınabilir `IEnumerable(Of XElement)` .

## <a name="example"></a>Örnek

 Aşağıdaki örnek, <xref:System.Xml.Linq.XElement.Value%2A> bir nesne koleksiyonundaki ilk düğüme erişmek için özelliğinin nasıl kullanılacağını gösterir <xref:System.Xml.Linq.XElement> . Örnek, nesnesinde olan adlı tüm alt düğümlerin koleksiyonunu almak için alt eksen özelliğini kullanır `phone` `contact` .

 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]

 Bu kod aşağıdaki metni görüntüler:

 `Phone number: 206-555-0144`

## <a name="example"></a>Örnek

 Aşağıdaki örnek bir nesne koleksiyonundan bir XML özniteliği değerinin nasıl alınacağını gösterir <xref:System.Xml.Linq.XAttribute> . Örnek, tüm öğelerin öznitelik değerini göstermek için öznitelik ekseni özelliğini kullanır `type` `phone` .

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
- [Visual Basic'de XML Oluşturma](../../programming-guide/language-features/xml/creating-xml.md)
- [Uzantı Metotları](../../programming-guide/language-features/procedures/extension-methods.md)
- [Extension Indexer Özelliği](extension-indexer-property.md)
- [XML Alt Axis Özelliği](xml-child-axis-property.md)
- [XML Özniteliği Axis Özelliği](xml-attribute-axis-property.md)
