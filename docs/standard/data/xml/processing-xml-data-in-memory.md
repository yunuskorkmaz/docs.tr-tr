---
title: XML Verilerini Bellek İçinde İşleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7fee2b5f4950efedc6ee335d5fbd417b8c178fbd
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424403"
---
# <a name="processing-xml-data-in-memory"></a>XML Verilerini Bellek İçinde İşleme
Microsoft .NET Framework, XML verilerini işlemek için üç model içerir: <xref:System.Xml.XmlDocument> sınıfı, <xref:System.Xml.XPath.XPathDocument> sınıfı ve [LINQ to XMLC#()](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) ve [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).  
  
 <xref:System.Xml.XmlDocument> sınıfı, W3C belge nesne modeli (DOM) düzey 1 çekirdeğini ve çekirdek DOM düzeyi 2 önerilerini uygular. DOM, bir XML belgesinin bellek içi (önbellek) ağaç gösterimidir. <xref:System.Xml.XmlDocument> ve ilgili sınıfları ile XML belgeleri oluşturabilir, verileri yükleyebilir ve erişebilir, verileri değiştirebilir ve değişiklikleri kaydedebilirsiniz.  
  
 <xref:System.Xml.XPath.XPathDocument> sınıfı, XPath veri modelini temel alan salt okunabilir, bellek içi veri deposudur. <xref:System.Xml.XPath.XPathNavigator> sınıfı, salt okunurdur <xref:System.Xml.XPath.XPathDocument> sınıfında ve <xref:System.Xml.XmlDocument> sınıfında yer alan XML belgeleri üzerinde bir imleç modeli kullanarak birkaç düzenleyici seçeneği ve gezinme özelliği sunar.  
  
 [LINQ to XML](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) , XML verilerini işlemek için .NET Framework sürüm 3,5 ' de tanıtılan bir modeldir. [Dil Ile tümleşik sorgu (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md)kullanan bellek içi bir modeldir. LINQ, yeni sorgu özellikleri sağlamak C# için ve Visual Basic dil sözdizimini genişletir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [DOM Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 XML verilerini işlemek için <xref:System.Xml.XmlDocument>ve ilgili sınıflarının kullanımını açıklar.  
  
 [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 XML verilerini işlemek için <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>ve <xref:System.Xml.XPath.XPathNavigator> sınıflarının kullanımını açıklar.  
  
 [LINQ to XML Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-linq-to-xml.md)  
 LINQ to XML kısa bir genel bakış sağlar ve LINQ to XML belgelerine bağlantılar sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [XML Belgeleri ve Verileri](../../../../docs/standard/data/xml/index.md)
