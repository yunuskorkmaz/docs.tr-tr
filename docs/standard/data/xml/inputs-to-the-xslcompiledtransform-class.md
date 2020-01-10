---
title: XslCompiledTransform Sınıfına Girişler
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 834049f1-ab41-449e-9f10-4a1d0701bc48
ms.openlocfilehash: 9aae85aa4516dc0555e959358ba1b7db3002145d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710745"
---
# <a name="inputs-to-the-xslcompiledtransform-class"></a>XslCompiledTransform Sınıfına Girişler
<xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi kaynak belge için üç giriş türü kabul eder: <xref:System.Xml.XPath.IXPathNavigable> arabirimini uygulayan bir nesne, kaynak belgeyi okuyan bir <xref:System.Xml.XmlReader> nesnesi veya dize URI 'SI.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı varsayılan olarak boşluğu korur. Bu, [W3C XSLT 1,0 önerisi 3,4 bölümüne](https://www.w3.org/TR/xslt.html#strip)göre belirlenir.  
  
## <a name="ixpathnavigable-interface"></a>Ixpathgezinebilir arabirimi  
 <xref:System.Xml.XPath.IXPathNavigable> arabirimi <xref:System.Xml.XmlNode> ve <xref:System.Xml.XPath.XPathDocument> sınıflarında uygulanır. Bu sınıflar, XML verilerinin bellek içi önbelleğini temsil eder.  
  
- <xref:System.Xml.XmlNode> sınıfı, W3C Belge Nesne Modeli (DOM) temel alır ve Düzenle özelliklerini içerir.  
  
- <xref:System.Xml.XPath.XPathDocument> sınıfı, XPath veri modelini temel alan bir salt okuma veri deposudur. <xref:System.Xml.XPath.XPathDocument> XSLT işleme için önerilen sınıftır. <xref:System.Xml.XmlNode> sınıfıyla karşılaştırıldığında daha hızlı performans sağlar.  
  
> [!NOTE]
> Dönüşümler belgeye bir bütün olarak uygulanır. Diğer bir deyişle, belge kök düğümü dışında bir düğüm geçirirseniz, bu, dönüşüm işleminin yüklenen belgedeki tüm düğümlere erişmesini engellemez. Bir düğüm parçasını dönüştürmek için, yalnızca düğüm parçasını içeren bir nesne oluşturmanız ve bu nesneyi <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemine iletmeniz gerekir. Daha fazla bilgi için bkz. [nasıl yapılır: düğüm parçasını dönüştürme](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md).  
  
 Aşağıdaki örnek,. xml dosyasını, Transform. xsl stil sayfasını kullanarak Books. html dosyasına dönüştürmek için <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> yöntemini kullanır. Books. xml ve Transform. XSL dosyaları bu konuda bulunabilir: [nasıl yapılır: bütünleştirilmiş kod kullanarak XSLT dönüşümü gerçekleştirme](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#1)]
 [!code-vb[XslCompiledTransform.Transform2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#1)]  
  
## <a name="xmlreader-object"></a>XmlReader nesnesi  
 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi, tüm alt öğeleri aracılığıyla <xref:System.Xml.XmlReader> geçerli düğümünden yüklenir. Bu, bir belgenin bir kısmını bağlam belgesi olarak kullanmanıza olanak sağlar. <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi çağrıldıktan sonra, <xref:System.Xml.XmlReader> bağlam belgesinin sonundan sonraki düğümde konumlandırılır. Belgenin sonuna ulaşılırsa <xref:System.Xml.XmlReader> dosyanın sonuna (EOF) yerleştirilir.  
  
 Aşağıdaki örnek,. xml dosyasını, Transform. xsl stil sayfasını kullanarak Books. html dosyasına dönüştürmek için <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> yöntemini kullanır. Books. xml ve Transform. XSL dosyaları bu konuda bulunabilir: [nasıl yapılır: bütünleştirilmiş kod kullanarak XSLT dönüşümü gerçekleştirme](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#2)]
 [!code-vb[XslCompiledTransform.Transform2#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#2)]  
  
## <a name="string-uri"></a>Dize URI 'SI  
 Ayrıca, XSLT girdisi olarak kaynak belge URI 'sini de belirtebilirsiniz. URI 'yi çözümlemek için bir <xref:System.Xml.XmlResolver> kullanılır. <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemine geçirerek kullanılacak <xref:System.Xml.XmlResolver> belirtebilirsiniz. <xref:System.Xml.XmlResolver> belirtilmemişse <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi, kimlik bilgileri olmadan varsayılan <xref:System.Xml.XmlUrlResolver> kullanır.  
  
 Aşağıdaki örnek,. xml dosyasını, Transform. xsl stil sayfasını kullanarak Books. html dosyasına dönüştürmek için <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> yöntemini kullanır. Books. xml ve Transform. XSL dosyaları bu konuda bulunabilir: [nasıl yapılır: bütünleştirilmiş kod kullanarak XSLT dönüşümü gerçekleştirme](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#3)]
 [!code-vb[XslCompiledTransform.Transform2#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#3)]  
  
 Daha fazla bilgi için bkz. [XSLT Işleme sırasında dış kaynakları çözümleme](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)
