---
title: LINQ - XML Genel Bakış (C#)
ms.date: 10/30/2018
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: 334788a50832b8fe42ecc9a3272dd71f2f2af4ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168421"
---
# <a name="linq-to-xml-overview-c"></a><span data-ttu-id="d5cb3-102">LINQ - XML Genel Bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="d5cb3-102">LINQ to XML Overview (C#)</span></span>

<span data-ttu-id="d5cb3-103">LINQ to XML, .NET Dil-Tümleşik Sorgu (LINQ) Çerçevesi'nden yararlanan bir bellek içi XML programlama arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-103">LINQ to XML provides an in-memory XML programming interface that leverages the .NET Language-Integrated Query (LINQ) Framework.</span></span> <span data-ttu-id="d5cb3-104">LINQ to XML .NET özelliklerini kullanır ve güncelleştirilmiş, yeniden tasarlanmış Belge Nesnesi Modeli (DOM) XML programlama arabirimiile karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-104">LINQ to XML uses .NET capabilities and is comparable to an updated, redesigned Document Object Model (DOM) XML programming interface.</span></span>

<span data-ttu-id="d5cb3-105">XML yaygın olarak birçok bağlamda veri biçimlendirmek için bir yol olarak kabul edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-105">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="d5cb3-106">Örneğin, XML'i Web'de, yapılandırma dosyalarında, Microsoft Office Word dosyalarında ve veritabanlarında bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-106">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="d5cb3-107">XML ile programlamaya güncel, yeniden tasarlanmış bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-107">is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="d5cb3-108">Belge Nesnesi Modeli'nin (DOM) bellek içi belge değişiklik özelliklerini sağlar ve LINQ sorgu ifadelerini destekler.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-108">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports LINQ query expressions.</span></span> <span data-ttu-id="d5cb3-109">Bu sorgu ifadeleri sözdizimi olarak XPath'ten farklı olsa da, benzer işlevler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-109">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>

## <a name="linq-to-xml-developers"></a><span data-ttu-id="d5cb3-110">LINQ XML Geliştiriciler için</span><span class="sxs-lookup"><span data-stu-id="d5cb3-110">LINQ to XML Developers</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="d5cb3-111">geliştiricilerin çeşitli hedefler.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-111">targets a variety of developers.</span></span> <span data-ttu-id="d5cb3-112">Sadece bir şey yapmak isteyen ortalama [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir geliştirici için, SQL benzer bir sorgu deneyimi sağlayarak XML kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-112">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="d5cb3-113">Sadece biraz çalışma ile, programcılar tercih ettikleri programlama dilinde kısa ve güçlü sorgular yazmayı öğrenebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-113">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>

<span data-ttu-id="d5cb3-114">Profesyonel geliştiriciler [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] büyük ölçüde verimliliklerini artırmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-114">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="d5cb3-115">Ile [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], onlar daha anlamlı, daha kompakt ve daha güçlü daha az kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-115">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="d5cb3-116">Aynı anda birden çok veri etki alanından gelen sorgu ifadelerini kullanabilirler.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-116">They can use query expressions from multiple data domains at the same time.</span></span>

## <a name="what-is-linq-to-xml"></a><span data-ttu-id="d5cb3-117">XML'e LINQ Nedir?</span><span class="sxs-lookup"><span data-stu-id="d5cb3-117">What Is LINQ to XML?</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="d5cb3-118">.NET Framework programlama dillerinden XML ile çalışmanızı sağlayan LINQ özellikli, bellek içi XML programlama arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-118">is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the .NET Framework programming languages.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="d5cb3-119">XML belgesini belleğe getirdiği Belge Nesnesi Modeli (DOM) gibidir.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-119">is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="d5cb3-120">Belgeyi sorgulayabilir ve değiştirebilir, değiştirdikten sonra da belgeyi bir dosyaya kaydedebilir veya seri hale getirebilir ve Internet üzerinden gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-120">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="d5cb3-121">Ancak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] DOM farklıdır: Daha hafif ve çalışması daha kolay yeni bir nesne modeli sağlar ve C#'daki dil özelliklerinden yararlanır.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-121">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in C#.</span></span>

<span data-ttu-id="d5cb3-122">Bunun en önemli [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] avantajı, Dil-Entegre Sorgu (LINQ) ile bütünleşmesidir.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-122">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with Language-Integrated Query (LINQ).</span></span> <span data-ttu-id="d5cb3-123">Bu tümleştirme, öğelerin ve özniteliklerin koleksiyonlarını almak için bellek içi XML belgesine sorgu yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-123">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="d5cb3-124">Sorgu yeteneği [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] xpath ve XQuery işlevsellik (sözdiziminde olmasa da) karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-124">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="d5cb3-125">LINQ'nin C# ile tümleştirilmesi daha güçlü yazma, derleme zamanı denetimi ve geliştirilmiş hata ayıklama desteği sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-125">The integration of LINQ in C# provides stronger typing, compile-time checking, and improved debugger support.</span></span>

<span data-ttu-id="d5cb3-126">Bir diğer [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] avantajı da sorgu sonuçlarını parametreler <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> olarak kullanabilmektir ve nesne oluşturucular XML ağaçları oluşturmak için güçlü bir yaklaşım sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-126">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="d5cb3-127">*İşlevsel yapı*adı verilen bu yaklaşım, geliştiricilerin XML ağaçlarını bir şekilden diğerine kolayca dönüştürmelerine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-127">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>

<span data-ttu-id="d5cb3-128">Örneğin, Örnek XML Dosyasında açıklandığı gibi tipik bir XML satın alma siparişine sahip [olabilirsiniz: Tipik Satınalma Siparişi (LINQ-XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="d5cb3-128">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span> <span data-ttu-id="d5cb3-129">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Kullanarak, satınalma siparişindeki her madde öğesi için parça numarası özniteliği değerini elde etmek için aşağıdaki sorguyu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d5cb3-129">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

<span data-ttu-id="d5cb3-130">Bu yöntem sözdizimi şeklinde yeniden yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="d5cb3-130">This can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

<span data-ttu-id="d5cb3-131">Başka bir örnek olarak, değeri 100 TL'den büyük olan öğelerin parça numarasına göre sıralanmış bir liste isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-131">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="d5cb3-132">Bu bilgileri elde etmek için aşağıdaki sorguyu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d5cb3-132">To obtain this information, you could run the following query:</span></span>

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

<span data-ttu-id="d5cb3-133">Yine, bu yöntem sözdizimi şeklinde yeniden yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="d5cb3-133">Again, this can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

<span data-ttu-id="d5cb3-134">Bu LINQ yeteneklerine ek [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] olarak, geliştirilmiş bir XML programlama arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-134">In addition to these LINQ capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="d5cb3-135">Kullanarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d5cb3-135">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>

- <span data-ttu-id="d5cb3-136">[XML'i dosyalardan](how-to-load-xml-from-a-file.md) veya [akışlardan](how-to-stream-xml-fragments-from-an-xmlreader.md)yükleyin.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-136">Load XML from [files](how-to-load-xml-from-a-file.md) or [streams](how-to-stream-xml-fragments-from-an-xmlreader.md).</span></span>

- <span data-ttu-id="d5cb3-137">XML'i dosyalara veya akışlara seri leştirin.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-137">Serialize XML to files or streams.</span></span>

- <span data-ttu-id="d5cb3-138">Fonksiyonel yapıyı kullanarak sıfırdan XML oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-138">Create XML from scratch by using functional construction.</span></span>

- <span data-ttu-id="d5cb3-139">XPath benzeri eksenler kullanarak XML sorgula.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-139">Query XML using XPath-like axes.</span></span>

- <span data-ttu-id="d5cb3-140">Bellek içi XML <xref:System.Xml.Linq.XContainer.Add%2A>ağacını , , <xref:System.Xml.Linq.XNode.Remove%2A> <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, ve <xref:System.Xml.Linq.XElement.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-140">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>

- <span data-ttu-id="d5cb3-141">XSD kullanarak XML ağaçlarını doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-141">Validate XML trees using XSD.</span></span>

- <span data-ttu-id="d5cb3-142">XML ağaçlarını bir şekilden diğerine dönüştürmek için bu özelliklerin bir birleşimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-142">Use a combination of these features to transform XML trees from one shape into another.</span></span>

## <a name="creating-xml-trees"></a><span data-ttu-id="d5cb3-143">XML Ağaçları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d5cb3-143">Creating XML Trees</span></span>

<span data-ttu-id="d5cb3-144">Programlamanın en önemli avantajlarından [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] biri XML ağaçları oluşturmak kolay olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-144">One of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="d5cb3-145">Örneğin, küçük bir XML ağacı oluşturmak için aşağıdaki gibi kod yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d5cb3-145">For example, to create a small XML tree, you can write code as follows:</span></span>

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

<span data-ttu-id="d5cb3-146">Daha fazla bilgi için Bkz. [XML Ağaçları Oluşturma (C#)](./creating-xml-trees-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="d5cb3-146">For more information, see [Creating XML Trees (C#)](./creating-xml-trees-linq-to-xml-2.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d5cb3-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5cb3-147">See also</span></span>

- [<span data-ttu-id="d5cb3-148">Başvuru (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="d5cb3-148">Reference (LINQ to XML)</span></span>](./reference-linq-to-xml.md)
- [<span data-ttu-id="d5cb3-149">LINQ - XML vs. DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="d5cb3-149">LINQ to XML vs. DOM (C#)</span></span>](./linq-to-xml-vs-dom.md)
- [<span data-ttu-id="d5cb3-150">LINQ ve XML ve Diğer XML Teknolojileri</span><span class="sxs-lookup"><span data-stu-id="d5cb3-150">LINQ to XML vs. Other XML Technologies</span></span>](./linq-to-xml-vs-other-xml-technologies.md)
- <xref:System.Xml.Linq>
