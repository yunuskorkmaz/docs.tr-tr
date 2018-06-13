---
title: Dış kaynaklara XSLT işleme sırasında çözme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 955b42a4bb9955a401265cf9537418bbfe8dd7c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569765"
---
# <a name="resolving-external-resources-during-xslt-processing"></a>Dış kaynaklara XSLT işleme sırasında çözme
Alırken birkaç kez XSLT dönüştürmesi sırasında dış kaynaklara çözmeniz gerekebilir.  
  
## <a name="using-the-xmlresolver-class"></a>XmlResolver sınıfını kullanma  
 <xref:System.Xml.XmlResolver> Sınıfı, dış kaynaklara çözmek için kullanılır. Aşağıdaki tabloda ne zaman açıklanmaktadır <xref:System.Xml.XmlResolver> XSLT işleme sırasında söz konusu olur.  
  
|XSLT görevi|XmlResolver için kullanılır|  
|---------------|--------------------------------------|  
|Stil sayfası derleyin.|Stil sayfası URI'sini çözümleyin.<br /><br /> - ve -<br /><br /> Herhangi bir URI başvuruları çözümlenemedi `xsl:import` veya `xsl:include` öğeleri.|  
|Stil sayfasını çalıştırın.|Bağlam belge URI'sini çözümleyin.<br /><br /> - ve -<br /><br /> Tüm XSLT URI başvuruları çözümleyin `document()` işlevleri.|  
  
 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> Ve <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemleri dahil almak aşırı bir <xref:System.Xml.XmlResolver> bağımsız değişkenlerinden biri olarak nesne. Varsa bir <xref:System.Xml.XmlResolver> belirtilmezse, varsayılan <xref:System.Xml.XmlUrlResolver> ile kimlik bilgileri kullanılır.  
  
 Aşağıdaki listede zaman belirtmek isteyebilirsiniz açıklanmaktadır bir <xref:System.Xml.XmlResolver> nesnesi:  
  
-   XSLT işlemi bir ağ kaynağına erişimi gerekiyorsa, kimlik doğrulaması gerektiren, kullanabileceğiniz bir <xref:System.Xml.XmlResolver> gerekli kimlik bilgilerine sahip.  
  
-   XSLT işlem erişebileceği kaynakları kısıtlamak istiyorsanız, kullanabileceğiniz bir <xref:System.Xml.XmlSecureResolver> doğru izniyle ayarlayın. Kullanım <xref:System.Xml.XmlSecureResolver> değil denetleyen veya güvenilmeyen olan bir kaynak açmanız gerekirse sınıfı.  
  
-   Davranışını özelleştirmek istiyorsanız, kendi uygulayabileceğiniz <xref:System.Xml.XmlResolver> sınıfı ve kaynakları gidermek için kullanın.  
  
-   Dış kaynak erişilen sağlamak istiyorsanız, belirtebilirsiniz `null` için <xref:System.Xml.XmlResolver> bağımsız değişkeni.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir ağ kaynağına depolanan bir stil sayfası derler. Bir <xref:System.Xml.XmlUrlResolver> nesne stil sayfası erişmek gereken kimlik bilgilerini belirtir.  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltSettings>  
 [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)
