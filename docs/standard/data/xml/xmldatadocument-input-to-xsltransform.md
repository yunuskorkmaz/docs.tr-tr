---
title: "Çok XmlDataDocument giriş"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0b536b6-cdb3-4a44-86c2-3b2ebc7bd4c9
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 813c240ca0115015158988e1226d25890cde6939
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="xmldatadocument-input-to-xsltransform"></a>Çok XmlDataDocument giriş
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Sınıftır'te eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Genişletilebilir Stil sayfası dili kullanarak Dönüşümleri (XSLT) dönüştürmeleri için gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bkz: [XslCompiledTransform sınıfını kullanarak](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [çok sınıfı geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.  
  
 Microsoft [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] XML belgelerini ve okuma, yazma ve XML belgelerini gezinmek için ek sınıfları veri erişimi sağlamak için XML belge nesnesi modeli'nı (DOM) uygular. <xref:System.Xml.XmlDataDocument>, Bulunan <xref:System.Xml> ad alanı, ilişkisel veri ile eşitlemek için kendi yeteneği olan ilişkisel verilere erişim sağlar <xref:System.Data.DataSet>. Aynı anda görüntülemek ve ilişkisel gösterimini aracılığıyla yapılandırılmış XML işlemek <xref:System.Data.DataSet> veya yarı yapılandırılmış XML DOM gösterimini aracılığıyla işleme <xref:System.Xml.XmlDataDocument>. <xref:System.Xml.XmlDataDocument> Bu nedenle XML'i ve ilişkili dünyaları sınırlarının kestiği.  
  
 İlişkisel yapısı içinde depolanır ve XSLT dönüştürmesi için giriş istediğiniz, ilişkisel verileri yükleyebilir bir <xref:System.Data.DataSet> ve bu ilişkilendirmeyi <xref:System.Xml.XmlDataDocument>. <xref:System.Xml.XPath.XPathNavigator>, Giriş <xref:System.Xml.Xsl.XslTransform>, üzerinde uygulanan <xref:System.Xml.XmlDataDocument> aracılığıyla <xref:System.Xml.XPath.IXPathNavigable> arabirimi. İlişkisel veri yararlanarak, içine yüklenirken bir <xref:System.Data.DataSet>ve içinde eşitleme kullanarak <xref:System.Xml.XmlDataDocument>, ilişkisel veri artık üzerinde gerçekleştirilen XSLT dönüştürmeleri olabilir.  
  
 İlişkisel veri için bir dönüşüm uygulama hakkında daha fazla bilgi için bkz: [XSLT dönüştürmesi bir veri kümesine uygulama](../../../../docs/framework/data/adonet/dataset-datatable-dataview/applying-an-xslt-transform-to-a-dataset.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.XmlDataDocument>  
 [Veri kümesi ve XmlDataDocument eşitleme](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
 [Çok sınıfı ile XSLT dönüştürmeler](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [XSLT işlemci çok sınıfı uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [Dönüşümleri XPathNavigator](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [Dönüşümleri XPathNodeIterator](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [Çok XPathDocument giriş](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [Çok XmlDocument giriş](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
