---
title: XML Verilerini Bellek İçinde İşleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
ms.openlocfilehash: 06863d162a9f9fbf67f41cb12ea4fbb1935b424d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291285"
---
# <a name="processing-xml-data-in-memory"></a>XML Verilerini Bellek İçinde İşleme
Microsoft .NET Framework, XML verilerini işlemek için üç model içerir: <xref:System.Xml.XmlDocument> Class, <xref:System.Xml.XPath.XPathDocument> class ve [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) ve [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).  
  
 <xref:System.Xml.XmlDocument>Sınıfı, W3C belge nesne modeli (DOM) düzey 1 çekirdeğini ve çekırdek DOM düzeyi 2 önerilerini uygular. DOM, bir XML belgesinin bellek içi (önbellek) ağaç gösterimidir. <xref:System.Xml.XmlDocument>Ve ilgili sınıfları Ile xml belgeleri oluşturabilir, verileri yükleyebilir ve erişebilir, verileri değiştirebilir ve değişiklikleri kaydedebilirsiniz.  
  
 <xref:System.Xml.XPath.XPathDocument>Sınıfı, XPath veri modelini temel alan salt okunabilir, bellek içi veri deposudur. <xref:System.Xml.XPath.XPathNavigator>Sınıfı, salt okunurdur sınıfının yanı sıra Read-Only sınıfında bulunan XML belgeleri üzerinde bir imleç modeli kullanarak birkaç düzen seçeneği ve gezinti özelliği sunar <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> .  
  
 [LINQ to XML](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) , XML verilerini işlemek için .NET Framework sürüm 3,5 ' de tanıtılan bir modeldir. [Dil Ile tümleşik sorgu (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md)kullanan bellek içi bir modeldir. LINQ, yeni sorgu özellikleri sağlamak için C# ve Visual Basic dil sözdizimini genişletir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DOM Modelini Kullanarak XML Verilerini İşleme](process-xml-data-using-the-dom-model.md)  
 <xref:System.Xml.XmlDocument>XML verilerini işlemek için ve ilgili sınıflarının kullanımını açıklar.  
  
 [XPath Veri Modelini Kullanarak XML Verilerini İşleme](process-xml-data-using-the-xpath-data-model.md)  
 <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDocument> <xref:System.Xml.XPath.XPathNavigator> XML verilerini işlemek için, ve sınıflarının kullanımını açıklar.  
  
 [LINQ to XML Kullanarak XML Verilerini İşleme](process-xml-data-using-linq-to-xml.md)  
 LINQ to XML kısa bir genel bakış sağlar ve LINQ to XML belgelerine bağlantılar sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [XML belgeleri ve verileri](index.md)
