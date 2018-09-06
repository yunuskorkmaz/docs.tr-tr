---
title: 'Nasıl yapılır: bir dize (C#) ayrıştırılamıyor'
ms.date: 07/20/2015
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: b6b955d2cc9a3ea0c6e17e68639ad7fc677c3fc7
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43744806"
---
# <a name="how-to-parse-a-string-c"></a><span data-ttu-id="a5eb0-102">Nasıl yapılır: bir dize (C#) ayrıştırılamıyor</span><span class="sxs-lookup"><span data-stu-id="a5eb0-102">How to: Parse a String (C#)</span></span>
<span data-ttu-id="a5eb0-103">Bu konuda, C# dilinde bir XML ağacı oluşturmak için bir dizeyi ayrıştırmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a5eb0-103">This topic shows how to parse a string to create an XML tree in C#.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5eb0-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a5eb0-104">Example</span></span>  
 <span data-ttu-id="a5eb0-105">Aşağıdaki C# kodu, bir dizeyi ayrıştırmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a5eb0-105">The following C# code shows how to parse a string.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a5eb0-106">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a5eb0-106">See Also</span></span>

- [<span data-ttu-id="a5eb0-107">XML Ayrıştırma (C#)</span><span class="sxs-lookup"><span data-stu-id="a5eb0-107">Parsing XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
