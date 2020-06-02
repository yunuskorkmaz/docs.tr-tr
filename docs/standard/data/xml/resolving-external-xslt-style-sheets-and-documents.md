---
title: Dış XSLT Stil Sayfaları ile Belgelerini Çözümleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 920cfe3b-d525-4bb2-abf6-9431651f9cf9
ms.openlocfilehash: 8e7f66d67f2520b47c30307a98ed2f3fb08455df
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291480"
---
# <a name="resolving-external-xslt-style-sheets-and-documents"></a>Dış XSLT Stil Sayfaları ile Belgelerini Çözümleme
Dış kaynakları çözmeniz gerekebilmeniz için bir dönüştürme sırasında birkaç zaman vardır.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform>Sınıf .NET Framework 2,0 ' de kullanılmıyor. Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> .  
  
 Dış kaynakları çözmeniz gerekebilmeniz için bir dönüştürme sırasında birkaç zaman vardır:  
  
- <xref:System.Xml.Xsl.XslTransform.Load%2A>Bir dış stil sayfasını bulmak için.  
  
- <xref:System.Xml.Xsl.XslTransform.Load%2A> `<xsl:include>` `<xsl:import>` Stil sayfasında bulunan veya öğelerinin çözümlenmesi sırasında.  
  
- <xref:System.Xml.Xsl.XslTransform.Transform%2A>Tüm işlevleri çözümlemek için `document()` .  
  
## <a name="using-the-xmlresolver-class"></a>XmlResolver sınıfını kullanma  
 Bir ağ kaynağına erişmek için kimlik doğrulaması gerekiyorsa, <xref:System.Xml.Xsl.XslTransform.Load%2A> <xref:System.Xml.XmlResolver> nesneyi geçirmek için <xref:System.Xml.XmlResolver> gerekli kimlik bilgisi özellikleri ayarlanmış bir parametreye sahip yöntemleri kullanın.  
  
 Kullanmak istediğiniz özel bir özel varsa <xref:System.Xml.XmlResolver> veya farklı kimlik bilgileri belirtmeniz gerekiyorsa, dış kaynağın çözümüne ne zaman ihtiyaç duydığına bağlı olarak, aşağıdaki tabloda gereken görev listelenmektedir.  
  
|Hangi işlemin çözülmesi gerekir|Görev gerekiyor|  
|--------------------------------------|-------------------|  
|<xref:System.Xml.Xsl.XslTransform.Load%2A>Stil sayfasını bulmak için.|<xref:System.Xml.Xsl.XslTransform.Load%2A> <xref:System.Xml.XmlResolver> Stil sayfası, kimlik bilgileri gerektiren bir kaynakta ise, bir parametresi olarak alan aşırı yüklenmiş yöntemi belirtin.|  
|<xref:System.Xml.Xsl.XslTransform.Load%2A>Veya sorununu çözmek `<xsl:include>` için `<xsl:import>` .|<xref:System.Xml.Xsl.XslTransform.Load%2A>Parametresi olarak, olan aşırı yüklenmiş yöntemi belirtin <xref:System.Xml.XmlResolver> . , <xref:System.Xml.XmlResolver> Veya deyimleri tarafından başvurulan stil sayfalarını yüklemek için kullanılır `import` `include` . ' `null` İ geçirirseniz, dış kaynaklar çözümlenmez.|  
|Bir dönüşüm sırasında `document()` işlevleri çözün.|<xref:System.Xml.XmlResolver> <xref:System.Xml.Xsl.XslTransform.Transform%2A> Bir bağımsız değişken alan yöntemi kullanarak dönüştürme sırasında öğesini belirtin <xref:System.Xml.XmlResolver> .|  
  
 `document()`İşlevi, giriş akışı tarafından sunulan Ilk XML verilerine ek olarak bir stil sayfasından DIĞER XML kaynaklarını alır. Bu işlev, başka bir yerde konumlandırılabilir XML verilerinin eklenmesine izin verdiğinden, <xref:System.Xml.XmlResolver> `null` yöntemi için sağlanan bir değer içeren bir değeri, <xref:System.Xml.Xsl.XslTransform.Transform%2A> `document()` işlevin yürütülmesini önler. İşlevini kullanmak istiyorsanız, `document()` <xref:System.Xml.Xsl.XslTransform.Transform%2A> <xref:System.Xml.XmlResolver> uygun izin kümesine sahip olmanın yanı sıra parametresi olarak alan yöntemi kullanın.  
  
 Yöntemi ve kullanımı hakkında daha fazla bilgi için <xref:System.Xml.Xsl.XslTransform.Load%2A> <xref:System.Xml.XmlResolver> , bkz <xref:System.Xml.Xsl.XslTransform.Load%28System.String%2CSystem.Xml.XmlResolver%29?displayProperty=nameWithType> ..  
  
 <xref:System.Xml.Xsl.XslTransform.Transform%2A>Yöntemi çağrıldığında, izinler yükleme zamanında verilen kanıtla karşılaştırılır ve bu izin kümesi tüm dönüştürme işlemine atanır. İşlev, `document()` küme içinde bulunamayan izinleri gerektiren bir eylem başlatmaya çalışırsa, bir özel durum oluşturulur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslTransform Sınıfı ile XSLT Dönüşümleri](xslt-transformations-with-the-xsltransform-class.md)
- [XslTransform Sınıfı XSLT İşlemcisini Uygular](xsltransform-class-implements-the-xslt-processor.md)
- [XslTransform Çıkışları](outputs-from-an-xsltransform.md)
- [Farklı Mağazalarda XSLT Dönüşümleri](xslt-transformations-over-different-stores.md)
- [Stil Sayfası Parametreleri ve Genişletme Nesneleri için XsltArgumentList](xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md)
- [Kullanarak XSLT stil sayfası betiği oluşturma\<msxsl:script>](xslt-stylesheet-scripting-using-msxsl-script.md)
- [msxsl:node-set() İşlevi Desteği](support-for-the-msxsl-node-set-function.md)
- [Dönüşümlerde XPathNavigator](xpathnavigator-in-transformations.md)
- [Dönüşümlerde XPathNodeIterator](xpathnodeiterator-in-transformations.md)
- [XslTransform’a XPathDocument Girişi](xpathdocument-input-to-xsltransform.md)
- [XslTransform’a XmlDataDocument Girişi](xmldatadocument-input-to-xsltransform.md)
- [XslTransform’a XmlDocument Girişi](xmldocument-input-to-xsltransform.md)
