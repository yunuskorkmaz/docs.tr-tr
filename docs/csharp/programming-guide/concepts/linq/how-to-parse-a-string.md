---
title: Dize ayrıştırma (C#)
ms.date: 07/20/2015
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: 79821eb9e5cd7187ac3c2a93f85eaae45c5c48ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345807"
---
# <a name="how-to-parse-a-string-c"></a><span data-ttu-id="a9511-102">Dize ayrıştırma (C#)</span><span class="sxs-lookup"><span data-stu-id="a9511-102">How to parse a string (C#)</span></span>

<span data-ttu-id="a9511-103">Bu konu, C#'da bir XML ağacı oluşturmak için bir dizeyi nasıl ayrıştırırın gösterir.</span><span class="sxs-lookup"><span data-stu-id="a9511-103">This topic shows how to parse a string to create an XML tree in C#.</span></span>

## <a name="example"></a><span data-ttu-id="a9511-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a9511-104">Example</span></span>

<span data-ttu-id="a9511-105">Aşağıdaki C# kodu, XML dizesini nasıl ayrışdırırsa gösterir:</span><span class="sxs-lookup"><span data-stu-id="a9511-105">The following C# code shows how to parse an XML string:</span></span>

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

<span data-ttu-id="a9511-106">Kök `Contacts` düğümünün iki `Contact` düğümü vardır.</span><span class="sxs-lookup"><span data-stu-id="a9511-106">The root `Contacts` node has two `Contact` nodes.</span></span> <span data-ttu-id="a9511-107">Ayrıştırılmış XML'inizdeki bazı belirli verilere erişmek için, bu durumda kök `Contacts` düğümün alt öğelerini döndüren [XElement.Elements()](xref:System.Xml.Linq.XContainer.Elements) yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a9511-107">To access some specific data in your parsed XML, use the [XElement.Elements()](xref:System.Xml.Linq.XContainer.Elements) method, which in this case returns the child elements of the root `Contacts` node.</span></span> <span data-ttu-id="a9511-108">Aşağıdaki örnekte konsola `Contact` ilk düğüm yazdırır:</span><span class="sxs-lookup"><span data-stu-id="a9511-108">The following example prints the first `Contact` node to the console:</span></span>

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```

## <a name="see-also"></a><span data-ttu-id="a9511-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9511-109">See also</span></span>

- [<span data-ttu-id="a9511-110">Belirli bir özniteliğe (C#) sahip bir öğe yi bulma</span><span class="sxs-lookup"><span data-stu-id="a9511-110">How to find an element with a specific attribute (C#)</span></span>](how-to-find-an-element-with-a-specific-attribute.md)
