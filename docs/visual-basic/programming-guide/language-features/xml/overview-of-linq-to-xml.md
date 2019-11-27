---
title: LINQ to XML’e Genel Bakış
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 80d94ecb7dcc196ad831be7418bfecc785015cf9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346230"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Visual Basic'de LINQ - XML Dönüşümüne Genel Bakış
Visual Basic, XML değişmez değerleri ve XML eksen özellikleri aracılığıyla [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] için destek sağlar. Bu, Visual Basic kodunuzda XML ile çalışmak için tanıdık, kullanışlı bir sözdizimi kullanmanıza olanak sağlar. *XML değişmez değerleri* doğrudan kodunuza XML dahil etme olanağı sağlar. *Xml eksen özellikleri* , bir XML sabit değerinin alt düğümlerine, alt düğümlerine ve özniteliklerine erişmenizi sağlar. Daha fazla bilgi için bkz. [XML değişmez değerlerine genel bakış](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md) ve [Visual Basic xml 'e erişme](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], özellikle de [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]yararlanmak için tasarlanan bir bellek içi XML programlama API 'sidir. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] API 'Lerini doğrudan çağırabilseniz de, yalnızca Visual Basic XML değişmez değerleri bildirmenize ve doğrudan XML ekseni özelliklerine erişebilmenize olanak sağlar.  
  
> [!NOTE]
> ASP.NET sayfasındaki bildirim temelli kodda XML sabit değerleri ve XML eksen özellikleri desteklenmez. Visual Basic XML özelliklerini kullanmak için kodunuzu ASP.NET uygulamanızdaki bir arka plan kod sayfasına koyun.  
  
 [Yürüt düğmesi](./media/overview-of-linq-to-xml/play-video-icon-example.gif) İlgili video gösterileri için bkz. [LINQ to XML nasıl başladım?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml) ve [LINQ to XML kullanarak Excel elektronik tabloları nasıl oluşturabilirim?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml).   
  
## <a name="creating-xml"></a>XML oluşturma  
 Visual Basic XML ağaçları oluşturmanın iki yolu vardır. Doğrudan kodda bir XML sabit değeri bildirebilirsiniz veya ağacı oluşturmak için [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] API 'Lerini kullanabilirsiniz. Her iki işlem de kodun XML ağacının son yapısını yansıtmasını sağlar. Örneğin, aşağıdaki kod örneği bir XML öğesi oluşturur:  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 Daha fazla bilgi için bkz. [VISUAL BASIC XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md).  
  
## <a name="accessing-and-navigating-xml"></a>XML 'e erişme ve gezinme  
 Visual Basic, XML yapılarına erişmek ve bunları gezinmek için XML eksen özellikleri sağlar. Bu özellikler, xml alt öğe adlarını belirterek XML öğelerine ve özniteliklerine erişmenizi sağlar. Alternatif olarak, öğeleri ve öznitelikleri gezinmek ve bulmak için [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] yöntemlerini açıkça çağırabilirsiniz. Örneğin, aşağıdaki kod örneği bir XML öğesinin özniteliklerine ve alt öğelerine başvurmak için XML eksen özelliklerini kullanır. Kod örneği, alt öğeleri almak için bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgusu kullanır ve bunları, etkin bir şekilde bir dönüşüm gerçekleştirerek XML öğeleri olarak çıktılar.  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 Daha fazla bilgi için bkz. [VISUAL BASIC XML 'e erişme](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
## <a name="xml-namespaces"></a>XML ad alanları  
 Visual Basic, `Imports` ifadesini kullanarak genel XML ad alanı için bir diğer ad belirtmenizi sağlar. Aşağıdaki örnek, bir XML ad alanını içeri aktarmak için `Imports` deyimin nasıl kullanılacağını gösterir:  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 Xml eksen özelliklerine eriştiğinizde ve XML belgeleri ve öğeleri için XML değişmez değerleri bildirdiğinizde bir XML ad alanı diğer adı kullanabilirsiniz.  
  
 [GetXmlNamespace işlecini](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)kullanarak belirli bir ad alanı öneki için bir <xref:System.Xml.Linq.XNamespace> nesnesi alabilirsiniz.  
  
 Daha fazla bilgi için bkz. [Imports bildirisi (XML ad alanı)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>XML sabit değerlerinde XML ad alanlarını kullanma  
 Aşağıdaki örnek, `ns`genel ad alanını kullanan bir <xref:System.Xml.Linq.XElement> nesnesinin nasıl oluşturulacağını gösterir:  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 Visual Basic Derleyicisi, XML ad alanı diğer adlarını içeren XML sabit değerlerini, `xmlns` özniteliğiyle XML ad alanlarını kullanmak için XML gösterimini kullanan eşdeğer koda çevirir. Derlendiğinde, önceki bölümdeki kod aşağıdaki örnekteki gibi temelde aynı çalıştırılabilir kodu üretir:  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>Xml eksen özelliklerinde XML ad alanlarını kullanma  
 XML sabit değerlerinde belirtilen XML ad alanları, XML ekseni özelliklerinde kullanım için kullanılamaz. Ancak, genel ad alanları XML ekseni özellikleriyle birlikte kullanılabilir. XML ad alanı önekini yerel öğe adından ayırmak için iki nokta üst üste kullanın. Aşağıda bir örnek verilmiştir:  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Visual Basic XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Visual Basic XML 'e erişme](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [Visual Basic XML 'yi düzenleme](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
