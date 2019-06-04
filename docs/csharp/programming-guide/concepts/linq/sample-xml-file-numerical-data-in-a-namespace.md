---
title: 'Örnek XML Dosyası: Bir Namespace3 alanında sayısal veriler'
ms.date: 07/20/2015
ms.assetid: 51750cab-3c66-4511-90fb-b9d211308d31
ms.openlocfilehash: 02788b73a7af9922b5a50237f2d2e401cba8abe2
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66483691"
---
# <a name="sample-xml-file-numerical-data-in-a-namespace"></a><span data-ttu-id="66341-102">Örnek XML Dosyası: Bir Ad Alanında Sayısal Veriler</span><span class="sxs-lookup"><span data-stu-id="66341-102">Sample XML File: Numerical Data in a Namespace</span></span>
<span data-ttu-id="66341-103">Aşağıdaki XML dosyasını çeşitli örneklerde kullanılan [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] belgeleri.</span><span class="sxs-lookup"><span data-stu-id="66341-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="66341-104">Bu dosya, birleşimi, ortalama ve Gruplama için sayısal veriler içerir.</span><span class="sxs-lookup"><span data-stu-id="66341-104">This file contains numerical data for summing, averaging, and grouping.</span></span> <span data-ttu-id="66341-105">Bir ad alanında XML'dir.</span><span class="sxs-lookup"><span data-stu-id="66341-105">The XML is in a namespace.</span></span>  
  
## <a name="data"></a><span data-ttu-id="66341-106">Veri</span><span class="sxs-lookup"><span data-stu-id="66341-106">Data</span></span>  
  
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
