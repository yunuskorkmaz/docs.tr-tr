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
ms.openlocfilehash: 660cebadc78d260350f2849f7f4926f9cef7c8d2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582193"
---
# <a name="extension-indexer-property-visual-basic"></a>Extension Indexer Özelliği (Visual Basic)
Bir koleksiyondaki tek tek öğelere erişim sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
object(index)  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`object`|Gerekli. Sorgulanabilir bir koleksiyon. Diğer bir deyişle, <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601> uygulayan bir koleksiyon.|  
|(|Gerekli. Dizin Oluşturucu özelliğinin başlangıcını gösterir.|  
|`index`|Gerekli. Koleksiyonun bir öğesinin sıfır tabanlı konumunu belirten bir tamsayı ifadesi.|  
|)|Gerekli. Dizin Oluşturucu özelliğinin sonunu belirtir.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Koleksiyonda belirtilen konumdan nesne veya dizin Aralık dışında `Nothing`.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir koleksiyondaki tek tek öğelere erişmek için uzantı Indexer özelliğini kullanabilirsiniz. Bu Indexer özelliği genellikle XML ekseni özelliklerinin çıkışında kullanılır. XML Child ve XML alt öğe ekseni özellikleri <xref:System.Xml.Linq.XElement> nesnelerinin veya bir öznitelik değerinin koleksiyonlarını döndürür.  
  
 Visual Basic derleyici, uzantı Dizin Oluşturucu özelliklerini `ElementAtOrDefault` yöntemine yapılan çağrılara dönüştürür. Dizi Indexer 'ın aksine, Dizin aralık dışında `ElementAtOrDefault` yöntemi `Nothing` döndürür. Bu davranış, bir koleksiyondaki öğe sayısını kolayca belirleyene zaman yararlı olur.  
  
 Bu Indexer özelliği <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601> uygulayan koleksiyonlar için bir uzantı özelliği gibidir: yalnızca koleksiyonda bir Dizin Oluşturucu veya varsayılan özellik yoksa kullanılır.  
  
 @No__t_0 veya <xref:System.Xml.Linq.XAttribute> nesneleri koleksiyonundaki ilk öğenin değerine erişmek için XML `Value` özelliğini kullanabilirsiniz. Daha fazla bilgi için bkz. [XML Value özelliği](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir <xref:System.Xml.Linq.XElement> nesneleri koleksiyonundaki ikinci alt düğüme erişmek için uzantı dizin oluşturucunun nasıl kullanılacağını gösterir. Koleksiyona, `contact` nesnesinde `phone` adlı tüm alt öğeleri alan alt eksen özelliği kullanılarak erişilir.  
  
 [!code-vb[VbXMLSamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#24)]  
  
 Bu kod aşağıdaki metni görüntüler:  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement>
- [XML Eksen Özellikleri](../../../visual-basic/language-reference/xml-axis/index.md)
- [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML Value Özelliği](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
