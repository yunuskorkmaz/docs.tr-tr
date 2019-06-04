---
title: 'Nasıl yapılır: LINQ to XML kullanarak sözlükleri çalışın (C#)'
ms.date: 07/20/2015
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: 196720ff9c17e62f8da9e65e1b8c481fed5074cc
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484719"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-c"></a><span data-ttu-id="cec9f-102">Nasıl yapılır: LINQ to XML kullanarak sözlükleri çalışın (C#)</span><span class="sxs-lookup"><span data-stu-id="cec9f-102">How to: Work with Dictionaries Using LINQ to XML (C#)</span></span>
<span data-ttu-id="cec9f-103">Genellikle, diğer veri yapılarını XML ve XML veri yapılarını çeşitleri dönüştürmek uygundur.</span><span class="sxs-lookup"><span data-stu-id="cec9f-103">It is often convenient to convert varieties of data structures to XML, and XML back to other data structures.</span></span> <span data-ttu-id="cec9f-104">Bu konuda dönüştürerek genel bu yaklaşım, belirli bir uygulama gösterilmektedir. bir <xref:System.Collections.Generic.Dictionary%602> XML ve geri.</span><span class="sxs-lookup"><span data-stu-id="cec9f-104">This topic shows a specific implementation of this general approach by converting a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cec9f-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="cec9f-105">Example</span></span>  
 <span data-ttu-id="cec9f-106">Bu örnekte bir form içinde bir sorgu projelerde yeni bir işlev oluşturma <xref:System.Xml.Linq.XElement> nesneleri ve sonuçta elde edilen koleksiyon geçirilen bağımsız değişken olarak kök oluşturucuya <xref:System.Xml.Linq.XElement> nesne.</span><span class="sxs-lookup"><span data-stu-id="cec9f-106">This example uses a form of functional construction in which a query projects new <xref:System.Xml.Linq.XElement> objects, and the resulting collection is passed as an argument to the constructor of the Root <xref:System.Xml.Linq.XElement> object.</span></span>  
  
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
  
 <span data-ttu-id="cec9f-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="cec9f-107">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="cec9f-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="cec9f-108">Example</span></span>  
 <span data-ttu-id="cec9f-109">Aşağıdaki kod, XML'den bir sözlük oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cec9f-109">The following code creates a dictionary from XML.</span></span>  
  
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
  
 <span data-ttu-id="cec9f-110">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="cec9f-110">This code produces the following output:</span></span>  
  
```  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  