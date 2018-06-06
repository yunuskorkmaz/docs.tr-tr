---
title: Visual Basic'de LINQ - XML Dönüşümüne Genel Bakış
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 65df48112834be04dc8d3b62b8b163316b06c4a6
ms.sourcegitcommit: d8bf4976eafe3289275be3811e7cb721bfff7e1e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753415"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a>Visual Basic'de LINQ - XML Dönüşümüne Genel Bakış
Visual Basic için destek sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML değişmez değerleri ve XML eksen özellikleri aracılığıyla. Bu, Visual Basic kodunda XML ile çalışmak için tanıdık ve kolay bir sözdizimi kullanmanıza olanak sağlar. *XML değişmez değerleri* kodunuzda doğrudan XML dahil olanak sağlar. *XML eksen özellikleri* erişim alt düğümleri, alt düğümleri ve XML değişmez değeri özniteliklerini etkinleştir. Daha fazla bilgi için bkz: [XML değişmez değerlerine genel bakış](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md) ve [Visual Basic'te erişme XML](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] olan bir bellek içi XML programlama özellikle yararlanmak için tasarlanmış API [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Çağırabilirsiniz rağmen [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] doğrudan API'leri, yalnızca Visual Basic XML değişmez değerlerini bildirme ve XML eksen özellikleri doğrudan erişmesine olanak sağlar.  
  
> [!NOTE]
>  XML değişmez değerleri ve XML eksen özellikleri bildirim temelli kod sayfası ile desteklenmez. Visual Basic XML özellikleri kullanmak için ASP.NET uygulamanızın arka plan kodu sayfasında kodunuzu yerleştirin.  
  
 ![video bağlantı](../../../../visual-basic/programming-guide/language-features/xml/media/playvideo.gif "PlayVideo") ilgili video gösterileri için bkz: [nasıl t ile çalışmaya başlama LINQ-XML musunuz?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml) ve [nasıl yedeklerim Excel LINQ-XML kullanarak elektronik tablolar oluşturma?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml).  
  
## <a name="creating-xml"></a>XML oluşturma  
 Visual Basic'te XML ağaçları oluşturmanın iki yolu vardır. XML değişmez değer doğrudan kodda bildirebilir veya kullanabilirsiniz [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] ağacı oluşturmak için API'ler. Her iki işlem son XML ağaç yapısını yansıtmak için kodu etkinleştirin. Örneğin, aşağıdaki kod örneğinde bir XML öğesi oluşturur:  
  
 [!code-vb[VbXmlSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_1.vb)]  
  
 Daha fazla bilgi için bkz: [Visual Basic'de XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md).  
  
## <a name="accessing-and-navigating-xml"></a>Verilere erişme ve XML gezinme  
 Visual Basic erişmek ve XML yapıları gezinme XML eksen özellikleri sağlar. Bu özellikleri XML alt öğe adları belirterek XML öğeleri ve özniteliklerinin erişmenizi sağlar. Alternatif olarak, açıkça çağırabilirsiniz [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] gezinme ve öğeleri ve özniteliklerinin bulma yöntemleri. Örneğin, aşağıdaki kod örneğinde öznitelikleri ve bir XML öğesi alt öğelerinin başvurmak için XML eksen özellikleri kullanır. Kod örneği kullanan bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] alt öğelerini almak ve bunları etkili bir şekilde bir dönüştürme gerçekleştirmek XML öğeleri çıkış sorgu.  
  
 [!code-vb[VbXmlSamples#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_2.vb)]  
  
 Daha fazla bilgi için bkz: [Visual Basic'te erişme XML](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md).  
  
## <a name="xml-namespaces"></a>XML ad alanları  
 Visual Basic kullanarak genel bir XML ad alanı için bir diğer ad belirtmenizi sağlar `Imports` deyimi. Aşağıdaki örnekte nasıl kullanılacağını gösterir `Imports` deyimi bir XML ad alanı içe aktarmak için:  
  
 [!code-vb[VbXMLSamples#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_3.vb)]  
  
 XML eksen özellikleri erişmek ve XML belgelerini ve öğeler için XML değişmez değerlerini bildirme bir XML ad alanı diğer adı kullanabilirsiniz.  
  
 Alabileceğiniz bir <xref:System.Xml.Linq.XNamespace> nesnesi kullanarak belirli ad alanı öneki için [GetXmlNamespace işleci](../../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md).  
  
 Daha fazla bilgi için bkz: [Imports deyimi (XML Namespace)](../../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
### <a name="using-xml-namespaces-in-xml-literals"></a>XML değişmez değerlerine XML ad alanlarını kullanma  
 Aşağıdaki örnekte nasıl oluşturulacağını gösterir bir <xref:System.Xml.Linq.XElement> genel ad alanı kullanan nesneyi `ns`:  
  
 [!code-vb[VbXMLSamples#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_4.vb)]  
  
 Visual Basic derleyici XML ad alanları ile kullanmak için XML gösterimini kullanan eşdeğer koda XML ad alanı diğer adlarını içeren XML değişmez değerleri çevirir `xmlns` özniteliği. Derlendiğinde, önceki bölümün örnekteki kod temelde aynı yürütülebilir kod aşağıdaki örnekteki gibi üretir:  
  
 [!code-vb[VbXMLSamples#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_5.vb)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a>XML eksen özellikleri XML ad alanlarını kullanma  
 XML değişmez değerlerine bildirilen XML ad alanları XML eksen özellikleri kullanmak için kullanılabilir değil. Ancak, genel ad alanları ile XML eksen özellikleri kullanılabilir. XML ad alanı öneki yerel öğe adından ayırmak için iki nokta kullanın. Aşağıda bir örnek verilmiştir:  
  
 [!code-vb[VbXMLSamples#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/overview-of-linq-to-xml_6.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [Visual Basic'de XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Visual Basic'de XML'e erişme](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [Visual Basic'te XML düzenleme](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
