---
title: XslCompiledTransform Sınıfına Girişler
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 834049f1-ab41-449e-9f10-4a1d0701bc48
ms.openlocfilehash: 1452bc19940a33aeebaccf3041857a07c976964d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287655"
---
# <a name="inputs-to-the-xslcompiledtransform-class"></a>XslCompiledTransform Sınıfına Girişler
<xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>Yöntemi, kaynak belge için üç giriş türü kabul eder: arabirimi uygulayan bir nesne <xref:System.Xml.XPath.IXPathNavigable> , <xref:System.Xml.XmlReader> kaynak belgeyi okuyan bir nesne veya dize URI 'si.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslCompiledTransform>Sınıfı varsayılan olarak boşluğu korur. Bu, [W3C XSLT 1,0 önerisi 3,4 bölümüne](https://www.w3.org/TR/xslt.html#strip)göre belirlenir.  
  
## <a name="ixpathnavigable-interface"></a>Ixpathgezinebilir arabirimi  
 <xref:System.Xml.XPath.IXPathNavigable>Arabirim, <xref:System.Xml.XmlNode> ve <xref:System.Xml.XPath.XPathDocument> sınıflarında uygulanır. Bu sınıflar, XML verilerinin bellek içi önbelleğini temsil eder.  
  
- <xref:System.Xml.XmlNode>Sınıfı, W3C belge nesne modeli (DOM) temel alır ve Düzenle özelliklerini içerir.  
  
- <xref:System.Xml.XPath.XPathDocument>Sınıfı, XPath veri modelini temel alan bir salt okuma veri deposudur. <xref:System.Xml.XPath.XPathDocument>XSLT işleme için önerilen sınıftır. Sınıfla karşılaştırıldığında daha hızlı performans sağlar <xref:System.Xml.XmlNode> .  
  
> [!NOTE]
> Dönüşümler belgeye bir bütün olarak uygulanır. Diğer bir deyişle, belge kök düğümü dışında bir düğüm geçirirseniz, bu, dönüşüm işleminin yüklenen belgedeki tüm düğümlere erişmesini engellemez. Bir düğüm parçasını dönüştürmek için, yalnızca düğüm parçasını içeren bir nesne oluşturmanız ve bu nesneyi yöntemine iletmeniz gerekir <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> . Daha fazla bilgi için bkz. [nasıl yapılır: düğüm parçasını dönüştürme](how-to-transform-a-node-fragment.md).  
  
 Aşağıdaki örnek,. <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> XML dosyasını, Transform. xsl stil sayfasını kullanarak Books. html dosyasına dönüştürmek için yöntemini kullanır. Books. xml ve Transform. XSL dosyaları bu konuda bulunabilir: [nasıl yapılır: bütünleştirilmiş kod kullanarak XSLT dönüşümü gerçekleştirme](how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#1)]
 [!code-vb[XslCompiledTransform.Transform2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#1)]  
  
## <a name="xmlreader-object"></a>XmlReader nesnesi  
 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>Yöntemi, öğesinin geçerli düğümünden <xref:System.Xml.XmlReader> tüm alt öğeleri aracılığıyla yüklenir. Bu, bir belgenin bir kısmını bağlam belgesi olarak kullanmanıza olanak sağlar. Yöntem çağrıldıktan sonra, bir <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> <xref:System.Xml.XmlReader> sonraki düğümde bağlam belgesi sonundan sonra konumlandırılır. Belgenin sonuna ulaşılırsa, <xref:System.Xml.XmlReader> dosyanın sonuna (EOF) yerleştirilir.  
  
 Aşağıdaki örnek,. <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> XML dosyasını, Transform. xsl stil sayfasını kullanarak Books. html dosyasına dönüştürmek için yöntemini kullanır. Books. xml ve Transform. XSL dosyaları bu konuda bulunabilir: [nasıl yapılır: bütünleştirilmiş kod kullanarak XSLT dönüşümü gerçekleştirme](how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#2)]
 [!code-vb[XslCompiledTransform.Transform2#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#2)]  
  
## <a name="string-uri"></a>Dize URI 'SI  
 Ayrıca, XSLT girdisi olarak kaynak belge URI 'sini de belirtebilirsiniz. , <xref:System.Xml.XmlResolver> URI 'yi çözümlemek için kullanılır. <xref:System.Xml.XmlResolver> <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> Yöntemini yöntemine geçirerek belirtebilirsiniz. <xref:System.Xml.XmlResolver>Belirtilmemişse, <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi <xref:System.Xml.XmlUrlResolver> kimlik bilgileri olmayan bir varsayılan kullanır.  
  
 Aşağıdaki örnek,. <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> XML dosyasını, Transform. xsl stil sayfasını kullanarak Books. html dosyasına dönüştürmek için yöntemini kullanır. Books. xml ve Transform. XSL dosyaları bu konuda bulunabilir: [nasıl yapılır: bütünleştirilmiş kod kullanarak XSLT dönüşümü gerçekleştirme](how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#3)]
 [!code-vb[XslCompiledTransform.Transform2#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#3)]  
  
 Daha fazla bilgi için bkz. [XSLT Işleme sırasında dış kaynakları çözümleme](resolving-external-resources-during-xslt-processing.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Dönüşümleri](xslt-transformations.md)
