---
title: Genel Bakış-LINQ to XML
description: LINQ to XML, .NET özelliklerine dayanan ve güncelleştirilmiş bir DOM API 'sine benzer bir bellek içi XML programlama arabirimi sağlar.
ms.date: 10/30/2018
dev_langs:
- csharp
- vb
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: f805d757c9059a07988c6cb16e41ffed017fe853
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553357"
---
# <a name="linq-to-xml-overview"></a><span data-ttu-id="7f4a5-103">LINQ to XML genel bakış</span><span class="sxs-lookup"><span data-stu-id="7f4a5-103">LINQ to XML overview</span></span>

<span data-ttu-id="7f4a5-104">LINQ to XML, .NET dil ile tümleşik sorgu (LINQ) çerçevesini kullanan bellek içi bir XML programlama arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-104">LINQ to XML provides an in-memory XML programming interface that leverages the .NET Language-Integrated Query (LINQ) Framework.</span></span> <span data-ttu-id="7f4a5-105">LINQ to XML, .NET yeteneklerini kullanır ve güncelleştirilmiş, yeniden tasarlanan Belge Nesne Modeli (DOM) XML programlama arabirimine benzer.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-105">LINQ to XML uses .NET capabilities and is comparable to an updated, redesigned Document Object Model (DOM) XML programming interface.</span></span>

<span data-ttu-id="7f4a5-106">XML, çok sayıda bağlamdaki verileri biçimlendirmeye yönelik bir yöntem olarak çok daha benimsemiştir.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-106">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="7f4a5-107">Örneğin, Web 'de, yapılandırma dosyalarında, Microsoft Office Word dosyalarında ve veritabanlarında XML bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-107">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>

<span data-ttu-id="7f4a5-108">LINQ to XML, XML ile programlamaya yönelik güncel ve yeniden tasarlanan bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-108">LINQ to XML is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="7f4a5-109">Belge Nesne Modeli (DOM) için bellek içi belge değiştirme yeteneklerini sağlar ve LINQ sorgu ifadelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-109">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports LINQ query expressions.</span></span> <span data-ttu-id="7f4a5-110">Bu sorgu ifadeleri XPath 'ten farklı bir şekilde farklılık içerse de, benzer işlevler sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-110">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>

## <a name="linq-to-xml-developers"></a><span data-ttu-id="7f4a5-111">LINQ to XML geliştiriciler</span><span class="sxs-lookup"><span data-stu-id="7f4a5-111">LINQ to XML developers</span></span>

<span data-ttu-id="7f4a5-112">LINQ to XML çeşitli geliştiricilere hedefler.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-112">LINQ to XML targets a variety of developers.</span></span> <span data-ttu-id="7f4a5-113">Yalnızca bir şey yapmak isteyen ortalama bir geliştirici için, SQL 'e benzer bir sorgu deneyimi sağlayarak XML 'i daha kolay hale getirir LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-113">For an average developer who just wants to get something done, LINQ to XML makes XML easier by providing a query experience that's similar to SQL.</span></span> <span data-ttu-id="7f4a5-114">Yalnızca bir çok çalışma sayesinde programcılar, tercih ettiğiniz programlama dilinde kısa ve güçlü sorgular yazmayı öğreniyor.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-114">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>

<span data-ttu-id="7f4a5-115">Profesyonel geliştiriciler, üretkenliğini önemli ölçüde artırmak için LINQ to XML kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-115">Professional developers can use LINQ to XML to greatly increase their productivity.</span></span> <span data-ttu-id="7f4a5-116">LINQ to XML sayesinde, daha açıklayıcı, daha kompakt ve daha güçlü bir kod yazabilir.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-116">With LINQ to XML, they can write less code that's more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="7f4a5-117">Aynı anda birden çok veri etki alanından sorgu ifadeleri kullanabilirler.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-117">They can use query expressions from multiple data domains at the same time.</span></span>

## <a name="linq-to-xml-is-an-xml-programming-interface"></a><span data-ttu-id="7f4a5-118">LINQ to XML bir XML programlama arabirimidir</span><span class="sxs-lookup"><span data-stu-id="7f4a5-118">LINQ to XML is an XML programming interface</span></span>

<span data-ttu-id="7f4a5-119">LINQ to XML, .NET programlama dillerinin içinden XML ile çalışmanıza olanak sağlayan, LINQ özellikli, bellek içi bir XML programlama arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-119">LINQ to XML is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the .NET programming languages.</span></span>

<span data-ttu-id="7f4a5-120">LINQ to XML, XML belgesini belleğe getiren Belge Nesne Modeli (DOM) gibidir.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-120">LINQ to XML is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="7f4a5-121">Belgeyi sorgulayabilir ve değiştirebilir ve değişiklik yaptıktan sonra dosyayı bir dosyaya kaydedebilir veya seri hale getirebilirsiniz ve Internet üzerinden gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-121">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="7f4a5-122">Ancak, LINQ to XML DOM 'dan farklıdır:</span><span class="sxs-lookup"><span data-stu-id="7f4a5-122">However, LINQ to XML differs from DOM:</span></span>

- <span data-ttu-id="7f4a5-123">Daha açık ağırlığı olan yeni bir nesne modeli sağlar ve bunlarla daha kolay çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-123">It provides a new object model that's lighter weight and easier to work with.</span></span>
- <span data-ttu-id="7f4a5-124">C# ve Visual Basic dil özelliklerinden yararlanır.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-124">It takes advantage of language features in C# and Visual Basic.</span></span>

<span data-ttu-id="7f4a5-125">LINQ to XML en önemli avantajı, dil ile tümleşik sorgu (LINQ) ile tümleştirmedir.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-125">The most important advantage of LINQ to XML is its integration with Language-Integrated Query (LINQ).</span></span> <span data-ttu-id="7f4a5-126">Bu tümleştirme, öğelerin ve özniteliklerin koleksiyonlarını almak için bellek içi XML belgesi üzerinde sorgular yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-126">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="7f4a5-127">LINQ to XML sorgu özelliği, XPath ve XQuery için (sözdiziminde olmasa da) işlev olarak karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-127">The query capability of LINQ to XML is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="7f4a5-128">C# ve Visual Basic LINQ 'ın tümleştirilmesi, daha güçlü yazma, derleme zamanı denetimi ve geliştirilmiş hata ayıklayıcı desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-128">The integration of LINQ in C# and Visual Basic provides stronger typing, compile-time checking, and improved debugger support.</span></span>

<span data-ttu-id="7f4a5-129">LINQ to XML başka bir avantajı, sorgu sonuçlarının parametre olarak kullanılması <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> nesne OLUŞTURUCULARı, xml ağaçları oluşturmaya yönelik güçlü bir yaklaşım sağlar.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-129">Another advantage of LINQ to XML is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="7f4a5-130">*İşlevsel oluşturma*olarak adlandırılan bu yaklaşım, geliştiricilerin XML ağaçlarını bir şekilden diğerine kolayca dönüştürmelerine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-130">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>

<span data-ttu-id="7f4a5-131">Örneğin, [örnek xml dosyası: tipik satın alma siparişi](sample-xml-file-typical-purchase-order.md)bölümünde açıklandığı gibi tıpık bir XML satın alma siparişiniz olabilir.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-131">For example, you might have a typical XML purchase order as described in [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span> <span data-ttu-id="7f4a5-132">LINQ to XML kullanarak, satın alma sırasındaki her öğe öğesi için bölüm numarası öznitelik değerini almak üzere aşağıdaki sorguyu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7f4a5-132">By using LINQ to XML, you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

```vb
' Load the XML file from our project directory containing the purchase orders
Dim filename = "PurchaseOrder.xml"
Dim currentDirectory = Directory.GetCurrentDirectory()
Dim purchaseOrderFilepath = Path.Combine(currentDirectory, filename)

Dim purchaseOrder As XElement = XElement.Load(purchaseOrderFilepath)

Dim partNos = _
    From item In purchaseOrder...<Item> _
    Select item.@PartNumber
```

<span data-ttu-id="7f4a5-133">C# dilinde bu, yöntem sözdizimi biçiminde yeniden yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="7f4a5-133">In C# this can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

<span data-ttu-id="7f4a5-134">Başka bir örnek olarak, $100 'den büyük bir değere sahip olan öğelerin bölüm numarasına göre sıralanmış bir liste olmasını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-134">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="7f4a5-135">Bu bilgileri almak için aşağıdaki sorguyu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7f4a5-135">To obtain this information, you could run the following query:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<XElement> pricesByPartNos =  from item in purchaseOrder.Descendants("Item")
                                 where (int) item.Element("Quantity") * (decimal) item.Element("USPrice") > 100
                                 orderby (string)item.Element("PartNumber")
                                 select item;
```

```vb
' Load the XML file from our project directory containing the purchase orders
Dim filename = "PurchaseOrder.xml"
Dim currentDirectory = Directory.GetCurrentDirectory()
Dim purchaseOrderFilepath = Path.Combine(currentDirectory, filename)

Dim purchaseOrder As XElement = XElement.Load(purchaseOrderFilepath)

Dim partNos = _
From item In purchaseOrder...<Item> _
Where (item.<Quantity>.Value * _
       item.<USPrice>.Value) > 100 _
Order By item.<PartNumber>.Value _
Select item
```

<span data-ttu-id="7f4a5-136">Yine C# dilinde bu, yöntem sözdizimi biçiminde yeniden yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="7f4a5-136">Again, in C# this can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

<span data-ttu-id="7f4a5-137">Bu LINQ özelliklerine ek olarak, LINQ to XML geliştirilmiş bir XML programlama arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-137">In addition to these LINQ capabilities, LINQ to XML provides an improved XML programming interface.</span></span> <span data-ttu-id="7f4a5-138">LINQ to XML kullanarak şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7f4a5-138">Using LINQ to XML, you can:</span></span>

- <span data-ttu-id="7f4a5-139">[Dosyalardan](load-xml-file.md) veya [akışlardan](stream-xml-fragments-xmlreader.md)XML yükleyin.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-139">Load XML from [files](load-xml-file.md) or [streams](stream-xml-fragments-xmlreader.md).</span></span>
- <span data-ttu-id="7f4a5-140">XML 'yi dosyalara veya akışlara seri hale getirme.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-140">Serialize XML to files or streams.</span></span>
- <span data-ttu-id="7f4a5-141">İşlevsel oluşturma kullanarak sıfırdan XML oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-141">Create XML from scratch by using functional construction.</span></span>
- <span data-ttu-id="7f4a5-142">XPath benzeri eksenleri kullanarak XML 'yi sorgula.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-142">Query XML using XPath-like axes.</span></span>
- <span data-ttu-id="7f4a5-143">,, Ve gibi yöntemleri kullanarak bellek içi xml ağacını işleme <xref:System.Xml.Linq.XContainer.Add%2A> <xref:System.Xml.Linq.XNode.Remove%2A> <xref:System.Xml.Linq.XNode.ReplaceWith%2A> <xref:System.Xml.Linq.XElement.SetValue%2A> .</span><span class="sxs-lookup"><span data-stu-id="7f4a5-143">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>
- <span data-ttu-id="7f4a5-144">XSD kullanarak XML ağaçlarını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-144">Validate XML trees using XSD.</span></span>
- <span data-ttu-id="7f4a5-145">XML ağaçlarını bir şekilden diğerine dönüştürmek için bu özelliklerin birleşimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-145">Use a combination of these features to transform XML trees from one shape into another.</span></span>

## <a name="create-xml-trees"></a><span data-ttu-id="7f4a5-146">XML ağaçları oluşturma</span><span class="sxs-lookup"><span data-stu-id="7f4a5-146">Create XML trees</span></span>

<span data-ttu-id="7f4a5-147">LINQ to XML ile programlama kullanmanın en önemli avantajlarından biri, XML ağaçları oluşturmanın kolay bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-147">One of the most significant advantages of programming with LINQ to XML is that it's easy to create XML trees.</span></span> <span data-ttu-id="7f4a5-148">Örneğin, küçük bir XML ağacı oluşturmak için aşağıdaki gibi bir kod yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="7f4a5-148">For example, to create a small XML tree, you can write code as follows:</span></span>

```csharp
XElement contacts =
new XElement("Contacts",
    new XElement("Contact",
        new XElement("Name", "Patrick Hines"),
        new XElement("Phone", "206-555-0144",
            new XAttribute("Type", "Home")),
        new XElement("phone", "425-555-0145",
            new XAttribute("Type", "Work")),
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

> [!NOTE]
> <span data-ttu-id="7f4a5-149">Örneğin Visual Basic sürümü XML sabit değerlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-149">The Visual Basic version of the example uses XML literals.</span></span> <span data-ttu-id="7f4a5-150">Ayrıca <xref:System.Xml.Linq.XElement> , C# sürümünde olduğu gibi Visual Basic de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-150">You can also use <xref:System.Xml.Linq.XElement> in Visual Basic, as in the C# version.</span></span>

<span data-ttu-id="7f4a5-151">Daha fazla bilgi için bkz. [xml ağaçları](functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="7f4a5-151">For more information, see [XML trees](functional-construction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7f4a5-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f4a5-152">See also</span></span>

- [<span data-ttu-id="7f4a5-153">Başvuru</span><span class="sxs-lookup"><span data-stu-id="7f4a5-153">Reference</span></span>](reference.md)
- [<span data-ttu-id="7f4a5-154">LINQ to XML ile DOM Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="7f4a5-154">LINQ to XML vs. DOM</span></span>](linq-xml-vs-dom.md)
- [<span data-ttu-id="7f4a5-155">LINQ to XML ve diğer XML Teknolojileri</span><span class="sxs-lookup"><span data-stu-id="7f4a5-155">LINQ to XML vs. other XML technologies</span></span>](linq-xml-vs-xml-technologies.md)
- <xref:System.Xml.Linq>
