---
title: LINQ to XML genel bakış (C#)
description: LINQ to XML, bellek içi belge değiştirme özellikleri ve XPath gibi işlevlerle sorgu ifadeleri sağlamak için .NET LINQ Framework 'ten yararlanır.
ms.date: 10/30/2018
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: d2e4cf4e63d1a6ed7c1f0c163c12bb422b55ba11
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165349"
---
# <a name="linq-to-xml-overview-c"></a><span data-ttu-id="9fe79-103">LINQ to XML genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="9fe79-103">LINQ to XML Overview (C#)</span></span>

<span data-ttu-id="9fe79-104">LINQ to XML, .NET dil ile tümleşik sorgu (LINQ) çerçevesini kullanan bellek içi bir XML programlama arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fe79-104">LINQ to XML provides an in-memory XML programming interface that leverages the .NET Language-Integrated Query (LINQ) Framework.</span></span> <span data-ttu-id="9fe79-105">LINQ to XML, .NET yeteneklerini kullanır ve güncelleştirilmiş, yeniden tasarlanan Belge Nesne Modeli (DOM) XML programlama arabirimine benzer.</span><span class="sxs-lookup"><span data-stu-id="9fe79-105">LINQ to XML uses .NET capabilities and is comparable to an updated, redesigned Document Object Model (DOM) XML programming interface.</span></span>

<span data-ttu-id="9fe79-106">XML, çok sayıda bağlamdaki verileri biçimlendirmeye yönelik bir yöntem olarak çok daha benimsemiştir.</span><span class="sxs-lookup"><span data-stu-id="9fe79-106">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="9fe79-107">Örneğin, Web 'de, yapılandırma dosyalarında, Microsoft Office Word dosyalarında ve veritabanlarında XML bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9fe79-107">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="9fe79-108">, XML ile programlamaya yönelik güncel ve yeniden tasarlanan bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="9fe79-108">is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="9fe79-109">Belge Nesne Modeli (DOM) için bellek içi belge değiştirme yeteneklerini sağlar ve LINQ sorgu ifadelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="9fe79-109">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports LINQ query expressions.</span></span> <span data-ttu-id="9fe79-110">Bu sorgu ifadeleri XPath 'ten farklı bir şekilde farklılık içerse de, benzer işlevler sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="9fe79-110">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>

## <a name="linq-to-xml-developers"></a><span data-ttu-id="9fe79-111">LINQ to XML geliştiriciler</span><span class="sxs-lookup"><span data-stu-id="9fe79-111">LINQ to XML Developers</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="9fe79-112">çeşitli geliştiricileri hedefler.</span><span class="sxs-lookup"><span data-stu-id="9fe79-112">targets a variety of developers.</span></span> <span data-ttu-id="9fe79-113">Yalnızca bir şey yapmak isteyen ortalama bir geliştirici için, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] SQL 'e benzer bir sorgu deneyimi sağlayarak xml 'i daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="9fe79-113">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="9fe79-114">Yalnızca bir çok çalışma sayesinde programcılar, tercih ettiğiniz programlama dilinde kısa ve güçlü sorgular yazmayı öğreniyor.</span><span class="sxs-lookup"><span data-stu-id="9fe79-114">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>

<span data-ttu-id="9fe79-115">Profesyonel geliştiriciler, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] üretkenliğini önemli ölçüde artırmak için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="9fe79-115">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="9fe79-116">İle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , daha açıklayıcı, daha kompakt ve daha güçlü bir kod yazabilir.</span><span class="sxs-lookup"><span data-stu-id="9fe79-116">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="9fe79-117">Aynı anda birden çok veri etki alanından sorgu ifadeleri kullanabilirler.</span><span class="sxs-lookup"><span data-stu-id="9fe79-117">They can use query expressions from multiple data domains at the same time.</span></span>

## <a name="what-is-linq-to-xml"></a><span data-ttu-id="9fe79-118">LINQ to XML nedir?</span><span class="sxs-lookup"><span data-stu-id="9fe79-118">What Is LINQ to XML?</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="9fe79-119">, .NET programlama dillerinin içinden XML ile çalışmanıza olanak sağlayan, LINQ özellikli, bellek içi bir XML programlama arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="9fe79-119">is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the .NET programming languages.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="9fe79-120">, XML belgesini belleğe getiren Belge Nesne Modeli (DOM) gibidir.</span><span class="sxs-lookup"><span data-stu-id="9fe79-120">is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="9fe79-121">Belgeyi sorgulayabilir ve değiştirebilir ve değişiklik yaptıktan sonra dosyayı bir dosyaya kaydedebilir veya seri hale getirebilirsiniz ve Internet üzerinden gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9fe79-121">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="9fe79-122">Ancak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Dom 'dan farklıdır: daha hafif ve daha kolay bir şekilde çalışmak ve C# ' deki dil özelliklerinden yararlanmak için daha kolay olan yeni bir nesne modeli sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fe79-122">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in C#.</span></span>

<span data-ttu-id="9fe79-123">Uygulamasının en önemli avantajı, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dil Ile tümleşik sorgu (LINQ) ile tümleştirmedir.</span><span class="sxs-lookup"><span data-stu-id="9fe79-123">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with Language-Integrated Query (LINQ).</span></span> <span data-ttu-id="9fe79-124">Bu tümleştirme, öğelerin ve özniteliklerin koleksiyonlarını almak için bellek içi XML belgesi üzerinde sorgular yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fe79-124">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="9fe79-125">Öğesinin sorgu özelliği, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XPath ve XQuery için işlevsellik (sözdiziminde değil) ile karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="9fe79-125">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="9fe79-126">C# ' deki LINQ tümleştirmesi daha güçlü yazma, derleme zamanı denetimi ve geliştirilmiş hata ayıklayıcı desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fe79-126">The integration of LINQ in C# provides stronger typing, compile-time checking, and improved debugger support.</span></span>

<span data-ttu-id="9fe79-127">' In başka bir avantajı, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu sonuçlarının parametre olarak kullanılması <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> nesne oluşturucuları, xml ağaçları oluşturmaya yönelik güçlü bir yaklaşım sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fe79-127">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="9fe79-128">*İşlevsel oluşturma*olarak adlandırılan bu yaklaşım, geliştiricilerin XML ağaçlarını bir şekilden diğerine kolayca dönüştürmelerine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fe79-128">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>

<span data-ttu-id="9fe79-129">Örneğin, örnek XML dosyasında açıklandığı gibi tipik bir XML satın alma siparişiniz olabilir [: tipik satın alma siparişi (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="9fe79-129">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span> <span data-ttu-id="9fe79-130">Kullanarak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , satın alma sırasındaki her öğe öğesi için bölüm numarası öznitelik değerini almak üzere aşağıdaki sorguyu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9fe79-130">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

<span data-ttu-id="9fe79-131">Bu, yöntem sözdizimi biçiminde yeniden yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="9fe79-131">This can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

<span data-ttu-id="9fe79-132">Başka bir örnek olarak, $100 'den büyük bir değere sahip olan öğelerin bölüm numarasına göre sıralanmış bir liste olmasını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9fe79-132">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="9fe79-133">Bu bilgileri almak için aşağıdaki sorguyu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9fe79-133">To obtain this information, you could run the following query:</span></span>

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

<span data-ttu-id="9fe79-134">Bu, yöntem sözdizimi biçiminde yeniden yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="9fe79-134">Again, this can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

<span data-ttu-id="9fe79-135">Bu LINQ özelliklerine ek olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] geliştirilmiş BIR XML programlama arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fe79-135">In addition to these LINQ capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="9fe79-136">Kullanarak şunları [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9fe79-136">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>

- <span data-ttu-id="9fe79-137">[Dosyalardan](how-to-load-xml-from-a-file.md) veya [akışlardan](how-to-stream-xml-fragments-from-an-xmlreader.md)XML yükleyin.</span><span class="sxs-lookup"><span data-stu-id="9fe79-137">Load XML from [files](how-to-load-xml-from-a-file.md) or [streams](how-to-stream-xml-fragments-from-an-xmlreader.md).</span></span>

- <span data-ttu-id="9fe79-138">XML 'yi dosyalara veya akışlara seri hale getirme.</span><span class="sxs-lookup"><span data-stu-id="9fe79-138">Serialize XML to files or streams.</span></span>

- <span data-ttu-id="9fe79-139">İşlevsel oluşturma kullanarak sıfırdan XML oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9fe79-139">Create XML from scratch by using functional construction.</span></span>

- <span data-ttu-id="9fe79-140">XPath benzeri eksenleri kullanarak XML 'yi sorgula.</span><span class="sxs-lookup"><span data-stu-id="9fe79-140">Query XML using XPath-like axes.</span></span>

- <span data-ttu-id="9fe79-141">,, Ve gibi yöntemleri kullanarak bellek içi xml ağacını işleme <xref:System.Xml.Linq.XContainer.Add%2A> <xref:System.Xml.Linq.XNode.Remove%2A> <xref:System.Xml.Linq.XNode.ReplaceWith%2A> <xref:System.Xml.Linq.XElement.SetValue%2A> .</span><span class="sxs-lookup"><span data-stu-id="9fe79-141">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>

- <span data-ttu-id="9fe79-142">XSD kullanarak XML ağaçlarını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="9fe79-142">Validate XML trees using XSD.</span></span>

- <span data-ttu-id="9fe79-143">XML ağaçlarını bir şekilden diğerine dönüştürmek için bu özelliklerin birleşimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="9fe79-143">Use a combination of these features to transform XML trees from one shape into another.</span></span>

## <a name="creating-xml-trees"></a><span data-ttu-id="9fe79-144">XML Ağaçları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9fe79-144">Creating XML Trees</span></span>

<span data-ttu-id="9fe79-145">Programlama kullanmanın en önemli avantajlarından biri, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] xml ağaçları oluşturmak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="9fe79-145">One of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="9fe79-146">Örneğin, küçük bir XML ağacı oluşturmak için aşağıdaki gibi bir kod yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9fe79-146">For example, to create a small XML tree, you can write code as follows:</span></span>

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

<span data-ttu-id="9fe79-147">Daha fazla bilgi için bkz. [xml ağaçları oluşturma (C#)](./creating-xml-trees-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="9fe79-147">For more information, see [Creating XML Trees (C#)](./creating-xml-trees-linq-to-xml-2.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9fe79-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9fe79-148">See also</span></span>

- [<span data-ttu-id="9fe79-149">Başvuru (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="9fe79-149">Reference (LINQ to XML)</span></span>](./reference-linq-to-xml.md)
- [<span data-ttu-id="9fe79-150">LINQ to XML vs. DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="9fe79-150">LINQ to XML vs. DOM (C#)</span></span>](./linq-to-xml-vs-dom.md)
- [<span data-ttu-id="9fe79-151">LINQ to XML ile Diğer XML Teknolojileri Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="9fe79-151">LINQ to XML vs. Other XML Technologies</span></span>](./linq-to-xml-vs-other-xml-technologies.md)
- <xref:System.Xml.Linq>
