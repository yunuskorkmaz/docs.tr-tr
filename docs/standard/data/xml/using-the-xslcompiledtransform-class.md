---
title: XslCompiledTransform Sınıfını Kullanma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
ms.openlocfilehash: 8212e37171ce693ee5624541f7886ef33a33b1da
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710056"
---
# <a name="using-the-xslcompiledtransform-class"></a>XslCompiledTransform Sınıfını Kullanma
<xref:System.Xml.Xsl.XslCompiledTransform> sınıfı, Microsoft .NET Framework XSLT işlemcisidir. Bu sınıf, stil sayfalarını derlemek ve XSLT dönüştürmelerini yürütmek için kullanılır.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslCompiledTransform> sınıfının genel performansı <xref:System.Xml.Xsl.XslTransform> sınıfından daha iyidir, ancak <xref:System.Xml.Xsl.XslCompiledTransform> sınıfının <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemi, bir dönüşümde ilk kez çağrıldığında <xref:System.Xml.Xsl.XslTransform.Load%2A> sınıfının <xref:System.Xml.Xsl.XslTransform> yönteminden daha yavaş çalışabilir. Bunun nedeni XSLT dosyasının yüklenmeden önce derlenmesi gerekir. Daha fazla bilgi için şu blog gönderisine bakın: [XslCompiledTransform, XslTransform 'Dan daha yavaş?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [XslCompiledTransform Sınıfına Girişler](../../../../docs/standard/data/xml/inputs-to-the-xslcompiledtransform-class.md)  
 Kullanılabilir XSLT giriş seçeneklerini açıklar.  
  
 [XslCompiledTransform Sınıfındaki Çıkış Seçenekleri](../../../../docs/standard/data/xml/output-options-on-the-xslcompiledtransform-class.md)  
 Kullanılabilir XSLT çıkış seçeneklerini açıklar.  
  
 [XSLT İşleme Sırasında Dış Kaynakları Çözümleme](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 Dış kaynakları çözümlemek için <xref:System.Xml.XmlResolver> sınıfını kullanmayı açıklar.  
  
 [XSLT Stil Sayfalarını Genişletme](../../../../docs/standard/data/xml/extending-xslt-style-sheets.md)  
 XSLT uzantılarının nasıl desteklendiğini açıklar.  
  
|||  
|-|-|  
|[Kurtarılabilir XSLT Hataları](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)|World Wide Web Konsorsiyumu (W3C) XSLT 1,0 önerisi tarafından izin verilen isteğe bağlı davranışları listeler ve bu davranışların <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı tarafından nasıl işlendiğini açıklar.|  
|[Nasıl yapılır: Düğüm Parçasını Dönüştürme](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)|Bir düğüm parçasının nasıl dönüştürüleceğini açıklar.|  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [XslTransform Sınıfından Geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <xref:System.Xml.Xsl.XslTransform> sınıfından kodun nasıl geçirileceğiyle anlatılmaktadır  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Xsl.XsltSettings>
- <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
