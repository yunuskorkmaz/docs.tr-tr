---
title: 'Nasıl yapılır: Bul konumu (XPath-LINQ-XML) göre alt öğeleri (C#)'
ms.date: 07/20/2015
ms.assetid: e35bb269-ec86-4c96-8321-12491a0eb2c3
ms.openlocfilehash: ffe10bd5b263e56b6f2ee1708688523a2b0dd018
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317508"
---
# <a name="how-to-find-child-elements-based-on-position-xpath-linq-to-xml-c"></a><span data-ttu-id="06777-102">Nasıl yapılır: Bul konumu (XPath-LINQ-XML) göre alt öğeleri (C#)</span><span class="sxs-lookup"><span data-stu-id="06777-102">How to: Find Child Elements Based on Position (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="06777-103">Bazen kendi konumuna bağlı öğeleri bulmak istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="06777-103">Sometimes you want to find elements based on their position.</span></span> <span data-ttu-id="06777-104">İkinci öğe bulmak istediğiniz veya üçüncü beşinci öğe aracılığıyla bulmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06777-104">You might want to find the second element, or you might want to find the third through the fifth element.</span></span>  
  
 <span data-ttu-id="06777-105">XPath ifadesi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="06777-105">The XPath expression is:</span></span>  
  
 `Test[position() >= 2 and position() <= 4]`  
  
 <span data-ttu-id="06777-106">Bu yazma için iki yaklaşım vardır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yavaş bir şekilde sorgu.</span><span class="sxs-lookup"><span data-stu-id="06777-106">There are two approaches to writing this [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query in a lazy way.</span></span> <span data-ttu-id="06777-107">Kullanabileceğiniz <xref:System.Linq.Enumerable.Skip%2A> ve <xref:System.Linq.Enumerable.Take%2A> işleçleri veya kullanabilirsiniz <xref:System.Linq.Enumerable.Where%2A> dizin alan aşırı.</span><span class="sxs-lookup"><span data-stu-id="06777-107">You can use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> operators, or you can use the <xref:System.Linq.Enumerable.Where%2A> overload that takes an index.</span></span> <span data-ttu-id="06777-108">Kullandığınızda <xref:System.Linq.Enumerable.Where%2A> aşırı yüklemesi, iki bağımsız değişken almayan bir lambda ifadesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="06777-108">When you use the <xref:System.Linq.Enumerable.Where%2A> overload, you use a lambda expression that takes two arguments.</span></span> <span data-ttu-id="06777-109">Aşağıdaki örnek, her iki yöntem konumuna bağlı seçme gösterir.</span><span class="sxs-lookup"><span data-stu-id="06777-109">The following example shows both methods of selecting based on position.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06777-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="06777-110">Example</span></span>  
 <span data-ttu-id="06777-111">Bu örnek dördüncü aracılığıyla ikinci bulur `Test` öğesi.</span><span class="sxs-lookup"><span data-stu-id="06777-111">This example finds the second through the fourth `Test` element.</span></span> <span data-ttu-id="06777-112">Öğe koleksiyonunu sonucudur.</span><span class="sxs-lookup"><span data-stu-id="06777-112">The result is a collection of elements.</span></span>  
  
 <span data-ttu-id="06777-113">Bu örnekte aşağıdaki XML belgesi kullanır: [örnek XML dosyası: Test yapılandırmasını (LINQ-XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="06777-113">This example uses the following XML document: [Sample XML File: Test Configuration (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="06777-114">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="06777-114">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="06777-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="06777-115">See Also</span></span>  
 [<span data-ttu-id="06777-116">LINQ-XML XPath kullanıcıların (C#)</span><span class="sxs-lookup"><span data-stu-id="06777-116">LINQ to XML for XPath Users (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
