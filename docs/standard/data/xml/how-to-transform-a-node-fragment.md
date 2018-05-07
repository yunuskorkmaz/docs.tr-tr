---
title: 'Nasıl yapılır: bir düğümü parça dönüştürme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 73a6c582-b9d7-4fa7-9a05-6d931e1f3de8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4cd35e469a16dc2fdb3a7f4afd89d04f67185cd5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-transform-a-node-fragment"></a>Nasıl yapılır: bir düğümü parça dönüştürme
Dönüştürme zaman bulunan verileri bir <xref:System.Xml.XmlDocument> veya <xref:System.Xml.XPath.XPathDocument> XSLT dönüştürmeleri bir bütün olarak belgeye nesne. Belge kök düğümü dışında bir düğümünde geçirirseniz, diğer bir deyişle, bu dönüştürme süreci yüklenen belgedeki tüm düğümleri erişmesini engellemez. Bir düğüm parça dönüştürmek için yalnızca düğüm parça içeren ayrı bir nesne oluşturmak ve gerekir, nesneyi geçirmek <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi.  
  
## <a name="procedures"></a>Yordamlar  
  
#### <a name="to-transform-a-node-fragment"></a>Bir düğüm parça dönüştürmek için  
  
1.  Kaynak belge içeren bir nesne oluşturun.  
  
2.  Dönüştürmek istediğiniz düğümü parça bulun.  
  
3.  Ayrı bir nesne yalnızca düğüm parça ile oluşturun.  
  
4.  Düğüm parça geçirmek <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir düğüm parça dönüştürür ve sonuçlarını konsola çıkarır.  
  
 [!code-csharp[XSLT_NodeFrag#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_NodeFrag/CS/xslt_frag.cs#1)]
 [!code-vb[XSLT_NodeFrag#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_NodeFrag/VB/xslt_frag.vb#1)]  
  
### <a name="input"></a>Giriş  
  
##### <a name="booksxml"></a>Books.XML  
 [!code-xml[XML_Core_Files#1](../../../../samples/snippets/xml/VS_Snippets_Data/XML_Core_Files/XML/books.xml#1)]  
  
##### <a name="singlexsl"></a>Single.xsl  
 [!code-xml[XSLT_NodeFrag#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_NodeFrag/XML/single.xsl#2)]  
  
### <a name="output"></a>Çıkış  
 GÜVENİRLİK Man'ye kitap başlığı olduğu  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XslCompiledTransform Sınıfını Kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)
