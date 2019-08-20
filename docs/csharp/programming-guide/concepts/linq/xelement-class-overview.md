---
title: XElement sınıfına genel bakışC#()
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: e742741f56f3e39f93b9f1d6be30a54a4ede67f3
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590888"
---
# <a name="xelement-class-overview-c"></a><span data-ttu-id="345c6-102">XElement sınıfına genel bakışC#()</span><span class="sxs-lookup"><span data-stu-id="345c6-102">XElement Class Overview (C#)</span></span>
<span data-ttu-id="345c6-103">Sınıfı, içindeki [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]temel sınıflardan biridir. <xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="345c6-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="345c6-104">Bir XML öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="345c6-104">It represents an XML element.</span></span> <span data-ttu-id="345c6-105">Bu sınıfı, öğeler oluşturmak için kullanabilirsiniz; öğenin içeriğini değiştirme; alt öğeleri ekleyin, değiştirin veya silin; özniteliği bir öğeye ekleyin; veya metin biçimindeki bir öğenin içeriğini seri hale getirme.</span><span class="sxs-lookup"><span data-stu-id="345c6-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="345c6-106">Ayrıca, ve <xref:System.Xml?displayProperty=nameWithType> <xref:System.Xml.XmlWriter> <xref:System.Xml.XmlReader> gibidiğersınıflarladabirliktekullanabilirsiniz<xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="345c6-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
<span data-ttu-id="345c6-107">Bu konu, <xref:System.Xml.Linq.XElement> sınıfının sunduğu işlevselliği açıklar.</span><span class="sxs-lookup"><span data-stu-id="345c6-107">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
## <a name="constructing-xml-trees"></a><span data-ttu-id="345c6-108">XML ağaçları oluşturma</span><span class="sxs-lookup"><span data-stu-id="345c6-108">Constructing XML Trees</span></span>  
 <span data-ttu-id="345c6-109">Aşağıdakiler dahil olmak üzere çeşitli yollarla XML ağaçları oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="345c6-109">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
- <span data-ttu-id="345c6-110">Kodda bir XML ağacı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="345c6-110">You can construct an XML tree in code.</span></span> <span data-ttu-id="345c6-111">Daha fazla bilgi için bkz. [xml ağaçları oluşturmaC#()](./linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="345c6-111">For more information, see [Creating XML Trees (C#)](./linq-to-xml-overview.md).</span></span>  
  
- <span data-ttu-id="345c6-112">Bir <xref:System.IO.TextReader>metin dosyası veya bir Web adresi (URL) dahil olmak üzere çeşitli kaynaklardan XML ayrıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="345c6-112">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="345c6-113">Daha fazla bilgi için bkz. [XML (C#) ayrıştırma](./how-to-parse-a-string.md).</span><span class="sxs-lookup"><span data-stu-id="345c6-113">For more information, see [Parsing XML (C#)](./how-to-parse-a-string.md).</span></span>  
  
- <span data-ttu-id="345c6-114">Ağacı doldurmak <xref:System.Xml.XmlReader> için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="345c6-114">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="345c6-115">Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="345c6-115">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
- <span data-ttu-id="345c6-116">İçine içerik <xref:System.Xml.XmlWriter>yazabileceği bir modülünüzün varsa, bir yazıcı oluşturmak, yazıcıyı modüle <xref:System.Xml.Linq.XContainer.CreateWriter%2A> geçirmek ve ardından XML ağacını doldurmak <xref:System.Xml.XmlWriter> için öğesine yazılan içeriği kullanmak için yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="345c6-116">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="345c6-117">Ancak, bir XML ağacı oluşturmanın en yaygın yolu aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="345c6-117">However, the most common way to create an XML tree is as follows:</span></span>  
  
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
  
 <span data-ttu-id="345c6-118">Bir XML ağacı oluşturmaya yönelik başka bir çok yaygın teknik, aşağıdaki örnekte gösterildiği gibi [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] , bir xml ağacını doldurmak için bir sorgunun sonuçlarının kullanılmasını içerir:</span><span class="sxs-lookup"><span data-stu-id="345c6-118">Another very common technique for creating an XML tree involves using the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to populate an XML tree, as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="345c6-119">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="345c6-119">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="serializing-xml-trees"></a><span data-ttu-id="345c6-120">XML Ağaçlarını Serileştirme</span><span class="sxs-lookup"><span data-stu-id="345c6-120">Serializing XML Trees</span></span>  
 <span data-ttu-id="345c6-121">XML ağacını bir <xref:System.IO.File>, a <xref:System.IO.TextWriter>veya <xref:System.Xml.XmlWriter>olarak seri hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="345c6-121">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="345c6-122">Daha fazla bilgi için bkz. [XML ağaçlarını serileştirmeC#()](./preserving-white-space-while-serializing.md).</span><span class="sxs-lookup"><span data-stu-id="345c6-122">For more information, see [Serializing XML Trees (C#)](./preserving-white-space-while-serializing.md).</span></span>  
  
## <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="345c6-123">XML verilerini eksen yöntemleri aracılığıyla alma</span><span class="sxs-lookup"><span data-stu-id="345c6-123">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="345c6-124">Öznitelikleri, alt öğeleri, alt öğeleri ve üst öğeleri almak için eksen yöntemlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="345c6-124">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]<span data-ttu-id="345c6-125">sorgular eksen yöntemleri üzerinde çalışır ve bir XML ağacı üzerinde gezinmek ve işlemek için çeşitli esnek ve güçlü yollar sunar.</span><span class="sxs-lookup"><span data-stu-id="345c6-125">queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="345c6-126">Daha fazla bilgi için bkz. [LINQ to XML eksenleriC#()](./linq-to-xml-axes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="345c6-126">For more information, see [LINQ to XML Axes (C#)](./linq-to-xml-axes-overview.md).</span></span>  
  
## <a name="querying-xml-trees"></a><span data-ttu-id="345c6-127">XML Ağaçlarını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="345c6-127">Querying XML Trees</span></span>  
 <span data-ttu-id="345c6-128">XML ağacından veri [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] çıkaran sorgular yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="345c6-128">You can write [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="345c6-129">Daha fazla bilgi için bkz. [XML ağaçlarını sorgulamaC#()](./how-to-find-an-element-with-a-specific-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="345c6-129">For more information, see [Querying XML Trees (C#)](./how-to-find-an-element-with-a-specific-attribute.md).</span></span>  
  
## <a name="modifying-xml-trees"></a><span data-ttu-id="345c6-130">XML ağaçlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="345c6-130">Modifying XML Trees</span></span>  
 <span data-ttu-id="345c6-131">Bir öğeyi, içeriğini veya özniteliklerini değiştirme gibi çeşitli yollarla değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="345c6-131">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="345c6-132">Ayrıca bir öğeyi üst öğesinden da kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="345c6-132">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="345c6-133">Daha fazla bilgi için bkz. [XML ağaçlarını değiştirme (LINQ to XML)C#()](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="345c6-133">For more information, see [Modifying XML Trees (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="345c6-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="345c6-134">See also</span></span>

- [<span data-ttu-id="345c6-135">LINQ to XML programlamaya genel bakışC#()</span><span class="sxs-lookup"><span data-stu-id="345c6-135">LINQ to XML Programming Overview (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
