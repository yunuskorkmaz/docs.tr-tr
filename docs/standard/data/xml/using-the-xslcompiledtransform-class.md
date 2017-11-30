---
title: "XslCompiledTransform sınıfını kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9b074f6-d6f4-49dd-a093-df510bf0cf7b
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5a5c71a7796790343bf39de5bbfd03997c25d5f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-xslcompiledtransform-class"></a>XslCompiledTransform sınıfını kullanma
<xref:System.Xml.Xsl.XslCompiledTransform> Microsoft .NET Framework XSLT işlemci bir sınıftır. Bu sınıf, stil sayfaları derlemek ve XSLT dönüştürmeleri yürütmek için kullanılır.  
  
> [!NOTE]
>  Ancak genel performansını <xref:System.Xml.Xsl.XslCompiledTransform> sınıftır daha iyi <xref:System.Xml.Xsl.XslTransform> sınıfı, <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemi <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı daha gerçekleştirebileceğiniz daha yavaş <xref:System.Xml.Xsl.XslTransform.Load%2A> yöntemi <xref:System.Xml.Xsl.XslTransform> sınıfı ilk kez üzerinde dönüştürme adı verilir. XSLT dosyasının yüklendiği önce derlenmelidir olmasıdır. Daha fazla bilgi için aşağıdaki blog gönderisine bakın: [XslCompiledTransform çok daha yavaş?](http://go.microsoft.com/fwlink/?LinkId=130590)  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [XslCompiledTransform sınıfı girişleri](../../../../docs/standard/data/xml/inputs-to-the-xslcompiledtransform-class.md)  
 Kullanılabilir XSLT giriş seçenekleri açıklar.  
  
 [Çıkış seçenekleri XslCompiledTransform sınıfı](../../../../docs/standard/data/xml/output-options-on-the-xslcompiledtransform-class.md)  
 Kullanılabilir XSLT çıkış seçeneklerini açıklar.  
  
 [Dış kaynaklara XSLT işleme sırasında çözme](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 Kullanarak açıklanır <xref:System.Xml.XmlResolver> dış kaynaklara çözümlemek için sınıf.  
  
 [XSLT stil sayfaları genişletme](../../../../docs/standard/data/xml/extending-xslt-style-sheets.md)  
 XSLT uzantıları nasıl desteklediği açıklanır.  
  
|||  
|-|-|  
|[Kurtarılabilir XSLT hataları](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)|İsteğe bağlı davranışları 1.0 öneri World Wide Web Konsorsiyumu (W3C) XSLT tarafından izin verilen listeler ve bu davranışların tarafından nasıl işleneceğini açıklayan <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.|  
|[Nasıl yapılır: bir düğümü parça dönüştürme](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)|Bir düğüm parça dönüştürme açıklar.|  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Çok sınıftan geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 Koddan geçirmek nasıl ele <xref:System.Xml.Xsl.XslTransform> sınıfı  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Xsl.XsltSettings>  
 <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
