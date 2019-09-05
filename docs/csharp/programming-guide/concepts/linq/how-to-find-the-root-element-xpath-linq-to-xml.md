---
title: 'Nasıl yapılır: Kök öğeyi bul (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: d53fbaf089e54d50422e39cd047ee960bc8e46c3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253607"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a><span data-ttu-id="d5343-102">Nasıl yapılır: Kök öğeyi bul (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d5343-102">How to: Find the Root Element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="d5343-103">Bu konu, XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]ile kök öğesinin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5343-103">This topic shows how to get the root element with XPath and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="d5343-104">XPath ifadesi:</span><span class="sxs-lookup"><span data-stu-id="d5343-104">The XPath expression is:</span></span>  
  
 `/PurchaseOrders`  
  
## <a name="example"></a><span data-ttu-id="d5343-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="d5343-105">Example</span></span>  
 <span data-ttu-id="d5343-106">Bu örnek, kök öğesini bulur.</span><span class="sxs-lookup"><span data-stu-id="d5343-106">This example finds the root element.</span></span>  
  
 <span data-ttu-id="d5343-107">Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Birden çok satın alma siparişi (](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)LINQ to XML).</span><span class="sxs-lookup"><span data-stu-id="d5343-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
XElement el1 = po.Root;  
  
// XPath expression  
XElement el2 = po.XPathSelectElement("/PurchaseOrders");  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1.Name);  
```  
  
 <span data-ttu-id="d5343-108">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="d5343-108">This example produces the following output:</span></span>  
  
```output  
Results are identical  
PurchaseOrders  
```  
