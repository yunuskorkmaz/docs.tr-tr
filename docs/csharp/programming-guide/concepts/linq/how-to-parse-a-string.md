---
title: 'Nasıl yapılır: bir dizeyi ayrıştırma (C#)'
ms.date: 07/20/2015
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: da1c9d2573ac09a9db7f87c619f67bf0b2fb23ba
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834184"
---
# <a name="how-to-parse-a-string-c"></a><span data-ttu-id="914dd-102">Nasıl yapılır: bir dizeyi ayrıştırma (C#)</span><span class="sxs-lookup"><span data-stu-id="914dd-102">How to: Parse a String (C#)</span></span>

<span data-ttu-id="914dd-103">Bu konuda, içinde C#bir XML ağacı oluşturmak için bir dizeyi ayrıştırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="914dd-103">This topic shows how to parse a string to create an XML tree in C#.</span></span>

## <a name="example"></a><span data-ttu-id="914dd-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="914dd-104">Example</span></span>

<span data-ttu-id="914dd-105">Aşağıdaki C# kod, bir XML dizesinin nasıl ayrıştıralınacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="914dd-105">The following C# code shows how to parse an XML string:</span></span>

```csharp
XElement contacts = XElement.Parse(
    @"<Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone Type=""home"">206-555-0144</Phone>
            <Phone Type=""work"">425-555-0145</Phone>
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

<span data-ttu-id="914dd-106">Kök `Contacts` düğümünün iki `Contact` düğümü vardır.</span><span class="sxs-lookup"><span data-stu-id="914dd-106">The root `Contacts` node has two `Contact` nodes.</span></span> <span data-ttu-id="914dd-107">Ayrıştırılmış XML 'inizdeki bazı belirli verilere erişmek için, bu örnekte kök `Contacts` düğümünün alt öğelerini döndüren [XElement. Elements ()](xref:System.Xml.Linq.XContainer.Elements) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="914dd-107">To access some specific data in your parsed XML, use the [XElement.Elements()](xref:System.Xml.Linq.XContainer.Elements) method, which in this case returns the child elements of the root `Contacts` node.</span></span> <span data-ttu-id="914dd-108">Aşağıdaki örnek, ilk `Contact` düğümünü konsola yazdırır:</span><span class="sxs-lookup"><span data-stu-id="914dd-108">The following example prints the first `Contact` node to the console:</span></span>

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```
