---
title: XML Değişmez Değerlerinde Boşluk (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 903928087d5ad9c51040ba6bf65639f44d8c7dd6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64627434"
---
# <a name="white-space-in-xml-literals-visual-basic"></a>XML Değişmez Değerlerinde Boşluk (Visual Basic)
Oluştururken bir XML değişmez değeri yalnızca önemli boşluk karakterlerinden Visual Basic Derleyicisi içerir. bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesne. Önemsiz beyaz boşluk karakterleri dahil değildir.  
  
## <a name="significant-and-insignificant-white-space"></a>Önemli ve önemsiz boşluk  
 XML değişmez değerlerinde boşluk karakterleri yalnızca üç alanda büyük/küçük harf önemlidir:  
  
- Bir öznitelik değerinde olduklarında.  
  
- Bir öğenin metin içeriğini parçasıdır ve metin, ayrıca diğer karakterler içeriyor.  
  
- Bir öğenin metin içeriğini için katıştırılmış bir ifadede olduklarında.  
  
 Aksi halde, derleyici beyaz boşluk karakterleri önemsiz olarak değerlendirir ve ardından içinde içermez [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] değişmez değer nesnesi.  
  
 XML değişmez değer Önemsiz boşluk eklemek için boşluk bir dize içeren bir katıştırılmış deyim kullanın.  
  
> [!NOTE]
>  Varsa `xml:space` özniteliği görünür bir XML öğesi değişmez değeri, öznitelik, Visual Basic Derleyicisi içerir <xref:System.Xml.Linq.XElement> nesne, ancak bu öznitelik derleyici boşluk nasıl işler değişmez ekleme.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki örnek, dış ve iç iki XML öğelerini içerir. Her iki öğe, metin içeriğini boşluk içerir. Dış öğe boşluk, boşluk ve bir XML öğesinin içerdiği için önemsizdir. İç öğe boşluk, boşluk ve metnin içerdiği için önemlidir.  
  
 [!code-vb[VbXMLSamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#29)]  
  
 Bu kod, çalıştırdığınızda, aşağıdaki metni görüntüler.  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
