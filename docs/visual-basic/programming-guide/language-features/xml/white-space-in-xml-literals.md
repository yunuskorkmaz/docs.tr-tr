---
title: XML Değişmez Değerlerinde Boşluk (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6d23aa54b150748aac9aa955f4bd86ee88358ea
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="white-space-in-xml-literals-visual-basic"></a>XML Değişmez Değerlerinde Boşluk (Visual Basic)
Visual Basic derleyici oluştururken bir XML değişmez değeri yalnızca önemli boşluk karakterlerinden içerir bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesnesi. Önemsiz boşluk karakterleri dahil değildir.  
  
## <a name="significant-and-insignificant-white-space"></a>Önemli ve önemsiz beyaz alan  
 XML değişmez değerlerinde boşluk karakterleri yalnızca üç alana önemlidir:  
  
-   Bir öznitelik değeri olduklarında.  
  
-   Ne zaman bir öğenin metin içeriğini parçasıdır ve metin ayrıca diğer karakterler içeriyor.  
  
-   Bir öğenin metin içeriği katıştırılmış bir ifadede olduklarında.  
  
 Aksi takdirde derleyici boşluk karakterleri önemsiz olarak değerlendirir ve ardından eklememeyi [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] değişmez değeri için nesnesi.  
  
 XML değişmez değer anlamsız boşluk eklemek için bir boşluk ile değişmez dize değeri içeren katıştırılmış ifade kullanın.  
  
> [!NOTE]
>  Varsa `xml:space` özniteliği görünür bir XML öğesi değişmez değeri, Visual Basic derleyici özniteliğinde içeren <xref:System.Xml.Linq.XElement> nesnesi, ancak bu öznitelik derleyici boşluk nasıl işler değiştirmez ekleme.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki örnek, dış ve iç iki XML öğeleri içerir. Her iki öğeler, metin içeriğini boşluk içerir. Boşluk Dış öğede yalnızca boşluk ve bir XML öğesi içerdiğinden önemsizdir. Boşluk iç öğesinde, boşluk ve metin içerdiği için önemlidir.  
  
 [!code-vb[VbXMLSamples#29](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/white-space-in-xml-literals_1.vb)]  
  
 Bu kodu çalıştırdığınızda, aşağıdaki metni görüntüler.  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
