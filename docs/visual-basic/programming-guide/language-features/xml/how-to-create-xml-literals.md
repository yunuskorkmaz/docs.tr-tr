---
title: 'Nasıl yapılır: XML değişmez değerleri (Visual Basic) oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: 0e74dccac0b3528fe73d091670a3368328baeaab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560600"
---
# <a name="how-to-create-xml-literals-visual-basic"></a>Nasıl yapılır: XML değişmez değerleri (Visual Basic) oluşturma
XML değişmez değeri kullanarak doğrudan kod içinde bir XML belgesi, parça veya öğesi oluşturabilirsiniz. Bu konudaki örnekler, üç alt öğeleri olan bir XML öğesi oluşturma ve bir XML belgesi oluşturma işlemini gösterir.  
  
 Ayrıca [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] oluşturmak için API'ler [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesneleri. Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XElement>.  
  
### <a name="to-create-an-xml-element"></a>Bir XML öğesi oluşturmak için  
  
-   XML satır içi gerçek XML sözdizimi aynıdır XML değişmez değer sözdizimini kullanarak oluşturun.  
  
     [!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_1.vb)]  
  
     Kodu çalıştırın. Bu kodun çıktısı şöyledir:  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a>Bir XML belgesi oluşturmak için  
  
-   XML belge satır içi oluşturun. Aşağıdaki kod, değişmez değer söz dizimi, bir XML bildirimi, bir işlem yönergesi, bir açıklama ve başka bir öğe içeren bir öğeyi içeren bir XML belgesi oluşturur.  
  
     [!code-vb[VbXMLSamples#30](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_2.vb)]  
  
     Kodu çalıştırın. Bu kodun çıktısı şöyledir:  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a>Ayrıca bkz.
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Visual Basic'de XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML Öğesi Değişmez Değeri](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML Belgesi Değişmez Değeri](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
