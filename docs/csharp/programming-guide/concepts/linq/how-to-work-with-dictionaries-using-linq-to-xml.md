---
title: LINQ to XML (C#) kullanarak sözlüklerle nasıl çalışIlir?
ms.date: 07/20/2015
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: 1a98293f208e80e969362fca27014ecd2e5c4183
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347219"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a><span data-ttu-id="23c85-102">LINQ to XML (C#) kullanarak sözlüklerle nasıl çalışIlir?</span><span class="sxs-lookup"><span data-stu-id="23c85-102">How to work with dictionaries using LINQ to XML (C#)</span></span>
<span data-ttu-id="23c85-103">Veri yapılarının çeşitlerini XML'e, XML'i ise diğer veri yapılarına dönüştürmek genellikle uygundur.</span><span class="sxs-lookup"><span data-stu-id="23c85-103">It is often convenient to convert varieties of data structures to XML, and XML back to other data structures.</span></span> <span data-ttu-id="23c85-104">Bu konu, bir <xref:System.Collections.Generic.Dictionary%602> XML ve geri dönüştürerek bu genel yaklaşımın belirli bir uygulama gösterir.</span><span class="sxs-lookup"><span data-stu-id="23c85-104">This topic shows a specific implementation of this general approach by converting a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23c85-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="23c85-105">Example</span></span>  
 <span data-ttu-id="23c85-106">Bu örnek, sorgunun yeni <xref:System.Xml.Linq.XElement> nesneleri oluşturduğu ve ortaya çıkan koleksiyonun Kök <xref:System.Xml.Linq.XElement> nesnenin oluşturucusu için bağımsız değişken olarak geçtiği işlevsel bir yapı biçimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="23c85-106">This example uses a form of functional construction in which a query projects new <xref:System.Xml.Linq.XElement> objects, and the resulting collection is passed as an argument to the constructor of the Root <xref:System.Xml.Linq.XElement> object.</span></span>  
  
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
  
 <span data-ttu-id="23c85-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="23c85-107">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="23c85-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="23c85-108">Example</span></span>  
 <span data-ttu-id="23c85-109">Aşağıdaki kod XML bir sözlük oluşturur.</span><span class="sxs-lookup"><span data-stu-id="23c85-109">The following code creates a dictionary from XML.</span></span>  
  
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
  
 <span data-ttu-id="23c85-110">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="23c85-110">This code produces the following output:</span></span>  
  
```output  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
