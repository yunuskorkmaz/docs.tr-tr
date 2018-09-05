---
title: 'Nasıl yapılır: alt öğeleri bulma (XPath-LINQ to XML) konuma göre (C#)'
ms.date: 07/20/2015
ms.assetid: e35bb269-ec86-4c96-8321-12491a0eb2c3
ms.openlocfilehash: 5d62418fe6d89c8dc5c7ddb4975404f1a7e0aa2d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517099"
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-c"></a>Nasıl yapılır: alt öğeleri bulma (XPath-LINQ to XML) konuma göre (C#)
Bazen kendi konumlarına göre öğeleri bulmak istediğiniz. İkinci öğe bulmak isteyebilirsiniz veya beşinci öğeyi aracılığıyla üçüncü bulmak isteyebilirsiniz.  
  
 XPath ifadesidir:  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 Bu yazma için iki yaklaşım vardır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yavaş bir şekilde sorgu. Kullanabileceğiniz <xref:System.Linq.Enumerable.Skip%2A> ve <xref:System.Linq.Enumerable.Take%2A> işleçleri veya kullanabileceğiniz <xref:System.Linq.Enumerable.Where%2A> dizin alan aşırı yüklemesini. Kullanırken <xref:System.Linq.Enumerable.Where%2A> aşırı yüklemesi, iki bağımsız değişken alan bir lambda ifadesi kullanın. Aşağıdaki örnek, iki yöntem de konumlarına göre seçme gösterir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte ikinci dördüncü aracılığıyla bulur `Test` öğesi. Öğelerinin bir koleksiyonunu sonucudur.  
  
 Bu örnekte aşağıdaki XML belgesi: [örnek XML dosyası: Test yapılandırması (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).  
  
```csharp  
XElement testCfg = XElement.Load("TestConfig.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    testCfg  
    .Elements("Test")  
    .Skip(1)  
    .Take(3);  
  
// LINQ to XML query  
IEnumerable<XElement> list2 =  
    testCfg  
    .Elements("Test")  
    .Where((el, idx) => idx >= 1 && idx <= 3);  
  
// XPath expression  
IEnumerable<XElement> list3 =  
  testCfg.XPathSelectElements("Test[position() >= 2 and position() <= 4]");  
  
if (list1.Count() == list2.Count() &&  
    list1.Count() == list3.Count() &&  
    list1.Intersect(list2).Count() == list1.Count() &&  
    list1.Intersect(list3).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```  
Results are identical  
<Test TestId="0002" TestType="CMD">  
  <Name>Find succeeding characters</Name>  
  <CommandLine>Examp2.EXE</CommandLine>  
  <Input>abc</Input>  
  <Output>def</Output>  
</Test>  
<Test TestId="0003" TestType="GUI">  
  <Name>Convert multiple numbers to strings</Name>  
  <CommandLine>Examp2.EXE /Verbose</CommandLine>  
  <Input>123</Input>  
  <Output>One Two Three</Output>  
</Test>  
<Test TestId="0004" TestType="GUI">  
  <Name>Find correlated key</Name>  
  <CommandLine>Examp3.EXE</CommandLine>  
  <Input>a1</Input>  
  <Output>b1</Output>  
</Test>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [LINQ to XML için XPath kullanıcıları (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
