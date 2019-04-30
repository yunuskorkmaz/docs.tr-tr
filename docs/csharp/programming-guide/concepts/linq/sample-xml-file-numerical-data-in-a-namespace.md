---
title: 'Örnek XML Dosyası: Bir Namespace3 alanında sayısal veriler'
ms.date: 07/20/2015
ms.assetid: 51750cab-3c66-4511-90fb-b9d211308d31
ms.openlocfilehash: d00ad41c6703945b80dd49ff5f375a3896b43bed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61712545"
---
# <a name="sample-xml-file-numerical-data-in-a-namespace"></a><span data-ttu-id="640c8-102">Örnek XML Dosyası: Bir Ad Alanında Sayısal Veriler</span><span class="sxs-lookup"><span data-stu-id="640c8-102">Sample XML File: Numerical Data in a Namespace</span></span>
<span data-ttu-id="640c8-103">Aşağıdaki XML dosyasını çeşitli örneklerde kullanılan [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] belgeleri.</span><span class="sxs-lookup"><span data-stu-id="640c8-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="640c8-104">Bu dosya, birleşimi, ortalama ve Gruplama için sayısal veriler içerir.</span><span class="sxs-lookup"><span data-stu-id="640c8-104">This file contains numerical data for summing, averaging, and grouping.</span></span> <span data-ttu-id="640c8-105">Bir ad alanında XML'dir.</span><span class="sxs-lookup"><span data-stu-id="640c8-105">The XML is in a namespace.</span></span>  
  
## <a name="data"></a><span data-ttu-id="640c8-106">Veri</span><span class="sxs-lookup"><span data-stu-id="640c8-106">Data</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="640c8-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="640c8-107">See also</span></span>

- [<span data-ttu-id="640c8-108">Örnek XML Belgeleri (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="640c8-108">Sample XML Documents (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)
