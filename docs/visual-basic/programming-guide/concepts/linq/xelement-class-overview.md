---
title: "XElement sınıfına genel bakış (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: decd7c4f805de0d23b091972ee95a323baf0b7d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="xelement-class-overview-visual-basic"></a><span data-ttu-id="12726-102">XElement sınıfına genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12726-102">XElement Class Overview (Visual Basic)</span></span>
<span data-ttu-id="12726-103"><xref:System.Xml.Linq.XElement> Sınıfı temel sınıflarda biridir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12726-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="12726-104">Bir XML öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="12726-104">It represents an XML element.</span></span> <span data-ttu-id="12726-105">Bu sınıf, öğeleri oluşturmak için kullanabilirsiniz; öğenin içeriğini değiştirme; ekleme, değiştirme veya alt öğeleri silme; öznitelikleri için bir öğe ekleyin; veya içeriği, bir öğenin metin biçiminde seri hale.</span><span class="sxs-lookup"><span data-stu-id="12726-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="12726-106">Ayrıca diğer sınıflarda ile çalışabilirler <xref:System.Xml?displayProperty=nameWithType>, gibi <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, ve <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="12726-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="xelement-functionality"></a><span data-ttu-id="12726-107">XElement işlevi</span><span class="sxs-lookup"><span data-stu-id="12726-107">XElement Functionality</span></span>  
 <span data-ttu-id="12726-108">Bu konuda tarafından sağlanan işlevleri açıklanmaktadır <xref:System.Xml.Linq.XElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="12726-108">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
### <a name="constructing-xml-trees"></a><span data-ttu-id="12726-109">XML ağaçları oluşturma</span><span class="sxs-lookup"><span data-stu-id="12726-109">Constructing XML Trees</span></span>  
 <span data-ttu-id="12726-110">Aşağıdakiler dahil olmak üzere çeşitli XML ağaçlarında oluşturabileceğiniz:</span><span class="sxs-lookup"><span data-stu-id="12726-110">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
-   <span data-ttu-id="12726-111">Kod XML ağacında oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12726-111">You can construct an XML tree in code.</span></span> <span data-ttu-id="12726-112">Daha fazla bilgi için bkz: [XML ağaçları oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="12726-112">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
-   <span data-ttu-id="12726-113">XML dahil olmak üzere çeşitli kaynaklardan ayrıştıramıyor bir <xref:System.IO.TextReader>, metin dosyaları veya bir Web adresi (URL).</span><span class="sxs-lookup"><span data-stu-id="12726-113">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="12726-114">Daha fazla bilgi için bkz: [XML Ayrıştırma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md).</span><span class="sxs-lookup"><span data-stu-id="12726-114">For more information, see [Parsing XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md).</span></span>  
  
-   <span data-ttu-id="12726-115">Kullanabileceğiniz bir <xref:System.Xml.XmlReader> ağaç doldurmak için.</span><span class="sxs-lookup"><span data-stu-id="12726-115">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="12726-116">Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="12726-116">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
-   <span data-ttu-id="12726-117">İçeriği yazabilen bir modül varsa bir <xref:System.Xml.XmlWriter>, kullanabileceğiniz <xref:System.Xml.Linq.XContainer.CreateWriter%2A> bir yazıcı oluşturmak, yazıcı modülü geçirmek ve yazılan içeriği kullanmak için yöntemi <xref:System.Xml.XmlWriter> XML ağaç doldurmak için.</span><span class="sxs-lookup"><span data-stu-id="12726-117">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="12726-118">Ancak, bir XML ağacı oluşturmak için en yaygın yolu şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="12726-118">However, the most common way to create an XML tree is as follows:</span></span>  
  
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
  
 <span data-ttu-id="12726-119">Bir XML ağacı oluşturmak için başka bir yaygın yöntem sonuçlarını kullanılmasına bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] aşağıdaki örnekte gösterildiği gibi bir XML ağacı doldurmak için sorgu:</span><span class="sxs-lookup"><span data-stu-id="12726-119">Another very common technique for creating an XML tree involves using the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to populate an XML tree, as shown in the following example:</span></span>  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where el.Value > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 <span data-ttu-id="12726-120">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="12726-120">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a><span data-ttu-id="12726-121">XML ağaçları seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="12726-121">Serializing XML Trees</span></span>  
 <span data-ttu-id="12726-122">XML ağaca serileştirebiliyorsa bir <xref:System.IO.File>, <xref:System.IO.TextWriter>, veya bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="12726-122">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="12726-123">Daha fazla bilgi için bkz: [seri hale getirme XML ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="12726-123">For more information, see [Serializing XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md).</span></span>  
  
### <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="12726-124">Eksen yöntemleriyle XML verilerini alma</span><span class="sxs-lookup"><span data-stu-id="12726-124">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="12726-125">Eksen yöntemleri öznitelikleri, alt öğe, alt öğeleri ve üst öğeleri almak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12726-125">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]<span data-ttu-id="12726-126">sorguları eksen yöntemlere çalışır ve aracılığıyla gidin ve bir XML ağacı işlemek için birden fazla esnek ve güçlü yollar sağlar.</span><span class="sxs-lookup"><span data-stu-id="12726-126"> queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="12726-127">Daha fazla bilgi için bkz: [LINQ-XML eksenleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md).</span><span class="sxs-lookup"><span data-stu-id="12726-127">For more information, see [LINQ to XML Axes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md).</span></span>  
  
### <a name="querying-xml-trees"></a><span data-ttu-id="12726-128">XML ağaçları sorgulama</span><span class="sxs-lookup"><span data-stu-id="12726-128">Querying XML Trees</span></span>  
 <span data-ttu-id="12726-129">Yazabileceğiniz [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] bir XML ağacından veri ayıklamak sorgular.</span><span class="sxs-lookup"><span data-stu-id="12726-129">You can write [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="12726-130">Daha fazla bilgi için bkz: [sorgulama XML ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="12726-130">For more information, see [Querying XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md).</span></span>  
  
### <a name="modifying-xml-trees"></a><span data-ttu-id="12726-131">XML ağaçlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="12726-131">Modifying XML Trees</span></span>  
 <span data-ttu-id="12726-132">Öğenin, içeriği veya özniteliklerini değiştirme dahil olmak üzere çeşitli değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12726-132">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="12726-133">Ayrıca, bir öğenin üst öğesinden kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12726-133">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="12726-134">Daha fazla bilgi için bkz: [XML ağaçlarını değiştirme (LINQ-XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="12726-134">For more information, see [Modifying XML Trees (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12726-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="12726-135">See Also</span></span>  
 [<span data-ttu-id="12726-136">LINQ-XML programlamaya genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12726-136">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
