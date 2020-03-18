---
title: Konuma göre alt öğeleri bulma (XPath-LINQ - XML) (C#)
ms.date: 07/20/2015
ms.assetid: e35bb269-ec86-4c96-8321-12491a0eb2c3
ms.openlocfilehash: cc0ff5639345d36ebb0423a12b66de8f1a70ade1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141127"
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-c"></a>Konuma göre alt öğeleri bulma (XPath-LINQ - XML) (C#)
Bazen konumlarına göre öğeleri bulmak istiyorum. İkinci öğeyi bulmak isteyebilirsiniz veya üçüncü öğeyi beşinci öğe ile bulmak isteyebilirsiniz.  
  
 XPath ifadesi:  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 Bu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorguyu tembel bir şekilde yazmak için iki yaklaşım vardır. İşleçleri <xref:System.Linq.Enumerable.Skip%2A> veya dizin gerektiren <xref:System.Linq.Enumerable.Where%2A> aşırı yüklemeyi kullanabilirsiniz. <xref:System.Linq.Enumerable.Take%2A> Aşırı yüklemeyi <xref:System.Linq.Enumerable.Where%2A> kullandığınızda, iki bağımsız değişken alan bir lambda ifadesi kullanırsınız. Aşağıdaki örnek, konuma göre seçim her iki yöntemi gösterir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, dördüncü `Test` öğe ile ikinci bulur. Sonuç, öğelertopluluğudur.  
  
 Bu örnekte aşağıdaki XML belgesi kullanır: [Örnek XML Dosyası: Test Yapılandırması (LINQ -XML)](./sample-xml-file-test-configuration-linq-to-xml.md).  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
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
