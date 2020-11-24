---
title: XSLT İşleme Sırasında Dış Kaynakları Çözümleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
ms.openlocfilehash: 5d50711eda266cecdb817c778f04aa845fa4c342
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686650"
---
# <a name="resolving-external-resources-during-xslt-processing"></a>XSLT İşleme Sırasında Dış Kaynakları Çözümleme

Dış kaynakları çözmeniz gerekebilmeniz için bir XSLT dönüştürmesi sırasında birkaç zaman vardır.  
  
## <a name="using-the-xmlresolver-class"></a>XmlResolver sınıfını kullanma  

 <xref:System.Xml.XmlResolver>Sınıfı, dış kaynakları çözümlemek için kullanılır. Aşağıdaki tabloda <xref:System.Xml.XmlResolver> XSLT işleme sırasında ne zaman dahil olduğu açıklanır.  
  
|XSLT görevi|İçin XmlResolver kullanılma|  
|---------------|--------------------------------------|  
|Stil sayfasını derleyin.|Stil sayfasının URI 'sini çözümleyin.<br /><br /> '<br /><br /> Herhangi bir veya öğesinde URI başvurularını çözümleyin `xsl:import` `xsl:include` .|  
|Stil sayfasını yürütün.|Bağlam belgesinin URI 'sini çözümleyin.<br /><br /> '<br /><br /> Tüm XSLT işlevlerinde URI başvurularını çözümleyin `document()` .|  
  
 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A>Ve <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemleri, <xref:System.Xml.XmlResolver> bağımsız değişkenlerinden biri olarak bir nesne alan aşırı yüklemeleri içerir. <xref:System.Xml.XmlResolver>Belirtilmemişse, <xref:System.Xml.XmlUrlResolver> kimlik bilgileri olmayan bir varsayılan kullanılır.  
  
 Aşağıdaki listede bir nesne belirtmek isteyebileceğiniz zaman açıklanmaktadır <xref:System.Xml.XmlResolver> :  
  
- XSLT işleminin kimlik doğrulaması gerektiren bir ağ kaynağına erişmesi gerekiyorsa, <xref:System.Xml.XmlResolver> gerekli kimlik bilgileriyle bir kullanabilirsiniz.  
  
- XSLT işleminin erişebileceği kaynakları kısıtlamak istiyorsanız, <xref:System.Xml.XmlSecureResolver> doğru izin kümesiyle bir kullanabilirsiniz. <xref:System.Xml.XmlSecureResolver>Denetlediğiniz veya güvenilmeyen bir kaynağı açmanız gerekiyorsa sınıfını kullanın.  
  
- Davranışı özelleştirmek istiyorsanız kendi <xref:System.Xml.XmlResolver> sınıfınızı uygulayabilir ve kaynakları çözümlemek için kullanabilirsiniz.  
  
- Hiçbir dış kaynağa erişilmemesini sağlamak istiyorsanız `null` <xref:System.Xml.XmlResolver> bağımsız değişkeni için belirtebilirsiniz.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, bir ağ kaynağında depolanan bir stil sayfasını derler. Bir <xref:System.Xml.XmlUrlResolver> nesne, stil sayfasına erişmek için gereken kimlik bilgilerini belirtir.  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Xsl.XslCompiledTransform>
- <xref:System.Xml.Xsl.XsltSettings>
- [XSLT Dönüşümleri](xslt-transformations.md)
