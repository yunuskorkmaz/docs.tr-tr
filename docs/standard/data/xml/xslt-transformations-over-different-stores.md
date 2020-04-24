---
title: Farklı Mağazalarda XSLT Dönüşümleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 369850e9-004a-45d2-b5c3-5060d9135adb
ms.openlocfilehash: 490ac30a3e4f0c50cb5d011f1d583c6e5ce9e672
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709666"
---
# <a name="xslt-transformations-over-different-stores"></a>Farklı Mağazalarda XSLT Dönüşümleri
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Sınıf .NET Framework 2,0 ' de kullanılmıyor. <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfını kullanarak dönüşümler Için Genişletilebilir Stil sayfası DILI (XSLT) dönüşümleri gerçekleştirebilirsiniz. Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 .NET Framework ADO.NET ve XML sınıfları, verilere erişmek için birleştirilmiş bir programlama modeli sağlar. Bu veriler hem Etiketler tarafından ayrılmış metin hem de satır ve sütunlardan oluşan tablolar olan ilişkisel veriler olarak temsil edilen XML verisi olarak temsil edilir. .NET Framework XML verileri programlı olarak erişilebilen XML Belge Nesne Modeli (DOM) düğüm ağaçlarına XML verilerini okur, ancak ADO.NET bir <xref:System.Data.DataSet> nesne içindeki ilişkisel verilere erişme ve bunları işleme araçlarını sağlar.  
  
 XML DOM, XML belgelerindeki verilere ve XML belgelerinde okuma, yazma ve gitme için ek sınıflarda erişim sağlar. Bu sınıflar <xref:System.Xml> ad alanında desteklenir ve bu da ADO.NET tarafından sunulan veri ERIŞIM HIZMETLERIYLE XML DOM 'yi birleştirir. , <xref:System.Xml.XmlDataDocument> Verilere ilişkisel erişim sağlar. XML <xref:System.Xml.XmlDataDocument> , bir ADO.net <xref:System.Data.DataSet>içindeki ilişkisel verilerle eşlenir. Tüm .NET Framework tabanlı uygulamalar, <xref:System.Xml> <xref:System.Xml.XmlDataDocument>içindeki XML belgelerini ve ilişkisel verileri erişmek ve yönetmek için ad alanındaki sınıfları kullanabilir. Bu uygulama, verilerin toplanması ve dağıtılması için n katmanlı mimarilerin kullanılmasını destekler. Daha fazla bilgi için bkz. [Ilişkisel verilerle XML tümleştirmesi ve ADO.net](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
