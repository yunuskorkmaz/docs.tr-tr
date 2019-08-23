---
title: XslCompiledTransform Sınıfını Kullanma
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a524b80d8789567dc2aa943d7321fd49fe3c7c33
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939419"
---
# <a name="using-the-xslcompiledtransform-class"></a>XslCompiledTransform Sınıfını Kullanma
<xref:System.Xml.Xsl.XslCompiledTransform> Sınıfı, Microsoft .NET Framework XSLT işlemcisidir. Bu sınıf, stil sayfalarını derlemek ve XSLT dönüştürmelerini yürütmek için kullanılır.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfının genel performansı <xref:System.Xml.Xsl.XslTransform> sınıfından daha iyi olsa da <xref:System.Xml.Xsl.XslCompiledTransform> , <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> sınıfının yöntemi ilk kez <xref:System.Xml.Xsl.XslTransform> sınıfın <xref:System.Xml.Xsl.XslTransform.Load%2A> yönteminden daha yavaş çalışabilir. bir dönüşümde çağrılır. Bunun nedeni XSLT dosyasının yüklenmeden önce derlenmesi gerekir. Daha fazla bilgi için aşağıdaki blog gönderisine bakın: [XslCompiledTransform, XslTransform 'dan daha yavaş?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [XslCompiledTransform Sınıfına Girişler](../../../../docs/standard/data/xml/inputs-to-the-xslcompiledtransform-class.md)  
 Kullanılabilir XSLT giriş seçeneklerini açıklar.  
  
 [XslCompiledTransform Sınıfındaki Çıkış Seçenekleri](../../../../docs/standard/data/xml/output-options-on-the-xslcompiledtransform-class.md)  
 Kullanılabilir XSLT çıkış seçeneklerini açıklar.  
  
 [XSLT İşleme Sırasında Dış Kaynakları Çözümleme](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 Dış kaynakları çözümlemek <xref:System.Xml.XmlResolver> için sınıfının kullanımını açıklar.  
  
 [XSLT Stil Sayfalarını Genişletme](../../../../docs/standard/data/xml/extending-xslt-style-sheets.md)  
 XSLT uzantılarının nasıl desteklendiğini açıklar.  
  
|||  
|-|-|  
|[Kurtarılabilir XSLT Hataları](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)|World Wide Web Konsorsiyumu (W3C) XSLT 1,0 önerisi tarafından izin verilen isteğe bağlı davranışları listeler ve bu davranışların <xref:System.Xml.Xsl.XslCompiledTransform> sınıf tarafından nasıl işlendiğini açıklar.|  
|[Nasıl yapılır: Düğüm parçasını dönüştürme](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)|Bir düğüm parçasının nasıl dönüştürüleceğini açıklar.|  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [XslTransform Sınıfından Geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 <xref:System.Xml.Xsl.XslTransform> Sınıfından kodun nasıl geçirileceğiyle anlatılmaktadır  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Xsl.XsltSettings>
- <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
