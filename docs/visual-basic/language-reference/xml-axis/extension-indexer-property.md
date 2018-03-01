---
title: "Extension Indexer Özelliği (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 99d14b6e54a59ffc904a9e786c22498d23ee8ab6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="extension-indexer-property-visual-basic"></a>Extension Indexer Özelliği (Visual Basic)
Bir koleksiyondaki tek tek öğelere erişim sağlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
object(index)  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`object`|Gerekli. Sorgulanabilir bir koleksiyon. Diğer bir deyişle, uygulayan koleksiyondan <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601>.|  
|(|Gerekli. Dizin Oluşturucu özelliği başlangıcını gösterir.|  
|`index`|Gerekli. Koleksiyonun bir öğesi sıfır tabanlı konumu belirten bir tamsayı ifade.|  
|)|Gerekli. Dizin Oluşturucu özelliği sonunu gösterir.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Koleksiyonun belirtilen konumda nesnesinden veya `Nothing` dizini aralık dışında olması durumunda.  
  
## <a name="remarks"></a>Açıklamalar  
 Extension Indexer özelliği ayrı ayrı öğeler bir koleksiyondaki erişmek için kullanabilirsiniz. Bu dizin oluşturucu özelliği, genellikle XML eksen özellikleri Çıkışta kullanılır. XML descendent axis özellikleri ve XML alt koleksiyonları dönmek <xref:System.Xml.Linq.XElement> nesneleri veya bir öznitelik değeri.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Derleyici çağrıları uzantı dizin oluşturucu özellikleri dönüştürür `ElementAtOrDefault` yöntemi. Bir dizi dizin oluşturucu aksine `ElementAtOrDefault` yöntemi döndürür `Nothing` dizini aralık dışında olması durumunda. Bu davranış, bir koleksiyondaki öğe sayısını kolayca belirleyemezsiniz yararlıdır.  
  
 Uzantı özelliği uygulamak koleksiyonlar için bu dizin oluşturucu özelliği benzer <xref:System.Collections.Generic.IEnumerable%601> veya <xref:System.Linq.IQueryable%601>: yalnızca koleksiyon bir dizin oluşturucu veya varsayılan bir özellik yoksa kullanılır.  
  
 Bir koleksiyonu ilk öğe değerini erişmek için <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> nesneleri, XML kullanabileceğiniz `Value` özelliği. Daha fazla bilgi için bkz: [XML değeri özelliği](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek uzantı dizin oluşturucu koleksiyonu ikinci alt düğümünde erişmek için nasıl kullanılacağını gösterir <xref:System.Xml.Linq.XElement> nesneleri. Koleksiyon adlı tüm alt öğeleri alır child axis özelliği kullanılarak erişilir `phone` içinde `contact` nesnesi.  
  
 [!code-vb[VbXMLSamples#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/extension-indexer-property_1.vb)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Linq.XElement>  
 [XML eksen özellikleri](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [XML değişmez değerleri](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Visual Basic'de XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [XML değeri özelliği](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
