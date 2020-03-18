---
title: Belirli bir alt öğe (C#) ile bir öğeyi bulma
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 0536b1b92d4d7fc18b5d406bbcd24aefc6a840c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141152"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a>Belirli bir alt öğe (C#) ile bir öğeyi bulma
Bu konu, belirli bir değere sahip bir alt öğeye sahip belirli bir öğeyi nasıl bulabileceğinizi gösterir.  
  
## <a name="example"></a>Örnek  
 Örnek, "Examp2.EXE" değerine sahip bir `Test` `CommandLine` alt öğeye sahip öğeyi bulur.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Test Yapılandırması (LINQ -XML)](./sample-xml-file-test-configuration-linq-to-xml.md).  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```output  
0002  
0006  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ad alanında olan XML için aynı sorguyu gösterir. Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Ad alanında Test Yapılandırması.](./sample-xml-file-test-configuration-in-a-namespace1.md)  
  
```csharp  
XElement root = XElement.Load("TestConfigInNamespace.xml");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<XElement> tests =  
    from el in root.Elements(ad + "Test")  
    where (string)el.Element(ad + "CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```output  
0002  
0006  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Standart Sorgu Operatörlerine Genel Bakış (C#)](./standard-query-operators-overview.md)
- [Projeksiyon İşlemleri (C#)](./projection-operations.md)
