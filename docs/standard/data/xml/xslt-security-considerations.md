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
  
- Betikler `msxsl:script` uzantı öğesi kullanılarak stil sayfasına katıştırılabilir.  
  
### <a name="extension-objects"></a>Uzantı nesneleri  
 Uzantı nesneleri <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi kullanılarak eklenir. Uzantı nesnelerini desteklemek için FullTrust izin kümesi gereklidir. Bu, uzantı nesne kodu yürütüldüğünde izinlerin yükselmesinin gerçekleşmemesini sağlar. <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> metodunu FullTrust izinleri olmadan çağırmaya çalışmak, bir güvenlik özel durumunun oluşturulması durumunda oluşur.  
  
### <a name="style-sheet-scripts"></a>Stil sayfası betikleri  
 Betikler `msxsl:script` uzantı öğesi kullanılarak bir stil sayfasına gömülebilir. Betik desteği, varsayılan olarak devre dışı bırakılan <xref:System.Xml.Xsl.XslCompiledTransform> sınıfında isteğe bağlı bir özelliktir. Komut dosyası, <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> özelliği `true` olarak ayarlanarak ve <xref:System.Xml.Xsl.XsltSettings> nesnesini <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemine geçirerek etkinleştirilebilir.  
  
#### <a name="guidelines"></a>Kuralları  
 Komut dosyasını yalnızca stil sayfası güvenilen bir kaynaktan geldiğinde etkinleştirin. Stil sayfasının kaynağını doğrulayamezseniz veya stil sayfası güvenilen bir kaynaktan geliyorsa, XSLT ayarları bağımsız değişkeni için `null` geçirin.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 XSLT dili `xsl:import`, `xsl:include`veya `document()` işlevi gibi özelliklere sahiptir ve bu, işlemcinin URI başvurularını çözmesi gerekir. <xref:System.Xml.XmlResolver> sınıfı, dış kaynakları çözümlemek için kullanılır. Dış kaynakların aşağıdaki iki durumda çözümlenmesi gerekebilir:  
  
- Bir stil sayfası derlenirken, <xref:System.Xml.XmlResolver> `xsl:import` ve `xsl:include` çözümleme için kullanılır.  
  
- Dönüşüm yürütürken, `document()` işlevi çözümlemek için <xref:System.Xml.XmlResolver> kullanılır.  
  
    > [!NOTE]
    > `document()` işlevi <xref:System.Xml.Xsl.XslCompiledTransform> sınıfında varsayılan olarak devre dışıdır. Bu özellik, <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> özelliği `true` olarak ayarlanarak ve <xref:System.Xml.Xsl.XsltSettings> nesnesini <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemine geçirerek etkinleştirilebilir.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> ve <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemlerinin her biri, bağımsız değişkenlerinden biri olarak bir <xref:System.Xml.XmlResolver> kabul eden aşırı yüklemeleri içerir. Bir <xref:System.Xml.XmlResolver> belirtilmemişse, kimlik bilgileri olmayan bir varsayılan <xref:System.Xml.XmlUrlResolver> kullanılır.  
  
#### <a name="guidelines"></a>Kuralları  
 `document()` işlevini yalnızca stil sayfası güvenilen bir kaynaktan geldiğinde etkinleştirin.  
  
 Aşağıdaki listede bir <xref:System.Xml.XmlResolver> nesnesi belirtmek isteyebileceğiniz zaman açıklanmaktadır:  
  
- XSLT işleminin kimlik doğrulaması gerektiren bir ağ kaynağına erişmesi gerekiyorsa, gerekli kimlik bilgileriyle bir <xref:System.Xml.XmlResolver> kullanabilirsiniz.  
  
- XSLT işleminin erişebileceği kaynakları kısıtlamak istiyorsanız, doğru izin kümesiyle bir <xref:System.Xml.XmlSecureResolver> kullanabilirsiniz. Denetlediğiniz veya güvenilmeyen bir kaynağı açmanız gerekiyorsa <xref:System.Xml.XmlSecureResolver> sınıfını kullanın.  
  
- Davranışı özelleştirmek istiyorsanız kendi <xref:System.Xml.XmlResolver> sınıfınızı uygulayabilir ve kaynakları çözümlemek için kullanabilirsiniz.  
  
- Dış kaynaklara erişilmemesini sağlamak istiyorsanız <xref:System.Xml.XmlResolver> bağımsız değişkeni için `null` belirtebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)
- [XSLT İşleme Sırasında Dış Kaynakları Çözümleme](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)
- [Kod erişim güvenliği](../../../../docs/framework/misc/code-access-security.md)
