---
title: LINQ to XML’e Genel Bakış
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 044aca634f5a0aa6e557a7dd9c0e1de64e35dc15
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374661"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Visual Basic'de LINQ - XML Dönüşümüne Genel Bakış
Visual Basic, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML değişmez değerleri ve xml eksen özellikleri için destek sağlar. Bu, Visual Basic kodunuzda XML ile çalışmak için tanıdık, kullanışlı bir sözdizimi kullanmanıza olanak sağlar. *XML değişmez değerleri* doğrudan kodunuza XML dahil etme olanağı sağlar. *Xml eksen özellikleri* , bir XML sabit değerinin alt düğümlerine, alt düğümlerine ve özniteliklerine erişmenizi sağlar. Daha fazla bilgi için bkz. [XML değişmez değerlerine genel bakış](xml-literals-overview.md) ve [Visual Basic xml 'e erişme](accessing-xml.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], özellikle dil ile tümleşik sorgu (LINQ) avantajlarından yararlanmak için tasarlanan, bellek içi bir XML programlama API 'sidir. LINQ API 'Lerini doğrudan çağırabilseniz de yalnızca Visual Basic, XML değişmez değerlerini bildirmenize ve doğrudan XML ekseni özelliklerine erişebilmenize olanak sağlar.  
  
> [!NOTE]
> ASP.NET sayfasındaki bildirim temelli kodda XML sabit değerleri ve XML eksen özellikleri desteklenmez. Visual Basic XML özelliklerini kullanmak için kodunuzu ASP.NET uygulamanızdaki bir arka plan kod sayfasına koyun.  
  
 [Yürüt düğmesi](./media/overview-of-linq-to-xml/play-video-icon-example.gif) İlgili video gösterileri için bkz. [LINQ to XML nasıl başladım?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml) ve [LINQ to XML kullanarak Excel elektronik tabloları nasıl oluşturabilirim?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml).
  
## <a name="creating-xml"></a>XML oluşturma  
 Visual Basic XML ağaçları oluşturmanın iki yolu vardır. Doğrudan kodda bir XML sabit değeri bildirebilirsiniz veya ağacı oluşturmak için LINQ API 'Lerini kullanabilirsiniz. Her iki işlem de kodun XML ağacının son yapısını yansıtmasını sağlar. Örneğin, aşağıdaki kod örneği bir XML öğesi oluşturur:  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 Daha fazla bilgi için bkz. [VISUAL BASIC XML oluşturma](creating-xml.md).  
  
## <a name="accessing-and-navigating-xml"></a>XML 'e erişme ve gezinme  
 Visual Basic, XML yapılarına erişmek ve bunları gezinmek için XML eksen özellikleri sağlar. Bu özellikler, xml alt öğe adlarını belirterek XML öğelerine ve özniteliklerine erişmenizi sağlar. Alternatif olarak, öğeleri ve öznitelikleri gezinmek ve bulmak için LINQ yöntemlerini açık bir şekilde çağırabilirsiniz. Örneğin, aşağıdaki kod örneği bir XML öğesinin özniteliklerine ve alt öğelerine başvurmak için XML eksen özelliklerini kullanır. Kod örneği, alt öğeleri almak için bir LINQ sorgusu kullanır ve bunları, etkin bir şekilde bir dönüşüm gerçekleştirerek XML öğeleri olarak çıktılar.  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 Daha fazla bilgi için bkz. [VISUAL BASIC XML 'e erişme](accessing-xml.md).  
  
## <a name="xml-namespaces"></a>XML ad alanları  
 Visual Basic, bir genel XML ad alanı için ifadesini kullanarak bir diğer ad belirtmenizi sağlar `Imports` . Aşağıdaki örnek, `Imports` BIR XML ad alanını içeri aktarmak için deyimin nasıl kullanılacağını gösterir:  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 Xml eksen özelliklerine eriştiğinizde ve XML belgeleri ve öğeleri için XML değişmez değerleri bildirdiğinizde bir XML ad alanı diğer adı kullanabilirsiniz.  
  
 <xref:System.Xml.Linq.XNamespace> [GetXmlNamespace işlecini](../../../language-reference/operators/getxmlnamespace-operator.md)kullanarak belirli bir ad alanı öneki için bir nesne alabilirsiniz.  
  
 Daha fazla bilgi için bkz. [Imports bildirisi (XML ad alanı)](../../../language-reference/statements/imports-statement-xml-namespace.md).  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>XML sabit değerlerinde XML ad alanlarını kullanma  
 Aşağıdaki örnek, <xref:System.Xml.Linq.XElement> genel ad alanını kullanan bir nesnenin nasıl oluşturulacağını gösterir `ns` :  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 Visual Basic Derleyicisi, XML ad alanı diğer adlarını içeren XML değişmez değerlerini özniteliği ile XML ad alanlarını kullanmak için XML gösterimini kullanan eşdeğer koda çevirir `xmlns` . Derlendiğinde, önceki bölümdeki kod aşağıdaki örnekteki gibi temelde aynı çalıştırılabilir kodu üretir:  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>Xml eksen özelliklerinde XML ad alanlarını kullanma  
 XML sabit değerlerinde belirtilen XML ad alanları, XML ekseni özelliklerinde kullanım için kullanılamaz. Ancak, genel ad alanları XML ekseni özellikleriyle birlikte kullanılabilir. XML ad alanı önekini yerel öğe adından ayırmak için iki nokta üst üste kullanın. Aşağıda bir örnek verilmiştir:  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML](index.md)
- [Visual Basic'de XML Oluşturma](creating-xml.md)
- [Visual Basic'de XML'e Erişme](accessing-xml.md)
- [Visual Basic'de XML'i Düzenleme](manipulating-xml.md)
