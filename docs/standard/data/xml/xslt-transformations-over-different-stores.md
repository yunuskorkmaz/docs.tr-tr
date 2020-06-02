---
title: Farklı Mağazalarda XSLT Dönüşümleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 369850e9-004a-45d2-b5c3-5060d9135adb
ms.openlocfilehash: 0eb98aad00227688df3e097ad674b44a29e5cb1a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281719"
---
# <a name="xslt-transformations-over-different-stores"></a>Farklı Mağazalarda XSLT Dönüşümleri
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform>Sınıf .NET Framework 2,0 ' de kullanılmıyor. Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> . Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](migrating-from-the-xsltransform-class.md) .  
  
 .NET Framework ADO.NET ve XML sınıfları, verilere erişmek için birleştirilmiş bir programlama modeli sağlar. Bu veriler hem Etiketler tarafından ayrılmış metin hem de satır ve sütunlardan oluşan tablolar olan ilişkisel veriler olarak temsil edilen XML verisi olarak temsil edilir. .NET Framework XML verileri programlı olarak erişilebilen XML Belge Nesne Modeli (DOM) düğüm ağaçlarına XML verilerini okur, ancak ADO.NET bir nesne içindeki ilişkisel verilere erişme ve bunları işleme araçlarını sağlar <xref:System.Data.DataSet> .  
  
 XML DOM, XML belgelerindeki verilere ve XML belgelerinde okuma, yazma ve gitme için ek sınıflarda erişim sağlar. Bu sınıflar <xref:System.Xml> ad alanında desteklenir ve bu da ADO.NET tarafından sunulan veri erişim HIZMETLERIYLE XML DOM 'yi birleştirir. , <xref:System.Xml.XmlDataDocument> Verilere ilişkisel erişim sağlar. <xref:System.Xml.XmlDataDocument>XML, bir ADO.NET içindeki ilişkisel verilerle eşlenir <xref:System.Data.DataSet> . Tüm .NET Framework tabanlı uygulamalar <xref:System.Xml> , IÇINDEKI XML belgelerini ve ilişkisel verileri erişmek ve yönetmek için ad alanındaki sınıfları kullanabilir <xref:System.Xml.XmlDataDocument> . Bu uygulama, verilerin toplanması ve dağıtılması için n katmanlı mimarilerin kullanılmasını destekler. Daha fazla bilgi için bkz. [Ilişkisel verilerle XML tümleştirmesi ve ADO.net](xml-integration-with-relational-data-and-adonet.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslTransform Sınıfı XSLT İşlemcisini Uygular](xsltransform-class-implements-the-xslt-processor.md)
