---
title: LINQ to XML genel bakış (C#)
ms.date: 07/20/2015
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: 5b557c95993d7f1e907a8eb6ef1e5ec23a2988ab
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43856627"
---
# <a name="linq-to-xml-overview-c"></a><span data-ttu-id="6f498-102">LINQ to XML genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="6f498-102">LINQ to XML Overview (C#)</span></span>
<span data-ttu-id="6f498-103">XML, yaygın olarak birçok bağlamları verileri biçimlendirme bir yolu olarak benimsenmiştir.</span><span class="sxs-lookup"><span data-stu-id="6f498-103">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="6f498-104">Örneğin, yapılandırma dosyalarını, Microsoft Office Word dosyaları ve veritabanlarının Web XML bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f498-104">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="6f498-105"> güncel ve yeniden tasarlanan XML ile programlamaya yaklaşımıdır.</span><span class="sxs-lookup"><span data-stu-id="6f498-105"> is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="6f498-106">Bellek içi belge değiştirme özelliklerini belge nesne modeli (DOM) sağlar ve destekleyen [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadelerinde.</span><span class="sxs-lookup"><span data-stu-id="6f498-106">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="6f498-107">Bu sorgu ifadeleri XPath sözdizimi kurallarına göre farklı olsa da, benzer bir işlevsellik sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="6f498-107">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>  
  
## <a name="linq-to-xml-developers"></a><span data-ttu-id="6f498-108">LINQ to XML geliştiriciler</span><span class="sxs-lookup"><span data-stu-id="6f498-108">LINQ to XML Developers</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="6f498-109"> geliştiricilerin çeşitli hedefler.</span><span class="sxs-lookup"><span data-stu-id="6f498-109"> targets a variety of developers.</span></span> <span data-ttu-id="6f498-110">Yalnızca bir şey yapmanız, almak isteyen bir ortalama geliştiricinin [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML SQL'e benzeyen bir sorgu deneyimi sunarak daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="6f498-110">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="6f498-111">Yalnızca bir bit öğrenim, programcılar kendi seçtiğiniz programlama dilinde birleştiren ve güçlü sorgular yazmak bilgi edinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f498-111">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>  
  
 <span data-ttu-id="6f498-112">Profesyonel Geliştiriciler [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] üretkenliklerini büyük ölçüde artırmak için.</span><span class="sxs-lookup"><span data-stu-id="6f498-112">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="6f498-113">İle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], bunlar daha ifadesel, daha küçük ve daha güçlü daha az kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f498-113">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="6f498-114">Aynı anda birden çok veri etki alanından bunlar sorgu ifadeleri kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f498-114">They can use query expressions from multiple data domains at the same time.</span></span>  
  
## <a name="what-is-linq-to-xml"></a><span data-ttu-id="6f498-115">LINQ to XML nedir?</span><span class="sxs-lookup"><span data-stu-id="6f498-115">What Is LINQ to XML?</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="6f498-116"> XML ile içinden çalışmanızı sağlayan bir LINQ-etkin, bellek içi XML programlama arabirimi olan [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] programlama.</span><span class="sxs-lookup"><span data-stu-id="6f498-116"> is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] programming languages.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="6f498-117"> XML belgesi belleğe getirdiği belge nesne modeli (DOM) gibi olmamasıdır.</span><span class="sxs-lookup"><span data-stu-id="6f498-117"> is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="6f498-118">Sorgulamak ve belgeyi değiştirmesine ve değiştirdikten sonra bir dosyaya kaydedebilir veya bu seri hale getirmek ve Internet üzerinden gönder.</span><span class="sxs-lookup"><span data-stu-id="6f498-118">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="6f498-119">Ancak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] DOM farklıdır: açık ağırlığı olan yeni bir nesne modeli sağlar ve çalışmak, daha kolay ve, dil özellikleri C# ' de yararlanır.</span><span class="sxs-lookup"><span data-stu-id="6f498-119">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in C#.</span></span>  
  
 <span data-ttu-id="6f498-120">En önemli avantajı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tümleştirmesi sayesinde olan [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6f498-120">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span></span> <span data-ttu-id="6f498-121">Bu tümleştirme, öğeleri ve özniteliklerinin koleksiyonu almak için bellek içi XML belgesi sorgular yazmaya olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6f498-121">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="6f498-122">Sorgu yeteneğini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] (değil, ancak sözdizimi) işlevselliği karşılaştırılabilir XPath ve XQuery.</span><span class="sxs-lookup"><span data-stu-id="6f498-122">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="6f498-123">Tümleştirmesini [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] C# ' de daha güçlü yazım, denetleme ve geliştirilmiş hata ayıklayıcı desteği zamanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f498-123">The integration of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] in C# provides stronger typing, compile-time checking, and improved debugger support.</span></span>  
  
 <span data-ttu-id="6f498-124">Başka bir avantajı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu sonuçları için parametre olarak kullanma olanağı <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> nesne oluşturucuları XML ağaçları oluşturma için güçlü bir yaklaşım sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f498-124">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="6f498-125">Adlandırılan bu yaklaşım *işlevsel oluşturma*, geliştiricilerin bir şekilden XML ağaçlarını başka bir kolayca dönüştürüp olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6f498-125">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>  
  
 <span data-ttu-id="6f498-126">Örneğin, satınalma siparişi açıklandığı gibi tipik bir XML olabilir [örnek XML dosyası: tipik satın alma siparişi (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="6f498-126">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span> <span data-ttu-id="6f498-127">Kullanarak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], satın alma siparişi her öğe öğe için bölüm numarası özniteliği değeri elde etmek için şu sorguyu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6f498-127">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>  
  
```csharp  
IEnumerable<string> partNos =  
from item in purchaseOrder.Descendants("Item")  
select (string) item.Attribute("PartNumber");  
```  
  
 <span data-ttu-id="6f498-128">Başka bir örnek olarak $100'den büyük bir değer ile öğelerinin parça numarası tarafından sıralanan bir liste isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f498-128">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="6f498-129">Bu bilgiler edinmek için şu sorguyu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6f498-129">To obtain this information, you could run the following query:</span></span>  
  
```csharp  
IEnumerable<XElement> partNos =  
from item in purchaseOrder.Descendants("Item")  
where (int) item.Element("Quantity") *  
    (decimal) item.Element("USPrice") > 100  
orderby (string)item.Element("PartNumber")  
select item;  
```  
  
 <span data-ttu-id="6f498-130">Bunların yanı sıra [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] yeteneklerini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] geliştirilmiş bir XML programlama arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6f498-130">In addition to these [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="6f498-131">Kullanarak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6f498-131">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>  
  
-   <span data-ttu-id="6f498-132">XML dosyaları ya da akış'ı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="6f498-132">Load XML from files or streams.</span></span>  
  
-   <span data-ttu-id="6f498-133">XML dosyaları ya da akış serileştirir.</span><span class="sxs-lookup"><span data-stu-id="6f498-133">Serialize XML to files or streams.</span></span>  
  
-   <span data-ttu-id="6f498-134">XML işlevsel oluşturma kullanarak sıfırdan oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6f498-134">Create XML from scratch by using functional construction.</span></span>  
  
-   <span data-ttu-id="6f498-135">Sorgu XPath benzeri eksen kullanılarak XML.</span><span class="sxs-lookup"><span data-stu-id="6f498-135">Query XML using XPath-like axes.</span></span>  
  
-   <span data-ttu-id="6f498-136">Bellek içi XML ağacı yöntemleri kullanarak işleme <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, ve <xref:System.Xml.Linq.XElement.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="6f498-136">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>  
  
-   <span data-ttu-id="6f498-137">XML ağaçlarını XSD kullanarak doğrulama.</span><span class="sxs-lookup"><span data-stu-id="6f498-137">Validate XML trees using XSD.</span></span>  
  
-   <span data-ttu-id="6f498-138">Başka bir şekilden XML ağaçlarını dönüştürmek için bu özellikleri bir birleşimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="6f498-138">Use a combination of these features to transform XML trees from one shape into another.</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="6f498-139">XML ağaçları oluşturma</span><span class="sxs-lookup"><span data-stu-id="6f498-139">Creating XML Trees</span></span>  
 <span data-ttu-id="6f498-140">Programlama ile en önemli avantajlarından biri [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML ağaçları oluşturma kolay olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="6f498-140">One of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="6f498-141">Örneğin, küçük bir XML ağacı oluşturmak için kod şu şekilde yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6f498-141">For example, to create a small XML tree, you can write code as follows:</span></span>  
  
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
  
 <span data-ttu-id="6f498-142">Daha fazla bilgi için [XML ağaçları oluşturma (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="6f498-142">For more information, see [Creating XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f498-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6f498-143">See Also</span></span>

- <xref:System.Xml.Linq>  
- [<span data-ttu-id="6f498-144">Başlarken (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="6f498-144">Getting Started (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
