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
# <a name="how-to-parse-a-string-linq-to-xml"></a><span data-ttu-id="ec13c-103">Bir dizeyi ayrıştırma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="ec13c-103">How to parse a string (LINQ to XML)</span></span>

<span data-ttu-id="ec13c-104">Bu makalede, C# ' de ve Visual Basic bir XML ağacı oluşturmak için bir dizeyi ayrıştırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ec13c-104">This article shows how to parse a string to create an XML tree in C# and in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="ec13c-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="ec13c-105">Example</span></span>

<span data-ttu-id="ec13c-106">Aşağıdaki C# kodu bir XML dizesinin nasıl ayrıştıralınacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="ec13c-106">The following C# code shows how to parse an XML string:</span></span>

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

<span data-ttu-id="ec13c-107">Visual Basic bir dizeyi benzer bir şekilde ayrıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec13c-107">You can parse a string in Visual Basic in a similar manner.</span></span> <span data-ttu-id="ec13c-108">Ancak, XML değişmez değerleri bir dizeden XML ayrıştırılırken aynı performans yaptırımlarından etkilemediğinden, aşağıdaki kodda gösterildiği gibi XML değişmez değerleri kullanmak daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="ec13c-108">However, it's more efficient to use XML literals, as shown in following code, because XML literals don't suffer from the same performance penalties as parsing XML from a string.</span></span>

<span data-ttu-id="ec13c-109">XML sabit değerlerini kullanarak yalnızca XML dosyanızı Visual Basic programınıza kopyalayabilir ve yapıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ec13c-109">By using XML literals, you can just copy and paste your XML into your Visual Basic program.</span></span>

> [!NOTE]
> <span data-ttu-id="ec13c-110">Bir metin dosyasından metin ayrıştırma veya bir XML belgesi yükleme, işlevsel oluşturma işleminden daha az verimlidir.</span><span class="sxs-lookup"><span data-stu-id="ec13c-110">Parsing text or loading an XML document from a text file is less efficient than functional construction.</span></span> <span data-ttu-id="ec13c-111">Koddan bir XML ağacı başladıysanız, işlevsel oluşturma işlevinin metin ayrıştırılmaya kıyasla daha az işlemci süresi sürer.</span><span class="sxs-lookup"><span data-stu-id="ec13c-111">If you're initializing an XML tree from code, it takes less processor time to use functional construction than to parse text.</span></span>

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

<span data-ttu-id="ec13c-112">Kök `Contacts` düğümün iki düğümü vardır `Contact` .</span><span class="sxs-lookup"><span data-stu-id="ec13c-112">The root `Contacts` node has two `Contact` nodes.</span></span> <span data-ttu-id="ec13c-113">Ayrıştırılmış XML 'inizdeki bazı belirli verilere erişmek için, bu örnekte kök düğümün alt öğelerini döndüren [XElement. Elements ()](xref:System.Xml.Linq.XContainer.Elements) yöntemini kullanın `Contacts` .</span><span class="sxs-lookup"><span data-stu-id="ec13c-113">To access some specific data in your parsed XML, use the [XElement.Elements()](xref:System.Xml.Linq.XContainer.Elements) method, which in this case returns the child elements of the root `Contacts` node.</span></span> <span data-ttu-id="ec13c-114">Aşağıdaki örnek, `Contact` konsola ilk düğümü yazdırır:</span><span class="sxs-lookup"><span data-stu-id="ec13c-114">The following example prints the first `Contact` node to the console:</span></span>

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```

```vb
Dim contactNodes As List(Of XElement) = contacts.Elements("Contact").ToList()
Console.WriteLine(contactNodes(0))
```

## <a name="see-also"></a><span data-ttu-id="ec13c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec13c-115">See also</span></span>

- [<span data-ttu-id="ec13c-116">Belirli bir özniteliğe sahip öğeyi bulma</span><span class="sxs-lookup"><span data-stu-id="ec13c-116">How to find an element with a specific attribute</span></span>](find-element-specific-attribute.md)
