---
title: XElement sınıfına genel bakış
description: XElement sınıfı XML öğelerini temsil eder. Öğeleri oluşturmak ve değiştirmek, öznitelikleri ve alt öğeleri eklemek ve seri hale getirmek için kullanabilirsiniz.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: 325afd09661532fe44aecf89fe9784520274638e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553129"
---
# <a name="xelement-class-overview"></a><span data-ttu-id="9db4f-104">XElement sınıfına genel bakış</span><span class="sxs-lookup"><span data-stu-id="9db4f-104">XElement class overview</span></span>

<span data-ttu-id="9db4f-105"><xref:System.Xml.Linq.XElement>Sınıfı, LINQ to XML temel sınıflardan biridir.</span><span class="sxs-lookup"><span data-stu-id="9db4f-105">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in LINQ to XML.</span></span> <span data-ttu-id="9db4f-106">Bir XML öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9db4f-106">It represents an XML element.</span></span> <span data-ttu-id="9db4f-107">Aşağıdaki liste, için bu sınıfı neleri kullanacağınızı gösterir:</span><span class="sxs-lookup"><span data-stu-id="9db4f-107">The following list shows what you can use this class for:</span></span>

- <span data-ttu-id="9db4f-108">Öğeleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9db4f-108">Create elements.</span></span>
- <span data-ttu-id="9db4f-109">Öğenin içeriğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="9db4f-109">Change the content of the element.</span></span>
- <span data-ttu-id="9db4f-110">Alt öğeleri ekleyin, değiştirin veya silin.</span><span class="sxs-lookup"><span data-stu-id="9db4f-110">Add, change, or delete child elements.</span></span>
- <span data-ttu-id="9db4f-111">Öznitelikleri bir öğeye ekleyin.</span><span class="sxs-lookup"><span data-stu-id="9db4f-111">Add attributes to an element.</span></span>
- <span data-ttu-id="9db4f-112">Metin biçimindeki bir öğenin içeriğini seri hale getirme.</span><span class="sxs-lookup"><span data-stu-id="9db4f-112">Serialize the contents of an element in text form.</span></span>

<span data-ttu-id="9db4f-113">Ayrıca, ve gibi diğer sınıflarla da birlikte kullanabilirsiniz <xref:System.Xml?displayProperty=nameWithType> <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="9db4f-113">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

<span data-ttu-id="9db4f-114">Bu makalede, sınıfı tarafından sunulan işlevleri açıklanmaktadır <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="9db4f-114">This article describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>

## <a name="construct-xml-trees"></a><span data-ttu-id="9db4f-115">XML ağaçları oluşturun</span><span class="sxs-lookup"><span data-stu-id="9db4f-115">Construct XML trees</span></span>

<span data-ttu-id="9db4f-116">XML ağaçlarını aşağıdakiler dahil farklı yollarla oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9db4f-116">You can construct XML trees in different ways, including the following:</span></span>

- <span data-ttu-id="9db4f-117">Kodda bir XML ağacı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9db4f-117">You can construct an XML tree in code.</span></span> <span data-ttu-id="9db4f-118">Daha fazla bilgi için bkz. [xml ağaçları](functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="9db4f-118">For more information, see [XML trees](functional-construction.md).</span></span>
- <span data-ttu-id="9db4f-119">Bir <xref:System.IO.TextReader> metin dosyası veya bir Web adresi (URL) dahil olmak üzere çeşitli kaynaklardan XML ayrıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9db4f-119">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="9db4f-120">Daha fazla bilgi için bkz. [XML 'ı ayrıştırma](parse-string.md).</span><span class="sxs-lookup"><span data-stu-id="9db4f-120">For more information, see [Parse XML](parse-string.md).</span></span>
- <span data-ttu-id="9db4f-121"><xref:System.Xml.XmlReader>Ağacı doldurmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9db4f-121">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="9db4f-122">Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="9db4f-122">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>
- <span data-ttu-id="9db4f-123">İçine içerik yazabileceği bir modülünüzün varsa, bir <xref:System.Xml.XmlWriter> <xref:System.Xml.Linq.XContainer.CreateWriter%2A> yazıcı oluşturmak, yazıcıyı modüle geçirmek ve ardından <xref:System.Xml.XmlWriter> XML ağacını doldurmak için öğesine yazılan içeriği kullanmak için yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9db4f-123">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that's written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>

<span data-ttu-id="9db4f-124">Aşağıdaki örnek bir ağaç oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9db4f-124">The following example creates a tree.</span></span> <span data-ttu-id="9db4f-125">C# sürümü iç içe öğe oluşturmaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="9db4f-125">The C# version uses nested element creations.</span></span> <span data-ttu-id="9db4f-126">Aynı tekniği Visual Basic de kullanabilirsiniz, ancak bu örnekte XML değişmez değerleri kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9db4f-126">You can use the same technique in Visual Basic, but this example uses XML literals.</span></span>

```csharp
XElement contacts =
    new XElement("Contacts",
        new XElement("Contact",
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),
            new XElement("Address",
                new XElement("Street1", "123 Main St"),
                new XElement("City", "Mercer Island"),
                new XElement("State", "WA"),
                new XElement("Postal", "68042")
            )
        )
    );
```

```vb
Dim contacts As XElement = _
    <Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone>206-555-0144</Phone>
            <Address>
                <Street1>123 Main St</Street1>
                <City>Mercer Island</City>
                <State>WA</State>
                <Postal>68042</Postal>
            </Address>
        </Contact>
    </Contacts>
```

<span data-ttu-id="9db4f-127">Ayrıca, aşağıdaki örnekte gösterildiği gibi bir XML ağacını doldurmak için LINQ to XML bir sorgu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9db4f-127">You can also use a LINQ to XML query to populate an XML tree, as shown in the following example:</span></span>

```csharp
XElement srcTree = new XElement("Root",
    new XElement("Element", 1),
    new XElement("Element", 2),
    new XElement("Element", 3),
    new XElement("Element", 4),
    new XElement("Element", 5)
);
XElement xmlTree = new XElement("Root",
    new XElement("Child", 1),
    new XElement("Child", 2),
    from el in srcTree.Elements()
    where (int)el > 2
    select el
);
Console.WriteLine(xmlTree);
```

```vb
Dim srcTree As XElement = _
    <Root>
        <Element>1</Element>
        <Element>2</Element>
        <Element>3</Element>
        <Element>4</Element>
        <Element>5</Element>
    </Root>
Dim xmlTree As XElement = _
    <Root>
        <Child>1</Child>
        <Child>2</Child>
        <%= From el In srcTree.Elements() _
            Where el.Value > 2 _
            Select el %>
    </Root>
Console.WriteLine(xmlTree)
```

<span data-ttu-id="9db4f-128">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="9db4f-128">This example produces the following output:</span></span>

```xml
<Root>
  <Child>1</Child>
  <Child>2</Child>
  <Element>3</Element>
  <Element>4</Element>
  <Element>5</Element>
</Root>
```

## <a name="serialize-xml-trees"></a><span data-ttu-id="9db4f-129">XML ağaçlarını serileştirme</span><span class="sxs-lookup"><span data-stu-id="9db4f-129">Serialize XML trees</span></span>

<span data-ttu-id="9db4f-130">XML ağacını bir <xref:System.IO.File> , a veya olarak seri hale getirebilirsiniz <xref:System.IO.TextWriter> <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="9db4f-130">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="9db4f-131">Daha fazla bilgi için bkz. [XML ağaçlarını serileştirme](preserve-white-space-serializing.md).</span><span class="sxs-lookup"><span data-stu-id="9db4f-131">For more information, see [Serialize XML trees](preserve-white-space-serializing.md).</span></span>

## <a name="retrieve-xml-data-via-axis-methods"></a><span data-ttu-id="9db4f-132">XML verilerini eksen yöntemleri aracılığıyla alma</span><span class="sxs-lookup"><span data-stu-id="9db4f-132">Retrieve XML data via axis methods</span></span>

<span data-ttu-id="9db4f-133">Öznitelikleri, alt öğeleri, alt öğeleri ve üst öğeleri almak için eksen yöntemlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9db4f-133">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> <span data-ttu-id="9db4f-134">LINQ to XML sorguları eksen yöntemleri üzerinde çalışır ve bir XML ağacı üzerinde gezinmek ve işlemek için çeşitli esnek ve güçlü yollar sunar.</span><span class="sxs-lookup"><span data-stu-id="9db4f-134">LINQ to XML queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>

<span data-ttu-id="9db4f-135">Daha fazla bilgi için bkz. [LINQ to XML eksenlerine genel bakış](linq-xml-axes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9db4f-135">For more information, see [LINQ to XML axes overview](linq-xml-axes-overview.md).</span></span>

## <a name="query-xml-trees"></a><span data-ttu-id="9db4f-136">XML ağaçlarını sorgula</span><span class="sxs-lookup"><span data-stu-id="9db4f-136">Query XML trees</span></span>

<span data-ttu-id="9db4f-137">Bir XML ağacından veri çıkaran LINQ to XML sorguları yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9db4f-137">You can write LINQ to XML queries that extract data from an XML tree.</span></span>

<span data-ttu-id="9db4f-138">Daha fazla bilgi için bkz. [sorgu xml ağaçlarına genel bakış](query-xml-trees-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9db4f-138">For more information, see [Query XML trees overview](query-xml-trees-overview.md).</span></span>

## <a name="modify-xml-trees"></a><span data-ttu-id="9db4f-139">XML ağaçlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="9db4f-139">Modify XML trees</span></span>

<span data-ttu-id="9db4f-140">Bir öğeyi, içeriğini veya özniteliklerini değiştirme gibi farklı yollarla değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9db4f-140">You can modify an element in different ways, including changing its content or attributes.</span></span> <span data-ttu-id="9db4f-141">Ayrıca bir öğeyi üst öğesinden da kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9db4f-141">You can also remove an element from its parent.</span></span>

<span data-ttu-id="9db4f-142">Daha fazla bilgi için bkz. [XML ağaçlarını değiştirme](in-memory-xml-tree-modification-vs-functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="9db4f-142">For more information, see [Modify XML trees](in-memory-xml-tree-modification-vs-functional-construction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9db4f-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9db4f-143">See also</span></span>

- [<span data-ttu-id="9db4f-144">LINQ to XML programlamaya genel bakış</span><span class="sxs-lookup"><span data-stu-id="9db4f-144">LINQ to XML programming overview</span></span>](functional-vs-procedural-programming.md)
