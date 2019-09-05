---
title: 'Nasıl yapılır: LINQ to XML (C#) kullanarak sözlüklerle çalışma'
ms.date: 07/20/2015
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: 55512e6039010d74d390c805c119935c436f9834
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253234"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a><span data-ttu-id="3fd7f-102">Nasıl yapılır: LINQ to XML (C#) kullanarak sözlüklerle çalışma</span><span class="sxs-lookup"><span data-stu-id="3fd7f-102">How to: Work with Dictionaries Using LINQ to XML (C#)</span></span>
<span data-ttu-id="3fd7f-103">Çok sayıda veri yapısını XML 'e ve XML 'e diğer veri yapılarına dönüştürmek genellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="3fd7f-103">It is often convenient to convert varieties of data structures to XML, and XML back to other data structures.</span></span> <span data-ttu-id="3fd7f-104">Bu konu, bir <xref:System.Collections.Generic.Dictionary%602> XML ve geri dönüştürerek bu genel yaklaşımın belirli bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3fd7f-104">This topic shows a specific implementation of this general approach by converting a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fd7f-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="3fd7f-105">Example</span></span>  
 <span data-ttu-id="3fd7f-106">Bu örnek, bir sorgu projelerinin yeni <xref:System.Xml.Linq.XElement> nesne ve elde edilen koleksiyonun bir bağımsız değişken olarak kök <xref:System.Xml.Linq.XElement> nesnenin oluşturucusuna geçirildiği işlevsel oluşturma formunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="3fd7f-106">This example uses a form of functional construction in which a query projects new <xref:System.Xml.Linq.XElement> objects, and the resulting collection is passed as an argument to the constructor of the Root <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
Dictionary<string, string> dict = new Dictionary<string, string>();  
dict.Add("Child1", "Value1");  
dict.Add("Child2", "Value2");  
dict.Add("Child3", "Value3");  
dict.Add("Child4", "Value4");  
XElement root = new XElement("Root",  
    from keyValue in dict  
    select new XElement(keyValue.Key, keyValue.Value)  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="3fd7f-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="3fd7f-107">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="3fd7f-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="3fd7f-108">Example</span></span>  
 <span data-ttu-id="3fd7f-109">Aşağıdaki kod XML 'den bir sözlük oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3fd7f-109">The following code creates a dictionary from XML.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "Value1"),  
    new XElement("Child2", "Value2"),  
    new XElement("Child3", "Value3"),  
    new XElement("Child4", "Value4")  
);  
  
Dictionary<string, string> dict = new Dictionary<string, string>();  
foreach (XElement el in root.Elements())  
    dict.Add(el.Name.LocalName, el.Value);  
foreach (string str in dict.Keys)  
    Console.WriteLine("{0}:{1}", str, dict[str]);  
```  
  
 <span data-ttu-id="3fd7f-110">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="3fd7f-110">This code produces the following output:</span></span>  
  
```output  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
