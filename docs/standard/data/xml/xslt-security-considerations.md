---
title: XSLT Güvenlik Konuları
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: fea695be-617c-4977-9567-140e820436fc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 683cf4a38ed08e0c569df62778c2ff80323ef261
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910486"
---
# <a name="xslt-security-considerations"></a>XSLT Güvenlik Konuları
XSLT dili, size harika bir güç ve esneklik sağlayan zengin bir özellik kümesine sahiptir. Bu, yararlı olsa da dış kaynaklar tarafından da yararlanılabilen birçok özellik içerir. XSLT 'yi güvenli bir şekilde kullanabilmek için XSLT kullanırken ortaya çıkan güvenlik sorunlarının türlerini ve bu riskleri azaltmak için kullanabileceğiniz temel stratejileri anlamanız gerekir.  
  
## <a name="xslt-extensions"></a>XSLT uzantıları  
 En popüler iki XSLT uzantısı stil sayfası komut dosyası ve uzantı nesneleridir. Bu uzantılar XSLT işlemcisinin kod yürütmesine izin verir.  
  
- Uzantı nesneleri, XSL dönüşümlerine programlama özellikleri ekler.  
  
- Betikler, `msxsl:script` uzantı öğesi kullanılarak stil sayfasına gömülebilir.  
  
### <a name="extension-objects"></a>Uzantı nesneleri  
 Uzantı nesneleri <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi kullanılarak eklenir. Uzantı nesnelerini desteklemek için FullTrust izin kümesi gereklidir. Bu, uzantı nesne kodu yürütüldüğünde izinlerin yükselmesinin gerçekleşmemesini sağlar. Metodu FullTrust izinleri olmadan <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> çağırmaya çalışmak, bir güvenlik özel durumunun oluşturulması durumunda oluşur.  
  
### <a name="style-sheet-scripts"></a>Stil sayfası betikleri  
 Betikler `msxsl:script` uzantı öğesi kullanılarak bir stil sayfasına gömülebilir. Komut dosyası desteği varsayılan olarak devre dışı bırakılan <xref:System.Xml.Xsl.XslCompiledTransform> sınıf üzerinde isteğe bağlı bir özelliktir. Komut dosyası, <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> özelliği olarak `true` ayarlanarak ve <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemine <xref:System.Xml.Xsl.XsltSettings> nesnesine geçirerek etkinleştirilebilir.  
  
#### <a name="guidelines"></a>Kuralları  
 Komut dosyasını yalnızca stil sayfası güvenilen bir kaynaktan geldiğinde etkinleştirin. Stil sayfasının kaynağını doğrulayamezseniz veya stil sayfası güvenilir bir kaynaktan geliyorsa XSLT ayarları bağımsız değişkenine geçiş `null` yapın.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 XSLT dili, `xsl:import` `xsl:include`, veya `document()` gibi özelliklere sahiptir; burada işlemci, URI başvurularını çözümlemek için gereklidir. Sınıfı <xref:System.Xml.XmlResolver> , dış kaynakları çözümlemek için kullanılır. Dış kaynakların aşağıdaki iki durumda çözümlenmesi gerekebilir:  
  
- Bir stil sayfası <xref:System.Xml.XmlResolver> derlerken, ve `xsl:include` çözümü için `xsl:import` kullanılır.  
  
- Dönüşüm <xref:System.Xml.XmlResolver> yürütürken `document()` işlevi çözümlemek için kullanılır.  
  
    > [!NOTE]
    > İşlev, <xref:System.Xml.Xsl.XslCompiledTransform> sınıfında varsayılan olarak devre dışıdır. `document()` Bu özellik, <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> özelliği olarak `true` ayarlanarak ve <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemine <xref:System.Xml.Xsl.XsltSettings> nesnesine geçirerek etkinleştirilebilir.  
  
 Ve yöntemlerinin her biri bağımsız değişkenlerinden biri <xref:System.Xml.XmlResolver> olarak kabul eden aşırı yüklemeleri içerir. <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> Belirtilmemişse, kimlik bilgileri olmayan bir varsayılan <xref:System.Xml.XmlUrlResolver> kullanılır. <xref:System.Xml.XmlResolver>  
  
#### <a name="guidelines"></a>Kuralları  
 `document()` İşlevi yalnızca, stil sayfası güvenilir bir kaynaktan geldiğinde etkinleştirin.  
  
 Aşağıdaki listede bir <xref:System.Xml.XmlResolver> nesne belirtmek isteyebileceğiniz zaman açıklanmaktadır:  
  
- XSLT işleminin kimlik doğrulaması gerektiren bir ağ kaynağına erişmesi gerekiyorsa, gerekli kimlik bilgileriyle bir <xref:System.Xml.XmlResolver> kullanabilirsiniz.  
  
- XSLT işleminin erişebileceği kaynakları kısıtlamak istiyorsanız, doğru izin kümesiyle bir <xref:System.Xml.XmlSecureResolver> kullanabilirsiniz. Denetlediğiniz veya güvenilmeyen bir kaynağı açmanız gerekiyorsa sınıfınıkullanın.<xref:System.Xml.XmlSecureResolver>  
  
- Davranışı özelleştirmek istiyorsanız kendi <xref:System.Xml.XmlResolver> sınıfınızı uygulayabilir ve kaynakları çözümlemek için kullanabilirsiniz.  
  
- Hiçbir dış kaynağa erişilmemesini sağlamak istiyorsanız `null` <xref:System.Xml.XmlResolver> bağımsız değişkeni için belirtebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)
- [XSLT İşleme Sırasında Dış Kaynakları Çözümleme](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)
- [Kod erişim güvenliği](../../../../docs/framework/misc/code-access-security.md)
