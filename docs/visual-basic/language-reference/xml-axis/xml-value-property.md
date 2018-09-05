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
ms.openlocfilehash: 2b0719320db5843d5d010bfbd70e551646e3ded9
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43533397"
---
# <a name="xml-value-property-visual-basic"></a>XML Değeri Özelliği (Visual Basic)
Koleksiyonunu ilk öğenin değerini erişim sağlayan <xref:System.Xml.Linq.XElement> nesneleri.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
object.Value  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`object`|Gerekli. Koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 A `String` koleksiyonun ilk öğenin değerini içeren veya `Nothing` koleksiyonu boş ise.  
  
## <a name="remarks"></a>Açıklamalar  
 <xref:System.Xml.Linq.XElement.Value%2A> Özelliği bir koleksiyondaki ilk öğenin değere erişmek kolaylaştırır <xref:System.Xml.Linq.XElement> nesneleri. Bu özellik, ilk koleksiyon en az bir nesne içerip içermediğini denetler. Bu özellik koleksiyonu boş ise döndürür `Nothing`. Aksi takdirde, bu özellik değerini döndürür <xref:System.Xml.Linq.XElement.Value%2A> koleksiyondaki ilk öğenin özellik.  
  
> [!NOTE]
>  Kullanarak bir XML özniteliği değeri eriştiğinizde '\@' tanımlayıcısı, öznitelik değeri olarak döndürülür bir `String` ve açıkça belirtmeniz gerekmez <xref:System.Xml.Linq.XAttribute.Value%2A> özelliği.  
  
 Bir koleksiyondaki diğer öğelere erişmek için XML uzantı dizin oluşturucu özelliği kullanabilirsiniz. Daha fazla bilgi için [Extension Indexer özelliği](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).  
  
## <a name="inheritance"></a>Devralma  
 Çoğu kullanıcı uygulamak zorunda <xref:System.Collections.Generic.IEnumerable%601>ve bu nedenle bu bölüm yoksayabilirsiniz.  
  
 <xref:System.Xml.Linq.XElement.Value%2A> Özelliği uygulayan türler için bir uzantı özelliği `IEnumerable(Of XElement)`. Uzantı yöntemleri bağlama gibi bağlamadır bu uzantı özelliğinin: Bu özellik bir tür arabirimlerinden birini uygular ve "Value" adına sahip bir özelliğini tanımlar, uzantı özelliği önceliğe sahiptir. Diğer bir deyişle, bu <xref:System.Xml.Linq.XElement.Value%2A> özelliği, yeni bir özelliği uygulayan bir sınıf tanımlayarak kılınabilir `IEnumerable(Of XElement)`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Xml.Linq.XElement.Value%2A> koleksiyonunu ilk düğüm erişmek için özelliği <xref:System.Xml.Linq.XElement> nesneleri. Örnek child axis özelliği adlı tüm alt düğümleri koleksiyonu almak için kullanır. `phone` bulunan `contact` nesne.  
  
 [!code-vb[VbXMLSamples#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_1.vb)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek koleksiyonundan bir XML özniteliği değeri almak nasıl gösterir <xref:System.Xml.Linq.XAttribute> nesneleri. Örnek attribute axis özelliği değerini görüntülemek için kullanır. `type` özniteliği için tüm `phone` öğeleri.  
  
 [!code-vb[VbXMLSamples#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_2.vb)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Linq.XElement>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [XML Eksen Özellikleri](../../../visual-basic/language-reference/xml-axis/index.md)  
 [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Visual Basic'de XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Genişletme Yöntemleri](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [Extension Indexer Özelliği](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)  
 [XML Alt Axis Özelliği](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [XML Özniteliği Axis Özelliği](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
