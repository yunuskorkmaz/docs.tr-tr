---
title: XML Değişmez Değerlerinde Boşluk (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: f72dcc25b158d793850069e5cc32c3a3c02fad17
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939208"
---
# <a name="white-space-in-xml-literals-visual-basic"></a>XML Değişmez Değerlerinde Boşluk (Visual Basic)
Visual Basic derleyici bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesne oluşturduğunda yalnızca bir XML sabit değerinden önemli boşluk karakterleri ekler. Önemli boşluk karakterleri dahil değildir.  
  
## <a name="significant-and-insignificant-white-space"></a>Önemli ve çok önemli boşluk  
 XML değişmez değerlerinde boşluk karakterleri yalnızca üç alanda önemlidir:  
  
- Bir öznitelik değeri olduğunda.  
  
- Bir öğenin metin içeriğinin bir parçası olduklarında ve metin diğer karakterleri de içeriyorsa.  
  
- Bir öğenin metin içeriği için gömülü bir ifadede olduklarında.  
  
 Aksi halde, derleyici boşluk karakterlerini önemli olarak değerlendirir ve daha sonra [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] değişmez değer için nesnesine içermez.  
  
 Bir XML sabit değerinde boş bir boşluk eklemek için, boşluk içeren bir dize sabit değeri içeren gömülü bir ifade kullanın.  
  
> [!NOTE]
> Öznitelik bir XML öğesi değişmez değerinde görünürse, Visual Basic derleyici <xref:System.Xml.Linq.XElement> nesnedeki özniteliği içerir, ancak bu özniteliği eklemek derleyicinin boşluk olarak nasıl davrandığını değiştirmez. `xml:space`  
  
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
