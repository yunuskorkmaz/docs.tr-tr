---
title: Extension Indexer Özelliği (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: a02c482db81d9d76752cfe66a292dc57c48b2acb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58841284"
---
# <a name="extension-indexer-property-visual-basic"></a>Extension Indexer Özelliği (Visual Basic)
Bir koleksiyondaki öğelere erişim sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
object(index)  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`object`|Gerekli. Sorgulanabilir bir koleksiyonu. Diğer bir deyişle, uygulayan koleksiyondan <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601>.|  
|(|Gerekli. Dizin Oluşturucu özelliği başlangıcını gösterir.|  
|`index`|Gerekli. Koleksiyonun bir öğesi sıfır tabanlı konumu belirten bir tamsayı ifade.|  
|)|Gerekli. Dizin Oluşturucu özelliği sonunu gösterir.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Belirtilen konumda koleksiyon nesnesinden veya `Nothing` dizini aralık dışında ise.  
  
## <a name="remarks"></a>Açıklamalar  
 Extension Indexer özelliği, bir koleksiyondaki tek tek öğelere erişmek için kullanabilirsiniz. Bu dizin oluşturucu özelliği, genellikle XML eksen özellikleri üzerinde çıkışını kullanılır. XML descendent axis özellikleri ve XML alt koleksiyonları dönüş <xref:System.Xml.Linq.XElement> nesneler veya bir öznitelik değeri.  
  
 Visual Basic derleyici çağrıları uzantı dizin oluşturucu özellikleri dönüştürür `ElementAtOrDefault` yöntemi. Bir dizi dizin oluşturucu aksine `ElementAtOrDefault` yöntemi döndürür `Nothing` dizini aralık dışında ise. Bu davranış, bir koleksiyondaki öğe sayısını kolayca belirlenemiyor yararlıdır.  
  
 Bu dizin oluşturucu özelliği, bir uzantı özelliği uygulayan koleksiyonlar için benzer <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601>: yalnızca koleksiyon bir dizin oluşturucu veya varsayılan bir özellik yoksa, kullanılır.  
  
 Değerin bir koleksiyondaki ilk öğenin erişmek için <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> nesneler, XML kullanabileceğiniz `Value` özelliği. Daha fazla bilgi için [XML değeri özelliği](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir koleksiyonu ikinci alt düğümünde erişmek için uzantı dizin oluşturucu kullanmayı gösterir <xref:System.Xml.Linq.XElement> nesneleri. Koleksiyon adlı tüm alt öğe alır child axis özelliği kullanılarak erişilir `phone` içinde `contact` nesne.  
  
 [!code-vb[VbXMLSamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#24)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement>
- [XML Eksen Özellikleri](../../../visual-basic/language-reference/xml-axis/index.md)
- [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic'de XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML Value Özelliği](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
