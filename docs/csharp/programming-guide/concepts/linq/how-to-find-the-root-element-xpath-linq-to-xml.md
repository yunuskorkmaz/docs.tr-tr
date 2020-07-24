---
title: Kök öğeyi bulma (XPath-LINQ to XML) (C#)
description: Bu C# örneği, örnek bir XML belgesi için kök öğe alma için XPath 'i LINQ to XML karşılaştırır.
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 220899823210c5cd6e9834541ca87e4d8394b4ff
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105185"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a><span data-ttu-id="10cf5-103">Kök öğeyi bulma (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="10cf5-103">How to find the root element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="10cf5-104">Bu konu, XPath ve ile kök öğesinin nasıl alınacağını gösterir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="10cf5-104">This topic shows how to get the root element with XPath and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="10cf5-105">XPath ifadesi:</span><span class="sxs-lookup"><span data-stu-id="10cf5-105">The XPath expression is:</span></span>  
  
 `/PurchaseOrders`  
  
## <a name="example"></a><span data-ttu-id="10cf5-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="10cf5-106">Example</span></span>  
 <span data-ttu-id="10cf5-107">Bu örnek, kök öğesini bulur.</span><span class="sxs-lookup"><span data-stu-id="10cf5-107">This example finds the root element.</span></span>  
  
 <span data-ttu-id="10cf5-108">Bu örnek, şu XML belgesini kullanır: [örnek xml dosyası: birden fazla satın alma siparişi (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="10cf5-108">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="10cf5-109">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="10cf5-109">This example produces the following output:</span></span>  
  
```output  
Results are identical  
PurchaseOrders  
```  
