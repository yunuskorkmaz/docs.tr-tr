---
title: 'Nasıl yapılır: LINQ to XML (Visual Basic) kullanarak sözlükleri ile çalışma'
ms.date: 07/20/2015
ms.assetid: 6cb3f969-1986-414a-b850-87418712edea
ms.openlocfilehash: 9f08430aeb92b9c6e0b7b08481027fb3b5b77cad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572350"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-visual-basic"></a><span data-ttu-id="62b7b-102">Nasıl yapılır: LINQ to XML (Visual Basic) kullanarak sözlükleri ile çalışma</span><span class="sxs-lookup"><span data-stu-id="62b7b-102">How to: Work with Dictionaries Using LINQ to XML (Visual Basic)</span></span>
<span data-ttu-id="62b7b-103">Genellikle, diğer veri yapılarını XML ve XML veri yapılarını çeşitleri dönüştürmek uygundur.</span><span class="sxs-lookup"><span data-stu-id="62b7b-103">It is often convenient to convert varieties of data structures to XML, and XML back to other data structures.</span></span> <span data-ttu-id="62b7b-104">Bu konuda dönüştürerek genel bu yaklaşım, belirli bir uygulama gösterilmektedir. bir <xref:System.Collections.Generic.Dictionary%602> XML ve geri.</span><span class="sxs-lookup"><span data-stu-id="62b7b-104">This topic shows a specific implementation of this general approach by converting a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62b7b-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="62b7b-105">Example</span></span>  
 <span data-ttu-id="62b7b-106">Bu örnek, XML değişmez değerleri ve bir sorgu katıştırılmış bir ifadede kullanır.</span><span class="sxs-lookup"><span data-stu-id="62b7b-106">This example uses XML literals and a query in an embedded expression.</span></span> <span data-ttu-id="62b7b-107">Yeni sorgu projeleri <xref:System.Xml.Linq.XElement> nesneleri, hangi, daha sonra yeni içeriği haline `Root` <xref:System.Xml.Linq.XElement> nesne.</span><span class="sxs-lookup"><span data-stu-id="62b7b-107">The query projects new <xref:System.Xml.Linq.XElement> objects, which then become the new content for the `Root` <xref:System.Xml.Linq.XElement> object.</span></span>  
  
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
  
 <span data-ttu-id="62b7b-108">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="62b7b-108">This code produces the following output:</span></span>  
  
```xml  
          <Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="62b7b-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="62b7b-109">Example</span></span>  
 <span data-ttu-id="62b7b-110">Aşağıdaki kod, XML'den bir sözlük oluşturur.</span><span class="sxs-lookup"><span data-stu-id="62b7b-110">The following code creates a dictionary from XML.</span></span>  
  
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
  
 <span data-ttu-id="62b7b-111">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="62b7b-111">This code produces the following output:</span></span>  
  
```  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a><span data-ttu-id="62b7b-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62b7b-112">See also</span></span>
- [<span data-ttu-id="62b7b-113">Projeksiyonlar ve Dönüşümler (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62b7b-113">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
