---
title: 'Örnek XML dosyası: Bir Namespace3 alanında sayısal veriler'
ms.date: 07/20/2015
ms.assetid: 51750cab-3c66-4511-90fb-b9d211308d31
ms.openlocfilehash: 5a752f477d17cee50b98bc88bd39cabda2bd3bf6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43393574"
---
# <a name="sample-xml-file-numerical-data-in-a-namespace"></a><span data-ttu-id="682c0-102">Örnek XML dosyası: Sayısal veriler bir Namespace</span><span class="sxs-lookup"><span data-stu-id="682c0-102">Sample XML File: Numerical Data in a Namespace</span></span>
<span data-ttu-id="682c0-103">Aşağıdaki XML dosyasını çeşitli örneklerde kullanılan [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] belgeleri.</span><span class="sxs-lookup"><span data-stu-id="682c0-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="682c0-104">Bu dosya, birleşimi, ortalama ve Gruplama için sayısal veriler içerir.</span><span class="sxs-lookup"><span data-stu-id="682c0-104">This file contains numerical data for summing, averaging, and grouping.</span></span> <span data-ttu-id="682c0-105">Bir ad alanında XML'dir.</span><span class="sxs-lookup"><span data-stu-id="682c0-105">The XML is in a namespace.</span></span>  
  
## <a name="data"></a><span data-ttu-id="682c0-106">Veri</span><span class="sxs-lookup"><span data-stu-id="682c0-106">Data</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="682c0-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="682c0-107">See Also</span></span>  
 [<span data-ttu-id="682c0-108">Örnek XML Belgeleri (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="682c0-108">Sample XML Documents (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)
