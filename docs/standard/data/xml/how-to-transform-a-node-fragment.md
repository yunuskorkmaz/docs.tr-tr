---
title: 'Nasıl yapılır: Düğüm Parçasını Dönüştürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
ms.openlocfilehash: f5eb8e7826dd132fd46f6f476335416e7dd03269
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722693"
---
# <a name="how-to-transform-a-node-fragment"></a>Nasıl yapılır: Düğüm Parçasını Dönüştürme

Bir veya nesnesinde bulunan verileri dönüştürdüğünüzde <xref:System.Xml.XmlDocument> <xref:System.Xml.XPath.XPathDocument> XSLT dönüştürmeleri bir belge için bir bütün olarak uygulanır. Diğer bir deyişle, belge kök düğümü dışında bir düğüm geçirirseniz, bu, dönüşüm işleminin yüklenen belgedeki tüm düğümlere erişmesini engellemez. Bir düğüm parçasını dönüştürmek için yalnızca düğüm parçasını içeren ayrı bir nesne oluşturmanız ve bu nesneyi yöntemine iletmeniz gerekir <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> .  
  
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
  
##### <a name="booksxml"></a>books.xml  

 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a>tek. Xsl  

 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a>Çıkış  

 Kitap başlığı, güvenirlik Man.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslCompiledTransform Sınıfını Kullanma](using-the-xslcompiledtransform-class.md)
