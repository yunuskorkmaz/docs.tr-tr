---
title: XML Belgeleri ve Verileri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
ms.openlocfilehash: 6d2a52567a1fc8bdbbb1d039ac583c889d77d4af
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540140"
---
# <a name="xml-documents-and-data"></a>XML Belgeleri ve Verileri

.NET Framework, XML kullanan uygulamaları kolayca oluşturmanıza olanak tanıyan kapsamlı ve tümleşik bir sınıf kümesi sağlar. Aşağıdaki ad alanlarındaki sınıflar, XML 'i ayrıştırmayı ve yazmayı, bellekte XML verilerini düzenlemenizi, veri doğrulamayı ve XSLT dönüşümünü destekler.

- <xref:System.Xml>

- <xref:System.Xml.XPath>

- <xref:System.Xml.Xsl>

- <xref:System.Xml.Schema>

- <xref:System.Xml.Linq>

Tam liste için [.NET API tarayıcısında](../../../../api/index.md?term=system.xml)"System.Xml" araması yapın.

Bu ad alanındaki sınıflar World Wide Web Konsorsiyumu (W3C) önerilerini destekler. Örnek:

- <xref:System.Xml.XmlDocument?displayProperty=nameWithType>Sınıfı, [W3C belge nesne MODELI (DOM) düzey 1 Core](https://www.w3.org/TR/REC-DOM-Level-1/) ve [DOM düzey 2 temel](https://www.w3.org/TR/DOM-Level-2-Core/) önerilerini uygular.

- <xref:System.Xml.XmlReader?displayProperty=nameWithType>Ve <xref:System.Xml.XmlWriter?displayProperty=nameWithType> SıNıFLARı [W3C XML 1,0](https://www.w3.org/TR/2006/REC-xml-20060816/) ' i ve XML önerilerinde [ad alanlarını](https://www.w3.org/TR/REC-xml-names/) destekler.

- <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType>Sınıftaki şemalar [W3C XML şeması Bölüm 1: yapılar](https://www.w3.org/TR/xmlschema-1/) ve [XML şeması Bölüm 2: veri türleri](https://www.w3.org/TR/xmlschema-2/) önerilerini destekler.

- <xref:System.Xml.Xsl?displayProperty=nameWithType>Ad alanındaki sınıflar, [W3C XSLT 1,0](https://www.w3.org/TR/xslt) ÖNERISI ile uyumlu XSLT dönüştürmelerini destekler.

.NET Framework XML sınıfları şu avantajları sağlar:

- **Kişilere.** [LINQ to XML (C#)](../../linq/linq-xml-overview.md) ve [LINQ to XML (VISUAL BASIC)](../../linq/linq-xml-overview.md) , XML ile PROGRAMLANMASıNı kolaylaştırır ve SQL 'e benzer bir sorgu deneyimi sağlar.

- **Genişletme.** .NET Framework XML sınıfları soyut temel sınıfların ve Sanal yöntemlerin kullanımı ile genişletilebilir. Örneğin, <xref:System.Xml.XmlUrlResolver> önbellek akışını yerel diske depolayan sınıfın türetilmiş bir sınıfını oluşturabilirsiniz.

- **Takılabilir mimari.** .NET Framework, bileşenlerin bir diğeri tarafından kullanılabilecek bir mimari sağlar ve verilerin bileşenler arasında akışı yapılabilir. Örneğin, bir veya nesnesi gibi bir veri deposu <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> <xref:System.Xml.Xsl.XslCompiledTransform> sınıfıyla dönüştürülebilir ve daha sonra çıktı, başka bir depoya akışı yapılabilir veya bir Web hizmetinden akış olarak döndürülür.

- **Mının.** Daha iyi uygulama performansı için .NET Framework bazı XML sınıfları aşağıdaki özelliklerle akış tabanlı bir modeli destekler:

  - Yalnızca iletme, çekme modeli ayrıştırma () için en az önbelleğe alma <xref:System.Xml.XmlReader> .

  - Yalnızca ileri doğrulama ( <xref:System.Xml.XmlReader> ).

  - Belgeye rastgele erişim sağlarken, düğüm oluşturmayı tek bir sanal düğüme en aza indiren imleç stili gezintisi <xref:System.Xml.XPath.XPathNavigator> .

  XSLT işleme gerektiğinde daha iyi performans için, <xref:System.Xml.XPath.XPathDocument> sınıfıyla verimli şekilde çalışacak şekilde tasarlanan XPath sorguları için iyileştirilmiş, salt okunurdur bir depo olan sınıfını kullanabilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> .

- **ADO.NET ile tümleştirme.** XML sınıfları ve [ADO.net](../../../framework/data/adonet/index.md) , ilişkisel VERILERI ve XML 'yi biraraya getirmek için sıkı bir şekilde tümleşiktir. <xref:System.Data.DataSet>Sınıfı, bir veritabanından alınan verilerin bellek içi önbelleğidir. <xref:System.Data.DataSet>Sınıfı, ve sınıflarını kullanarak XML okuma ve yazma özelliğine sahiptir <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> , iç ILIŞKISEL şema yapısını XML şemaları (xsd) olarak kalıcı hale getırmek ve bir XML belgesinin şema yapısını çıkarması için.

## <a name="in-this-section"></a>Bu Bölümde

[XML Işleme seçenekleri](xml-processing-options.md) XML verilerini işlemeye yönelik seçenekleri açıklar.

[XML verilerini bellek Içinde işleme](processing-xml-data-in-memory.md) XML verilerini bellek içinde işlemeye yönelik üç modeli açıklar: [LINQ to XML (C#)](../../linq/linq-xml-overview.md) ve [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md), <xref:System.Xml.XmlDocument> sınıfı (W3C belge nesne modeli göre) ve <xref:System.Xml.XPath.XPathDocument> sınıfı (XPath veri modeline göre).

[XSLT dönüşümleri](xslt-transformations.md)\
XSLT işlemcisinin nasıl kullanılacağını açıklar.

[XML şema nesne modeli (SOM)](xml-schema-object-model-som.md)\
<xref:System.Xml.Schema.XmlSchema>Bir şemayı yüklemek ve düzenlemek için bir sınıf sağlayarak xml şemaları (xsd) oluşturmak ve işlemek için kullanılan sınıfları açıklar.

[Ilişkisel verilerle XML tümleştirmesi ve ADO.NET](xml-integration-with-relational-data-and-adonet.md)\
.NET Framework, nesne ve nesne aracılığıyla hem ilişkisel hem de hiyerarşik veri temsillerine gerçek zamanlı, zaman uyumlu erişim nasıl olanak sağladığını açıklar <xref:System.Data.DataSet> <xref:System.Xml.XmlDataDocument> .

[XML belgesinde ad alanlarını yönetme](managing-namespaces-in-an-xml-document.md)\
<xref:System.Xml.XmlNamespaceManager>Sınıfının ad alanı bilgilerini depolamak ve korumak için nasıl kullanıldığını açıklar.

[System.Xml sınıflarında destek yazın](type-support-in-the-system-xml-classes.md)\
XML veri türlerinin CLR türleriyle nasıl eşlendikleri, XML veri türlerinin nasıl dönüştürüleceği ve sınıflardaki diğer tür desteğinin nasıl değiştirileceği açıklanmaktadır <xref:System.Xml> .

## <a name="related-sections"></a>İlgili Bölümler

[ADO.NET](../../../framework/data/adonet/index.md)\
ADO.NET kullanarak verilere erişme hakkında bilgi sağlar.

[Güven](../../security/index.md)\
.NET Framework güvenlik sistemine genel bir bakış sağlar.
