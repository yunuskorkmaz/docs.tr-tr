---
title: Visual Basic'de LINQ - XML Dönüşümüne Genel Bakış
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 65df48112834be04dc8d3b62b8b163316b06c4a6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421249"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Visual Basic'de LINQ - XML Dönüşümüne Genel Bakış
Visual Basic için destek sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML sabit değerleri ve XML eksen özellikleri. Bu, Visual Basic kodunuzda XML ile çalışmak için tanıdık, kullanışlı bir söz dizimi kullanmanıza olanak sağlar. *XML değişmez değerleri* kodunuzda doğrudan XML dahil olanak sağlar. *XML eksen özellikleri* erişim alt düğümleri, alt düğümleri ve bir XML değişmez değeri özniteliklerini etkinleştirin. Daha fazla bilgi için [XML değişmez değerlerine genel bakış](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md) ve [Visual Basic'te erişme XML](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir bellek içi XML programlama API özellikle yararlanmak için tasarlanmış olan [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Çağırabilirsiniz rağmen [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] doğrudan API'leri, yalnızca Visual Basic, XML değişmez değerlerini bildirme ve XML eksen özellikleri doğrudan erişim sağlar.  
  
> [!NOTE]
>  Bir ASP.NET sayfasında bildirime dayalı kodda XML sabit değerleri ve XML eksen özellikleri desteklenmez. Visual Basic XML özelliklerini kullanmak için bir arka plan kod sayfası, ASP.NET uygulamasının kodunuzu yerleştirin.  
  
 ![video bağlantısı](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo") ilgili video gösterimi için bkz. [bunu nasıl kullanmaya başlayabilirim LINQ to XML ile?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml) ve [nasıl yaparım Excel kullanarak LINQ to XML elektronik tablolar oluşturabilir?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml).  
  
## <a name="creating-xml"></a>XML oluşturma  
 Visual Basic'de XML ağaçlarını oluşturmanın iki yolu vardır. XML değişmez değer kodda doğrudan bildirebilirsiniz veya kullanabilirsiniz [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ağacı oluşturmak için API'ler. Her iki işlem XML ağacının son yapısını yansıtmak için kodu etkinleştirin. Örneğin, aşağıdaki kod örneği bir XML öğesi oluşturur:  
  
 [!code-vb[VbXmlSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_1.vb)]  
  
 Daha fazla bilgi için [Visual Basic'de XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md).  
  
## <a name="accessing-and-navigating-xml"></a>Erişim ve XML gezinme  
 Visual Basic erişmek ve XML yapıları gezinme için XML eksen özellikleri sağlar. Bu özellikler, XML alt öğe adları belirterek XML öğeleri ve özniteliklerinin erişim sağlar. Alternatif olarak, açıkça çağırabilirsiniz [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] gezinme ve öğeler ve öznitelikler bulma yöntemleri. Örneğin, aşağıdaki kod örneği, bir XML öğesinin alt öğeleri ve öznitelikleri başvurmak için XML eksen özellikleri kullanır. Kod örneği kullanan bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] alt öğeleri almak ve bunları etkili bir şekilde dönüşüm gerçekleştirme XML öğeleri çıkış için sorgu.  
  
 [!code-vb[VbXmlSamples#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_2.vb)]  
  
 Daha fazla bilgi için [Visual Basic'te erişme XML](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
## <a name="xml-namespaces"></a>XML ad alanları  
 Visual Basic kullanarak genel bir XML ad alanı diğer ad belirtmenize imkan tanır `Imports` deyimi. Aşağıdaki örnek nasıl kullanılacağını gösterir `Imports` deyimi bir XML ad alanı içeri aktarmak için:  
  
 [!code-vb[VbXMLSamples#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_3.vb)]  
  
 XML eksen özelliklerine erişmek ve XML belgeleri ve öğeleri için XML değişmez değerlerini bildirme bir XML ad alanı diğer adlarını kullanabilirsiniz.  
  
 Alabileceğiniz bir <xref:System.Xml.Linq.XNamespace> nesnesi kullanarak bir özel ad alanı ön eki [GetXmlNamespace işleci](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md).  
  
 Daha fazla bilgi için [Imports deyimi (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>XML değişmez değerlerine XML ad alanlarını kullanma  
 Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Xml.Linq.XElement> genel ad alanı kullanan nesne `ns`:  
  
 [!code-vb[VbXMLSamples#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_4.vb)]  
  
 Visual Basic Derleyicisi ile XML ad alanları, kullanmak için XML gösterimi kullanan eşdeğer kod içine XML ad alanı eş adları içeren XML sabit değerleri çevirir `xmlns` özniteliği. Derlendiğinde, önceki bölümün örnek kodda aşağıdaki örnekteki gibi temelde aynı yürütülebilir kod üretir:  
  
 [!code-vb[VbXMLSamples#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_5.vb)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>XML ad alanları XML eksen özelliklerini kullanma  
 XML değişmez değerlerine bildirilen XML ad alanları, XML eksen özellikleri kullanmak için kullanılamaz. Ancak, genel ad alanları XML eksen özellikleri ile kullanılabilir. XML ad alanı öneki yerel öğe addan ayırmak için virgül kullanın. Bir örneği verilmiştir:  
  
 [!code-vb[VbXMLSamples#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_6.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Visual Basic'de XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Visual Basic'de XML'e erişme](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [Visual Basic'de XML düzenleme](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
