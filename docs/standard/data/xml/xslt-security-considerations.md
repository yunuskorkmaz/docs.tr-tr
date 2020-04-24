---
title: XSLT Güvenlik Konuları
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: fea695be-617c-4977-9567-140e820436fc
ms.openlocfilehash: e6e490c0f637aace57dacc88ef49cc9be87532cd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709692"
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
 Betikler `msxsl:script` uzantı öğesi kullanılarak bir stil sayfasına gömülebilir. Komut dosyası desteği varsayılan olarak devre dışı bırakılan <xref:System.Xml.Xsl.XslCompiledTransform> sınıf üzerinde isteğe bağlı bir özelliktir. <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> Komut dosyası, özelliği `true` olarak ayarlanarak ve <xref:System.Xml.Xsl.XsltSettings> <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemine nesnesine geçirerek etkinleştirilebilir.  
  
#### <a name="guidelines"></a>Yönergeler  
 Komut dosyasını yalnızca stil sayfası güvenilen bir kaynaktan geldiğinde etkinleştirin. Stil sayfasının kaynağını doğrulayamezseniz veya stil sayfası güvenilir bir kaynaktan geliyorsa XSLT ayarları bağımsız değişkenine geçiş `null` yapın.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 XSLT dili, `xsl:import` `xsl:include`, veya `document()` gibi özelliklere sahiptir; burada işlemci, URI başvurularını çözümlemek için gereklidir. Sınıfı <xref:System.Xml.XmlResolver> , dış kaynakları çözümlemek için kullanılır. Dış kaynakların aşağıdaki iki durumda çözümlenmesi gerekebilir:  
  
- Bir stil sayfası <xref:System.Xml.XmlResolver> derlerken, ve `xsl:import` `xsl:include` çözümü için kullanılır.  
  
- Dönüşüm <xref:System.Xml.XmlResolver> yürütürken `document()` işlevi çözümlemek için kullanılır.  
  
    > [!NOTE]
    > `document()` İşlev, <xref:System.Xml.Xsl.XslCompiledTransform> sınıfında varsayılan olarak devre dışıdır. <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> Bu özellik, özelliği `true` olarak ayarlanarak ve <xref:System.Xml.Xsl.XsltSettings> <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemine nesnesine geçirerek etkinleştirilebilir.  
  
 Ve yöntemlerinin her biri bağımsız değişkenlerinden biri <xref:System.Xml.XmlResolver> olarak kabul eden aşırı yüklemeleri içerir. <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> <xref:System.Xml.XmlResolver> Belirtilmemişse, kimlik bilgileri olmayan bir varsayılan <xref:System.Xml.XmlUrlResolver> kullanılır.  
  
#### <a name="guidelines"></a>Yönergeler  
 `document()` İşlevi yalnızca, stil sayfası güvenilir bir kaynaktan geldiğinde etkinleştirin.  
  
 Aşağıdaki listede bir <xref:System.Xml.XmlResolver> nesne belirtmek isteyebileceğiniz zaman açıklanmaktadır:  
  
- XSLT işleminin kimlik doğrulaması gerektiren bir ağ kaynağına erişmesi gerekiyorsa, gerekli kimlik bilgileriyle bir <xref:System.Xml.XmlResolver> kullanabilirsiniz.  
  
- XSLT işleminin erişebileceği kaynakları kısıtlamak istiyorsanız, doğru izin kümesiyle bir <xref:System.Xml.XmlSecureResolver> kullanabilirsiniz. Denetlediğiniz veya <xref:System.Xml.XmlSecureResolver> güvenilmeyen bir kaynağı açmanız gerekiyorsa sınıfını kullanın.  
  
- Davranışı özelleştirmek istiyorsanız kendi <xref:System.Xml.XmlResolver> sınıfınızı uygulayabilir ve kaynakları çözümlemek için kullanabilirsiniz.  
  
- Hiçbir dış kaynağa erişilmemesini sağlamak istiyorsanız `null` <xref:System.Xml.XmlResolver> bağımsız değişkeni için belirtebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)
- [XSLT İşleme Sırasında Dış Kaynakları Çözümleme](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)
- [Kod Erişimi Güvenliği](../../../../docs/framework/misc/code-access-security.md)
