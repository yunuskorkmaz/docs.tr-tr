---
title: 'Nasıl yapılır: bir dize (C#) ayrıştırılamıyor'
ms.date: 07/20/2015
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: fe1ef6d601b97252eb2d146f28003cad352b2d84
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33320150"
---
# <a name="how-to-parse-a-string-c"></a><span data-ttu-id="99d11-102">Nasıl yapılır: bir dize (C#) ayrıştırılamıyor</span><span class="sxs-lookup"><span data-stu-id="99d11-102">How to: Parse a String (C#)</span></span>
<span data-ttu-id="99d11-103">Bu konuda, bir XML ağacı C# ' ta oluşturmak için bir dize ayrıştırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="99d11-103">This topic shows how to parse a string to create an XML tree in C#.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99d11-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="99d11-104">Example</span></span>  
 <span data-ttu-id="99d11-105">Aşağıdaki C# kod bir dize ayrıştırmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="99d11-105">The following C# code shows how to parse a string.</span></span>  
  
```csharp  
XElement contacts = XElement.Parse(  
    @"<Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone Type=""home"">206-555-0144</Phone>  
            <Phone type=""work"">425-555-0145</Phone>  
            <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
            </Address>  
            <NetWorth>10</NetWorth>  
        </Contact>  
        <Contact>  
            <Name>Gretchen Rivas</Name>  
            <Phone Type=""mobile"">206-555-0163</Phone>  
            <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
            </Address>  
            <NetWorth>11</NetWorth>  
        </Contact>  
    </Contacts>");  
Console.WriteLine(contacts);  
```  
  
## <a name="see-also"></a><span data-ttu-id="99d11-106">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="99d11-106">See Also</span></span>  
 [<span data-ttu-id="99d11-107">XML Ayrıştırma (C#)</span><span class="sxs-lookup"><span data-stu-id="99d11-107">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
