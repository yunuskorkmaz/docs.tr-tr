---
title: 'Nasıl yapılır: Kök öğeyi bul (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 1fea4cc630dd708a86a0f0595ac727f8b8fa40af
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593381"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a><span data-ttu-id="035eb-102">Nasıl yapılır: Kök öğeyi bul (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="035eb-102">How to: Find the Root Element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="035eb-103">Bu konu, XPath ve [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]ile kök öğesinin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="035eb-103">This topic shows how to get the root element with XPath and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="035eb-104">XPath ifadesi:</span><span class="sxs-lookup"><span data-stu-id="035eb-104">The XPath expression is:</span></span>  
  
 `/PurchaseOrders`  
  
## <a name="example"></a><span data-ttu-id="035eb-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="035eb-105">Example</span></span>  
 <span data-ttu-id="035eb-106">Bu örnek, kök öğesini bulur.</span><span class="sxs-lookup"><span data-stu-id="035eb-106">This example finds the root element.</span></span>  
  
 <span data-ttu-id="035eb-107">Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Birden çok satın alma siparişi (](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md)LINQ to XML).</span><span class="sxs-lookup"><span data-stu-id="035eb-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="035eb-108">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="035eb-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
PurchaseOrders  
```  
