---
title: Extension Indexer Özelliği
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
ms.openlocfilehash: c91061d49e22e648b7bf75a812071b352793abcb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401348"
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
|`object`|Gereklidir. Sorgulanabilir bir koleksiyon. Diğer bir deyişle, veya uygulayan bir <xref:System.Collections.Generic.IEnumerable%601> koleksiyon <xref:System.Linq.IQueryable%601> .|  
|(|Gereklidir. Dizin Oluşturucu özelliğinin başlangıcını gösterir.|  
|`index`|Gereklidir. Koleksiyonun bir öğesinin sıfır tabanlı konumunu belirten bir tamsayı ifadesi.|  
|)|Gereklidir. Dizin Oluşturucu özelliğinin sonunu belirtir.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Koleksiyonda belirtilen konumdan nesne veya `Nothing` Dizin aralık dışında.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir koleksiyondaki tek tek öğelere erişmek için uzantı Indexer özelliğini kullanabilirsiniz. Bu Indexer özelliği genellikle XML ekseni özelliklerinin çıkışında kullanılır. XML alt ve XML alt öğe ekseni özellikleri, nesne koleksiyonlarını <xref:System.Xml.Linq.XElement> veya bir öznitelik değerini döndürür.  
  
 Visual Basic derleyici, uzantı Dizin Oluşturucu özelliklerini yöntemine yapılan çağrılara dönüştürür `ElementAtOrDefault` . Dizi Indexer 'ın aksine, `ElementAtOrDefault` Yöntem `Nothing` Dizin aralık dışında olduğunda döndürür. Bu davranış, bir koleksiyondaki öğe sayısını kolayca belirleyene zaman yararlı olur.  
  
 Bu Indexer özelliği veya uygulayan koleksiyonlar için bir uzantı özelliği gibidir <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Linq.IQueryable%601> : yalnızca koleksiyonda bir Dizin Oluşturucu veya varsayılan özellik yoksa kullanılır.  
  
 Bir veya nesneleri koleksiyonundaki ilk öğenin değerine erişmek için <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> XML `Value` özelliğini kullanabilirsiniz. Daha fazla bilgi için bkz. [XML Value özelliği](xml-value-property.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir nesne koleksiyonundaki ikinci alt düğüme erişmek için uzantı dizin oluşturucunun nasıl kullanılacağını gösterir <xref:System.Xml.Linq.XElement> . Koleksiyonda, nesne içinde adlı tüm alt öğeleri alan alt eksen özelliği kullanılarak erişilir `phone` `contact` .  
  
 [!code-vb[VbXMLSamples#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#24)]  
  
 Bu kod aşağıdaki metni görüntüler:  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement>
- [XML Eksen Özellikleri](index.md)
- [XML Değişmez Değerleri](../xml-literals/index.md)
- [Visual Basic'de XML Oluşturma](../../programming-guide/language-features/xml/creating-xml.md)
- [XML Value Özelliği](xml-value-property.md)
