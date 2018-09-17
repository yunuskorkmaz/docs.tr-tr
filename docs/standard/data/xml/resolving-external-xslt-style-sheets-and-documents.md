---
title: Dış XSLT stil sayfaları ile belgelerini çözümleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 920cfe3b-d525-4bb2-abf6-9431651f9cf9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 39e8afd8c22ca757141d2a7b556b115f8380e731
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45964644"
---
# <a name="resolving-external-xslt-style-sheets-and-documents"></a>Dış XSLT stil sayfaları ile belgelerini çözümleme
Bazı birkaç kez dönüştürme sırasında dış kaynakları çözümleme gerekebilir.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Sınıftır eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) dönüştürmeleri için kullanarak gerçekleştirebileceğiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.  
  
 Bazı birkaç kez dönüştürme sırasında dış kaynakları çözümleme gerekebilir:  
  
-   Sırasında <xref:System.Xml.Xsl.XslTransform.Load%2A> bir dış stil sayfası bulunamadı.  
  
-   Sırasında <xref:System.Xml.Xsl.XslTransform.Load%2A> herhangi çözümlenecek `<xsl:include>` veya `<xsl:import>` öğeleri stil sayfası bulunamadı.  
  
-   Sırasında <xref:System.Xml.Xsl.XslTransform.Transform%2A> herhangi çözümlenecek `document()` işlevleri.  
  
## <a name="using-the-xmlresolver-class"></a>XmlResolver sınıfını kullanma  
 Bir ağ kaynağına erişmek için kimlik doğrulaması gerekiyorsa kullanın <xref:System.Xml.Xsl.XslTransform.Load%2A> içeren yöntemlerin bir <xref:System.Xml.XmlResolver> geçirilecek parametre <xref:System.Xml.XmlResolver> gerekli kimlik bilgisi özellikleri olan nesne.  
  
 Özel bir varsa <xref:System.Xml.XmlResolver> kullanmak istediğiniz veya farklı kimlik bilgileri belirtmeniz gerekiyorsa, dış kaynak çözümleme gerektiğinde bağlı olarak, gerekli görev aşağıdaki tabloda listelenmiştir.  
  
|Hangi işlemin çözümlemesi gerektirir.|Gerekli görev|  
|--------------------------------------|-------------------|  
|Sırasında <xref:System.Xml.Xsl.XslTransform.Load%2A> stil sayfası bulunamadı.|Aşırı yüklenen belirtin <xref:System.Xml.Xsl.XslTransform.Load%2A> yönteminin, bir parametre olarak alan bir <xref:System.Xml.XmlResolver> stil sayfası kimlik bilgileri gerektiren bir kaynakta ise.|  
|Sırasında <xref:System.Xml.Xsl.XslTransform.Load%2A> çözümlenecek `<xsl:include>` veya `<xsl:import>`.|Aşırı yüklenen belirtin <xref:System.Xml.Xsl.XslTransform.Load%2A> yönteminin, bir parametre olarak alan bir <xref:System.Xml.XmlResolver>. <xref:System.Xml.XmlResolver> Tarafından başvurulan stil sayfaları yüklemek için kullanılan `import` veya `include` deyimleri. İçinde geçirirseniz `null`, dış kaynaklara çözümlenmedi.|  
|Tüm çözmek için bir dönüştürme sırasında `document()` işlevleri.|Belirtin <xref:System.Xml.XmlResolver> kullanarak dönüştürme sırasında <xref:System.Xml.Xsl.XslTransform.Transform%2A> gereken yöntemini bir <xref:System.Xml.XmlResolver> bağımsız değişken.|  
  
 `document()` İşlevi alır. diğer XML kaynakları bir stil sayfası, ayrıca Giriş akışı tarafından sağlanan ilk XML verileri için. Bu işlev eklenmesi olabilir XML verileri, başka bir yerde, bulunan olanak tanıdığından bir <xref:System.Xml.XmlResolver> ile bir `null` için sağlanan değer <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi engeller `document()` yürütülmesini işlevi. Kullanmak istiyorsanız `document()` işlev, kullanın <xref:System.Xml.Xsl.XslTransform.Transform%2A> gereken yöntemini bir <xref:System.Xml.XmlResolver> uygun izinlere sahip olmaya ek olarak, bir parametre olarak ayarlayın.  
  
 Daha fazla bilgi için <xref:System.Xml.Xsl.XslTransform.Load%2A> yöntemi ve kullanımı <xref:System.Xml.XmlResolver>, bkz: <xref:System.Xml.Xsl.XslTransform.Load%28System.String%2CSystem.Xml.XmlResolver%29?displayProperty=nameWithType>.  
  
 Zaman <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çağrıldığında, izinleri yükleme sırasında sağlanan kanıt karşı hesaplandığı ve izin kümesi atanan tüm dönüştürme işlemi. Varsa `document()` işlevi izinleri bulunamadı kümesinde bir özel durum gerektiren bir eylem başlatmak dener.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslTransform Sınıfı ile XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
- [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
- [XslTransform Çıkışları](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md)  
- [Farklı Mağazalarda XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations-over-different-stores.md)  
- [Stil Sayfası Parametreleri ve Genişletme Nesneleri için XsltArgumentList](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md)  
- [XSLT stil sayfası komut dosyalarını kullanarak \<msxsl: script >](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md)  
- [msxsl:node-set() İşlevi Desteği](../../../../docs/standard/data/xml/support-for-the-msxsl-node-set-function.md)  
- [Dönüşümlerde XPathNavigator](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
- [Dönüşümlerde XPathNodeIterator](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
- [XslTransform’a XPathDocument Girişi](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
- [XslTransform’a XmlDataDocument Girişi](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
- [XslTransform’a XmlDocument Girişi](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
