---
title: LINQ to XML’e Genel Bakış
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 0481a140541a7f45c682c5150bc1c3d647de90bd
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266904"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Visual Basic'de LINQ - XML Dönüşümüne Genel Bakış
Visual Basic, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML literals ve XML eksen özellikleri aracılığıyla destek sağlar. Bu, Visual Basic kodunuzda XML ile çalışmak için tanıdık ve kullanışlı bir sözdizimini kullanmanıza olanak tanır. *XML literals* doğrudan kodunuza XML eklemenize olanak sağlar. *XML eksen özellikleri,* alt düğümlere, soyundan gelen düğümlere ve XML gerçek özniteliklerine erişmenizi sağlar. Daha fazla bilgi için Visual Basic'te [XML Literals Genel Bakış](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md) ve [XML'e Erişim'e](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)bakın.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Dil-Entegre Sorgu (LINQ) yararlanmak için özel olarak tasarlanmış bir bellek içi XML programlama API'sidir. LINQ API'lerini doğrudan arayabilmenize rağmen, yalnızca Visual Basic XML literallerini bildirmenize ve XML ekseni özelliklerine doğrudan erişmenizi sağlar.  
  
> [!NOTE]
> XML literals ve XML eksen özellikleri ASP.NET bir sayfada bildirim kodu nda desteklenmez. Visual Basic XML özelliklerini kullanmak için, ASP.NET uygulamanızda kod arkadaki bir sayfaya kodunuzu koyun.  
  
 [Oynat düğmesi](./media/overview-of-linq-to-xml/play-video-icon-example.gif) İlgili video gösterileri için [LINQ'dan XML'e Nasıl Başlarım](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml) ve [LINQ'dan XML'e Kullanarak Excel Elektronik Tablolarını Nasıl Oluştururum'a](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml)bakın.
  
## <a name="creating-xml"></a>XML oluşturma  
 Visual Basic'te XML ağaçları oluşturmanın iki yolu vardır. Bir XML harfini doğrudan kod olarak bildirebilir veya ağacı oluşturmak için LINQ API'lerini kullanabilirsiniz. Her iki işlem de kodun XML ağacının son yapısını yansıtmasını sağlar. Örneğin, aşağıdaki kod örneği bir XML öğesi oluşturur:  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 Daha fazla bilgi için [Visual Basic'te XML Oluşturma'ya](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)bakın.  
  
## <a name="accessing-and-navigating-xml"></a>XML'e Erişim ve Gezinme  
 Visual Basic, XML yapılarına erişmek ve gezinmek için XML ekseni özellikleri sağlar. Bu özellikler, XML alt öğe adlarını belirterek XML öğelerine ve özniteliklerine erişmenizi sağlar. Alternatif olarak, öğeleri ve öznitelikleri gezinme kullanabilirsiniz ve bulmak için LINQ yöntemlerini açıkça arayabilirsiniz. Örneğin, aşağıdaki kod örneği, bir XML öğesinin özniteliklerine ve alt öğelerine başvurmak için XML ekseni özelliklerini kullanır. Kod örneği, alt öğeleri almak ve bunları XML öğeleri olarak çıktılamak için bir LINQ sorgusu kullanır ve bunları etkili bir dönüştürme gerçekleştirir.  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 Daha fazla bilgi için [Visual Basic'te XML'e erişim](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)e bakın.  
  
## <a name="xml-namespaces"></a>XML İsim Boşlukları  
 Visual `Imports` Basic, deyimi kullanarak global bir XML ad alanına takma ad belirtmenizi sağlar. Aşağıdaki örnek, bir XML ad alanı almak için deyimin nasıl kullanılacağını `Imports` gösterir:  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 XML eksen özelliklerine eriştikçe ve XML belgeleri ve öğeleri için XML gerçek lerini bildirdiğinizde XML ad alanı takma adını kullanabilirsiniz.  
  
 <xref:System.Xml.Linq.XNamespace> [GetXmlNamespace](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)Operatör'üni kullanarak belirli bir ad alanı öneki için bir nesne alabilirsiniz.  
  
 Daha fazla bilgi [için, İçe Aktarım Bildirimi 'ne (XML Ad Alanı)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)bakın.  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>XML Literals'de XML Ad Boşluklarını Kullanma  
 Aşağıdaki örnek, genel ad <xref:System.Xml.Linq.XElement> alanını `ns`kullanan bir nesnenin nasıl oluşturultur olduğunu gösterir:  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 Visual Basic derleyicisi, XML ad alanı diğer adlarını içeren XML gerçek adlarını, öznitelik ile `xmlns` Birlikte XML ad alanlarını kullanmak için XML gösterimini kullanan eşdeğer koda çevirir. Derlendiğinde, önceki bölümün örneğindeki kod temelde aşağıdaki örnekle aynı yürütülebilir kodu üretir:  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>XML Eksen Özelliklerinde XML Ad Boşluklarını Kullanma  
 XML literals bildirilen XML ad alanları XML eksenözelliklerinde kullanılmak üzere kullanılamaz. Ancak, xml ekseni özellikleriyle genel ad alanları kullanılabilir. XML ad alanı önekini yerel öğe adından ayırmak için bir üst üste kullanın. Aşağıda bir örnek verilmiştir:  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Xml](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [Visual Basic'de XML Oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Visual Basic'de XML'e Erişme](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [Visual Basic'de XML'i Düzenleme](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
