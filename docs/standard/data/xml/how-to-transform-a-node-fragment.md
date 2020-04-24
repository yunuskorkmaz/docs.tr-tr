---
title: 'Nasıl yapılır: Düğüm Parçasını Dönüştürme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
ms.openlocfilehash: 56e9ef6031a5736acfa066ed6c068f954bd5af8d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710823"
---
# <a name="how-to-transform-a-node-fragment"></a>Nasıl yapılır: Düğüm Parçasını Dönüştürme
Bir <xref:System.Xml.XmlDocument> veya <xref:System.Xml.XPath.XPathDocument> NESNESINDE bulunan verileri dönüştürdüğünüzde XSLT dönüştürmeleri bir belge için bir bütün olarak uygulanır. Diğer bir deyişle, belge kök düğümü dışında bir düğüm geçirirseniz, bu, dönüşüm işleminin yüklenen belgedeki tüm düğümlere erişmesini engellemez. Bir düğüm parçasını dönüştürmek için yalnızca düğüm parçasını içeren ayrı bir nesne oluşturmanız ve bu nesneyi <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemine iletmeniz gerekir.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-transform-a-node-fragment"></a>Düğüm parçasını dönüştürmek için  
  
1. Kaynak belgeyi içeren bir nesne oluşturun.  
  
2. Dönüştürmek istediğiniz düğüm parçasını bulun.  
  
3. Yalnızca düğüm parçamı ile ayrı bir nesne oluşturun.  
  
4. Düğüm parçasını <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> metoduna geçirin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir düğüm parçasını dönüştürür ve sonuçları konsola verir.  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a>Giriş  
  
##### <a name="booksxml"></a>Books. xml  
 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a>tek. Xsl  
 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a>Çıktı  
 Kitap başlığı, güvenirlik Man.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslCompiledTransform Sınıfını Kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
