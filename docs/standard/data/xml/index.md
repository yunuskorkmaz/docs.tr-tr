---
title: XML Belgeleri ve Verileri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b5c774d566766936ebe043f264040ce26b8e9e3
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50202965"
---
# <a name="xml-documents-and-data"></a>XML Belgeleri ve Verileri
.NET Framework XML algılayan uygulamaları kolayca oluşturmanıza olanak tanıyan sınıf kapsamlı ve tümleşik kümesi sağlar. Aşağıdaki ad alanındaki sınıflar, ayrıştırma ve XML, bellek, veri doğrulama ve XSLT dönüşümü XML verilerini düzenleme yazma desteği.  
  
-   <xref:System.Xml>  
  
-   <xref:System.Xml.XPath>  
  
-   <xref:System.Xml.Xsl>  
  
-   <xref:System.Xml.Schema>  
  
-   <xref:System.Xml.Linq>  
  
 Tam bir listesi için bkz [System.Xml ad alanlarında](https://msdn.microsoft.com/library/gg145036.aspx) Web sayfası.  
  
 Bu ad alanındaki sınıflar, World Wide Web Consortium (W3C) önerileri destekler. Örneğin:  
  
-   <xref:System.Xml.XmlDocument?displayProperty=nameWithType> Sınıfının Implements [W3C belge nesne modeli (DOM) Düzey 1 çekirdek](https://www.w3.org/TR/REC-DOM-Level-1/) ve [DOM düzeyi 2 Çekirdek](https://www.w3.org/TR/DOM-Level-2-Core/) öneriler.  
  
-   <xref:System.Xml.XmlReader?displayProperty=nameWithType> Ve <xref:System.Xml.XmlWriter?displayProperty=nameWithType> destek sınıfları [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) ve [ad alanları XML](https://www.w3.org/TR/REC-xml-names/) öneriler.  
  
-   Şemalarda <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> sınıf destek [W3C XML Şeması Kısım 1: yapıları](https://www.w3.org/TR/xmlschema-1/) ve [XML şema bölümü 2: veri türleri](https://www.w3.org/TR/xmlschema-2/) öneriler.  
  
-   Sınıflar <xref:System.Xml.Xsl?displayProperty=nameWithType> uygun ad alanı desteği XSLT dönüşümleri [W3C XSLT 1.0](https://www.w3.org/TR/xslt) öneri.  
  
 .NET Framework XML sınıflarda aşağıdaki avantajları sağlar:  
  
-   **Üretkenlik.** [LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) XML programla kolaylaştırır ve SQL'e benzeyen bir sorgu deneyimi sağlar.  
  
-   **Genişletilebilirlik.** .NET Framework'te XML sınıflarının soyut temel sınıflar ve sanal yöntemleri kullanılarak genişletilebilir. Örneğin, türetilmiş bir sınıf oluşturabilirsiniz <xref:System.Xml.XmlUrlResolver> yerel disk önbellek akışa depolayan sınıf.  
  
-   **Eklenebilir mimari.** .NET Framework bileşenleri, birbirleriyle kullanabilir ve bileşenler arasında verilerin gönderilebilen bir mimari sağlar. Örneğin, bir veri deposu gibi bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesne, ile dönüştürülebilir <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı ve çıktısını ardından olabilir ya da başka bir depoya akış yoluyla veya bir web hizmetinden bir akış olarak döndürdü.  
  
-   **Performans.** Daha iyi uygulama performansını için .NET Framework XML sınıflarda bazıları aşağıdaki özelliklere sahip bir akış tabanlı model destekler:  
  
    -   Yalnızca iletme, çekme modeli ayrıştırmak için en az önbelleğe alma (<xref:System.Xml.XmlReader>).  
  
    -   Yalnızca iletme doğrulama (<xref:System.Xml.XmlReader>).  
  
    -   Tek bir sanal düğüm için düğüm oluşturma belge için rastgele erişim sağlarken en aza indirir, imleç stil Gezinti (<xref:System.Xml.XPath.XPathNavigator>).  
  
     Daha iyi performans için XSLT işleme gerektiğinde kullanabileceğiniz <xref:System.Xml.XPath.XPathDocument> bir XPath sorguları ile verimli bir şekilde çalışmak üzere tasarlanmış için iyileştirilmiş, salt okunur depo sınıfını <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.  
  
-   **ADO.NET ile tümleştirme.** XML sınıfları ve [ADO.NET](../../../../docs/framework/data/adonet/index.md) ilişkisel veriler ve XML bir araya getirmek için sıkı bir şekilde tümleştirilmiştir. <xref:System.Data.DataSet> Sınıfı, bir bellek içi önbelleği bir veritabanından alınan veri. <xref:System.Data.DataSet> Sınıfında okuma ve XML kullanarak yazma olanağı <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter> sınıfları, iç ilişkisel şema yapısını XML şemaları (XSD) kalıcı hale getirmek için ve bir XML belgesi şema yapısını çıkarsamak için.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [XML İşleme Seçenekleri](../../../../docs/standard/data/xml/xml-processing-options.md)  
 XML verilerini işlemek için seçenekleri açıklar.  
  
 [XML Verilerini Bellek İçinde İşleme](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md)  
 XML verilerini bellek içi işleme için üç model açıklanmaktadır. [LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13), <xref:System.Xml.XmlDocument> (W3C belge nesnesi modeline dayalı), sınıf ve <xref:System.Xml.XPath.XPathDocument> sınıfı (XPath veri modelini temel).  
  
 [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)  
 XSLT işlemci kullanmayı açıklar.  
  
 [XML Şema Nesne Modeli (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 XML şemaları (XSD) sağlayarak düzenleme ve oluşturma için kullanılan sınıfları açıklar bir <xref:System.Xml.Schema.XmlSchema> yüklemek ve bir şema düzenlemek için sınıf.  
  
 [İlişkisel Veriler ve ADO.NET ile XML Tümleştirmesi](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md)  
 .NET Framework verilerine ilişkisel ve hiyerarşik temsillerini gerçek zamanlı, zaman uyumlu erişimi nasıl sağladığını açıklar <xref:System.Data.DataSet> nesne ve <xref:System.Xml.XmlDataDocument> nesne.  
  
 [XML Belgesinde Ad Alanlarını Yönetme](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)  
 Açıklayan nasıl <xref:System.Xml.XmlNamespaceManager> sınıfı depolamak ve ad alanı bilgileri korumak için kullanılır.  
  
 [System.Xml Sınıflarında Tür Desteği](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)  
 Nasıl XML veri türü eşlemesi için CLR türleri, XML veri türleri ve diğer tür destek özellikleri nasıl dönüştürme yapılacağını açıklar <xref:System.Xml> sınıfları.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 ADO.NET kullanarak veri erişim hakkında bilgi sağlar.  
  
 [Güvenlik](../../../../docs/standard/security/index.md)  
 .NET Framework güvenlik sistemini genel bir bakış sağlar.  
  