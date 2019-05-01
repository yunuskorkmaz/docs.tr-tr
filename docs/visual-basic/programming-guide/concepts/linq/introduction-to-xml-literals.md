---
title: Görsel Basic2 XML değişmez değerlerine giriş
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: 68ba1e018d4ad9501532745a88090f0f756b5c17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61834281"
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a><span data-ttu-id="2a5b1-102">Visual Basic'de XML değişmez değerlerine giriş</span><span class="sxs-lookup"><span data-stu-id="2a5b1-102">Introduction to XML Literals in Visual Basic</span></span>
<span data-ttu-id="2a5b1-103">Bu bölümde, Visual Basic'te XML ağaçları oluşturma hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-103">This section provides information about creating XML trees in Visual Basic.</span></span>  
  
 <span data-ttu-id="2a5b1-104">LINQ sorguları sonuçları içerik olarak bir XML ağacı için kullanma hakkında daha fazla bilgi için bkz: [işlevsel oluşturma (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2a5b1-104">For information about using the results of LINQ queries as the content for an XML tree, see [Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="2a5b1-105">Visual Basic'de XML değişmez değerleri hakkında daha fazla bilgi için bkz. [XML Visual Basic'te LINQ genel bakış](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2a5b1-105">For more information on XML literals in Visual Basic, see [Overview of LINQ to XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="2a5b1-106">XML Ağaçları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2a5b1-106">Creating XML Trees</span></span>  
 <span data-ttu-id="2a5b1-107">Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Xml.Linq.XElement>, bu durumda `contacts`:</span><span class="sxs-lookup"><span data-stu-id="2a5b1-107">The following example shows how to create an <xref:System.Xml.Linq.XElement>, in this case `contacts`:</span></span>  
  
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
  
### <a name="creating-an-xelement-with-simple-content"></a><span data-ttu-id="2a5b1-108">Bir XElement ile basit içerik oluşturma</span><span class="sxs-lookup"><span data-stu-id="2a5b1-108">Creating an XElement with Simple Content</span></span>  
 <span data-ttu-id="2a5b1-109">Oluşturabileceğiniz bir <xref:System.Xml.Linq.XElement> basit içerik aşağıdaki gibi içerir:</span><span class="sxs-lookup"><span data-stu-id="2a5b1-109">You can create an <xref:System.Xml.Linq.XElement> that contains simple content, as follows:</span></span>  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)   
```  
  
 <span data-ttu-id="2a5b1-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="2a5b1-110">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a><span data-ttu-id="2a5b1-111">Boş bir öğe oluşturma</span><span class="sxs-lookup"><span data-stu-id="2a5b1-111">Creating an Empty Element</span></span>  
 <span data-ttu-id="2a5b1-112">Boş bir oluşturabilirsiniz <xref:System.Xml.Linq.XElement>gibi:</span><span class="sxs-lookup"><span data-stu-id="2a5b1-112">You can create an empty <xref:System.Xml.Linq.XElement>, as follows:</span></span>  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="2a5b1-113">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="2a5b1-113">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a><span data-ttu-id="2a5b1-114">Katıştırılmış ifadeler kullanma</span><span class="sxs-lookup"><span data-stu-id="2a5b1-114">Using Embedded Expressions</span></span>  
 <span data-ttu-id="2a5b1-115">XML değişmez değerlerini ve önemli bir özelliği, katıştırılmış ifadeler sağlarlar ' dir.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-115">An important feature of XML literals is that they allow embedded expressions.</span></span> <span data-ttu-id="2a5b1-116">Katıştırılmış ifadeler bir ifadeyi değerlendirir ve sonuçları XML ağacına eklemek etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-116">Embedded expressions enable you to evaluate an expression and insert the results of the expression into the XML tree.</span></span> <span data-ttu-id="2a5b1-117">İfade için bir tür olarak değerlendirilirse <xref:System.Xml.Linq.XElement>, öğenin ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-117">If the expression evaluates to a type of <xref:System.Xml.Linq.XElement>, an element is inserted into the tree.</span></span> <span data-ttu-id="2a5b1-118">İfade için bir tür olarak değerlendirilirse <xref:System.Xml.Linq.XAttribute>, bir öznitelik ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-118">If the expression evaluates to a type of <xref:System.Xml.Linq.XAttribute>, an attribute is inserted into the tree.</span></span> <span data-ttu-id="2a5b1-119">Yalnızca geçerli olduğu yerlerde ağacına öğeler ve öznitelikler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-119">You can insert elements and attributes into the tree only where they are valid.</span></span>  
  
 <span data-ttu-id="2a5b1-120">Tek bir ifade yalnızca katıştırılmış bir ifadeyi gidebilirsiniz dikkat edin önemlidir.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-120">It is important to note that only a single expression can go into an embedded expression.</span></span> <span data-ttu-id="2a5b1-121">Birden çok deyime katıştırılamıyor.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-121">You cannot embed multiple statements.</span></span> <span data-ttu-id="2a5b1-122">Bir ifade tek bir satır geçerse, satır devamı karakteri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-122">If an expression extends beyond a single line, you must use the line continuation character.</span></span>  
  
 <span data-ttu-id="2a5b1-123">Var olan düğümleri (öğeler dahil) ve yeni bir XML ağacı öznitelikleri ve var olan düğümleri zaten shapemap varsa eklemek için bir katıştırılmış deyim kullanırsanız, düğüm klonlanır.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-123">If you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree and if the existing nodes are already parented, the nodes are cloned.</span></span> <span data-ttu-id="2a5b1-124">Yeni kopyalanan düğümleri yeni XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-124">The newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="2a5b1-125">Var olan düğümleri arasındaki shapemap değil, düğümler yalnızca yeni XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-125">If the existing nodes are not parented, the nodes are simply attached to the new XML tree.</span></span> <span data-ttu-id="2a5b1-126">Bu konu Son örnekte bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-126">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="2a5b1-127">Aşağıdaki örnek, katıştırılmış bir ifade ağacına bir öğe eklemek için kullanır:</span><span class="sxs-lookup"><span data-stu-id="2a5b1-127">The following example uses an embedded expression to insert an element into the tree:</span></span>  
  
```vb  
xmlTree1 As XElement = _  
    <Root>  
        <Child>Contents</Child>  
    </Root>  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child> %>  
    </Root>  
Console.WriteLine(xmlTree2)  
```  
  
 <span data-ttu-id="2a5b1-128">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="2a5b1-128">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>Contents</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-content"></a><span data-ttu-id="2a5b1-129">İçerik için katıştırılmış ifadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="2a5b1-129">Using Embedded Expressions for Content</span></span>  
 <span data-ttu-id="2a5b1-130">Bir öğenin içeriğini sağlamak için katıştırılmış bir ifade kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2a5b1-130">You can use an embedded expression to supply the content of an element:</span></span>  
  
```vb  
Dim str As String  
str = "Some content"  
Dim root As XElement = <Root><%= str %></Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="2a5b1-131">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="2a5b1-131">This example produces the following output:</span></span>  
  
```xml  
<Root>Some content</Root>  
```  
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a><span data-ttu-id="2a5b1-132">Katıştırılmış bir ifadede bir LINQ Sorgu kullanma</span><span class="sxs-lookup"><span data-stu-id="2a5b1-132">Using a LINQ Query in an Embedded Expression</span></span>  
 <span data-ttu-id="2a5b1-133">Bir öğenin içeriğini bir LINQ sorgusunun sonuçları kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2a5b1-133">You can use the results of a LINQ query for the content of an element:</span></span>  
  
```vb  
Dim arr As Integer() = {1, 2, 3}  
  
Dim n As XElement = _  
    <Root>  
        <%= From i In arr Select <Child><%= i %></Child> %>  
    </Root>  
  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="2a5b1-134">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="2a5b1-134">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Child>3</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-node-names"></a><span data-ttu-id="2a5b1-135">Düğüm adları için katıştırılmış ifadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="2a5b1-135">Using Embedded Expressions for Node Names</span></span>  
 <span data-ttu-id="2a5b1-136">Katıştırılmış ifadeler, öznitelik adları, öznitelik değerleri, öğe adları ve değerleri hesaplamak için de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2a5b1-136">You can also use embedded expressions to calculate attribute names, attribute values, element names, and element values:</span></span>  
  
```vb  
Dim eleName As String = "ele"  
Dim attName As String = "att"  
Dim attValue As String = "aValue"  
Dim eleValue As String = "eValue"  
Dim n As XElement = _  
    <Root <%= attName %>=<%= attValue %>>  
        <<%= eleName %>>  
            <%= eleValue %>  
        </>  
    </Root>  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="2a5b1-137">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="2a5b1-137">This example produces the following output:</span></span>  
  
```xml  
<Root att="aValue">  
  <ele>eValue</ele>  
</Root>  
```  
  
### <a name="cloning-vs-attaching"></a><span data-ttu-id="2a5b1-138">Kopyalama ve Ekleme Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="2a5b1-138">Cloning vs. Attaching</span></span>  
 <span data-ttu-id="2a5b1-139">Var olan düğümleri arasındaki shapemap zaten varsa var olan düğümleri (öğeler dahil) ve öznitelikler yeni bir XML ağacına eklemek için bir katıştırılmış deyim kullanırsanız, daha önce belirtildiği gibi düğümler kopyalanır ve yeni kopyalanan düğümleri yeni XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-139">As mentioned earlier, if you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree, if the existing nodes are already parented, the nodes are cloned and the newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="2a5b1-140">Var olan düğümleri arasındaki shapemap değil, bunlar yalnızca yeni XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-140">If the existing nodes are not parented, they are simply attached to the new XML tree.</span></span>  
  
```vb  
' Create a tree with a child element.  
Dim xmlTree1 As XElement = _  
    <Root>  
        <Child1>1</Child1>  
    </Root>  
  
' Create an element that is not parented.  
Dim child2 As XElement = <Child2>2</Child2>  
  
' Create a tree and add Child1 and Child2 to it.  
Dim xmlTree2 As XElement = _  
    <Root>  
        <%= xmlTree1.<Child1>(0) %>  
        <%= child2 %>  
    </Root>  
  
' Compare Child1 identity.  
Console.WriteLine("Child1 was {0}", _  
    IIf(xmlTree1.Element("Child1") Is xmlTree2.Element("Child1"), _  
    "attached", "cloned"))  
  
' Compare Child2 identity.  
Console.WriteLine("Child2 was {0}", _  
    IIf(child2 Is xmlTree2.Element("Child2"), _  
    "attached", "cloned"))  
```  
  
 <span data-ttu-id="2a5b1-141">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="2a5b1-141">This example produces the following output:</span></span>  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a5b1-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a5b1-142">See also</span></span>

- [<span data-ttu-id="2a5b1-143">XML ağaçları (Visual Basic) oluşturma</span><span class="sxs-lookup"><span data-stu-id="2a5b1-143">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
