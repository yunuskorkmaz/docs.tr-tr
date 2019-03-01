---
title: 'Nasıl yapılır: XML değişmez değerleri (Visual Basic) oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: c79b607f9ce5c779539b7700feafb7d4e3d67d24
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974256"
---
# <a name="how-to-create-xml-literals-visual-basic"></a>Nasıl yapılır: XML değişmez değerleri (Visual Basic) oluşturma
XML değişmez değeri kullanarak doğrudan kod içinde bir XML belgesi, parça veya öğesi oluşturabilirsiniz. Bu konudaki örnekler, üç alt öğeleri olan bir XML öğesi oluşturma ve bir XML belgesi oluşturma işlemini gösterir.  
  
 Ayrıca [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] oluşturmak için API'ler [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesneleri. Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XElement>.  
  
### <a name="to-create-an-xml-element"></a>Bir XML öğesi oluşturmak için  
  
-   XML satır içi gerçek XML sözdizimi aynıdır XML değişmez değer sözdizimini kullanarak oluşturun.  
  
     [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
     Kodu çalıştırın. Bu kodun çıktısı şöyledir:  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a>Bir XML belgesi oluşturmak için  
  
-   XML belge satır içi oluşturun. Aşağıdaki kod, değişmez değer söz dizimi, bir XML bildirimi, bir işlem yönergesi, bir açıklama ve başka bir öğe içeren bir öğeyi içeren bir XML belgesi oluşturur.  
  
     [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
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
