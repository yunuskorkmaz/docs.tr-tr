---
title: "Örnek XML dosyası: Bir Namespace3 sayısal verileri"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 51750cab-3c66-4511-90fb-b9d211308d31
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2437f22c1c76d1a24883cc2ed5b0e9c5f068e55b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="sample-xml-file-numerical-data-in-a-namespace"></a><span data-ttu-id="7544a-102">Örnek XML dosyası: Bir Namespace sayısal verileri</span><span class="sxs-lookup"><span data-stu-id="7544a-102">Sample XML File: Numerical Data in a Namespace</span></span>
<span data-ttu-id="7544a-103">Aşağıdaki XML dosyasını çeşitli örneklerde kullanılan [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] belgeleri.</span><span class="sxs-lookup"><span data-stu-id="7544a-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="7544a-104">Bu dosya, toplama, ortalama ve gruplandırma sayısal verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="7544a-104">This file contains numerical data for summing, averaging, and grouping.</span></span> <span data-ttu-id="7544a-105">XML ad alanında ' dir.</span><span class="sxs-lookup"><span data-stu-id="7544a-105">The XML is in a namespace.</span></span>  
  
## <a name="data"></a><span data-ttu-id="7544a-106">Veri</span><span class="sxs-lookup"><span data-stu-id="7544a-106">Data</span></span>  
  
```xml  
<Root xmlns='http://www.adatum.com'>  
  <TaxRate>7.25</TaxRate>  
  <Data>  
    <Category>A</Category>  
    <Quantity>3</Quantity>  
    <Price>24.50</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>1</Quantity>  
    <Price>89.99</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>5</Quantity>  
    <Price>4.95</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>3</Quantity>  
    <Price>66.00</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>10</Quantity>  
    <Price>.99</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>15</Quantity>  
    <Price>29.00</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>8</Quantity>  
    <Price>6.99</Price>  
  </Data>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7544a-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7544a-107">See Also</span></span>  
 [<span data-ttu-id="7544a-108">Örnek XML belgeleri (LINQ-XML)</span><span class="sxs-lookup"><span data-stu-id="7544a-108">Sample XML Documents (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)
