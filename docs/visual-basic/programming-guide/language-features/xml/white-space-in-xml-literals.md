---
title: XML Değişmez Değerlerinde Boşluk
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 56ededeb12d07e979bc86b03924e1ae0f0432822
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336004"
---
# <a name="white-space-in-xml-literals-visual-basic"></a>XML Değişmez Değerlerinde Boşluk (Visual Basic)
Visual Basic Derleyicisi, bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesnesi oluşturduğunda yalnızca bir XML sabit değerinden önemli boşluk karakterleri ekler. Önemli boşluk karakterleri dahil değildir.  
  
## <a name="significant-and-insignificant-white-space"></a>Önemli ve çok önemli boşluk  
 XML değişmez değerlerinde boşluk karakterleri yalnızca üç alanda önemlidir:  
  
- Bir öznitelik değeri olduğunda.  
  
- Bir öğenin metin içeriğinin bir parçası olduklarında ve metin diğer karakterleri de içeriyorsa.  
  
- Bir öğenin metin içeriği için gömülü bir ifadede olduklarında.  
  
 Aksi halde, derleyici boşluk karakterlerini önemli olarak değerlendirir ve daha sonra değişmez değer için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesnesine eklemez.  
  
 Bir XML sabit değerinde boş bir boşluk eklemek için, boşluk içeren bir dize sabit değeri içeren gömülü bir ifade kullanın.  
  
> [!NOTE]
> `xml:space` özniteliği bir XML öğesi değişmez değerinde görünürse, Visual Basic Derleyicisi <xref:System.Xml.Linq.XElement> nesnesine özniteliğini içerir, ancak bu özniteliği eklemek derleyicinin boşluk olarak nasıl davrandığını değiştirmez.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki örnek, Outer ve Inner olmak üzere iki XML öğesi içerir. Her iki öğe de metin içeriklerinde boşluk içeriyor. Dış öğedeki boşluk, yalnızca boşluk ve bir XML öğesi içerdiği için çok önemlidir. İç öğedeki boşluk, boşluk ve metin içerdiğinden önemlidir.  
  
 [!code-vb[VbXMLSamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#29)]  
  
 Çalıştırıldığında, bu kod aşağıdaki metni görüntüler.  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
