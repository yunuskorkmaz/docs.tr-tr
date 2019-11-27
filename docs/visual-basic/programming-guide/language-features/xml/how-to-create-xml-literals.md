---
title: 'Nasıl yapılır: XML Değişmez Değerleri Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: e3af5185d2c2106e6a696a6569ef59897d0f1fe1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332997"
---
# <a name="how-to-create-xml-literals-visual-basic"></a>Nasıl yapılır: XML Değişmez Değerleri Oluşturma (Visual Basic)
Bir XML sabit değeri kullanarak doğrudan kodda bir XML belgesi, parça veya öğe oluşturabilirsiniz. Bu konudaki örneklerde, üç alt öğesi olan bir XML öğesinin nasıl oluşturulacağı ve bir XML belgesinin nasıl oluşturulacağı gösterilmektedir.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesneleri oluşturmak için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API 'Lerini de kullanabilirsiniz. Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XElement>.  
  
### <a name="to-create-an-xml-element"></a>Bir XML öğesi oluşturmak için  
  
- XML sabit değeri olan XML değişmez sözdizimini kullanarak XML satır içi oluşturun, bu da gerçek XML sözdizimi ile aynıdır.  
  
     [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
     Kodu çalıştırın. Bu kodun çıktısı:  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a>Bir XML belgesi oluşturmak için  
  
- XML belgesini satır içi olarak oluşturun. Aşağıdaki kod, değişmez sözdizimi, XML bildirimi, işleme yönergesi, açıklama ve başka bir öğesi içeren bir öğesi olan bir XML belgesi oluşturur.  
  
     [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
     Kodu çalıştırın. Bu kodun çıktısı:  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Visual Basic XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML Öğesi Değişmez Değeri](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML Belgesi Değişmez Değeri](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
