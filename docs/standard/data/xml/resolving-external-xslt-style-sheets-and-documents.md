---
title: Dış XSLT Stil Sayfaları ile Belgelerini Çözümleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 920cfe3b-d525-4bb2-abf6-9431651f9cf9
ms.openlocfilehash: 504519532d9a6988209cf04fd6b6196796f929f8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710303"
---
# <a name="resolving-external-xslt-style-sheets-and-documents"></a>Dış XSLT Stil Sayfaları ile Belgelerini Çözümleme
Dış kaynakları çözmeniz gerekebilmeniz için bir dönüştürme sırasında birkaç zaman vardır.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Sınıf .NET Framework 2,0 ' de kullanılmıyor. <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfını kullanarak dönüşümler Için Genişletilebilir Stil sayfası DILI (XSLT) dönüşümleri gerçekleştirebilirsiniz.  
  
 Dış kaynakları çözmeniz gerekebilmeniz için bir dönüştürme sırasında birkaç zaman vardır:  
  
- Bir dış <xref:System.Xml.Xsl.XslTransform.Load%2A> stil sayfasını bulmak için.  
  
- Stil <xref:System.Xml.Xsl.XslTransform.Load%2A> sayfasında bulunan `<xsl:include>` veya `<xsl:import>` öğelerinin çözümlenmesi sırasında.  
  
- Tüm <xref:System.Xml.Xsl.XslTransform.Transform%2A> `document()` işlevleri çözümlemek için.  
  
## <a name="using-the-xmlresolver-class"></a>XmlResolver sınıfını kullanma  
 Bir ağ kaynağına erişmek için kimlik doğrulaması gerekiyorsa, <xref:System.Xml.Xsl.XslTransform.Load%2A> <xref:System.Xml.XmlResolver> <xref:System.Xml.XmlResolver> nesneyi geçirmek için gerekli kimlik bilgisi özellikleri ayarlanmış bir parametreye sahip yöntemleri kullanın.  
  
 Kullanmak istediğiniz özel bir özel <xref:System.Xml.XmlResolver> varsa veya farklı kimlik bilgileri belirtmeniz gerekiyorsa, dış kaynağın çözümüne ne zaman ihtiyaç duydığına bağlı olarak, aşağıdaki tabloda gereken görev listelenmektedir.  
  
|Hangi işlemin çözülmesi gerekir|Görev gerekiyor|  
|--------------------------------------|-------------------|  
|Stil <xref:System.Xml.Xsl.XslTransform.Load%2A> sayfasını bulmak için.|Stil sayfası, <xref:System.Xml.Xsl.XslTransform.Load%2A> kimlik bilgileri gerektiren bir kaynakta ise, bir parametresi <xref:System.Xml.XmlResolver> olarak alan aşırı yüklenmiş yöntemi belirtin.|  
|Veya <xref:System.Xml.Xsl.XslTransform.Load%2A> `<xsl:import>`sorununu çözmek `<xsl:include>` için.|Parametresi olarak, <xref:System.Xml.Xsl.XslTransform.Load%2A> olan aşırı yüklenmiş yöntemi belirtin <xref:System.Xml.XmlResolver>. <xref:System.Xml.XmlResolver> , `import` Veya `include` deyimleri tarafından başvurulan stil sayfalarını yüklemek için kullanılır. ' `null`İ geçirirseniz, dış kaynaklar çözümlenmez.|  
|Bir dönüşüm sırasında `document()` işlevleri çözün.|Bir <xref:System.Xml.XmlResolver> bağımsız <xref:System.Xml.XmlResolver> değişken alan <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi kullanarak dönüştürme sırasında öğesini belirtin.|  
  
 `document()` İşlevi, giriş akışı tarafından sunulan ilk XML verilerine ek olarak bir stil SAYFASıNDAN diğer XML kaynaklarını alır. Bu işlev, başka bir yerde konumlandırılabilir XML verilerinin eklenmesine <xref:System.Xml.XmlResolver> izin verdiğinden, `null` <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi için sağlanan bir değer içeren bir değeri, `document()` işlevin yürütülmesini önler. `document()` İşlevini kullanmak istiyorsanız, uygun izin kümesine sahip olmanın yanı <xref:System.Xml.Xsl.XslTransform.Transform%2A> sıra parametresi <xref:System.Xml.XmlResolver> olarak alan yöntemi kullanın.  
  
 <xref:System.Xml.Xsl.XslTransform.Load%2A> Yöntemi ve kullanımı hakkında daha fazla bilgi için <xref:System.Xml.XmlResolver>, bkz <xref:System.Xml.Xsl.XslTransform.Load%28System.String%2CSystem.Xml.XmlResolver%29?displayProperty=nameWithType>..  
  
 <xref:System.Xml.Xsl.XslTransform.Transform%2A> Yöntemi çağrıldığında, izinler yükleme zamanında verilen kanıtla karşılaştırılır ve bu izin kümesi tüm dönüştürme işlemine atanır. `document()` İşlev, küme içinde bulunamayan izinleri gerektiren bir eylem başlatmaya çalışırsa, bir özel durum oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslTransform Sınıfı ile XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
- [XslTransform Çıkışları](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md)
- [Farklı Mağazalarda XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations-over-different-stores.md)
- [Stil Sayfası Parametreleri ve Genişletme Nesneleri için XsltArgumentList](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md)
- [Msxsl: Script \<>kullanarak XSLT stil sayfası betiği oluşturma](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md)
- [msxsl:node-set() İşlevi Desteği](../../../../docs/standard/data/xml/support-for-the-msxsl-node-set-function.md)
- [Dönüşümlerde XPathNavigator](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [Dönüşümlerde XPathNodeIterator](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [XslTransform’a XPathDocument Girişi](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [XslTransform’a XmlDataDocument Girişi](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
- [XslTransform’a XmlDocument Girişi](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
