---
title: Dış XSLT Stil Sayfaları ile Belgelerini Çözümleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 920cfe3b-d525-4bb2-abf6-9431651f9cf9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 381b7c1eb091bafbcdc8ea842597c539c6be3a57
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945628"
---
# <a name="resolving-external-xslt-style-sheets-and-documents"></a>Dış XSLT Stil Sayfaları ile Belgelerini Çözümleme
Dış kaynakları çözmeniz gerekebilmeniz için bir dönüştürme sırasında birkaç zaman vardır.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Sınıf .NET Framework 2,0 ' de kullanılmıyor. <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz.  
  
 Dış kaynakları çözmeniz gerekebilmeniz için bir dönüştürme sırasında birkaç zaman vardır:  
  
- Bir dış stil sayfasını bulmak için.<xref:System.Xml.Xsl.XslTransform.Load%2A>  
  
- Stil <xref:System.Xml.Xsl.XslTransform.Load%2A> sayfasında bulunan `<xsl:include>` veya`<xsl:import>` öğelerinin çözümlenmesi sırasında.  
  
- <xref:System.Xml.Xsl.XslTransform.Transform%2A> Tüm`document()` işlevleri çözümlemek için.  
  
## <a name="using-the-xmlresolver-class"></a>XmlResolver sınıfını kullanma  
 Bir ağ kaynağına erişmek için kimlik doğrulaması gerekiyorsa, <xref:System.Xml.Xsl.XslTransform.Load%2A> <xref:System.Xml.XmlResolver> nesneyi geçirmek için gerekli kimlik bilgisi özellikleri <xref:System.Xml.XmlResolver> ayarlanmış bir parametreye sahip yöntemleri kullanın.  
  
 Kullanmak istediğiniz özel bir özel <xref:System.Xml.XmlResolver> varsa veya farklı kimlik bilgileri belirtmeniz gerekiyorsa, dış kaynağın çözümüne ne zaman ihtiyaç duydığına bağlı olarak, aşağıdaki tabloda gereken görev listelenmektedir.  
  
|Hangi işlemin çözülmesi gerekir|Görev gerekiyor|  
|--------------------------------------|-------------------|  
|Stil sayfasını bulmak için. <xref:System.Xml.Xsl.XslTransform.Load%2A>|Stil sayfası, <xref:System.Xml.Xsl.XslTransform.Load%2A> kimlik bilgileri gerektiren bir kaynakta ise, bir parametresi <xref:System.Xml.XmlResolver> olarak alan aşırı yüklenmiş yöntemi belirtin.|  
|Veya <xref:System.Xml.Xsl.XslTransform.Load%2A> `<xsl:include>`sorununuçözmekiçin. `<xsl:import>`|<xref:System.Xml.Xsl.XslTransform.Load%2A> Parametresi<xref:System.Xml.XmlResolver>olarak, olan aşırı yüklenmiş yöntemi belirtin. <xref:System.Xml.XmlResolver> , `import` Veya deyimleri`include` tarafından başvurulan stil sayfalarını yüklemek için kullanılır. ' `null`İ geçirirseniz, dış kaynaklar çözümlenmez.|  
|Bir dönüşüm sırasında `document()` işlevleri çözün.|<xref:System.Xml.Xsl.XslTransform.Transform%2A> <xref:System.Xml.XmlResolver> Bir<xref:System.Xml.XmlResolver> bağımsız değişken alan yöntemi kullanarak dönüştürme sırasında öğesini belirtin.|  
  
 `document()` İşlevi, giriş akışı tarafından sunulan ilk XML verilerine ek olarak bir stil sayfasından diğer XML kaynaklarını alır. Bu işlev, başka bir yerde konumlandırılabilir XML verilerinin <xref:System.Xml.XmlResolver> eklenmesine izin verdiğinden, <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi `document()` için sağlanan bir `null` değer içeren bir değeri, işlevin yürütülmesini önler. `document()` İşlevini kullanmak istiyorsanız, uygun izin kümesine sahip olmanın yanı <xref:System.Xml.Xsl.XslTransform.Transform%2A> sıra parametresi <xref:System.Xml.XmlResolver> olarak alan yöntemi kullanın.  
  
 <xref:System.Xml.Xsl.XslTransform.Load%2A> Yöntemi ve kullanımı <xref:System.Xml.XmlResolver>hakkında daha fazla bilgi için, bkz <xref:System.Xml.Xsl.XslTransform.Load%28System.String%2CSystem.Xml.XmlResolver%29?displayProperty=nameWithType>.  
  
 <xref:System.Xml.Xsl.XslTransform.Transform%2A> Yöntemi çağrıldığında, izinler yükleme zamanında verilen kanıtla karşılaştırılır ve bu izin kümesi tüm dönüştürme işlemine atanır. `document()` İşlev, küme içinde bulunamayan izinleri gerektiren bir eylem başlatmaya çalışırsa, bir özel durum oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslTransform Sınıfı ile XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
- [XslTransform Çıkışları](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md)
- [Farklı Mağazalarda XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations-over-different-stores.md)
- [Stil Sayfası Parametreleri ve Genişletme Nesneleri için XsltArgumentList](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md)
- [Msxsl: Script \<> kullanarak XSLT stil sayfası betiği oluşturma](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md)
- [msxsl:node-set() İşlevi Desteği](../../../../docs/standard/data/xml/support-for-the-msxsl-node-set-function.md)
- [Dönüşümlerde XPathNavigator](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [Dönüşümlerde XPathNodeIterator](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [XslTransform’a XPathDocument Girişi](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [XslTransform’a XmlDataDocument Girişi](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
- [XslTransform’a XmlDocument Girişi](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
