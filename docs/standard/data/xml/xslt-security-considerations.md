---
title: "XSLT güvenlik konuları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fea695be-617c-4977-9567-140e820436fc
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7388bbc388dd46a30486a2300150bc9d1566593e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="xslt-security-considerations"></a>XSLT güvenlik konuları
XSLT dili gücü ve esnekliği büyük bir bölümünü size özellikleri zengin bir dizi var. Dış kaynak tarafından kullanışlı olsa da yararlanılabilir, birçok özellik içerir. XSLT güvenli bir şekilde kullanmak için XSLT kullanırken çıkabilecek güvenlik sorunlarını ve bu riskleri azaltmak için uygulayabileceğiniz temel stratejileri türlerini anlamanız gerekir.  
  
## <a name="xslt-extensions"></a>XSLT uzantıları  
 İki popüler XSLT uzantıları stil sayfası komut dosyası ve uzantısı nesneleridir. Bu uzantılar XSLT işlemcisine kod yürütmesine izin verin.  
  
-   Uzantı nesneleri XSL Dönüşümleri programlama özellikleri ekleyin.  
  
-   Komut dosyaları katıştırılmış stil sayfası kullanımında `msxsl:script` uzantı öğesi.  
  
### <a name="extension-objects"></a>Uzantı nesneleri  
 Uzantı nesneleri kullanarak eklenir <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> yöntemi. FullTrust izin kümesi uzantısı nesnelerinin desteklemek için gereklidir. Bu uzantı nesne kodu çalıştırıldığında izinleri ayrıcalıkların gerçekleşmez sağlar. Çağrı girişimi <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> FullTrust izinlerini sonuçlarında oluşturulan bir güvenlik özel durumu olmadan yöntemi.  
  
### <a name="style-sheet-scripts"></a>Stil sayfası komut dosyaları  
 Komut dosyaları katıştırılmış kullanarak bir stil sayfası `msxsl:script` uzantı öğesi. Komut dosyası desteği üzerinde isteğe bağlı bir özellik olan <xref:System.Xml.Xsl.XslCompiledTransform> varsayılan olarak devre dışıdır sınıfı. Komut dosyası etkinleştirilebilir ayarlayarak <xref:System.Xml.Xsl.XsltSettings.EnableScript%2A?displayProperty=nameWithType> özelliğine `true` ve geçirme <xref:System.Xml.Xsl.XsltSettings> nesnesinin <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemi.  
  
#### <a name="guidelines"></a>Kuralları  
 Stil sayfası güvenilen bir kaynaktan geldiğinden, yalnızca komut dosyası etkinleştirin. Stil sayfası kaynağı doğrulanamıyor veya stil sayfası güvenilen bir kaynaktan geliyor değil, geçirin `null` XSLT ayarları bağımsız değişkeni.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 XSLT dili gibi özelliklere sahiptir `xsl:import`, `xsl:include`, veya `document()` işlevi, burada işlemci gereken URI başvuruları çözümlenemedi. <xref:System.Xml.XmlResolver> Sınıfı, dış kaynaklara çözmek için kullanılır. Dış kaynaklara aşağıdaki iki durumda da çözümlenmesi gerekebilir:  
  
-   Stil sayfası derlerken <xref:System.Xml.XmlResolver> için kullanılan `xsl:import` ve `xsl:include` çözümleme.  
  
-   Dönüşümün yürütürken <xref:System.Xml.XmlResolver> çözümlemek için kullanılan `document()` işlevi.  
  
    > [!NOTE]
    >  `document()` İşlevi devre dışı bırakılmış varsayılan olarak <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bu özellik ayarlayarak etkinleştirilebilir <xref:System.Xml.Xsl.XsltSettings.EnableDocumentFunction%2A?displayProperty=nameWithType> özelliğine `true` ve geçirme <xref:System.Xml.Xsl.XsltSettings> nesnesinin <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemi.  
  
 <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> Ve <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> yöntemleri, her dahil kabul aşırı bir <xref:System.Xml.XmlResolver> bağımsız değişkenlerinden biri olarak. Varsa bir <xref:System.Xml.XmlResolver> belirtilmezse, varsayılan <xref:System.Xml.XmlUrlResolver> ile kimlik bilgileri kullanılır.  
  
#### <a name="guidelines"></a>Kuralları  
 Etkinleştirme `document()` yalnızca stil sayfası güvenilir bir kaynaktan geldiğinde işlev.  
  
 Aşağıdaki listede zaman belirtmek isteyebilirsiniz açıklanmaktadır bir <xref:System.Xml.XmlResolver> nesnesi:  
  
-   XSLT işlemi bir ağ kaynağına erişimi gerekiyorsa, kimlik doğrulaması gerektiren, kullanabileceğiniz bir <xref:System.Xml.XmlResolver> gerekli kimlik bilgilerine sahip.  
  
-   XSLT işlem erişebileceği kaynakları kısıtlamak istiyorsanız, kullanabileceğiniz bir <xref:System.Xml.XmlSecureResolver> doğru izniyle ayarlayın. Kullanım <xref:System.Xml.XmlSecureResolver> değil denetleyen veya güvenilmeyen olan bir kaynak açmanız gerekirse sınıfı.  
  
-   Davranışını özelleştirmek istiyorsanız, kendi uygulayabileceğiniz <xref:System.Xml.XmlResolver> sınıfı ve kaynakları gidermek için kullanın.  
  
-   Dış kaynak erişilen sağlamak istiyorsanız, belirtebilirsiniz `null` için <xref:System.Xml.XmlResolver> bağımsız değişkeni.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [XSLT İşleme Sırasında Dış Kaynakları Çözümleme](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 [Kod erişimi güvenliği](http://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03)
