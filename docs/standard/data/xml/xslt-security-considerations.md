---
title: XSLT güvenlik konuları
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: fea695be-617c-4977-9567-140e820436fc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e369f570adf51355d02c73bde5d4b1a462e59870
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43422799"
---
# <a name="xslt-security-considerations"></a>XSLT güvenlik konuları
XSLT dili, güç ve esneklik büyük ölçüde size özellikleri zengin sahiptir. Bu, dış kaynaklar tarafından kullanışlı olsa da yararlanılabilir birçok özellik içerir. XSLT güvenli bir şekilde kullanmak için XSLT kullanma ortaya çıkan güvenlik sorunlarını ve bu riskleri azaltmak için uygulayabileceğiniz temel stratejiler türlerini anlamanız gerekir.  
  
## <a name="xslt-extensions"></a>XSLT uzantıları  
 İki popüler XSLT stil sayfası komut dosyası ve uzantı nesneleri uzantılarıdır. Bu uzantılar, kod yürütmek için XSLT işlemci izin verin.  
  
-   Genişletme nesneleri için XSL Dönüşümleri programlama özellikleri ekleyin.  
  
-   Betikler, stil sayfası kullanarak gömülebilir `msxsl:script` uzantı öğesi.  
  
### <a name="extension-objects"></a>Genişletme nesneleri  
 Genişletme nesneleri kullanarak eklenir <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi. FullTrust izin kümesi, genişletme nesneleri desteklemek için gereklidir. Bu uzantı nesne kod yürütüldüğünde izinler yükselmesi gerçekleşmez sağlar. Arama girişimi <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi olmadan oluşturulan bir güvenlik özel durumu FullTrust izinlerini sonuçlanır.  
  
### <a name="style-sheet-scripts"></a>Stil sayfası betikleri  
 Betikler, stil sayfası kullanılarak içinde gömülebilir `msxsl:script` uzantı öğesi. Betik desteği üzerinde isteğe bağlı bir özellik olan <xref:System.Xml.Xsl.XslCompiledTransform> varsayılan olarak devre dışıdır sınıfı. Komut dosyası kullanılarak etkinleştirilebilir ayarlayarak <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> özelliğini `true` ve geçirerek <xref:System.Xml.Xsl.XsltSettings> nesnesini <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemi.  
  
#### <a name="guidelines"></a>Kuralları  
 Stil sayfası güvenilir bir kaynaktan geldiğinden, yalnızca komut dosyasını etkinleştirin. Stil sayfası kaynak doğrulanamıyor veya stil sayfası, güvenilen bir kaynaktan geliyor değil, geçirin `null` XSLT ayarları bağımsız değişkeni.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 XSLT dili gibi özelliklere sahip `xsl:import`, `xsl:include`, veya `document()` işlemci gereken yere URI başvuruları çözümlemek için işlevi. <xref:System.Xml.XmlResolver> Sınıfı dış kaynakları çözümleme için kullanılır. Dış Kaynaklar aşağıdaki iki durumda da çözülmesi gerekebilir:  
  
-   Bir stil sayfası derlenirken <xref:System.Xml.XmlResolver> için kullanılan `xsl:import` ve `xsl:include` çözümleme.  
  
-   Dönüştürme yürütülürken <xref:System.Xml.XmlResolver> çözümlemek için kullanılan `document()` işlevi.  
  
    > [!NOTE]
    >  `document()` İşlevi varsayılan olarak devre dışıdır üzerinde <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bu özellik, ayarlayarak etkinleştirilebilir <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> özelliğini `true` ve geçirerek <xref:System.Xml.Xsl.XsltSettings> nesnesini <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemi.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> Ve <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemleri, her dahil kabul eden aşırı yüklemeler bir <xref:System.Xml.XmlResolver> bağımsız değişkenlerinden biri olarak. Varsa bir <xref:System.Xml.XmlResolver> belirtilmezse, varsayılan <xref:System.Xml.XmlUrlResolver> ile herhangi bir kimlik bilgisi kullanılır.  
  
#### <a name="guidelines"></a>Kuralları  
 Etkinleştirme `document()` stil sayfası güvenilir bir kaynaktan geldiğinde işlev.  
  
 Aşağıdaki listede, ne zaman belirtmek isteyebilirsiniz açıklar bir <xref:System.Xml.XmlResolver> nesnesi:  
  
-   XSLT işlemi bir ağ kaynağına erişmesi gerekiyorsa, kimlik doğrulama gerektiren, kullanabileceğiniz bir <xref:System.Xml.XmlResolver> gerekli kimlik bilgileriyle.  
  
-   XSLT işlemi erişebildiği kaynakları kısıtlamak istiyorsanız, kullanabileceğiniz bir <xref:System.Xml.XmlSecureResolver> ile doğru izni ayarlayın. Kullanım <xref:System.Xml.XmlSecureResolver> değil denetleyen veya güvenilmeyen olan bir kaynak açmanız gerekirse sınıfı.  
  
-   Davranışını özelleştirmek istiyorsanız, kendi uygulayabileceğiniz <xref:System.Xml.XmlResolver> sınıfı ve kaynakları çözümlemek için kullanın.  
  
-   Belirtebileceğiniz hiçbir dış kaynaklara erişildiğini sağlamak istiyorsanız, `null` için <xref:System.Xml.XmlResolver> bağımsız değişken.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [XSLT İşleme Sırasında Dış Kaynakları Çözümleme](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 [Kod erişimi güvenliği](https://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03)
