---
title: Farklı Mağazalarda XSLT Dönüşümleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 369850e9-004a-45d2-b5c3-5060d9135adb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0b5ff264f9a781c95ccf9bdbabf4b29806016362
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026633"
---
# <a name="xslt-transformations-over-different-stores"></a>Farklı Mağazalarda XSLT Dönüşümleri
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Sınıftır eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) dönüştürmeleri için kullanarak gerçekleştirebileceğiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bkz: [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [geçirme gelen XslTransform sınıfı](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.  
  
 ADO.NET ve XML'i sınıflar olarak [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] verilerine erişmek için birleşik bir programlama modeli sağlar. Bu veri etiketlerine göre ayrılmış metin olan XML verileri ve tablo satırları ve sütunları oluşan olan ilişkisel veri temsil edilir. XML'de [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] XML verileri içine XML belge nesne modeli (DOM) düğüm ağaçları burada verileri programlı olarak erişilebilir, ADO.NET erişmek ve içinde ilişkisel verileri işlemek için yol sağlarken, herhangi bir veri akışından okur bir <xref:System.Data.DataSet> nesne.  
  
 XML DOM XML belgeleri ve okuma, yazma ve XML belgelerinde gezinmek için ek sınıfları verilere erişim sağlar. Bu sınıfların desteklenen <xref:System.Xml> ad alanı da ADO.NET tarafından sağlanan veri erişim Hizmetleri ile XML DOM birleştirir. <xref:System.Xml.XmlDataDocument> İlişkisel verilere erişim sağlar. <xref:System.Xml.XmlDataDocument> XML ADO.NET ilişkisel verilere eşleyen <xref:System.Data.DataSet>. Tüm [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]-tabanlı uygulama sınıfları kullanabilirsiniz <xref:System.Xml> erişmek ve hem XML belgeleri hem de ilişkisel verileri işlemek için ad alanı <xref:System.Xml.XmlDataDocument>. Bu uygulama, toplama ve verileri dağıtmak için n katmanlı mimariler destekler. Daha fazla bilgi için [ilişkisel veriler ve ADO.NET ile XML tümleştirmesi](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
