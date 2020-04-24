---
title: XSLT İşleme Sırasında Dış Kaynakları Çözümleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
ms.openlocfilehash: 58407d5f0c6e602af15f5b19b9a19cc6379b9af7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710290"
---
# <a name="resolving-external-resources-during-xslt-processing"></a>XSLT İşleme Sırasında Dış Kaynakları Çözümleme
Dış kaynakları çözmeniz gerekebilmeniz için bir XSLT dönüştürmesi sırasında birkaç zaman vardır.  
  
## <a name="using-the-xmlresolver-class"></a>XmlResolver sınıfını kullanma  
 Sınıfı <xref:System.Xml.XmlResolver> , dış kaynakları çözümlemek için kullanılır. Aşağıdaki tabloda XSLT işleme sırasında ne <xref:System.Xml.XmlResolver> zaman dahil olduğu açıklanır.  
  
|XSLT görevi|İçin XmlResolver kullanılma|  
|---------------|--------------------------------------|  
|Stil sayfasını derleyin.|Stil sayfasının URI 'sini çözümleyin.<br /><br /> '<br /><br /> Herhangi bir `xsl:import` veya `xsl:include` öğesinde URI başvurularını çözümleyin.|  
|Stil sayfasını yürütün.|Bağlam belgesinin URI 'sini çözümleyin.<br /><br /> '<br /><br /> Tüm XSLT `document()` işlevlerinde URI başvurularını çözümleyin.|  
  
 Ve <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemleri, bağımsız değişkenlerinden biri olarak bir <xref:System.Xml.XmlResolver> nesne alan aşırı yüklemeleri içerir. <xref:System.Xml.XmlResolver> Belirtilmemişse, kimlik bilgileri olmayan bir varsayılan <xref:System.Xml.XmlUrlResolver> kullanılır.  
  
 Aşağıdaki listede bir <xref:System.Xml.XmlResolver> nesne belirtmek isteyebileceğiniz zaman açıklanmaktadır:  
  
- XSLT işleminin kimlik doğrulaması gerektiren bir ağ kaynağına erişmesi gerekiyorsa, gerekli kimlik bilgileriyle bir <xref:System.Xml.XmlResolver> kullanabilirsiniz.  
  
- XSLT işleminin erişebileceği kaynakları kısıtlamak istiyorsanız, doğru izin kümesiyle bir <xref:System.Xml.XmlSecureResolver> kullanabilirsiniz. Denetlediğiniz veya <xref:System.Xml.XmlSecureResolver> güvenilmeyen bir kaynağı açmanız gerekiyorsa sınıfını kullanın.  
  
- Davranışı özelleştirmek istiyorsanız kendi <xref:System.Xml.XmlResolver> sınıfınızı uygulayabilir ve kaynakları çözümlemek için kullanabilirsiniz.  
  
- Hiçbir dış kaynağa erişilmemesini sağlamak istiyorsanız `null` <xref:System.Xml.XmlResolver> bağımsız değişkeni için belirtebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir ağ kaynağında depolanan bir stil sayfasını derler. Bir <xref:System.Xml.XmlUrlResolver> nesne, stil sayfasına erişmek için gereken kimlik bilgilerini belirtir.  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Xsl.XslCompiledTransform>
- <xref:System.Xml.Xsl.XsltSettings>
- [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)
