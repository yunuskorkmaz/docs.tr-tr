---
title: 'Nasıl yapılır: düğüm parçasını dönüştürme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb258b61664e1fdbf6604afdf69074c48cf5bda4
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44061357"
---
# <a name="how-to-transform-a-node-fragment"></a>Nasıl yapılır: düğüm parçasını dönüştürme
İçerdiği verileri dönüştürme ne zaman bir <xref:System.Xml.XmlDocument> veya <xref:System.Xml.XPath.XPathDocument> XSLT dönüşümleri uygulamak için bir belgenin bir bütün olarak nesnesi. Belge kök düğümü dışındaki bir düğümde geçirirseniz, diğer bir deyişle, bu dönüştürme süreci yüklenen belgedeki tüm düğümleri erişmesini engellemez. Düğüm parçasını dönüştürme için yalnızca düğüm parçasını içeren ayrı bir nesne oluşturun ve gerekir, nesneyi geçirmek <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-transform-a-node-fragment"></a>Düğüm parçasını dönüştürme için  
  
1.  Kaynak belge içeren bir nesne oluşturun.  
  
2.  Dönüştürmek istediğiniz düğüm parçasını bulun.  
  
3.  Ayrı bir nesne yalnızca düğüm parçasını ile oluşturun.  
  
4.  Geçirmek için düğüm parçasını <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir düğüm parçasını dönüştürür ve sonuçlarını konsola çıkartır.  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a>Giriş  
  
##### <a name="booksxml"></a>Books.XML  
 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a>Single.xsl  
 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a>Çıkış  
 Güvenle el kitabı başlıktır  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslCompiledTransform Sınıfını Kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
