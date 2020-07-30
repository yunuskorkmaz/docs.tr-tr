---
title: Konuma göre alt öğeleri bulma (XPath-LINQ to XML) (C#)
description: Bir XPath ifadesi kullanarak konuma göre alt öğeleri bulmayı öğrenin. Örnek XML dosyası kullanan bir kod örneğini gözden geçirin.
ms.date: 07/20/2015
ms.assetid: e35bb269-ec86-4c96-8321-12491a0eb2c3
ms.openlocfilehash: 2603d3ac94ace645bde1ce85a43a43af7321014e
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301677"
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-c"></a><span data-ttu-id="48890-104">Konuma göre alt öğeleri bulma (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="48890-104">How to find child elements based on position (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="48890-105">Bazen, konumlarına göre öğeleri bulmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48890-105">Sometimes you want to find elements based on their position.</span></span> <span data-ttu-id="48890-106">İkinci öğeyi bulmak isteyebilirsiniz veya beşinci öğe aracılığıyla üçüncü öğeyi bulmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48890-106">You might want to find the second element, or you might want to find the third through the fifth element.</span></span>  
  
 <span data-ttu-id="48890-107">XPath ifadesi:</span><span class="sxs-lookup"><span data-stu-id="48890-107">The XPath expression is:</span></span>  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 <span data-ttu-id="48890-108">Bu sorguyu geç bir şekilde yazmak için iki yaklaşım vardır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="48890-108">There are two approaches to writing this [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query in a lazy way.</span></span> <span data-ttu-id="48890-109"><xref:System.Linq.Enumerable.Skip%2A>Ve <xref:System.Linq.Enumerable.Take%2A> işleçlerini kullanabilir veya <xref:System.Linq.Enumerable.Where%2A> bir dizini alan aşırı yüklemeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="48890-109">You can use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> operators, or you can use the <xref:System.Linq.Enumerable.Where%2A> overload that takes an index.</span></span> <span data-ttu-id="48890-110"><xref:System.Linq.Enumerable.Where%2A>Aşırı yüklemeyi kullandığınızda, iki bağımsız değişken alan bir lambda ifadesi kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="48890-110">When you use the <xref:System.Linq.Enumerable.Where%2A> overload, you use a lambda expression that takes two arguments.</span></span> <span data-ttu-id="48890-111">Aşağıdaki örnek, konum temelinde seçim yapmak için her iki yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="48890-111">The following example shows both methods of selecting based on position.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48890-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="48890-112">Example</span></span>  
 <span data-ttu-id="48890-113">Bu örnek, dördüncü öğe aracılığıyla ikincisini bulur `Test` .</span><span class="sxs-lookup"><span data-stu-id="48890-113">This example finds the second through the fourth `Test` element.</span></span> <span data-ttu-id="48890-114">Sonuç, öğelerin bir koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="48890-114">The result is a collection of elements.</span></span>  
  
 <span data-ttu-id="48890-115">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: test yapılandırması (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="48890-115">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="48890-116">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="48890-116">This example produces the following output:</span></span>  
  
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
