---
title: "LINQ-XML genel bakış (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1c66e87ecc72bf711dfda33cd7c0ea35f126c1e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-xml-overview-c"></a><span data-ttu-id="f03f6-102">LINQ-XML genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="f03f6-102">LINQ to XML Overview (C#)</span></span>
<span data-ttu-id="f03f6-103">XML yaygın olarak birçok bağlamlarında biçim verileri için bir yol olarak benimsemiştir.</span><span class="sxs-lookup"><span data-stu-id="f03f6-103">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="f03f6-104">Örneğin, Web, yapılandırma dosyalarını, Microsoft Office Word dosyaları ve veritabanları XML bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f03f6-104">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="f03f6-105">bir güncel, yeniden tasarlanan XML ile programlamaya yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="f03f6-105"> is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="f03f6-106">Bellek içi belge değişikliği özellikleri belge nesne modeli (DOM) sağlar ve destekleyen [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadeleri.</span><span class="sxs-lookup"><span data-stu-id="f03f6-106">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="f03f6-107">Bu sorgu ifadeleri XPath sözdizimsel olarak farklı olsa da, bunlar benzer bir işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="f03f6-107">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>  
  
## <a name="linq-to-xml-developers"></a><span data-ttu-id="f03f6-108">LINQ-XML geliştiriciler</span><span class="sxs-lookup"><span data-stu-id="f03f6-108">LINQ to XML Developers</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="f03f6-109">Geliştiriciler, çeşitli hedefler.</span><span class="sxs-lookup"><span data-stu-id="f03f6-109"> targets a variety of developers.</span></span> <span data-ttu-id="f03f6-110">Bir şey yapmanız, almak istediği bir ortalama geliştiriciye [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML SQL benzer bir sorgu deneyimi sağlayarak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="f03f6-110">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="f03f6-111">Yalnızca bir bit öğrenim, kendi seçtikleri programlama dilinde kısa ve güçlü sorgular yazmak programcıları öğrenebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f03f6-111">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>  
  
 <span data-ttu-id="f03f6-112">Profesyonel geliştiricilere kullanabileceğiniz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] üretkenliklerini büyük ölçüde artırmak için.</span><span class="sxs-lookup"><span data-stu-id="f03f6-112">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="f03f6-113">İle [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], daha açıklayıcı, daha küçük ve daha güçlü daha az kod yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f03f6-113">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="f03f6-114">Aynı anda birden çok veri etki alanından karşı sorgu ifadeleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="f03f6-114">They can use query expressions from multiple data domains at the same time.</span></span>  
  
## <a name="what-is-linq-to-xml"></a><span data-ttu-id="f03f6-115">LINQ-XML nedir?</span><span class="sxs-lookup"><span data-stu-id="f03f6-115">What Is LINQ to XML?</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="f03f6-116">XML ile içinden çalışmanıza olanak sağlayan bir LINQ etkin, bellek içi XML programlama arabirimidir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] programlama dilleri.</span><span class="sxs-lookup"><span data-stu-id="f03f6-116"> is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] programming languages.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="f03f6-117">XML belgesi belleğe getirir belge nesne modeli (DOM) gibi olmamasıdır.</span><span class="sxs-lookup"><span data-stu-id="f03f6-117"> is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="f03f6-118">Sorgulamak ve belgeyi değiştirmek, ve değiştirdikten sonra bir dosyaya kaydedin veya bu seri hale getirmek ve Internet üzerinden göndermek.</span><span class="sxs-lookup"><span data-stu-id="f03f6-118">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="f03f6-119">Ancak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] DOM farklıdır: açık ağırlığı yeni bir nesne modeli sağlar ve birlikte çalışmak daha kolay ve, dil özellikleri C# ' ta yararlanır.</span><span class="sxs-lookup"><span data-stu-id="f03f6-119">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in C#.</span></span>  
  
 <span data-ttu-id="f03f6-120">En önemli avantajlarından [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tümleştirmesi sayesinde olduğu [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f03f6-120">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span></span> <span data-ttu-id="f03f6-121">Bu tümleştirme öğeleri ve özniteliklerinin koleksiyonlarını almak için bellek içi XML belgesi sorguları yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f03f6-121">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="f03f6-122">Sorgu yeteneğini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] (değil, ancak sözdizimi) işlevselliği karşılaştırılabilir XPath ve XQuery.</span><span class="sxs-lookup"><span data-stu-id="f03f6-122">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="f03f6-123">Tümleştirmesini [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] C# ' ta daha güçlü yazarak, denetleme ve geliştirilmiş hata ayıklayıcı desteği zamanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f03f6-123">The integration of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] in C# provides stronger typing, compile-time checking, and improved debugger support.</span></span>  
  
 <span data-ttu-id="f03f6-124">Başka bir avantajı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu sonuçları için parametre olarak kullanmak için özelliği <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XAttribute> nesne oluşturucuları XML ağaçları oluşturmak için güçlü bir yaklaşım sağlar.</span><span class="sxs-lookup"><span data-stu-id="f03f6-124">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="f03f6-125">Adlandırılan bu yaklaşım *işlevsel yapım*, başka bir XML ağaçları bir şeklin kolayca dönüştürmek için geliştiricilere olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f03f6-125">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>  
  
 <span data-ttu-id="f03f6-126">Örneğin, satınalma siparişi açıklandığı gibi tipik bir XML olabilir [örnek XML dosyası: tipik satınalma siparişi (LINQ-XML)](http://msdn.microsoft.com/library/0606c09f-6e43-4f8d-95c8-e8e2e08d2348).</span><span class="sxs-lookup"><span data-stu-id="f03f6-126">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](http://msdn.microsoft.com/library/0606c09f-6e43-4f8d-95c8-e8e2e08d2348).</span></span> <span data-ttu-id="f03f6-127">Kullanarak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], satın alma siparişi her öğe öğesinde bölümü numara özniteliği değeri elde etmek için aşağıdaki sorguyu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f03f6-127">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>  
  
```csharp  
IEnumerable<string> partNos =  
from item in purchaseOrder.Descendants("Item")  
select (string) item.Attribute("PartNumber");  
```  
  
 <span data-ttu-id="f03f6-128">Başka bir örnek olarak, bölümü sayısı $100'den büyük bir değere sahip öğeleri sıralı liste, isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f03f6-128">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="f03f6-129">Bu bilgiler edinmek için aşağıdaki sorguyu çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f03f6-129">To obtain this information, you could run the following query:</span></span>  
  
```csharp  
IEnumerable<XElement> partNos =  
from item in purchaseOrder.Descendants("Item")  
where (int) item.Element("Quantity") *  
    (decimal) item.Element("USPrice") > 100  
orderby (string)item.Element("PartNumber")  
select item;  
```  
  
 <span data-ttu-id="f03f6-130">Bunların yanı sıra [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] özellikleri, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] geliştirilmiş bir XML programlama arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f03f6-130">In addition to these [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="f03f6-131">Kullanarak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f03f6-131">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>  
  
-   <span data-ttu-id="f03f6-132">XML dosyaları veya akışlar yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="f03f6-132">Load XML from files or streams.</span></span>  
  
-   <span data-ttu-id="f03f6-133">XML dosyaları veya akışları serileştirir.</span><span class="sxs-lookup"><span data-stu-id="f03f6-133">Serialize XML to files or streams.</span></span>  
  
-   <span data-ttu-id="f03f6-134">XML işlevsel yapım kullanarak sıfırdan oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f03f6-134">Create XML from scratch by using functional construction.</span></span>  
  
-   <span data-ttu-id="f03f6-135">Sorgu XPath benzeri eksen kullanılarak XML.</span><span class="sxs-lookup"><span data-stu-id="f03f6-135">Query XML using XPath-like axes.</span></span>  
  
-   <span data-ttu-id="f03f6-136">Bellek içi XML ağaç yöntemleri kullanarak işlemek <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, ve <xref:System.Xml.Linq.XElement.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="f03f6-136">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>  
  
-   <span data-ttu-id="f03f6-137">XML ağaçları XSD kullanarak doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="f03f6-137">Validate XML trees using XSD.</span></span>  
  
-   <span data-ttu-id="f03f6-138">Başka bir şeklin XML ağaçları dönüştürmek için bu özellik bileşimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="f03f6-138">Use a combination of these features to transform XML trees from one shape into another.</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="f03f6-139">XML ağaçları oluşturma</span><span class="sxs-lookup"><span data-stu-id="f03f6-139">Creating XML Trees</span></span>  
 <span data-ttu-id="f03f6-140">En önemli avantajlarından biri ile programlama [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML ağaçları oluşturmanın kolay olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f03f6-140">One of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="f03f6-141">Örneğin, küçük bir XML ağacı oluşturmak için kod şu şekilde yazabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f03f6-141">For example, to create a small XML tree, you can write code as follows:</span></span>  
  
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
  
 <span data-ttu-id="f03f6-142">Daha fazla bilgi için bkz: [XML ağaçları (C#) oluşturma](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="f03f6-142">For more information, see [Creating XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f03f6-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f03f6-143">See Also</span></span>  
 <xref:System.Xml.Linq>  
 [<span data-ttu-id="f03f6-144">Başlarken (LINQ-XML)</span><span class="sxs-lookup"><span data-stu-id="f03f6-144">Getting Started (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
