---
title: XslCompiledTransform Sınıfını Kullanma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
ms.openlocfilehash: b9d14a79347610abcd2f770488acb53218ce3e46
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556778"
---
# <a name="using-the-xslcompiledtransform-class"></a>XslCompiledTransform Sınıfını Kullanma
<xref:System.Xml.Xsl.XslCompiledTransform>Sınıfı, Microsoft .NET Framework XSLT işlemcisidir. Bu sınıf, stil sayfalarını derlemek ve XSLT dönüştürmelerini yürütmek için kullanılır.  
  
> [!NOTE]
> Sınıfının genel performansı <xref:System.Xml.Xsl.XslCompiledTransform> sınıfından daha iyidir <xref:System.Xml.Xsl.XslTransform> , ancak <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> sınıfın yöntemi, <xref:System.Xml.Xsl.XslCompiledTransform> <xref:System.Xml.Xsl.XslTransform.Load%2A> <xref:System.Xml.Xsl.XslTransform> bir dönüşümde ilk kez çağrıldığında sınıfının yönteminden daha yavaş çalışabilir. Bunun nedeni XSLT dosyasının yüklenmeden önce derlenmesi gerekir. Daha fazla bilgi için şu blog gönderisine bakın: [XslCompiledTransform, XslTransform 'Dan daha yavaş?](/archive/blogs/antosha/xslcompiledtransform-slower-than-xsltransform)  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [XslCompiledTransform Sınıfına Girişler](inputs-to-the-xslcompiledtransform-class.md)  
 Kullanılabilir XSLT giriş seçeneklerini açıklar.  
  
 [XslCompiledTransform Sınıfındaki Çıkış Seçenekleri](output-options-on-the-xslcompiledtransform-class.md)  
 Kullanılabilir XSLT çıkış seçeneklerini açıklar.  
  
 [XSLT İşleme Sırasında Dış Kaynakları Çözümleme](resolving-external-resources-during-xslt-processing.md)  
 <xref:System.Xml.XmlResolver>Dış kaynakları çözümlemek için sınıfının kullanımını açıklar.  
  
 [XSLT Stil Sayfalarını Genişletme](extending-xslt-style-sheets.md)  
 XSLT uzantılarının nasıl desteklendiğini açıklar.  
  
|||  
|-|-|  
|[Kurtarılabilir XSLT Hataları](recoverable-xslt-errors.md)|World Wide Web Konsorsiyumu (W3C) XSLT 1,0 önerisi tarafından izin verilen isteğe bağlı davranışları listeler ve bu davranışların sınıf tarafından nasıl işlendiğini açıklar <xref:System.Xml.Xsl.XslCompiledTransform> .|  
|[Nasıl yapılır: Düğüm Parçasını Dönüştürme](how-to-transform-a-node-fragment.md)|Bir düğüm parçasının nasıl dönüştürüleceğini açıklar.|  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [XslTransform Sınıfından Geçirme](migrating-from-the-xsltransform-class.md)  
 Sınıfından kodun nasıl geçirileceğiyle anlatılmaktadır <xref:System.Xml.Xsl.XslTransform>  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Xsl.XsltSettings>
- <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
