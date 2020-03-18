---
title: XElement Sınıfına Genel Bakış (C#)
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: 6a93dd4bdaf16fddff800b08b0f3146ecb63f9b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167900"
---
# <a name="xelement-class-overview-c"></a><span data-ttu-id="58edf-102">XElement Sınıfına Genel Bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="58edf-102">XElement Class Overview (C#)</span></span>
<span data-ttu-id="58edf-103">Sınıf, <xref:System.Xml.Linq.XElement> .................................................................................................. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58edf-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="58edf-104">Bir XML öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="58edf-104">It represents an XML element.</span></span> <span data-ttu-id="58edf-105">Bu sınıfı öğeleri oluşturmak için kullanabilirsiniz; öğenin içeriğini değiştirmek; alt öğeleri ekleme, değiştirme veya silme; bir öğeye öznitelikleri eklemek; veya metin biçiminde bir öğenin içeriğini serihale.</span><span class="sxs-lookup"><span data-stu-id="58edf-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="58edf-106"><xref:System.Xml?displayProperty=nameWithType>Ayrıca, <xref:System.Xml.XmlReader>, , <xref:System.Xml.XmlWriter>, ve <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="58edf-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
<span data-ttu-id="58edf-107">Bu <xref:System.Xml.Linq.XElement> konu, sınıf tarafından sağlanan işlevselliği açıklar.</span><span class="sxs-lookup"><span data-stu-id="58edf-107">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
## <a name="constructing-xml-trees"></a><span data-ttu-id="58edf-108">XML Ağaçlarının İnşası</span><span class="sxs-lookup"><span data-stu-id="58edf-108">Constructing XML Trees</span></span>  
 <span data-ttu-id="58edf-109">XML ağaçları aşağıdakiler de dahil olmak üzere çeşitli şekillerde oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="58edf-109">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
- <span data-ttu-id="58edf-110">Kod da bir XML ağacı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58edf-110">You can construct an XML tree in code.</span></span> <span data-ttu-id="58edf-111">Daha fazla bilgi için Bkz. [XML Ağaçları Oluşturma (C#)](./linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="58edf-111">For more information, see [Creating XML Trees (C#)](./linq-to-xml-overview.md).</span></span>  
  
- <span data-ttu-id="58edf-112">XML'i <xref:System.IO.TextReader>metin dosyaları veya Web adresi (URL) dahil olmak üzere çeşitli kaynaklardan ayrışdırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58edf-112">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="58edf-113">Daha fazla bilgi için Bkz. [Ayrıştırma XML (C#)](./how-to-parse-a-string.md).</span><span class="sxs-lookup"><span data-stu-id="58edf-113">For more information, see [Parsing XML (C#)](./how-to-parse-a-string.md).</span></span>  
  
- <span data-ttu-id="58edf-114">Ağacı doldurmak <xref:System.Xml.XmlReader> için bir kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58edf-114">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="58edf-115">Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="58edf-115">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
- <span data-ttu-id="58edf-116">Bir içeriğe içerik yazabilen <xref:System.Xml.XmlWriter>bir modülüz <xref:System.Xml.Linq.XContainer.CreateWriter%2A> varsa, bir yazar oluşturmak, yazarı modüle geçirmek ve ardından XML <xref:System.Xml.XmlWriter> ağacını doldurmak için yazılan içeriği kullanmak için yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58edf-116">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="58edf-117">Ancak, bir XML ağacı oluşturmak için en yaygın yolu aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="58edf-117">However, the most common way to create an XML tree is as follows:</span></span>  
  
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
  
 <span data-ttu-id="58edf-118">Bir XML ağacı oluşturmak için başka bir çok yaygın teknik aşağıdaki örnekte gösterildiği gibi, bir XML ağacı doldurmak için bir LINQ sorgusunun sonuçlarını kullanarak içerir:</span><span class="sxs-lookup"><span data-stu-id="58edf-118">Another very common technique for creating an XML tree involves using the results of a LINQ query to populate an XML tree, as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="58edf-119">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="58edf-119">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="serializing-xml-trees"></a><span data-ttu-id="58edf-120">XML Ağaçlarını Serileştirme</span><span class="sxs-lookup"><span data-stu-id="58edf-120">Serializing XML Trees</span></span>  
 <span data-ttu-id="58edf-121">XML ağacını bir <xref:System.IO.File>, a <xref:System.IO.TextWriter>veya bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="58edf-121">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="58edf-122">Daha fazla bilgi için bkz: [Serializing XML Ağaçlar (C#)](./preserving-white-space-while-serializing.md).</span><span class="sxs-lookup"><span data-stu-id="58edf-122">For more information, see [Serializing XML Trees (C#)](./preserving-white-space-while-serializing.md).</span></span>  
  
## <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="58edf-123">Eksen Yöntemleri ile XML Veri alma</span><span class="sxs-lookup"><span data-stu-id="58edf-123">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="58edf-124">Öznitelikleri, alt öğeleri, soyundan gelen öğeleri ve ata öğelerini almak için eksen yöntemlerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58edf-124">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> <span data-ttu-id="58edf-125">LINQ sorguları eksen yöntemleri üzerinde çalışır ve bir XML ağacında gezinmek ve işlemek için birkaç esnek ve güçlü yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="58edf-125">LINQ queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="58edf-126">Daha fazla bilgi için [LinQ to XML Axes (C#)](./linq-to-xml-axes-overview.md)için bkz.</span><span class="sxs-lookup"><span data-stu-id="58edf-126">For more information, see [LINQ to XML Axes (C#)](./linq-to-xml-axes-overview.md).</span></span>  
  
## <a name="querying-xml-trees"></a><span data-ttu-id="58edf-127">XML Ağaçlarını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="58edf-127">Querying XML Trees</span></span>  
 <span data-ttu-id="58edf-128">Bir XML ağacından veri ayıklayan LINQ sorguları yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58edf-128">You can write LINQ queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="58edf-129">Daha fazla bilgi için Bkz. [XML AğaçLarını Sorgula (C#)](./how-to-find-an-element-with-a-specific-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="58edf-129">For more information, see [Querying XML Trees (C#)](./how-to-find-an-element-with-a-specific-attribute.md).</span></span>  
  
## <a name="modifying-xml-trees"></a><span data-ttu-id="58edf-130">XML Ağaçlarını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="58edf-130">Modifying XML Trees</span></span>  
 <span data-ttu-id="58edf-131">Bir öğeyi, içeriğini veya özniteliklerini değiştirme de dahil olmak üzere çeşitli şekillerde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58edf-131">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="58edf-132">Bir öğeyi üst öğesinden de kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58edf-132">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="58edf-133">Daha fazla bilgi için bkz: [XML Ağaçlarını Değiştirme (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="58edf-133">For more information, see [Modifying XML Trees (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58edf-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58edf-134">See also</span></span>

- [<span data-ttu-id="58edf-135">LINQ - XML Programlamaya Genel Bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="58edf-135">LINQ to XML Programming Overview (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
