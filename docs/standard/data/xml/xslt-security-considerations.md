---
title: XSLT Güvenlik Konuları
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: fea695be-617c-4977-9567-140e820436fc
ms.openlocfilehash: 81db764016607ebe6facfc530dbb2bac8e6b8cfe
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282520"
---
# <a name="xslt-security-considerations"></a>XSLT Güvenlik Konuları
XSLT dili, size harika bir güç ve esneklik sağlayan zengin bir özellik kümesine sahiptir. Bu, yararlı olsa da dış kaynaklar tarafından da yararlanılabilen birçok özellik içerir. XSLT 'yi güvenli bir şekilde kullanabilmek için XSLT kullanırken ortaya çıkan güvenlik sorunlarının türlerini ve bu riskleri azaltmak için kullanabileceğiniz temel stratejileri anlamanız gerekir.  
  
## <a name="xslt-extensions"></a>XSLT uzantıları  
 En popüler iki XSLT uzantısı stil sayfası komut dosyası ve uzantı nesneleridir. Bu uzantılar XSLT işlemcisinin kod yürütmesine izin verir.  
  
- Uzantı nesneleri, XSL dönüşümlerine programlama özellikleri ekler.  
  
- Betikler, uzantı öğesi kullanılarak stil sayfasına gömülebilir `msxsl:script` .  
  
### <a name="extension-objects"></a>Uzantı nesneleri  
 Uzantı nesneleri yöntemi kullanılarak eklenir <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> . Uzantı nesnelerini desteklemek için FullTrust izin kümesi gereklidir. Bu, uzantı nesne kodu yürütüldüğünde izinlerin yükselmesinin gerçekleşmemesini sağlar. <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>Metodu FullTrust izinleri olmadan çağırmaya çalışmak, bir güvenlik özel durumunun oluşturulması durumunda oluşur.  
  
### <a name="style-sheet-scripts"></a>Stil sayfası betikleri  
 Betikler uzantı öğesi kullanılarak bir stil sayfasına gömülebilir `msxsl:script` . Komut dosyası desteği <xref:System.Xml.Xsl.XslCompiledTransform> Varsayılan olarak devre dışı bırakılan sınıf üzerinde isteğe bağlı bir özelliktir. Komut dosyası, <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> özelliği olarak ayarlanarak `true` ve <xref:System.Xml.Xsl.XsltSettings> yöntemine nesnesine geçirerek etkinleştirilebilir <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> .  
  
#### <a name="guidelines"></a>Yönergeler  
 Komut dosyasını yalnızca stil sayfası güvenilen bir kaynaktan geldiğinde etkinleştirin. Stil sayfasının kaynağını doğrulayamezseniz veya stil sayfası güvenilir bir kaynaktan geliyorsa `null` XSLT ayarları bağımsız değişkenine geçiş yapın.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 XSLT dili,, veya gibi özelliklere sahiptir; `xsl:import` `xsl:include` `document()` burada işlemci, URI başvurularını çözümlemek için gereklidir. <xref:System.Xml.XmlResolver>Sınıfı, dış kaynakları çözümlemek için kullanılır. Dış kaynakların aşağıdaki iki durumda çözümlenmesi gerekebilir:  
  
- Bir stil sayfası derlerken, <xref:System.Xml.XmlResolver> `xsl:import` ve çözümü için kullanılır `xsl:include` .  
  
- Dönüşüm yürütürken <xref:System.Xml.XmlResolver> İşlevi çözümlemek için kullanılır `document()` .  
  
    > [!NOTE]
    > `document()`İşlev, sınıfında varsayılan olarak devre dışıdır <xref:System.Xml.Xsl.XslCompiledTransform> . Bu özellik, <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> özelliği olarak ayarlanarak `true` ve <xref:System.Xml.Xsl.XsltSettings> yöntemine nesnesine geçirerek etkinleştirilebilir <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> .  
  
 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A>Ve <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemlerinin her biri <xref:System.Xml.XmlResolver> bağımsız değişkenlerinden biri olarak kabul eden aşırı yüklemeleri içerir. <xref:System.Xml.XmlResolver>Belirtilmemişse, <xref:System.Xml.XmlUrlResolver> kimlik bilgileri olmayan bir varsayılan kullanılır.  
  
#### <a name="guidelines"></a>Yönergeler  
 `document()`İşlevi yalnızca, stil sayfası güvenilir bir kaynaktan geldiğinde etkinleştirin.  
  
 Aşağıdaki listede bir nesne belirtmek isteyebileceğiniz zaman açıklanmaktadır <xref:System.Xml.XmlResolver> :  
  
- XSLT işleminin kimlik doğrulaması gerektiren bir ağ kaynağına erişmesi gerekiyorsa, <xref:System.Xml.XmlResolver> gerekli kimlik bilgileriyle bir kullanabilirsiniz.  
  
- XSLT işleminin erişebileceği kaynakları kısıtlamak istiyorsanız, <xref:System.Xml.XmlSecureResolver> doğru izin kümesiyle bir kullanabilirsiniz. <xref:System.Xml.XmlSecureResolver>Denetlediğiniz veya güvenilmeyen bir kaynağı açmanız gerekiyorsa sınıfını kullanın.  
  
- Davranışı özelleştirmek istiyorsanız kendi <xref:System.Xml.XmlResolver> sınıfınızı uygulayabilir ve kaynakları çözümlemek için kullanabilirsiniz.  
  
- Hiçbir dış kaynağa erişilmemesini sağlamak istiyorsanız `null` <xref:System.Xml.XmlResolver> bağımsız değişkeni için belirtebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Dönüşümleri](xslt-transformations.md)
- [XSLT İşleme Sırasında Dış Kaynakları Çözümleme](resolving-external-resources-during-xslt-processing.md)
- [Kod Erişimi Güvenliği](../../../framework/misc/code-access-security.md)
