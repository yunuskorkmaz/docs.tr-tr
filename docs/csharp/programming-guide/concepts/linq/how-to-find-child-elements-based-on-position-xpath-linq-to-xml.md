---
title: 'Nasıl yapılır: Konuma göre alt öğeleri bul (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: e35bb269-ec86-4c96-8321-12491a0eb2c3
ms.openlocfilehash: b55e2df5a97446da9d02fd3979f5d8d584228ba2
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593492"
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-c"></a><span data-ttu-id="7d16c-102">Nasıl yapılır: Konuma göre alt öğeleri bul (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="7d16c-102">How to: Find Child Elements Based on Position (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="7d16c-103">Bazen, konumlarına göre öğeleri bulmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d16c-103">Sometimes you want to find elements based on their position.</span></span> <span data-ttu-id="7d16c-104">İkinci öğeyi bulmak isteyebilirsiniz veya beşinci öğe aracılığıyla üçüncü öğeyi bulmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d16c-104">You might want to find the second element, or you might want to find the third through the fifth element.</span></span>  
  
 <span data-ttu-id="7d16c-105">XPath ifadesi:</span><span class="sxs-lookup"><span data-stu-id="7d16c-105">The XPath expression is:</span></span>  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 <span data-ttu-id="7d16c-106">Bu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorguyu geç bir şekilde yazmak için iki yaklaşım vardır.</span><span class="sxs-lookup"><span data-stu-id="7d16c-106">There are two approaches to writing this [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query in a lazy way.</span></span> <span data-ttu-id="7d16c-107"><xref:System.Linq.Enumerable.Skip%2A> Ve<xref:System.Linq.Enumerable.Take%2A> işleçlerini kullanabilir<xref:System.Linq.Enumerable.Where%2A> veya bir dizini alan aşırı yüklemeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d16c-107">You can use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> operators, or you can use the <xref:System.Linq.Enumerable.Where%2A> overload that takes an index.</span></span> <span data-ttu-id="7d16c-108"><xref:System.Linq.Enumerable.Where%2A> Aşırı yüklemeyi kullandığınızda, iki bağımsız değişken alan bir lambda ifadesi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="7d16c-108">When you use the <xref:System.Linq.Enumerable.Where%2A> overload, you use a lambda expression that takes two arguments.</span></span> <span data-ttu-id="7d16c-109">Aşağıdaki örnek, konum temelinde seçim yapmak için her iki yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="7d16c-109">The following example shows both methods of selecting based on position.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d16c-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="7d16c-110">Example</span></span>  
 <span data-ttu-id="7d16c-111">Bu örnek, dördüncü `Test` öğe aracılığıyla ikincisini bulur.</span><span class="sxs-lookup"><span data-stu-id="7d16c-111">This example finds the second through the fourth `Test` element.</span></span> <span data-ttu-id="7d16c-112">Sonuç, öğelerin bir koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="7d16c-112">The result is a collection of elements.</span></span>  
  
 <span data-ttu-id="7d16c-113">Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Test yapılandırması (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7d16c-113">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="7d16c-114">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="7d16c-114">This example produces the following output:</span></span>  
  
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
