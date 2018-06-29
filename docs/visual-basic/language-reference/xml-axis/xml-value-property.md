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
ms.openlocfilehash: 927158f940d9b96cd06873c7d3e710be91b887e9
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37071625"
---
# <a name="xml-value-property-visual-basic"></a>XML Değeri Özelliği (Visual Basic)
Bir ilk öğesinin değeri erişim sağlayan <xref:System.Xml.Linq.XElement> nesneleri.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
object.Value  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`object`|Gerekli. Koleksiyonu <xref:System.Xml.Linq.XElement> nesneleri.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 A `String` koleksiyonun ilk öğesinin değeri içeren veya `Nothing` koleksiyonu boş ise.  
  
## <a name="remarks"></a>Açıklamalar  
 <xref:System.Xml.Linq.XElement.Value%2A> Özellik koleksiyonu ilk öğe değerini erişmek kolaylaştırır <xref:System.Xml.Linq.XElement> nesneleri. Bu özellik ilk koleksiyon en az bir nesne içerip içermediğini denetler. Koleksiyon boş ise, bu özellik döndürür `Nothing`. Aksi takdirde, bu özellik değerini döndürür <xref:System.Xml.Linq.XElement.Value%2A> koleksiyondaki ilk öğesi özelliği.  
  
> [!NOTE]
>  Bir XML özniteliği kullanılarak değerini eriştiğinizde '\@' tanımlayıcısı, öznitelik değeri olarak döndürülür bir `String` ve açıkça belirtmek gerekmez <xref:System.Xml.Linq.XAttribute.Value%2A> özelliği.  
  
 Bir koleksiyondaki diğer öğeler erişmek için XML uzantı dizin oluşturucu özelliği kullanabilirsiniz. Daha fazla bilgi için bkz: [Extension Indexer özelliği](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).  
  
## <a name="inheritance"></a>Devralma  
 Kullanıcıların çoğunun uygulamak zorunda kalmazsınız <xref:System.Collections.Generic.IEnumerable%601>ve bu nedenle bu bölüm göz ardı edebilirsiniz.  
  
 <xref:System.Xml.Linq.XElement.Value%2A> Özelliktir uygulama türleri için bir uzantı özelliği `IEnumerable(Of XElement)`. Bu uzantı özelliği bağlama genişletme yöntemleri bağlama gibi olduğu: Bu özellik türü arabirimlerinden biri, uygular ve "Value" adına sahip bir özelliğini tanımlar, uzantı özelliği önceliğe sahip. Diğer bir deyişle, bu <xref:System.Xml.Linq.XElement.Value%2A> özelliğinin yeni özellik uygulayan bir sınıf tanımlama tarafından geçersiz kılınmış `IEnumerable(Of XElement)`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Xml.Linq.XElement.Value%2A> koleksiyonu ilk düğüm erişmek için özelliğini <xref:System.Xml.Linq.XElement> nesneleri. Örnek, tüm alt düğümleri adlı koleksiyonunu alma için child axis özelliği kullanır. `phone` olan `contact` nesnesi.  
  
 [!code-vb[VbXMLSamples#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_1.vb)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir XML özniteliğinin değeri bir koleksiyonundan almak gösterilmiştir <xref:System.Xml.Linq.XAttribute> nesneleri. Örnek attribute axis özelliği değerini görüntülemek için kullanır. `type` özniteliği için tüm `phone` öğeleri.  
  
 [!code-vb[VbXMLSamples#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_2.vb)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Linq.XElement>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [XML Eksen Özellikleri](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Visual Basic'de XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Genişletme Yöntemleri](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [Extension Indexer Özelliği](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)  
 [XML Alt Axis Özelliği](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [XML Özniteliği Axis Özelliği](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
