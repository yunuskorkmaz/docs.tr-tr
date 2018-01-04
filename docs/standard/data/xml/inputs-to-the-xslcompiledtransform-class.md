---
title: "XslCompiledTransform sınıfı girişleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 834049f1-ab41-449e-9f10-4a1d0701bc48
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7aac1e85bdc27c9c8394eadcae841069115b369d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="inputs-to-the-xslcompiledtransform-class"></a>XslCompiledTransform sınıfı girişleri
<xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> Yöntemi kabul türleri kaynak belge için üç giriş: uygulayan bir nesne <xref:System.Xml.XPath.IXPathNavigable> arabirimi, bir <xref:System.Xml.XmlReader> kaynak belge ya da bir dize URI okur nesnesi.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı, varsayılan olarak boşluk korur. Bu W3C XSLT 1.0 öneri (Bölüm 3.4, http://www.w3.org/TR/xslt.html#strip) uygun şekilde 3.4 bölümüdür.  
  
## <a name="ixpathnavigable-interface"></a>IXPathNavigable arabirimi  
 <xref:System.Xml.XPath.IXPathNavigable> Arabirimi uygulandığına <xref:System.Xml.XmlNode> ve <xref:System.Xml.XPath.XPathDocument> sınıfları. Bu sınıfların XML verileri, bir bellek içi önbelleğini temsil eder.  
  
-   <xref:System.Xml.XmlNode> Sınıfı W3C belge nesne modeli (DOM) üzerinde temel alır ve düzenleme özellikleri içerir.  
  
-   <xref:System.Xml.XPath.XPathDocument> XPath veri modelini temel alan bir salt okunur veri deposu bir sınıftır. <xref:System.Xml.XPath.XPathDocument>XSLT için önerilen sınıf işliyor. Karşılaştırıldığında daha hızlı performans sağlar <xref:System.Xml.XmlNode> sınıfı.  
  
> [!NOTE]
>  Dönüşümleri belgeye bir bütün olarak uygulayın. Belge kök düğümü dışında bir düğümünde geçirirseniz, diğer bir deyişle, bu dönüştürme süreci yüklenen belgedeki tüm düğümleri erişmesini engellemez. Bir düğüm parça dönüştürmek için yalnızca düğüm parçasını içeren bir nesne oluşturmak ve gerekir, nesneyi geçirmek <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi. Daha fazla bilgi için bkz: [nasıl yapılır: bir düğümü parça dönüştürme](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md).  
  
 Aşağıdaki örnek kullanır <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> transform.xsl stil sayfası kullanılarak books.html dosya books.xml dosyasına dönüştürmek için yöntem. Books.xml ve transform.xsl dosyaları bu konu başlığı altında bulunabilir: [nasıl yapılır: bir derlemeyi kullanarak XSLT dönüşümü gerçekleştirmeye](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#1)]
 [!code-vb[XslCompiledTransform.Transform2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#1)]  
  
## <a name="xmlreader-object"></a>XmlReader nesnesi  
 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> Yöntemi yükler geçerli düğümden <xref:System.Xml.XmlReader> tüm alt öğelerini aracılığıyla. Bu, bir belgenin bir bölümünü bağlam belgesi olarak kullanmanıza olanak sağlar. Sonra <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi döndürür <xref:System.Xml.XmlReader> sonraki düğümü bağlam belgenin sonuna sonra yerleştirilir. Belgenin sonuna ulaşıldığında <xref:System.Xml.XmlReader> dosyanın sonuna (EOF) konumlandırıldı.  
  
 Aşağıdaki örnek kullanır <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> transform.xsl stil sayfası kullanılarak books.html dosya books.xml dosyasına dönüştürmek için yöntem. Books.xml ve transform.xsl dosyaları bu konu başlığı altında bulunabilir: [nasıl yapılır: bir derlemeyi kullanarak XSLT dönüşümü gerçekleştirmeye](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#2)]
 [!code-vb[XslCompiledTransform.Transform2#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#2)]  
  
## <a name="string-uri"></a>Dize URI  
 Ayrıca, kaynak belge URI giriş, XSLT belirtebilirsiniz. Bir <xref:System.Xml.XmlResolver> URI çözmek için kullanılır. Belirleyebileceğiniz <xref:System.Xml.XmlResolver> geçirerek kullanmak için <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi. Varsa bir <xref:System.Xml.XmlResolver> belirtilmezse, <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi kullanan bir varsayılan <xref:System.Xml.XmlUrlResolver> hiçbir kimlik bilgilerine sahip.  
  
 Aşağıdaki örnek kullanır <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=nameWithType> transform.xsl stil sayfası kullanılarak books.html dosya books.xml dosyasına dönüştürmek için yöntem. Books.xml ve transform.xsl dosyaları bu konu başlığı altında bulunabilir: [nasıl yapılır: bir derlemeyi kullanarak XSLT dönüşümü gerçekleştirmeye](../../../../docs/standard/data/xml/how-to-perform-an-xslt-transformation-by-using-an-assembly.md).  
  
 [!code-csharp[XslCompiledTransform.Transform2#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Transform2/CS/Program.cs#3)]
 [!code-vb[XslCompiledTransform.Transform2#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Transform2/VB/Module1.vb#3)]  
  
 Daha fazla bilgi için bkz: [çözme dış kaynaklara sırasında XSLT işleme](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)
