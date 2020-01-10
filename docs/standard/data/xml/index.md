---
title: XML Belgeleri ve Verileri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
ms.openlocfilehash: e0c3f3e99b06b65caf79d87a7831369f6fb33b08
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710797"
---
# <a name="xml-documents-and-data"></a>XML Belgeleri ve Verileri

.NET Framework, XML kullanan uygulamaları kolayca oluşturmanıza olanak tanıyan kapsamlı ve tümleşik bir sınıf kümesi sağlar. Aşağıdaki ad alanlarındaki sınıflar, XML 'i ayrıştırmayı ve yazmayı, bellekte XML verilerini düzenlemenizi, veri doğrulamayı ve XSLT dönüşümünü destekler.

- <xref:System.Xml>

- <xref:System.Xml.XPath>

- <xref:System.Xml.Xsl>

- <xref:System.Xml.Schema>

- <xref:System.Xml.Linq>

Tam liste için [.NET API tarayıcısı](https://docs.microsoft.com/dotnet/api/?term=system.xml)üzerinde "System. xml" araması yapın.

Bu ad alanındaki sınıflar World Wide Web Konsorsiyumu (W3C) önerilerini destekler. Örneğin:

- <xref:System.Xml.XmlDocument?displayProperty=nameWithType> sınıfı, [W3C belge nesne modeli (DOM) düzey 1 Core](https://www.w3.org/TR/REC-DOM-Level-1/) ve [DOM düzey 2 temel](https://www.w3.org/TR/DOM-Level-2-Core/) önerilerini uygular.

- <xref:System.Xml.XmlReader?displayProperty=nameWithType> ve <xref:System.Xml.XmlWriter?displayProperty=nameWithType> sınıfları [W3C xml 1,0](https://www.w3.org/TR/2006/REC-xml-20060816/) ' i ve XML önerilerinde [ad alanlarını](https://www.w3.org/TR/REC-xml-names/) destekler.

- <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> sınıfındaki şemalar [W3C XML şeması Bölüm 1: yapılar](https://www.w3.org/TR/xmlschema-1/) ve [XML şeması Bölüm 2: veri türleri](https://www.w3.org/TR/xmlschema-2/) önerilerini destekler.

- <xref:System.Xml.Xsl?displayProperty=nameWithType> ad alanındaki sınıflar, [W3C xslt 1,0](https://www.w3.org/TR/xslt) önerisi Ile uyumlu XSLT dönüştürmelerini destekler.

.NET Framework XML sınıfları şu avantajları sağlar:

- **Kişilere.** [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) ve [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) , XML ile programlanmasını kolaylaştırır ve SQL 'e benzer bir sorgu deneyimi sağlar.

- **Genişletme.** .NET Framework XML sınıfları soyut temel sınıfların ve Sanal yöntemlerin kullanımı ile genişletilebilir. Örneğin, önbellek akışını yerel diske depolayan <xref:System.Xml.XmlUrlResolver> sınıfının türetilmiş bir sınıfını oluşturabilirsiniz.

- **Takılabilir mimari.** .NET Framework, bileşenlerin bir diğeri tarafından kullanılabilecek bir mimari sağlar ve verilerin bileşenler arasında akışı yapılabilir. Örneğin, bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesnesi gibi bir veri deposu <xref:System.Xml.Xsl.XslCompiledTransform> sınıfıyla dönüştürülebilir ve çıkış daha sonra başka bir depoya akışı yapılabilir veya bir Web hizmetinden akış olarak döndürülür.

- **Performans.** Daha iyi uygulama performansı için .NET Framework bazı XML sınıfları aşağıdaki özelliklerle akış tabanlı bir modeli destekler:

  - Yalnızca iletme, çekme modeli ayrıştırma (<xref:System.Xml.XmlReader>) için en az önbelleğe alma.

  - Yalnızca ileri doğrulama (<xref:System.Xml.XmlReader>).

  - Belgeye rastgele erişim sağlarken, düğüm oluşturmayı tek bir sanal düğüme en aza indiren imleç stili Gezintisi (<xref:System.Xml.XPath.XPathNavigator>).

  XSLT işleme gerektiğinde daha iyi performans için, <xref:System.Xml.Xsl.XslCompiledTransform> sınıfıyla verimli şekilde çalışacak şekilde tasarlanan XPath sorguları için iyileştirilmiş, salt okunurdur bir depo olan <xref:System.Xml.XPath.XPathDocument> sınıfını kullanabilirsiniz.

- **ADO.NET ile tümleştirme.** XML sınıfları ve [ADO.net](../../../../docs/framework/data/adonet/index.md) , ilişkisel VERILERI ve XML 'yi biraraya getirmek için sıkı bir şekilde tümleşiktir. <xref:System.Data.DataSet> sınıfı, bir veritabanından alınan verilerin bellek içi önbelleğidir. <xref:System.Data.DataSet> sınıfı, iç ilişkisel şema yapısını XML şemaları (XSD) olarak kalıcı hale getirmek ve bir XML belgesinin şema yapısını çıkarması için <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter> sınıfları kullanarak XML okuma ve yazma özelliğine sahiptir.

## <a name="in-this-section"></a>Bu Bölümde

[XML Işleme seçenekleri](../../../../docs/standard/data/xml/xml-processing-options.md) XML verilerini işlemeye yönelik seçenekleri açıklar.

[XML verilerini bellek Içinde işleme](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md) XML verilerini bellek içinde işlemeye yönelik üç modeli açıklar: [LINQ to XMLC#()](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) ve [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md), <xref:System.Xml.XmlDocument> sınıfı (W3C belge nesne modeli tabanlı) ve <xref:System.Xml.XPath.XPathDocument> sınıfı (XPath veri modeline göre).

[XSLT dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)\
XSLT işlemcisinin nasıl kullanılacağını açıklar.

[XML şema nesne modeli (som)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)\
Bir şemayı yüklemek ve düzenlemek için bir <xref:System.Xml.Schema.XmlSchema> sınıfı sağlayarak XML şemaları (XSD) oluşturmak ve işlemek için kullanılan sınıfları açıklar.

[Ilişkisel verilerle XML tümleştirmesi ve ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md)\
.NET Framework, <xref:System.Data.DataSet> nesnesi ve <xref:System.Xml.XmlDataDocument> nesnesi aracılığıyla hem ilişkisel hem de hiyerarşik veri temsillerine gerçek zamanlı, zaman uyumlu erişim sağlar.

[BIR XML belgesinde ad alanlarını yönetme](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)\
Ad alanı bilgilerini depolamak ve korumak için <xref:System.Xml.XmlNamespaceManager> sınıfının nasıl kullanıldığını açıklar.

[System. xml sınıflarında support yazın](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)\
XML veri türlerinin CLR türlerini nasıl eşledikleri, XML veri türlerinin nasıl dönüştürüleceği ve <xref:System.Xml> sınıflarında diğer tür destek özelliklerinin nasıl eşlendikleri açıklanmaktadır.

## <a name="related-sections"></a>İlgili Bölümler

[ADO.NET](../../../../docs/framework/data/adonet/index.md)\
ADO.NET kullanarak verilere erişme hakkında bilgi sağlar.

[Güvenlik](../../../../docs/standard/security/index.md)\
.NET Framework güvenlik sistemine genel bir bakış sağlar.
