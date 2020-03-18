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
# <a name="how-to-parse-a-string-c"></a>Dize ayrıştırma (C#)

Bu konu, C#'da bir XML ağacı oluşturmak için bir dizeyi nasıl ayrıştırırın gösterir.

## <a name="example"></a>Örnek

Aşağıdaki C# kodu, XML dizesini nasıl ayrışdırırsa gösterir:

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

Kök `Contacts` düğümünün iki `Contact` düğümü vardır. Ayrıştırılmış XML'inizdeki bazı belirli verilere erişmek için, bu durumda kök `Contacts` düğümün alt öğelerini döndüren [XElement.Elements()](xref:System.Xml.Linq.XContainer.Elements) yöntemini kullanın. Aşağıdaki örnekte konsola `Contact` ilk düğüm yazdırır:

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```

## <a name="see-also"></a>Ayrıca bkz.

- [Belirli bir özniteliğe (C#) sahip bir öğe yi bulma](how-to-find-an-element-with-a-specific-attribute.md)
