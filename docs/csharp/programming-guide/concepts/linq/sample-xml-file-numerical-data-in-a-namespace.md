---
title: 'Örnek XML dosyası: bir Namespace3 içinde sayısal veriler'
description: Bu XML dosyası LINQ to XML belgelerindeki çeşitli örneklerde kullanılır. Toplam, ortalama ve gruplama verileri içerir. XML bir ad alanıdır.
ms.date: 07/20/2015
ms.assetid: 51750cab-3c66-4511-90fb-b9d211308d31
ms.openlocfilehash: fe467604840851c2af2533a620f9b7e32367fbb3
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302509"
---
# <a name="sample-xml-file-numerical-data-in-a-namespace"></a><span data-ttu-id="9f803-105">Örnek XML Dosyası: Bir Ad Alanında Sayısal Veriler</span><span class="sxs-lookup"><span data-stu-id="9f803-105">Sample XML File: Numerical Data in a Namespace</span></span>
<span data-ttu-id="9f803-106">Aşağıdaki XML dosyası belgelerindeki çeşitli örneklerde kullanılır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9f803-106">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="9f803-107">Bu dosya, toplam, ortalama ve gruplama için sayısal verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="9f803-107">This file contains numerical data for summing, averaging, and grouping.</span></span> <span data-ttu-id="9f803-108">XML bir ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="9f803-108">The XML is in a namespace.</span></span>  
  
## <a name="data"></a><span data-ttu-id="9f803-109">Veriler</span><span class="sxs-lookup"><span data-stu-id="9f803-109">Data</span></span>  
  
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
