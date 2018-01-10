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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a00ae5a2f54aee3d6ac16d0870f9171fe42ca289
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2018
---
# <a name="using-the-xslcompiledtransform-class"></a>XslCompiledTransform sınıfını kullanma
<xref:System.Xml.Xsl.XslCompiledTransform> Microsoft .NET Framework XSLT işlemci bir sınıftır. Bu sınıf, stil sayfaları derlemek ve XSLT dönüştürmeleri yürütmek için kullanılır.  
  
> [!NOTE]
>  Ancak genel performansını <xref:System.Xml.Xsl.XslCompiledTransform> sınıftır daha iyi <xref:System.Xml.Xsl.XslTransform> sınıfı, <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> yöntemi <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı daha gerçekleştirebileceğiniz daha yavaş <xref:System.Xml.Xsl.XslTransform.Load%2A> yöntemi <xref:System.Xml.Xsl.XslTransform> sınıfı ilk kez üzerinde dönüştürme adı verilir. XSLT dosyasının yüklendiği önce derlenmelidir olmasıdır. Daha fazla bilgi için aşağıdaki blog gönderisine bakın: [XslCompiledTransform çok daha yavaş?](https://blogs.msdn.microsoft.com/antosha/2006/07/16/xslcompiledtransform-slower-than-xsltransform/)  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [XslCompiledTransform Sınıfına Girişler](../../../../docs/standard/data/xml/inputs-to-the-xslcompiledtransform-class.md)  
 Kullanılabilir XSLT giriş seçenekleri açıklar.  
  
 [XslCompiledTransform Sınıfındaki Çıkış Seçenekleri](../../../../docs/standard/data/xml/output-options-on-the-xslcompiledtransform-class.md)  
 Kullanılabilir XSLT çıkış seçeneklerini açıklar.  
  
 [XSLT İşleme Sırasında Dış Kaynakları Çözümleme](../../../../docs/standard/data/xml/resolving-external-resources-during-xslt-processing.md)  
 Kullanarak açıklanır <xref:System.Xml.XmlResolver> dış kaynaklara çözümlemek için sınıf.  
  
 [XSLT Stil Sayfalarını Genişletme](../../../../docs/standard/data/xml/extending-xslt-style-sheets.md)  
 XSLT uzantıları nasıl desteklediği açıklanır.  
  
|||  
|-|-|  
|[Kurtarılabilir XSLT Hataları](../../../../docs/standard/data/xml/recoverable-xslt-errors.md)|İsteğe bağlı davranışları 1.0 öneri World Wide Web Konsorsiyumu (W3C) XSLT tarafından izin verilen listeler ve bu davranışların tarafından nasıl işleneceğini açıklayan <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.|  
|[Nasıl yapılır: Düğüm Parçasını Dönüştürme](../../../../docs/standard/data/xml/how-to-transform-a-node-fragment.md)|Bir düğüm parça dönüştürme açıklar.|  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [XslTransform Sınıfından Geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)  
 Koddan geçirmek nasıl ele <xref:System.Xml.Xsl.XslTransform> sınıfı  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Xsl.XsltSettings>  
 <xref:System.Xml.Xsl.XsltMessageEncounteredEventArgs>
