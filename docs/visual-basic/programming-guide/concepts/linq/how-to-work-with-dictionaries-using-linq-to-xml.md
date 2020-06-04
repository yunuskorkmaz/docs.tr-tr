---
title: 'Nasıl yapılır: LINQ to XML Kullanarak Sözlüklerle Çalışma'
ms.date: 07/20/2015
ms.assetid: 6cb3f969-1986-414a-b850-87418712edea
ms.openlocfilehash: 14c9c35693f323292849f01af79ae81f92921611
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397680"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-visual-basic"></a><span data-ttu-id="18c91-102">Nasıl yapılır: LINQ to XML kullanarak sözlüklerle çalışma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18c91-102">How to: Work with Dictionaries Using LINQ to XML (Visual Basic)</span></span>
<span data-ttu-id="18c91-103">Çok sayıda veri yapısını XML 'e ve XML 'e diğer veri yapılarına dönüştürmek genellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="18c91-103">It is often convenient to convert varieties of data structures to XML, and XML back to other data structures.</span></span> <span data-ttu-id="18c91-104">Bu konu, bir XML ve geri dönüştürerek bu genel yaklaşımın belirli bir uygulamasını gösterir <xref:System.Collections.Generic.Dictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="18c91-104">This topic shows a specific implementation of this general approach by converting a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18c91-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="18c91-105">Example</span></span>  
 <span data-ttu-id="18c91-106">Bu örnekte, katıştırılmış ifadede XML değişmez değerleri ve bir sorgu kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="18c91-106">This example uses XML literals and a query in an embedded expression.</span></span> <span data-ttu-id="18c91-107">Sorgu yeni <xref:System.Xml.Linq.XElement> nesneler, daha sonra nesne için yeni içerik haline gelir `Root` <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="18c91-107">The query projects new <xref:System.Xml.Linq.XElement> objects, which then become the new content for the `Root` <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```vb  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)()  
dict.Add("Child1", "Value1")  
dict.Add("Child2", "Value2")  
dict.Add("Child3", "Value3")  
dict.Add("Child4", "Value4")  
Dim root As XElement = _  
    <Root>  
        <%= From keyValue In dict _  
            Select New XElement(keyValue.Key, keyValue.Value) %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="18c91-108">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="18c91-108">This code produces the following output:</span></span>  
  
```xml  
          <Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="18c91-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="18c91-109">Example</span></span>  
 <span data-ttu-id="18c91-110">Aşağıdaki kod XML 'den bir sözlük oluşturur.</span><span class="sxs-lookup"><span data-stu-id="18c91-110">The following code creates a dictionary from XML.</span></span>  
  
```vb  
Dim root As XElement = _  
        <Root>  
            <Child1>Value1</Child1>  
            <Child2>Value2</Child2>  
            <Child3>Value3</Child3>  
            <Child4>Value4</Child4>  
        </Root>  
  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)  
For Each el As XElement In root.Elements  
    dict.Add(el.Name.LocalName, el.Value)  
Next  
For Each str As String In dict.Keys  
    Console.WriteLine("{0}:{1}", str, dict(str))  
Next  
```  
  
 <span data-ttu-id="18c91-111">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="18c91-111">This code produces the following output:</span></span>  
  
```console  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a><span data-ttu-id="18c91-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18c91-112">See also</span></span>

- [<span data-ttu-id="18c91-113">Tahminler ve dönüşümler (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18c91-113">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](projections-and-transformations-linq-to-xml.md)
