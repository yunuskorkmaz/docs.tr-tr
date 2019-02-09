---
title: XML verilerini işleme, bellek
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8e6e89cafeb4cc580edb9630ba7415a669ea750c
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904407"
---
# <a name="processing-xml-data-in-memory"></a>XML verilerini işleme, bellek
Microsoft .NET Framework XML verilerini işlemek için üç model içerir: <xref:System.Xml.XmlDocument> sınıfı <xref:System.Xml.XPath.XPathDocument> sınıfı ve [LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).  
  
 <xref:System.Xml.XmlDocument> Sınıfı W3C belge nesne modeli (DOM) Düzey 1 çekirdek uygular ve çekirdek DOM Düzey 2 öneriler. DOM bir bellek içi (önbellek) olan bir XML belgesi gösterimini ağaç. İle <xref:System.Xml.XmlDocument> ve ilişkili sınıflarının, XML belgeleri oluşturmak, yüklemek ve verilere erişir, verileri değiştirme ve değişiklikleri kaydedilsin.  
  
 <xref:System.Xml.XPath.XPathDocument> XPath veri modelini temel alan bir salt okunur, bellek içi veri deposuna bir sınıftır. <xref:System.Xml.XPath.XPathNavigator> Sınıfı sunar birkaç düzenleme seçeneklerini ve gezinti özellikleri salt okunur bulunan XML belgeleri üzerinde bir imleç modeli kullanarak <xref:System.Xml.XPath.XPathDocument> sınıfı yanı sıra <xref:System.Xml.XmlDocument> sınıfı.  
  
 [LINQ to XML](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) .NET Framework sürüm 3.5 XML verilerini işlemek için sunulan bir modeli. Bunu yararlanan bir bellek içi modelidir [dil ile tümleşik sorgu (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md). LINQ genişletir dili sözdizimi C# ve Visual Basic yeni sorgu işlevleri sağlayın.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DOM Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 Kullanımını açıklar <xref:System.Xml.XmlDocument>ve ilişkili sınıflarının XML verilerini işleme.  
  
 [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 Kullanımını açıklar <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, ve <xref:System.Xml.XPath.XPathNavigator> XML verilerini işleme sınıfları.  
  
 [LINQ to XML Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-linq-to-xml.md)  
 XML için LINQ kısa bir genel bakış sağlar ve LINQ to XML belgeleri için bağlantılar sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [XML Belgeleri ve Verileri](../../../../docs/standard/data/xml/index.md)
