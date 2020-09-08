---
title: Bir dizeyi ayrıştırma-LINQ to XML
description: C# ve Visual Basic bir XML ağacı oluşturmak için XElement. Parse ile bir dizeyi ayrıştırarak Visual Basic XML sabit değerlerini içeren bir XML ağacı oluşturabilirsiniz.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: f4bd22acbf3b11d801c791cc591d882810450fd4
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553076"
---
# <a name="how-to-parse-a-string-linq-to-xml"></a>Bir dizeyi ayrıştırma (LINQ to XML)

Bu makalede, C# ' de ve Visual Basic bir XML ağacı oluşturmak için bir dizeyi ayrıştırma gösterilmektedir.

## <a name="example"></a>Örnek

Aşağıdaki C# kodu bir XML dizesinin nasıl ayrıştıralınacağını gösterir:

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

Visual Basic bir dizeyi benzer bir şekilde ayrıştırabilirsiniz. Ancak, XML değişmez değerleri bir dizeden XML ayrıştırılırken aynı performans yaptırımlarından etkilemediğinden, aşağıdaki kodda gösterildiği gibi XML değişmez değerleri kullanmak daha etkilidir.

XML sabit değerlerini kullanarak yalnızca XML dosyanızı Visual Basic programınıza kopyalayabilir ve yapıştırabilirsiniz.

> [!NOTE]
> Bir metin dosyasından metin ayrıştırma veya bir XML belgesi yükleme, işlevsel oluşturma işleminden daha az verimlidir. Koddan bir XML ağacı başladıysanız, işlevsel oluşturma işlevinin metin ayrıştırılmaya kıyasla daha az işlemci süresi sürer.

```vb
Dim contacts as XElement = _
    <Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone Type="home">206-555-0144</Phone>
            <Phone Type="work">425-555-0145</Phone>
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
            <Phone Type="mobile">206-555-0163</Phone>
            <Address>
            <Street1>123 Main St</Street1>
            <City>Mercer Island</City>
            <State>WA</State>
            <Postal>68042</Postal>
            </Address>
            <NetWorth>11</NetWorth>
        </Contact>
    </Contacts>
```

Kök `Contacts` düğümün iki düğümü vardır `Contact` . Ayrıştırılmış XML 'inizdeki bazı belirli verilere erişmek için, bu örnekte kök düğümün alt öğelerini döndüren [XElement. Elements ()](xref:System.Xml.Linq.XContainer.Elements) yöntemini kullanın `Contacts` . Aşağıdaki örnek, `Contact` konsola ilk düğümü yazdırır:

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```

```vb
Dim contactNodes As List(Of XElement) = contacts.Elements("Contact").ToList()
Console.WriteLine(contactNodes(0))
```

## <a name="see-also"></a>Ayrıca bkz.

- [Belirli bir özniteliğe sahip öğeyi bulma](find-element-specific-attribute.md)
