---
title: XSLT işleme sırasında dış kaynakları çözümleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7f73edf5912f8158db51ed070da8816d5b988b8d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555485"
---
# <a name="resolving-external-resources-during-xslt-processing"></a>XSLT işleme sırasında dış kaynakları çözümleme
Bazı birkaç kez XSLT dönüştürmesi sırasında dış kaynakları çözümleme gerekebilir.  
  
## <a name="using-the-xmlresolver-class"></a>XmlResolver sınıfını kullanma  
 <xref:System.Xml.XmlResolver> Sınıfı dış kaynakları çözümleme için kullanılır. Aşağıdaki tabloda, ne zaman açıklanmaktadır <xref:System.Xml.XmlResolver> XSLT işleme sırasında ilgili hale gelir.  
  
|XSLT görevi|XmlResolver ne için kullanılır|  
|---------------|--------------------------------------|  
|Stil sayfası derleyin.|Stil Sayfası URI çözümleyin.<br /><br /> - ve -<br /><br /> Herhangi bir URI başvuruları çözümlemek `xsl:import` veya `xsl:include` öğeleri.|  
|Stil sayfası yürütün.|Bağlam belge URI'sini çözümleyin.<br /><br /> - ve -<br /><br /> Tüm XSLT URI başvuruları çözümlemek `document()` işlevleri.|  
  
 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> Ve <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemleri dahil olması aşırı yüklemeler bir <xref:System.Xml.XmlResolver> bağımsız değişkenlerinden biri nesnesi. Varsa bir <xref:System.Xml.XmlResolver> belirtilmezse, varsayılan <xref:System.Xml.XmlUrlResolver> ile herhangi bir kimlik bilgisi kullanılır.  
  
 Aşağıdaki listede, ne zaman belirtmek isteyebilirsiniz açıklar bir <xref:System.Xml.XmlResolver> nesnesi:  
  
-   XSLT işlemi bir ağ kaynağına erişmesi gerekiyorsa, kimlik doğrulama gerektiren, kullanabileceğiniz bir <xref:System.Xml.XmlResolver> gerekli kimlik bilgileriyle.  
  
-   XSLT işlemi erişebildiği kaynakları kısıtlamak istiyorsanız, kullanabileceğiniz bir <xref:System.Xml.XmlSecureResolver> ile doğru izni ayarlayın. Kullanım <xref:System.Xml.XmlSecureResolver> değil denetleyen veya güvenilmeyen olan bir kaynak açmanız gerekirse sınıfı.  
  
-   Davranışını özelleştirmek istiyorsanız, kendi uygulayabileceğiniz <xref:System.Xml.XmlResolver> sınıfı ve kaynakları çözümlemek için kullanın.  
  
-   Belirtebileceğiniz hiçbir dış kaynaklara erişildiğini sağlamak istiyorsanız, `null` için <xref:System.Xml.XmlResolver> bağımsız değişken.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir ağ kaynakta depolanan bir stil sayfası derler. Bir <xref:System.Xml.XmlUrlResolver> nesnesini stil sayfası erişmek gereken kimlik bilgilerini belirtir.  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Xsl.XslCompiledTransform>
- <xref:System.Xml.Xsl.XsltSettings>
- [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)
