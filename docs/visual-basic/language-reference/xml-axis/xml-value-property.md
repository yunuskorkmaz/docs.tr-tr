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
ms.openlocfilehash: 9edf95c7cedced55ab2441baf51b7c2052e4654c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942989"
---
# <a name="xml-value-property-visual-basic"></a>XML Değeri Özelliği (Visual Basic)
Bir <xref:System.Xml.Linq.XElement> nesne koleksiyonunun ilk öğesinin değerine erişim sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
object.Value  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`object`|Gerekli. <xref:System.Xml.Linq.XElement> Nesne koleksiyonu.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Koleksiyonun `String` ilk öğesinin değerini içeren bir veya `Nothing` koleksiyon boşsa.  
  
## <a name="remarks"></a>Açıklamalar  
 Özelliği <xref:System.Xml.Linq.XElement.Value%2A> , bir <xref:System.Xml.Linq.XElement> nesne koleksiyonundaki ilk öğenin değerine erişmeyi kolaylaştırır. Bu özellik önce koleksiyonun en az bir nesne içerip içermediğini denetler. Koleksiyon boşsa, bu özellik döndürür `Nothing`. Aksi takdirde, bu özellik koleksiyondaki ilk öğenin <xref:System.Xml.Linq.XElement.Value%2A> özelliğinin değerini döndürür.  
  
> [!NOTE]
> Bir xml özniteliğinin değerine '\@' tanımlayıcısını kullanarak eriştiğinizde, öznitelik değeri bir `String` olarak döndürülür ve <xref:System.Xml.Linq.XAttribute.Value%2A> özelliği açıkça belirtmeniz gerekmez.  
  
 Bir koleksiyondaki diğer öğelere erişmek için XML uzantısı Indexer özelliğini kullanabilirsiniz. Daha fazla bilgi için bkz. [uzantı Dizin Oluşturucu özelliği](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).  
  
## <a name="inheritance"></a>Devralma  
 Çoğu kullanıcının uygulaması <xref:System.Collections.Generic.IEnumerable%601>ve bu bölümü yoksayması gerekmez.  
  
 Özelliği, uygulayan `IEnumerable(Of XElement)`türler için bir genişletme özelliğidir. <xref:System.Xml.Linq.XElement.Value%2A> Bu uzantı özelliğinin bağlaması uzantı yöntemlerinin bağlaması gibidir: bir tür arabirimlerden birini uygular ve "Value" adlı bir özellik tanımlıyorsa, bu özellik uzantı özelliğine göre önceliğe sahiptir. Diğer bir deyişle, bu <xref:System.Xml.Linq.XElement.Value%2A> özellik, uygulayan `IEnumerable(Of XElement)`bir sınıfta yeni bir özellik tanımlayarak geçersiz kılınabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir <xref:System.Xml.Linq.XElement.Value%2A> <xref:System.Xml.Linq.XElement> nesne koleksiyonundaki ilk düğüme erişmek için özelliğinin nasıl kullanılacağını gösterir. Örnek, `phone` `contact` nesnesinde olan adlı tüm alt düğümlerin koleksiyonunu almak için alt eksen özelliğini kullanır.  
  
 [!code-vb[VbXMLSamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#15)]  
  
 Bu kod aşağıdaki metni görüntüler:  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir <xref:System.Xml.Linq.XAttribute> nesne koleksiyonundan bir XML özniteliği değerinin nasıl alınacağını gösterir. Örnek, tüm `type` `phone` öğelerin öznitelik değerini göstermek için öznitelik ekseni özelliğini kullanır.  
  
 [!code-vb[VbXMLSamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#16)]  
  
 Bu kod aşağıdaki metni görüntüler:  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement>
- <xref:System.Collections.Generic.IEnumerable%601>
- [XML Eksen Özellikleri](../../../visual-basic/language-reference/xml-axis/index.md)
- [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Genişletme Yöntemleri](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [Extension Indexer Özelliği](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)
- [XML Alt Axis Özelliği](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [XML Özniteliği Axis Özelliği](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
