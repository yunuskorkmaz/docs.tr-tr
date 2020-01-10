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
> <xref:System.Xml.Xsl.XslTransform> sınıfı, .NET Framework 2,0 ' de kullanılmıyor. <xref:System.Xml.Xsl.XslCompiledTransform> sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz.  
  
 Dış kaynakları çözmeniz gerekebilmeniz için bir dönüştürme sırasında birkaç zaman vardır:  
  
- Bir dış stil sayfasını bulmak için <xref:System.Xml.Xsl.XslTransform.Load%2A> sırasında.  
  
- Stil sayfasında bulunan `<xsl:include>` veya `<xsl:import>` öğelerini çözümlemek için <xref:System.Xml.Xsl.XslTransform.Load%2A> sırasında.  
  
- `document()` işlevleri çözümlemek için <xref:System.Xml.Xsl.XslTransform.Transform%2A> sırasında.  
  
## <a name="using-the-xmlresolver-class"></a>XmlResolver sınıfını kullanma  
 Bir ağ kaynağına erişmek için kimlik doğrulaması gerekiyorsa, gerekli kimlik bilgisi özellikleri ayarlanmış olan <xref:System.Xml.XmlResolver> nesnesini iletmek için <xref:System.Xml.XmlResolver> parametresine sahip <xref:System.Xml.Xsl.XslTransform.Load%2A> yöntemlerini kullanın.  
  
 Kullanmak istediğiniz özel bir <xref:System.Xml.XmlResolver> varsa veya farklı kimlik bilgileri belirtmeniz gerekiyorsa, dış kaynağın çözümüne ne zaman ihtiyaç duydığına bağlı olarak, aşağıdaki tabloda gereken görev listelenmektedir.  
  
|Hangi işlemin çözülmesi gerekir|Görev gerekiyor|  
|--------------------------------------|-------------------|  
|Stil sayfasını bulmak için <xref:System.Xml.Xsl.XslTransform.Load%2A> sırasında.|Stil sayfası kimlik bilgileri gerektiren bir kaynakta ise, bir <xref:System.Xml.XmlResolver> parametre olarak alan aşırı yüklenmiş <xref:System.Xml.Xsl.XslTransform.Load%2A> yöntemini belirtin.|  
|`<xsl:include>` veya `<xsl:import>`çözümlemek için <xref:System.Xml.Xsl.XslTransform.Load%2A> sırasında.|Bir parametre olarak bir <xref:System.Xml.XmlResolver>alan aşırı yüklenmiş <xref:System.Xml.Xsl.XslTransform.Load%2A> yöntemini belirtin. <xref:System.Xml.XmlResolver>, `import` veya `include` deyimlerinin başvurduğu stil sayfalarını yüklemek için kullanılır. `null`geçirirseniz, dış kaynaklar çözümlenmez.|  
|Bir dönüşüm sırasında `document()` işlevleri çözün.|Bir <xref:System.Xml.XmlResolver> bağımsız değişkeni alan <xref:System.Xml.Xsl.XslTransform.Transform%2A> metodunu kullanarak dönüştürme sırasında <xref:System.Xml.XmlResolver> belirtin.|  
  
 `document()` işlevi, giriş akışı tarafından sunulan ilk XML verilerine ek olarak bir stil sayfasından diğer XML kaynaklarını alır. Bu işlev, başka bir yerde konumlandırılabilir XML verilerinin eklenmesine izin verdiğinden, <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemine sağlanan `null` değeri olan bir <xref:System.Xml.XmlResolver> `document()` işlevinin yürütülmesini önler. `document()` işlevini kullanmak istiyorsanız, uygun izin kümesine sahip olmanın yanı sıra bir <xref:System.Xml.XmlResolver> parametre olarak alan <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi kullanın.  
  
 <xref:System.Xml.Xsl.XslTransform.Load%2A> yöntemi ve <xref:System.Xml.XmlResolver>kullanımı hakkında daha fazla bilgi için bkz. <xref:System.Xml.Xsl.XslTransform.Load%28System.String%2CSystem.Xml.XmlResolver%29?displayProperty=nameWithType>.  
  
 <xref:System.Xml.Xsl.XslTransform.Transform%2A> yöntemi çağrıldığında, izinler yükleme zamanında verilen kanıtla karşılaştırılır ve bu izin kümesi tüm dönüştürme işlemine atanır. `document()` işlev, küme içinde bulunamayan izinleri gerektiren bir eylemi başlatmaya çalışırsa, bir özel durum oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslTransform Sınıfı ile XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
- [XslTransform Çıkışları](../../../../docs/standard/data/xml/outputs-from-an-xsltransform.md)
- [Farklı Mağazalarda XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations-over-different-stores.md)
- [Stil Sayfası Parametreleri ve Genişletme Nesneleri için XsltArgumentList](../../../../docs/standard/data/xml/xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md)
- [\<msxsl: script > kullanarak XSLT stil sayfası betiği oluşturma](../../../../docs/standard/data/xml/xslt-stylesheet-scripting-using-msxsl-script.md)
- [msxsl:node-set() İşlevi Desteği](../../../../docs/standard/data/xml/support-for-the-msxsl-node-set-function.md)
- [Dönüşümlerde XPathNavigator](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)
- [Dönüşümlerde XPathNodeIterator](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)
- [XslTransform’a XPathDocument Girişi](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)
- [XslTransform’a XmlDataDocument Girişi](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)
- [XslTransform’a XmlDocument Girişi](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
