---
title: LINQ to XML genel bakış (C#)
ms.date: 10/30/2018
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: a9435027a7487af96227fdc7a0eae6f511d82b23
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484352"
---
# <a name="linq-to-xml-overview-c"></a><span data-ttu-id="746e5-102">LINQ to XML genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="746e5-102">LINQ to XML Overview (C#)</span></span>

<span data-ttu-id="746e5-103">LINQ to XML .NET Language-Integrated sorgu (LINQ) Framework yararlanan bir bellek içi XML programlama arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="746e5-103">LINQ to XML provides an in-memory XML programming interface that leverages the .NET Language-Integrated Query (LINQ) Framework.</span></span> <span data-ttu-id="746e5-104">LINQ to XML .NET özelliklerini kullanır ve bir güncelleştirilmiş, yeniden tasarlanan belge nesne modeli (DOM) XML programlama arabirimi için karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="746e5-104">LINQ to XML uses .NET capabilities and is comparable to an updated, redesigned Document Object Model (DOM) XML programming interface.</span></span> 
 
<span data-ttu-id="746e5-105">XML, yaygın olarak birçok bağlamları verileri biçimlendirme bir yolu olarak benimsenmiştir.</span><span class="sxs-lookup"><span data-stu-id="746e5-105">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="746e5-106">Örneğin, yapılandırma dosyalarını, Microsoft Office Word dosyaları ve veritabanlarının Web XML bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="746e5-106">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="746e5-107">güncel ve yeniden tasarlanan XML ile programlamaya yaklaşımıdır.</span><span class="sxs-lookup"><span data-stu-id="746e5-107">is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="746e5-108">Bellek içi belge değiştirme özelliklerini belge nesne modeli (DOM) sağlar ve destekleyen [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadelerinde.</span><span class="sxs-lookup"><span data-stu-id="746e5-108">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="746e5-109">Bu sorgu ifadeleri XPath sözdizimi kurallarına göre farklı olsa da, benzer bir işlevsellik sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="746e5-109">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>

## <a name="linq-to-xml-developers"></a><span data-ttu-id="746e5-110">LINQ to XML geliştiriciler</span><span class="sxs-lookup"><span data-stu-id="746e5-110">LINQ to XML Developers</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="746e5-111">geliştiricilerin çeşitli hedefler.</span><span class="sxs-lookup"><span data-stu-id="746e5-111">targets a variety of developers.</span></span> <span data-ttu-id="746e5-112">Yalnızca bir şey yapmanız, almak isteyen bir ortalama geliştiricinin [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML SQL'e benzeyen bir sorgu deneyimi sunarak daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="746e5-112">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="746e5-113">Yalnızca bir bit öğrenim, programcılar kendi seçtiğiniz programlama dilinde birleştiren ve güçlü sorgular yazmak bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="746e5-113">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>

<span data-ttu-id="746e5-114">Profesyonel Geliştiriciler [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] üretkenliklerini büyük ölçüde artırmak için.</span><span class="sxs-lookup"><span data-stu-id="746e5-114">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="746e5-115">İle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], bunlar daha ifadesel, daha küçük ve daha güçlü daha az kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="746e5-115">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="746e5-116">Aynı anda birden çok veri etki alanından bunlar sorgu ifadeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="746e5-116">They can use query expressions from multiple data domains at the same time.</span></span>

## <a name="what-is-linq-to-xml"></a><span data-ttu-id="746e5-117">LINQ to XML nedir?</span><span class="sxs-lookup"><span data-stu-id="746e5-117">What Is LINQ to XML?</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="746e5-118">.NET Framework XML'de çalışmanızı sağlayan bir LINQ-etkin, bellek içi XML programlama arabirimi programlama dilleri.</span><span class="sxs-lookup"><span data-stu-id="746e5-118">is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the .NET Framework programming languages.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="746e5-119">XML belgesi belleğe getirdiği belge nesne modeli (DOM) gibi olmamasıdır.</span><span class="sxs-lookup"><span data-stu-id="746e5-119">is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="746e5-120">Sorgulamak ve belgeyi değiştirmesine ve değiştirdikten sonra bir dosyaya kaydedebilir veya bu seri hale getirmek ve Internet üzerinden gönder.</span><span class="sxs-lookup"><span data-stu-id="746e5-120">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="746e5-121">Ancak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] DOM farklıdır: Açık ağırlığı olan yeni bir nesne modeli sağlar ve çalışmak, daha kolay ve dil özelliklerinden alan C#.</span><span class="sxs-lookup"><span data-stu-id="746e5-121">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in C#.</span></span>

<span data-ttu-id="746e5-122">En önemli avantajı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tümleştirmesi sayesinde olan [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="746e5-122">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span></span> <span data-ttu-id="746e5-123">Bu tümleştirme, öğeleri ve özniteliklerinin koleksiyonu almak için bellek içi XML belgesi sorgular yazmaya olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="746e5-123">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="746e5-124">Sorgu yeteneğini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] (değil, ancak sözdizimi) işlevselliği karşılaştırılabilir XPath ve XQuery.</span><span class="sxs-lookup"><span data-stu-id="746e5-124">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="746e5-125">Tümleştirmesini [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] C# ' de daha güçlü yazım, denetleme ve geliştirilmiş hata ayıklayıcı desteği zamanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="746e5-125">The integration of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] in C# provides stronger typing, compile-time checking, and improved debugger support.</span></span>

<span data-ttu-id="746e5-126">Başka bir avantajı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu sonuçları için parametre olarak kullanma olanağı <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> nesne oluşturucuları XML ağaçları oluşturma için güçlü bir yaklaşım sağlar.</span><span class="sxs-lookup"><span data-stu-id="746e5-126">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="746e5-127">Adlandırılan bu yaklaşım *işlevsel oluşturma*, geliştiricilerin bir şekilden XML ağaçlarını başka bir kolayca dönüştürüp olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="746e5-127">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>

<span data-ttu-id="746e5-128">Örneğin, satınalma siparişi açıklandığı gibi tipik bir XML olabilir [örnek XML dosyası: Tipik satın alma siparişi (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="746e5-128">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span> <span data-ttu-id="746e5-129">Kullanarak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], satın alma siparişi her öğe öğe için bölüm numarası özniteliği değeri elde etmek için şu sorguyu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="746e5-129">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load($"{purchaseOrderFilepath}");

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

<span data-ttu-id="746e5-130">Bu yöntem sözdizimi formunda yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="746e5-130">This can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

<span data-ttu-id="746e5-131">Başka bir örnek olarak $100'den büyük bir değer ile öğelerinin parça numarası tarafından sıralanan bir liste isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="746e5-131">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="746e5-132">Bu bilgiler edinmek için şu sorguyu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="746e5-132">To obtain this information, you could run the following query:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load($"{purchaseOrderFilepath}");

IEnumerable<XElement> pricesByPartNos =  from item in purchaseOrder.Descendants("Item")
                                 where (int) item.Element("Quantity") * (decimal) item.Element("USPrice") > 100
                                 orderby (string)item.Element("PartNumber")
                                 select item;
```

<span data-ttu-id="746e5-133">Yeniden, bu yöntem sözdizimi formunda yazılabilir:</span><span class="sxs-lookup"><span data-stu-id="746e5-133">Again, this can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

<span data-ttu-id="746e5-134">Bunların yanı sıra [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] yeteneklerini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] geliştirilmiş bir XML programlama arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="746e5-134">In addition to these [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="746e5-135">Kullanarak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="746e5-135">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>

- <span data-ttu-id="746e5-136">XML'den yük [dosyaları](how-to-load-xml-from-a-file.md) veya [akışları](how-to-stream-xml-fragments-from-an-xmlreader.md).</span><span class="sxs-lookup"><span data-stu-id="746e5-136">Load XML from [files](how-to-load-xml-from-a-file.md) or [streams](how-to-stream-xml-fragments-from-an-xmlreader.md).</span></span>

- <span data-ttu-id="746e5-137">XML dosyaları ya da akış serileştirir.</span><span class="sxs-lookup"><span data-stu-id="746e5-137">Serialize XML to files or streams.</span></span>

- <span data-ttu-id="746e5-138">XML işlevsel oluşturma kullanarak sıfırdan oluşturun.</span><span class="sxs-lookup"><span data-stu-id="746e5-138">Create XML from scratch by using functional construction.</span></span>

- <span data-ttu-id="746e5-139">Sorgu XPath benzeri eksen kullanılarak XML.</span><span class="sxs-lookup"><span data-stu-id="746e5-139">Query XML using XPath-like axes.</span></span>

- <span data-ttu-id="746e5-140">Bellek içi XML ağacı yöntemleri kullanarak işleme <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, ve <xref:System.Xml.Linq.XElement.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="746e5-140">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>

- <span data-ttu-id="746e5-141">XML ağaçlarını XSD kullanarak doğrulama.</span><span class="sxs-lookup"><span data-stu-id="746e5-141">Validate XML trees using XSD.</span></span>

- <span data-ttu-id="746e5-142">Başka bir şekilden XML ağaçlarını dönüştürmek için bu özellikleri bir birleşimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="746e5-142">Use a combination of these features to transform XML trees from one shape into another.</span></span>

## <a name="creating-xml-trees"></a><span data-ttu-id="746e5-143">XML Ağaçları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="746e5-143">Creating XML Trees</span></span>

<span data-ttu-id="746e5-144">Programlama ile en önemli avantajlarından biri [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML ağaçları oluşturma kolay olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="746e5-144">One of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="746e5-145">Örneğin, küçük bir XML ağacı oluşturmak için kod şu şekilde yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="746e5-145">For example, to create a small XML tree, you can write code as follows:</span></span>

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

<span data-ttu-id="746e5-146">Daha fazla bilgi için [XML ağaçları oluşturma (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="746e5-146">For more information, see [Creating XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="746e5-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="746e5-147">See also</span></span>

- [<span data-ttu-id="746e5-148">Başvuru (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="746e5-148">Reference (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/reference-linq-to-xml.md)
- [<span data-ttu-id="746e5-149">LINQ to XML ile DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="746e5-149">LINQ to XML vs. DOM (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)
- [<span data-ttu-id="746e5-150">LINQ to XML ile Diğer XML Teknolojileri Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="746e5-150">LINQ to XML vs. Other XML Technologies</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
- <xref:System.Xml.Linq>
