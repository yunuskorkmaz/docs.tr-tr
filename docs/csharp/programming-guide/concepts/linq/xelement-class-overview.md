---
title: XElement sınıfına genel bakış (C#)
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: 815b7b6523afe7106fcdcbe242d667c5ad6aa56e
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487010"
---
# <a name="xelement-class-overview-c"></a><span data-ttu-id="4bad0-102">XElement sınıfına genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="4bad0-102">XElement Class Overview (C#)</span></span>
<span data-ttu-id="4bad0-103"><xref:System.Xml.Linq.XElement> Sınıfın temel sınıflarında biridir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4bad0-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="4bad0-104">Bu, bir XML öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4bad0-104">It represents an XML element.</span></span> <span data-ttu-id="4bad0-105">Bu sınıf, öğeleri oluşturmak için kullanabilirsiniz; öğenin içeriğini değiştirmek; ekleme, değiştirme veya alt öğeleri silin; öznitelik, bir öğeye ekleyin; ya da metin biçiminde bir öğenin içeriği seri hale getirme.</span><span class="sxs-lookup"><span data-stu-id="4bad0-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="4bad0-106">İçindeki diğer sınıflarla çalışabilirler <xref:System.Xml?displayProperty=nameWithType>, gibi <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, ve <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="4bad0-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
<span data-ttu-id="4bad0-107">Bu konu tarafından sağlanan işlevselliği açıklar <xref:System.Xml.Linq.XElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="4bad0-107">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
## <a name="constructing-xml-trees"></a><span data-ttu-id="4bad0-108">XML ağaçları oluşturma</span><span class="sxs-lookup"><span data-stu-id="4bad0-108">Constructing XML Trees</span></span>  
 <span data-ttu-id="4bad0-109">XML ağaçlarını aşağıdakiler dahil olmak üzere çeşitli oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="4bad0-109">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
- <span data-ttu-id="4bad0-110">Bir XML ağacı kod oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4bad0-110">You can construct an XML tree in code.</span></span> <span data-ttu-id="4bad0-111">Daha fazla bilgi için [XML ağaçları oluşturma (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4bad0-111">For more information, see [Creating XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md).</span></span>  
  
- <span data-ttu-id="4bad0-112">XML dahil olmak üzere çeşitli kaynaklardan ayrıştırabilirsiniz bir <xref:System.IO.TextReader>, metin dosyaları veya bir Web adresi (URL).</span><span class="sxs-lookup"><span data-stu-id="4bad0-112">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="4bad0-113">Daha fazla bilgi için [XML Ayrıştırma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-parse-a-string.md).</span><span class="sxs-lookup"><span data-stu-id="4bad0-113">For more information, see [Parsing XML (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-parse-a-string.md).</span></span>  
  
- <span data-ttu-id="4bad0-114">Kullanabileceğiniz bir <xref:System.Xml.XmlReader> ağacını doldurmak için.</span><span class="sxs-lookup"><span data-stu-id="4bad0-114">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="4bad0-115">Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="4bad0-115">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
- <span data-ttu-id="4bad0-116">İçeriği yazabilen bir modül varsa bir <xref:System.Xml.XmlWriter>, kullanabileceğiniz <xref:System.Xml.Linq.XContainer.CreateWriter%2A> bir yazıcısı oluşturmak, yazıcı modülü geçirin ve ardından yazılan içeriği yöntemi <xref:System.Xml.XmlWriter> XML ağacını doldurmak için.</span><span class="sxs-lookup"><span data-stu-id="4bad0-116">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="4bad0-117">Ancak, bir XML ağacı oluşturmak için en yaygın yolu şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="4bad0-117">However, the most common way to create an XML tree is as follows:</span></span>  
  
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
  
 <span data-ttu-id="4bad0-118">Bir XML ağacı oluşturmak için başka bir yaygın yöntem sonuçlarını kullanılmasına bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] aşağıdaki örnekte gösterildiği gibi bir XML ağacı doldurma için sorgu:</span><span class="sxs-lookup"><span data-stu-id="4bad0-118">Another very common technique for creating an XML tree involves using the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to populate an XML tree, as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="4bad0-119">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="4bad0-119">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="serializing-xml-trees"></a><span data-ttu-id="4bad0-120">XML Ağaçlarını Serileştirme</span><span class="sxs-lookup"><span data-stu-id="4bad0-120">Serializing XML Trees</span></span>  
 <span data-ttu-id="4bad0-121">XML ağacına serileştirebilen bir <xref:System.IO.File>, <xref:System.IO.TextWriter>, veya bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="4bad0-121">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="4bad0-122">Daha fazla bilgi için [XML ağaçlarını serileştirme (C#)](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).</span><span class="sxs-lookup"><span data-stu-id="4bad0-122">For more information, see [Serializing XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).</span></span>  
  
## <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="4bad0-123">Eksen yöntemleri aracılığıyla XML verilerini alma</span><span class="sxs-lookup"><span data-stu-id="4bad0-123">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="4bad0-124">Eksen yöntemleri, öznitelikler, alt öğeleri, alt ve üst öğeleri almak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4bad0-124">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] <span data-ttu-id="4bad0-125">sorgular, eksen yöntemleri üzerinde çalışır ve gezinmek ve bir XML ağacı işlemek için çeşitli esnek ve güçlü yollarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4bad0-125">queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="4bad0-126">Daha fazla bilgi için [LINQ to XML eksenleri (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4bad0-126">For more information, see [LINQ to XML Axes (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md).</span></span>  
  
## <a name="querying-xml-trees"></a><span data-ttu-id="4bad0-127">XML Ağaçlarını Sorgulama</span><span class="sxs-lookup"><span data-stu-id="4bad0-127">Querying XML Trees</span></span>  
 <span data-ttu-id="4bad0-128">Yazabileceğiniz [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] XML ağacından verileri ayıklamak sorgular.</span><span class="sxs-lookup"><span data-stu-id="4bad0-128">You can write [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="4bad0-129">Daha fazla bilgi için [XML ağaçlarını sorgulama (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-an-element-with-a-specific-attribute.md).</span><span class="sxs-lookup"><span data-stu-id="4bad0-129">For more information, see [Querying XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-find-an-element-with-a-specific-attribute.md).</span></span>  
  
## <a name="modifying-xml-trees"></a><span data-ttu-id="4bad0-130">XML ağaçlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="4bad0-130">Modifying XML Trees</span></span>  
 <span data-ttu-id="4bad0-131">Bir öğeyi kendi içerik veya öznitelikleri değiştirme dahil olmak üzere çeşitli değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4bad0-131">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="4bad0-132">Ayrıca, bir öğenin üst öğesinden kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4bad0-132">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="4bad0-133">Daha fazla bilgi için [XML ağaçlarını değiştirme (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="4bad0-133">For more information, see [Modifying XML Trees (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bad0-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4bad0-134">See also</span></span>

- [<span data-ttu-id="4bad0-135">LINQ to XML programlamaya genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="4bad0-135">LINQ to XML Programming Overview (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
