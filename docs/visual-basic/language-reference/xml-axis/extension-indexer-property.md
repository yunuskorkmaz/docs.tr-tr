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
ms.openlocfilehash: ab9eacc3fb3796139d8ed8382146a4a6c2b28a97
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44189507"
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
  
 [!code-vb[VbXMLSamples#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/extension-indexer-property_1.vb)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Linq.XElement>  
 [XML Eksen Özellikleri](../../../visual-basic/language-reference/xml-axis/index.md)  
 [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Visual Basic'de XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [XML Value Özelliği](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
