---
title: XElement sınıfına genel bakış (C#)
description: XElement sınıfı, C# içindeki bir XML öğesini temsil eder. Bu, LINQ to XML temel sınıflardan biridir. XElement tarafından sunulan işlevsellik hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: f76f51703de054443f47531294777b43a9c0b004
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302184"
---
# <a name="xelement-class-overview-c"></a><span data-ttu-id="ba659-105">XElement sınıfına genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="ba659-105">XElement Class Overview (C#)</span></span>
<span data-ttu-id="ba659-106"><xref:System.Xml.Linq.XElement>Sınıfı, içindeki temel sınıflardan biridir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ba659-106">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="ba659-107">Bir XML öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ba659-107">It represents an XML element.</span></span> <span data-ttu-id="ba659-108">Bu sınıfı, öğeler oluşturmak için kullanabilirsiniz; öğenin içeriğini değiştirme; alt öğeleri ekleyin, değiştirin veya silin; özniteliği bir öğeye ekleyin; veya metin biçimindeki bir öğenin içeriğini seri hale getirme.</span><span class="sxs-lookup"><span data-stu-id="ba659-108">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="ba659-109">Ayrıca, ve gibi diğer sınıflarla da birlikte kullanabilirsiniz <xref:System.Xml?displayProperty=nameWithType> <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="ba659-109">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
<span data-ttu-id="ba659-110">Bu konu, sınıfının sunduğu işlevselliği açıklar <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="ba659-110">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
## <a name="constructing-xml-trees"></a><span data-ttu-id="ba659-111">XML ağaçları oluşturma</span><span class="sxs-lookup"><span data-stu-id="ba659-111">Constructing XML Trees</span></span>  
 <span data-ttu-id="ba659-112">Aşağıdakiler dahil olmak üzere çeşitli yollarla XML ağaçları oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ba659-112">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
- <span data-ttu-id="ba659-113">Kodda bir XML ağacı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba659-113">You can construct an XML tree in code.</span></span> <span data-ttu-id="ba659-114">Daha fazla bilgi için bkz. [xml ağaçları oluşturma (C#)](./linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ba659-114">For more information, see [Creating XML Trees (C#)](./linq-to-xml-overview.md).</span></span>  
  
- <span data-ttu-id="ba659-115">Bir <xref:System.IO.TextReader> metin dosyası veya bir Web adresi (URL) dahil olmak üzere çeşitli kaynaklardan XML ayrıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba659-115">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="ba659-116">Daha fazla bilgi için bkz. [XML 'ı ayrıştırma (C#)](./how-to-parse-a-string.md).</span><span class="sxs-lookup"><span data-stu-id="ba659-116">For more information, see [Parsing XML (C#)](./how-to-parse-a-string.md).</span></span>  
  
- <span data-ttu-id="ba659-117"><xref:System.Xml.XmlReader>Ağacı doldurmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba659-117">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="ba659-118">Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="ba659-118">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
- <span data-ttu-id="ba659-119">İçine içerik yazabileceği bir modülünüzün varsa, bir <xref:System.Xml.XmlWriter> <xref:System.Xml.Linq.XContainer.CreateWriter%2A> yazıcı oluşturmak, yazıcıyı modüle geçirmek ve ardından <xref:System.Xml.XmlWriter> XML ağacını doldurmak için öğesine yazılan içeriği kullanmak için yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba659-119">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="ba659-120">Ancak, bir XML ağacı oluşturmanın en yaygın yolu aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ba659-120">However, the most common way to create an XML tree is as follows:</span></span>  
  
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
  
 <span data-ttu-id="ba659-121">Bir XML ağacı oluşturmaya yönelik başka bir çok yaygın teknik, aşağıdaki örnekte gösterildiği gibi bir XML ağacını doldurmak için bir LINQ sorgusunun sonuçlarının kullanılmasını içerir:</span><span class="sxs-lookup"><span data-stu-id="ba659-121">Another very common technique for creating an XML tree involves using the results of a LINQ query to populate an XML tree, as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="ba659-122">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="ba659-122">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="serializing-xml-trees"></a><span data-ttu-id="ba659-123">XML Ağaçlarını Serileştirme</span><span class="sxs-lookup"><span data-stu-id="ba659-123">Serializing XML Trees</span></span>  
 <span data-ttu-id="ba659-124">XML ağacını bir <xref:System.IO.File> , a veya olarak seri hale getirebilirsiniz <xref:System.IO.TextWriter> <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="ba659-124">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="ba659-125">Daha fazla bilgi için bkz. [XML ağaçlarını serileştirme (C#)](./preserving-white-space-while-serializing.md).</span><span class="sxs-lookup"><span data-stu-id="ba659-125">For more information, see [Serializing XML Trees (C#)](./preserving-white-space-while-serializing.md).</span></span>  
  
## <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="ba659-126">XML verilerini eksen yöntemleri aracılığıyla alma</span><span class="sxs-lookup"><span data-stu-id="ba659-126">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="ba659-127">Öznitelikleri, alt öğeleri, alt öğeleri ve üst öğeleri almak için eksen yöntemlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba659-127">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> <span data-ttu-id="ba659-128">LINQ sorguları eksen yöntemleri üzerinde çalışır ve bir XML ağacı üzerinde gezinmek ve işlemek için çeşitli esnek ve güçlü yollar sunar.</span><span class="sxs-lookup"><span data-stu-id="ba659-128">LINQ queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="ba659-129">Daha fazla bilgi için bkz. [LINQ to XML eksenleri (C#)](./linq-to-xml-axes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ba659-129">For more information, see [LINQ to XML Axes (C#)](./linq-to-xml-axes-overview.md).</span></span>  
  
## <a name="querying-xml-trees"></a><span data-ttu-id="ba659-130">XML Ağaçlarını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="ba659-130">Querying XML Trees</span></span>  
 <span data-ttu-id="ba659-131">XML ağacından veri çıkaran LINQ sorguları yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba659-131">You can write LINQ queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="ba659-132">Daha fazla bilgi için bkz. [XML ağaçlarını sorgulama (C#)](./how-to-find-an-element-with-a-specific-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="ba659-132">For more information, see [Querying XML Trees (C#)](./how-to-find-an-element-with-a-specific-attribute.md).</span></span>  
  
## <a name="modifying-xml-trees"></a><span data-ttu-id="ba659-133">XML ağaçlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="ba659-133">Modifying XML Trees</span></span>  
 <span data-ttu-id="ba659-134">Bir öğeyi, içeriğini veya özniteliklerini değiştirme gibi çeşitli yollarla değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba659-134">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="ba659-135">Ayrıca bir öğeyi üst öğesinden da kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba659-135">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="ba659-136">Daha fazla bilgi için bkz. [XML ağaçlarını değiştirme (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ba659-136">For more information, see [Modifying XML Trees (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba659-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba659-137">See also</span></span>

- [<span data-ttu-id="ba659-138">LINQ to XML programlamaya genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="ba659-138">LINQ to XML Programming Overview (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
