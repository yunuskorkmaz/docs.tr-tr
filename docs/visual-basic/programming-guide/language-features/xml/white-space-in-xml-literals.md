---
title: XML Değişmez Değerlerinde Boşluk (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 60ee90c69aeda38f95107a6043801a4994972079
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245165"
---
# <a name="white-space-in-xml-literals-visual-basic"></a>XML Değişmez Değerlerinde Boşluk (Visual Basic)
Oluştururken bir XML değişmez değeri yalnızca önemli boşluk karakterlerinden Visual Basic Derleyicisi içerir. bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesne. Önemsiz beyaz boşluk karakterleri dahil değildir.  
  
## <a name="significant-and-insignificant-white-space"></a>Önemli ve önemsiz boşluk  
 XML değişmez değerlerinde boşluk karakterleri yalnızca üç alanda büyük/küçük harf önemlidir:  
  
-   Bir öznitelik değerinde olduklarında.  
  
-   Bir öğenin metin içeriğini parçasıdır ve metin, ayrıca diğer karakterler içeriyor.  
  
-   Bir öğenin metin içeriğini için katıştırılmış bir ifadede olduklarında.  
  
 Aksi halde, derleyici beyaz boşluk karakterleri önemsiz olarak değerlendirir ve ardından içinde içermez [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] değişmez değer nesnesi.  
  
 XML değişmez değer Önemsiz boşluk eklemek için boşluk bir dize içeren bir katıştırılmış deyim kullanın.  
  
> [!NOTE]
>  Varsa `xml:space` özniteliği görünür bir XML öğesi değişmez değeri, öznitelik, Visual Basic Derleyicisi içerir <xref:System.Xml.Linq.XElement> nesne, ancak bu öznitelik derleyici boşluk nasıl işler değişmez ekleme.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki örnek, dış ve iç iki XML öğelerini içerir. Her iki öğe, metin içeriğini boşluk içerir. Dış öğe boşluk, boşluk ve bir XML öğesinin içerdiği için önemsizdir. İç öğe boşluk, boşluk ve metnin içerdiği için önemlidir.  
  
 [!code-vb[VbXMLSamples#29](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]  
  
 Bu kod, çalıştırdığınızda, aşağıdaki metni görüntüler.  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
