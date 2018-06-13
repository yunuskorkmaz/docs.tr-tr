---
title: XML Belgeleri ve Verileri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5f286d0f64478bfc46ca207086e4a6b918ee47b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576096"
---
# <a name="xml-documents-and-data"></a>XML Belgeleri ve Verileri
.NET Framework XML algılayan uygulamaları kolayca oluşturmanıza olanak tanıyan sınıflar kapsamlı ve tümleşik bir dizi sağlar. Aşağıdaki ad alanındaki sınıflar, ayrıştırma ve XML, bellek, veri doğrulama ve XSLT dönüşümü XML verileri düzenleme yazmayı destekler.  
  
-   <xref:System.Xml>  
  
-   <xref:System.Xml.XPath>  
  
-   <xref:System.Xml.Xsl>  
  
-   <xref:System.Xml.Schema>  
  
-   <xref:System.Xml.Linq>  
  
 Tam listesi için bkz: [System.Xml ad alanları](https://msdn.microsoft.com/library/gg145036.aspx) Web sayfası.  
  
 Bu ad alanındaki sınıflar World Wide Web Konsorsiyumu (W3C) önerileri destekler. Örneğin:  
  
-   <xref:System.Xml.XmlDocument?displayProperty=nameWithType> Uygulayan sınıf [W3C belge nesne modeli (DOM) Düzey 1 çekirdek](https://www.w3.org/TR/REC-DOM-Level-1/) ve [DOM Düzey 2 Çekirdek](https://www.w3.org/TR/DOM-Level-2-Core/) öneriler.  
  
-   <xref:System.Xml.XmlReader?displayProperty=nameWithType> Ve <xref:System.Xml.XmlWriter?displayProperty=nameWithType> sınıfları Destek [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) ve [XML ad alanları](https://www.w3.org/TR/REC-xml-names/) öneriler.  
  
-   Şemalarda <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> sınıf destek [W3C XML Şeması Kısım 1: yapıları](https://www.w3.org/TR/xmlschema-1/) ve [XML Şeması Kısım 2: veri türleri](https://www.w3.org/TR/xmlschema-2/) öneriler.  
  
-   Sınıfları <xref:System.Xml.Xsl?displayProperty=nameWithType> uygun ad alanı destek XSLT dönüştürmeleri [W3C XSLT 1.0](http://www.w3.org/TR/xslt) öneri.  
  
 .NET Framework XML sınıflarda şu avantajları sağlar:  
  
-   **Verimliliği.** [LINQ-XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) XML programla kolaylaştırır ve SQL için benzer bir sorgu deneyimi sağlar.  
  
-   **Genişletilebilirlik.** .NET Framework XML sınıflarının soyut taban sınıfları ve sanal yöntemler kullanılarak genişletilebilir. Örneğin, türetilen bir sınıftan oluşturabilirsiniz <xref:System.Xml.XmlUrlResolver> yerel disk önbelleği akışa depolayan sınıf.  
  
-   **Eklenebilir mimari.** .NET Framework bileşenlerini birbirine kullanabilir ve bileşenler arasında veri akışı bir mimari sağlar. Örneğin, bir veri deposu gibi bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> nesne, ile dönüştürülebilir <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı ve çıkış sonra olabilir ya da başka bir depoya akışı veya bir web hizmetinden bir akış olarak döndürdü.  
  
-   **Performans.** Daha iyi uygulama performans için .NET Framework'teki XML sınıfların bazıları aşağıdaki özelliklere sahip bir akış tabanlı modeli destekler:  
  
    -   Yalnızca iletme, çekme modeli ayrıştırmak için en az önbelleğe alma (<xref:System.Xml.XmlReader>).  
  
    -   Yalnızca iletme doğrulama (<xref:System.Xml.XmlReader>).  
  
    -   Belge için rasgele erişim sağlarken düğümü oluşturmayı, tek bir sanal düğümü en aza indirir imleç stili Gezinti (<xref:System.Xml.XPath.XPathNavigator>).  
  
     Daha iyi performans için XSLT işleme gerektiğinde kullanabileceğiniz <xref:System.Xml.XPath.XPathDocument> verimli bir şekilde çalışmak için tasarlanmış XPath sorguları için en iyi duruma getirilmiş, salt okunur bir depo sınıfı <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.  
  
-   **ADO.NET ile tümleştirme.** XML sınıfları ve [ADO.NET](../../../../docs/framework/data/adonet/index.md) ilişkisel veri ve XML araya getirmek için sıkı bir şekilde tümleştirilmiştir. <xref:System.Data.DataSet> Sınıfı, bir bellek içi önbellek bir veritabanından alınan veri. <xref:System.Data.DataSet> Sınıfına sahip okuma ve XML kullanarak yazma yeteneği <xref:System.Xml.XmlReader> ve <xref:System.Xml.XmlWriter> sınıfları, iç ilişkisel şema yapısını XML şemaları (XSD) kalır ve bir XML belgesi şema yapısını anlamak için.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [XML İşleme Seçenekleri](../../../../docs/standard/data/xml/xml-processing-options.md)  
 XML verilerini işlemek için seçenekleri açıklar.  
  
 [XML Verilerini Bellek İçinde İşleme](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md)  
 XML veri bellek içi işleme için üç modeli açıklanır. [LINQ-XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13), <xref:System.Xml.XmlDocument> (W3C belge nesne modeli üzerinde tabanlı), sınıf ve <xref:System.Xml.XPath.XPathDocument> sınıfı (XPath veri modeline bağlı).  
  
 [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)  
 XSLT işlemci kullanımını açıklar.  
  
 [XML Şema Nesne Modeli (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 Derleme ve sağlayarak XML şemaları (XSD) işlemek için kullanılan sınıflar açıklanmaktadır bir <xref:System.Xml.Schema.XmlSchema> yüklemek ve bir şema düzenlemek için sınıf.  
  
 [İlişkisel Veriler ve ADO.NET ile XML Tümleştirmesi](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md)  
 .NET Framework verilerine ilişkisel ve hiyerarşik gösterimlerini gerçek zamanlı, zaman uyumlu erişim nasıl sağladığını açıklar <xref:System.Data.DataSet> nesne ve <xref:System.Xml.XmlDataDocument> nesne.  
  
 [XML Belgesinde Ad Alanlarını Yönetme](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)  
 Açıklar nasıl <xref:System.Xml.XmlNamespaceManager> sınıfı depolamak ve ad alanı bilgilerini korumak için kullanılır.  
  
 [System.Xml Sınıflarında Tür Desteği](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)  
 Nasıl XML veri türü eşlemesi için CLR türleri, XML veri türleri ve diğer tür destek özellikleri dönüştürme açıklar <xref:System.Xml> sınıfları.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 ADO.NET kullanarak veri erişim hakkında bilgi sağlar.  
  
 [Güvenlik](../../../../docs/standard/security/index.md)  
 .NET Framework güvenlik sistemi genel bir bakış sağlar.  
  