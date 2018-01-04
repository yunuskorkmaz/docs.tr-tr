---
title: "Mağazaya üzerinden XSLT dönüştürmeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 369850e9-004a-45d2-b5c3-5060d9135adb
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2b642a1f2c29c6b4143b3f520a3df47328fcb41d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="xslt-transformations-over-different-stores"></a>Mağazaya üzerinden XSLT dönüştürmeleri
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Sınıftır'te eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Genişletilebilir Stil sayfası dili kullanarak Dönüşümleri (XSLT) dönüştürmeleri için gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bkz: [XslCompiledTransform sınıfını kullanarak](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [çok sınıfı geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.  
  
 ADO.NET ve XML sınıfları içinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verilere erişmek için birleşik bir programlama modeli sağlar. Bu verileri etiketlere göre ayrılmış metin olan XML verileri ve satırları ve sütunları oluşan tabloları olan ilişkisel veri temsil edilir. XML'de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] XML belge nesne modeli (DOM) düğüm ağaçları burada veri erişilebilir programlı olarak erişmek ve içinde ilişkisel verileri işlemek için Araçlar ADO.NET sağlarken, içine herhangi bir veri akışından XML veri okuyan bir <xref:System.Data.DataSet> nesnesi.  
  
 XML DOM XML belgelerini ve okuma, yazma ve XML belgelerini gezinmek için ek sınıfları veri erişimi sağlar. Bu sınıfların desteklenen <xref:System.Xml> de ADO.NET tarafından sağlanan veri erişim Hizmetleri ile XML DOM birleştiren ad alanı. <xref:System.Xml.XmlDataDocument> İlişkisel verilere erişim sağlar. <xref:System.Xml.XmlDataDocument> Bir ADO.NET ilişkisel verileri XML eşlemeleri <xref:System.Data.DataSet>. Tüm [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]-tabanlı uygulama sınıflarda kullanabileceğiniz <xref:System.Xml> erişmek ve XML belgelerini ve ilişkisel verileri işlemek için ad alanı <xref:System.Xml.XmlDataDocument>. Bu uygulama, toplama ve veri dağıtmak için n katmanlı mimariyi destekler. Daha fazla bilgi için bkz: [ilişkisel veri ve ADO.NET XML tümleştirme](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
