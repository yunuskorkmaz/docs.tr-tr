---
title: XElement sınıfına genel bakış (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
ms.openlocfilehash: 321f812176fc129e0922878c1d071621c32ccf57
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199348"
---
# <a name="xelement-class-overview-visual-basic"></a><span data-ttu-id="756f7-102">XElement sınıfına genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="756f7-102">XElement Class Overview (Visual Basic)</span></span>
<span data-ttu-id="756f7-103"><xref:System.Xml.Linq.XElement> Sınıfın temel sınıflarında biridir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="756f7-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="756f7-104">Bu, bir XML öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="756f7-104">It represents an XML element.</span></span> <span data-ttu-id="756f7-105">Bu sınıf, öğeleri oluşturmak için kullanabilirsiniz; öğenin içeriğini değiştirmek; ekleme, değiştirme veya alt öğeleri silin; öznitelik, bir öğeye ekleyin; ya da metin biçiminde bir öğenin içeriği seri hale getirme.</span><span class="sxs-lookup"><span data-stu-id="756f7-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="756f7-106">İçindeki diğer sınıflarla çalışabilirler <xref:System.Xml?displayProperty=nameWithType>, gibi <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, ve <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="756f7-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="xelement-functionality"></a><span data-ttu-id="756f7-107">XElement işlevi</span><span class="sxs-lookup"><span data-stu-id="756f7-107">XElement Functionality</span></span>  
 <span data-ttu-id="756f7-108">Bu konu tarafından sağlanan işlevselliği açıklar <xref:System.Xml.Linq.XElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="756f7-108">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
### <a name="constructing-xml-trees"></a><span data-ttu-id="756f7-109">XML ağaçları oluşturma</span><span class="sxs-lookup"><span data-stu-id="756f7-109">Constructing XML Trees</span></span>  
 <span data-ttu-id="756f7-110">XML ağaçlarını aşağıdakiler dahil olmak üzere çeşitli oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="756f7-110">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
-   <span data-ttu-id="756f7-111">Bir XML ağacı kod oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="756f7-111">You can construct an XML tree in code.</span></span> <span data-ttu-id="756f7-112">Daha fazla bilgi için [XML ağaçları oluşturma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="756f7-112">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
-   <span data-ttu-id="756f7-113">XML dahil olmak üzere çeşitli kaynaklardan ayrıştırabilirsiniz bir <xref:System.IO.TextReader>, metin dosyaları veya bir Web adresi (URL).</span><span class="sxs-lookup"><span data-stu-id="756f7-113">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="756f7-114">Daha fazla bilgi için [XML Ayrıştırma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md).</span><span class="sxs-lookup"><span data-stu-id="756f7-114">For more information, see [Parsing XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md).</span></span>  
  
-   <span data-ttu-id="756f7-115">Kullanabileceğiniz bir <xref:System.Xml.XmlReader> ağacını doldurmak için.</span><span class="sxs-lookup"><span data-stu-id="756f7-115">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="756f7-116">Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="756f7-116">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
-   <span data-ttu-id="756f7-117">İçeriği yazabilen bir modül varsa bir <xref:System.Xml.XmlWriter>, kullanabileceğiniz <xref:System.Xml.Linq.XContainer.CreateWriter%2A> bir yazıcısı oluşturmak, yazıcı modülü geçirin ve ardından yazılan içeriği yöntemi <xref:System.Xml.XmlWriter> XML ağacını doldurmak için.</span><span class="sxs-lookup"><span data-stu-id="756f7-117">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="756f7-118">Ancak, bir XML ağacı oluşturmak için en yaygın yolu şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="756f7-118">However, the most common way to create an XML tree is as follows:</span></span>  
  
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
  
 <span data-ttu-id="756f7-119">Bir XML ağacı oluşturmak için başka bir yaygın yöntem sonuçlarını kullanılmasına bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] aşağıdaki örnekte gösterildiği gibi bir XML ağacı doldurma için sorgu:</span><span class="sxs-lookup"><span data-stu-id="756f7-119">Another very common technique for creating an XML tree involves using the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to populate an XML tree, as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="756f7-120">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="756f7-120">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a><span data-ttu-id="756f7-121">XML ağaçlarını serileştirme</span><span class="sxs-lookup"><span data-stu-id="756f7-121">Serializing XML Trees</span></span>  
 <span data-ttu-id="756f7-122">XML ağacına serileştirebilen bir <xref:System.IO.File>, <xref:System.IO.TextWriter>, veya bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="756f7-122">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="756f7-123">Daha fazla bilgi için [XML ağaçlarını serileştirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="756f7-123">For more information, see [Serializing XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md).</span></span>  
  
### <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="756f7-124">Eksen yöntemleri aracılığıyla XML verilerini alma</span><span class="sxs-lookup"><span data-stu-id="756f7-124">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="756f7-125">Eksen yöntemleri, öznitelikler, alt öğeleri, alt ve üst öğeleri almak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="756f7-125">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]<span data-ttu-id="756f7-126"> sorgular, eksen yöntemleri üzerinde çalışır ve gezinmek ve bir XML ağacı işlemek için çeşitli esnek ve güçlü yollarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="756f7-126"> queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="756f7-127">Daha fazla bilgi için [LINQ to XML eksenleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md).</span><span class="sxs-lookup"><span data-stu-id="756f7-127">For more information, see [LINQ to XML Axes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md).</span></span>  
  
### <a name="querying-xml-trees"></a><span data-ttu-id="756f7-128">XML ağaçlarını sorgulama</span><span class="sxs-lookup"><span data-stu-id="756f7-128">Querying XML Trees</span></span>  
 <span data-ttu-id="756f7-129">Yazabileceğiniz [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] XML ağacından verileri ayıklamak sorgular.</span><span class="sxs-lookup"><span data-stu-id="756f7-129">You can write [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="756f7-130">Daha fazla bilgi için [XML ağaçlarını sorgulama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="756f7-130">For more information, see [Querying XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md).</span></span>  
  
### <a name="modifying-xml-trees"></a><span data-ttu-id="756f7-131">XML ağaçlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="756f7-131">Modifying XML Trees</span></span>  
 <span data-ttu-id="756f7-132">Bir öğeyi kendi içerik veya öznitelikleri değiştirme dahil olmak üzere çeşitli değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="756f7-132">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="756f7-133">Ayrıca, bir öğenin üst öğesinden kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="756f7-133">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="756f7-134">Daha fazla bilgi için [XML ağaçlarını değiştirme (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="756f7-134">For more information, see [Modifying XML Trees (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="756f7-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="756f7-135">See Also</span></span>  
 [<span data-ttu-id="756f7-136">LINQ to XML programlamaya genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="756f7-136">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
