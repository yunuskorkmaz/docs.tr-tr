---
title: XML Belgeleri ve Verileri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
ms.openlocfilehash: e0c3f3e99b06b65caf79d87a7831369f6fb33b08
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75710797"
---
# <a name="xml-documents-and-data"></a>XML Belgeleri ve Verileri

.NET Framework, XML'e duyarlı uygulamaları kolayca oluşturmanıza olanak tanıyan kapsamlı ve entegre bir sınıf kümesi sağlar. Aşağıdaki ad alanlarındaki sınıflar XML'i ayrıştırma ve yazmayı, XML verilerini bellekte düzenlemeyi, veri doğrulamayı ve XSLT dönüşümlerini destekler.

- <xref:System.Xml>

- <xref:System.Xml.XPath>

- <xref:System.Xml.Xsl>

- <xref:System.Xml.Schema>

- <xref:System.Xml.Linq>

Tam liste için [.NET API tarayıcıda](https://docs.microsoft.com/dotnet/api/?term=system.xml)"System.Xml" araması yapın.

Bu ad alanlarındaki sınıflar World Wide Web Konsorsiyumu (W3C) önerilerini destekler. Örnek:

- Sınıf <xref:System.Xml.XmlDocument?displayProperty=nameWithType> [W3C Belge NesneSi Modeli (DOM) Düzey 1 Çekirdek](https://www.w3.org/TR/REC-DOM-Level-1/) ve [DOM Düzey 2 Core](https://www.w3.org/TR/DOM-Level-2-Core/) önerilerini uygular.

- Ve <xref:System.Xml.XmlReader?displayProperty=nameWithType> <xref:System.Xml.XmlWriter?displayProperty=nameWithType> sınıflar [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) ve [XML önerilerindeki Ad Alanları'nı](https://www.w3.org/TR/REC-xml-names/) destekler.

- Sınıftaki <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> şemalar [W3C XML Şema Bölüm 1: Yapılar](https://www.w3.org/TR/xmlschema-1/) ve [XML Şema Bölüm 2: Datatypes](https://www.w3.org/TR/xmlschema-2/) önerileri destekler.

- <xref:System.Xml.Xsl?displayProperty=nameWithType> Ad alanındaki [sınıflar, W3C XSLT 1.0](https://www.w3.org/TR/xslt) önerisine uygun XSLT dönüşümlerini destekler.

.NET Framework'deki XML sınıfları aşağıdaki avantajları sağlar:

- **Verimli -lik.** [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) ve [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) XML ile programlanmayı kolaylaştırır ve SQL'e benzer bir sorgu deneyimi sağlar.

- **Genişletilebilir -lik.** .NET Framework'deki XML sınıfları soyut temel sınıflar ve sanal yöntemler kullanarak genişletilebilir. Örneğin, önbellek akışını yerel diske <xref:System.Xml.XmlUrlResolver> depolayan sınıfın türetilmiş bir sınıfı oluşturabilirsiniz.

- **Takılabilir mimari.** .NET Framework, bileşenlerin birbirini kullanabileceği ve verilerin bileşenler arasında aktarılabildiği bir mimari sağlar. Örneğin, sınıfla birlikte <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> <xref:System.Xml.Xsl.XslCompiledTransform> bir veri deposu veya nesne dönüştürülebilir ve çıktı daha sonra başka bir depoya aktarılabilir veya bir web hizmetinden akış olarak döndürülebilir.

- **Performans.** Daha iyi uygulama performansı için,.NET Framework'deki Bazı XML sınıfları aşağıdaki özelliklere sahip akış tabanlı bir modeli destekler:

  - Yalnızca ileri, çekme modeli ayrıştama için<xref:System.Xml.XmlReader>minimum önbelleğe alma ( ).

  - Yalnızca ileri doğrulama<xref:System.Xml.XmlReader>( ).

  - Belgeye rasgele erişim sağlarken düğüm oluşturmayı tek bir sanal düğüme en<xref:System.Xml.XPath.XPathNavigator>aza indiren imleç stili gezintisi ( ).

  XSLT işleme gerektiğinde daha iyi performans için, <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.Xsl.XslCompiledTransform> sınıfla verimli bir şekilde çalışmak üzere tasarlanmış XPath sorguları için en iyi duruma getirilmiş, salt okunur bir depo olan sınıfı kullanabilirsiniz.

- **ADO.NET ile entegrasyon.** XML sınıfları ve [ADO.NET,](../../../../docs/framework/data/adonet/index.md) ilişkisel verileri ve XML'i bir araya getirmek için sıkıca entegre edilmiştir. Sınıf, <xref:System.Data.DataSet> veritabanından alınan verilerin bellek içi önbelleğidir. Sınıf, <xref:System.Data.DataSet> xml şemaları (XSD) olarak iç ilişkisel şema yapısını devam ettirebilmek <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter> bir XML belgesinin şema yapısını çıkarabilmek için XML'i ve sınıfları kullanarak XML okuma ve yazma yeteneğine sahiptir.

## <a name="in-this-section"></a>Bu Bölümde

[XML İşleme Seçenekleri](../../../../docs/standard/data/xml/xml-processing-options.md) XML verilerini işleme seçeneklerini tartışır.

[XML Verilerinin BellekTe İşlenmesi](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md) XML verilerinin bellekte işlenmesi için üç modeli tartışır: [LinQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) ve [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)sınıfı (W3C <xref:System.Xml.XmlDocument> Document Object Model'e dayalı) ve <xref:System.Xml.XPath.XPathDocument> sınıf (XPath veri modeline dayalı).

[XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)\
XSLT işlemcinin nasıl kullanılacağını açıklar.

[XML Şema Nesne Modeli (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)\
XML Şemaları (XSD) oluşturmak ve işlemek için kullanılan <xref:System.Xml.Schema.XmlSchema> sınıfları, bir şemayı yüklemek ve düzenlemek için bir sınıf sağlayarak açıklar.

[İlişkisel Verilerle XML Entegrasyonu ve ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md)\
.NET Framework'ün <xref:System.Data.DataSet> nesne ve <xref:System.Xml.XmlDataDocument> nesne aracılığıyla verilerin hem ilişkisel hem de hiyerarşik gösterimlerine gerçek zamanlı, eşzamanlı erişim sağladığını açıklar.

[XML Belgesinde Ad Alanlarını Yönetme](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)\
<xref:System.Xml.XmlNamespaceManager> Sınıfın ad alanı bilgilerini depolamak ve korumak için nasıl kullanıldığını açıklar.

[System.Xml Sınıflarında Tip Desteği](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)\
XML veri türlerinin CLR türleri ile nasıl eşleştiniriyi, <xref:System.Xml> XML veri türlerinin nasıl dönüştürülür ve sınıflardaki diğer tür destek özelliklerini açıklar.

## <a name="related-sections"></a>İlgili Bölümler

[ADO.NET](../../../../docs/framework/data/adonet/index.md)\
ADO.NET kullanarak verilere nasıl erişilir hakkında bilgi sağlar.

[Güvenlik](../../../../docs/standard/security/index.md)\
.NET Framework güvenlik sistemine genel bir bakış sağlar.
