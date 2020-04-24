---
title: XML Verilerini Bellek İçinde İşleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
ms.openlocfilehash: 038bcfcb9d40ee6087efa3487b6f27f252393f2c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710433"
---
# <a name="processing-xml-data-in-memory"></a>XML Verilerini Bellek İçinde İşleme
Microsoft .NET Framework <xref:System.Xml.XmlDocument> , XML verilerini işlemek için üç model içerir: Class, <xref:System.Xml.XPath.XPathDocument> Class ve [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) ve [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).  
  
 <xref:System.Xml.XmlDocument> Sınıfı, W3C belge nesne MODELI (DOM) düzey 1 çekirdeğini ve çekirdek DOM düzeyi 2 önerilerini uygular. DOM, bir XML belgesinin bellek içi (önbellek) ağaç gösterimidir. <xref:System.Xml.XmlDocument> Ve ilgili SıNıFLARı ile XML belgeleri oluşturabilir, verileri yükleyebilir ve erişebilir, verileri değiştirebilir ve değişiklikleri kaydedebilirsiniz.  
  
 <xref:System.Xml.XPath.XPathDocument> Sınıfı, XPath veri modelini temel alan salt okunabilir, bellek içi veri deposudur. <xref:System.Xml.XPath.XPathNavigator> Sınıfı, salt okunurdur sınıfının yanı sıra <xref:System.Xml.XmlDocument> Read-Only <xref:System.Xml.XPath.XPathDocument> sınıfında bulunan XML belgeleri üzerinde bir imleç modeli kullanarak birkaç düzen seçeneği ve gezinti özelliği sunar.  
  
 [LINQ to XML](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) , XML verilerini işlemek için .NET Framework sürüm 3,5 ' de tanıtılan bir modeldir. [Dil Ile tümleşik sorgu (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md)kullanan bellek içi bir modeldir. LINQ, yeni sorgu özellikleri sağlamak için C# ve Visual Basic dil sözdizimini genişletir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DOM Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 XML verilerini işlemek <xref:System.Xml.XmlDocument>için ve ilgili sınıflarının kullanımını açıklar.  
  
 [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 XML verilerini işlemek <xref:System.Xml.XPath.XPathDocument>için <xref:System.Xml.XmlDocument>, ve <xref:System.Xml.XPath.XPathNavigator> sınıflarının kullanımını açıklar.  
  
 [LINQ to XML Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-linq-to-xml.md)  
 LINQ to XML kısa bir genel bakış sağlar ve LINQ to XML belgelerine bağlantılar sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [XML Belgeleri ve Verileri](../../../../docs/standard/data/xml/index.md)
