---
title: XML değişmez değerlerine Visual Basic2 giriş
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: bac0a4a297dcecce5465e5a1a1c02e4cbc9848a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646815"
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a><span data-ttu-id="ebc7b-102">Visual Basic'de XML değişmez değerleri giriş</span><span class="sxs-lookup"><span data-stu-id="ebc7b-102">Introduction to XML Literals in Visual Basic</span></span>
<span data-ttu-id="ebc7b-103">Bu bölümde, Visual Basic'te XML ağaçları oluşturma hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ebc7b-103">This section provides information about creating XML trees in Visual Basic.</span></span>  
  
 <span data-ttu-id="ebc7b-104">LINQ sorgularını sonuçlarını içerik için bir XML ağacı kullanma hakkında daha fazla bilgi için bkz: [işlevsel yapımı (LINQ-XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ebc7b-104">For information about using the results of LINQ queries as the content for an XML tree, see [Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="ebc7b-105">Visual Basic'de XML değişmez değerleri hakkında daha fazla bilgi için bkz: [XML Visual Basic'te LINQ genel bakış](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ebc7b-105">For more information on XML literals in Visual Basic, see [Overview of LINQ to XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="ebc7b-106">XML ağaçları oluşturma</span><span class="sxs-lookup"><span data-stu-id="ebc7b-106">Creating XML Trees</span></span>  
 <span data-ttu-id="ebc7b-107">Aşağıdaki örnekte nasıl oluşturulacağını gösterir bir <xref:System.Xml.Linq.XElement>, bu durumda `contacts`:</span><span class="sxs-lookup"><span data-stu-id="ebc7b-107">The following example shows how to create an <xref:System.Xml.Linq.XElement>, in this case `contacts`:</span></span>  
  
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
  
### <a name="creating-an-xelement-with-simple-content"></a><span data-ttu-id="ebc7b-108">Basit içerikle bir XElement oluşturma</span><span class="sxs-lookup"><span data-stu-id="ebc7b-108">Creating an XElement with Simple Content</span></span>  
 <span data-ttu-id="ebc7b-109">Oluşturabileceğiniz bir <xref:System.Xml.Linq.XElement> basit içerik, aşağıdaki gibi içeren:</span><span class="sxs-lookup"><span data-stu-id="ebc7b-109">You can create an <xref:System.Xml.Linq.XElement> that contains simple content, as follows:</span></span>  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)   
```  
  
 <span data-ttu-id="ebc7b-110">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="ebc7b-110">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a><span data-ttu-id="ebc7b-111">Boş bir öğe oluşturma</span><span class="sxs-lookup"><span data-stu-id="ebc7b-111">Creating an Empty Element</span></span>  
 <span data-ttu-id="ebc7b-112">Boş bir oluşturabileceğiniz <xref:System.Xml.Linq.XElement>aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="ebc7b-112">You can create an empty <xref:System.Xml.Linq.XElement>, as follows:</span></span>  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="ebc7b-113">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="ebc7b-113">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a><span data-ttu-id="ebc7b-114">Katıştırılmış ifadeler kullanma</span><span class="sxs-lookup"><span data-stu-id="ebc7b-114">Using Embedded Expressions</span></span>  
 <span data-ttu-id="ebc7b-115">Katıştırılmış ifadeler izin XML değişmez değerleri, önemli özelliklerinden biridir.</span><span class="sxs-lookup"><span data-stu-id="ebc7b-115">An important feature of XML literals is that they allow embedded expressions.</span></span> <span data-ttu-id="ebc7b-116">Katıştırılmış ifadeler bir ifade değerlendirme ve ifade sonuçlarını XML ağacına eklemek etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="ebc7b-116">Embedded expressions enable you to evaluate an expression and insert the results of the expression into the XML tree.</span></span> <span data-ttu-id="ebc7b-117">İfade türü için değerlendirilirse <xref:System.Xml.Linq.XElement>, bir öğenin ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="ebc7b-117">If the expression evaluates to a type of <xref:System.Xml.Linq.XElement>, an element is inserted into the tree.</span></span> <span data-ttu-id="ebc7b-118">İfade türü için değerlendirilirse <xref:System.Xml.Linq.XAttribute>, bir öznitelik ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="ebc7b-118">If the expression evaluates to a type of <xref:System.Xml.Linq.XAttribute>, an attribute is inserted into the tree.</span></span> <span data-ttu-id="ebc7b-119">Yalnızca geçerli olduğu yerlerde ağacına öğeleri ve özniteliklerinin ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ebc7b-119">You can insert elements and attributes into the tree only where they are valid.</span></span>  
  
 <span data-ttu-id="ebc7b-120">Yalnızca tek bir ifade katıştırılmış bir ifadeyi gidebilirsiniz dikkate almak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="ebc7b-120">It is important to note that only a single expression can go into an embedded expression.</span></span> <span data-ttu-id="ebc7b-121">Birden çok deyime eklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="ebc7b-121">You cannot embed multiple statements.</span></span> <span data-ttu-id="ebc7b-122">Bir ifade tek bir satır geçerse, satır devamlılığı karakteri kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ebc7b-122">If an expression extends beyond a single line, you must use the line continuation character.</span></span>  
  
 <span data-ttu-id="ebc7b-123">(Öğeleri dahil) varolan düğümleri ve yeni bir XML ağacı öznitelikleri ve varolan düğümleri zaten üst öğe varsa eklemek için katıştırılmış bir ifade kullanırsanız, düğüm kopyalandığı.</span><span class="sxs-lookup"><span data-stu-id="ebc7b-123">If you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree and if the existing nodes are already parented, the nodes are cloned.</span></span> <span data-ttu-id="ebc7b-124">Yeni kopyalanmış düğümleri yeni XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="ebc7b-124">The newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="ebc7b-125">Varolan düğümleri üst öğe değil, düğümleri yalnızca yeni bir XML ağacı bağlanmış.</span><span class="sxs-lookup"><span data-stu-id="ebc7b-125">If the existing nodes are not parented, the nodes are simply attached to the new XML tree.</span></span> <span data-ttu-id="ebc7b-126">Bu konudaki son örnek bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ebc7b-126">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="ebc7b-127">Aşağıdaki örnek katıştırılmış bir ifade ağacına bir öğe eklemek için kullanır:</span><span class="sxs-lookup"><span data-stu-id="ebc7b-127">The following example uses an embedded expression to insert an element into the tree:</span></span>  
  
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
  
 <span data-ttu-id="ebc7b-128">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="ebc7b-128">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>Contents</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-content"></a><span data-ttu-id="ebc7b-129">İçerik için katıştırılmış ifadeler kullanma</span><span class="sxs-lookup"><span data-stu-id="ebc7b-129">Using Embedded Expressions for Content</span></span>  
 <span data-ttu-id="ebc7b-130">Katıştırılmış bir ifade, bir öğenin içeriğini sağlamak için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ebc7b-130">You can use an embedded expression to supply the content of an element:</span></span>  
  
```vb  
Dim str As String  
str = "Some content"  
Dim root As XElement = <Root><%= str %></Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="ebc7b-131">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="ebc7b-131">This example produces the following output:</span></span>  
  
```xml  
<Root>Some content</Root>  
```  
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a><span data-ttu-id="ebc7b-132">Katıştırılmış bir ifadede bir LINQ Sorgu kullanma</span><span class="sxs-lookup"><span data-stu-id="ebc7b-132">Using a LINQ Query in an Embedded Expression</span></span>  
 <span data-ttu-id="ebc7b-133">Bir öğenin içeriğini için bir LINQ Sorgu sonucunu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ebc7b-133">You can use the results of a LINQ query for the content of an element:</span></span>  
  
```vb  
Dim arr As Integer() = {1, 2, 3}  
  
Dim n As XElement = _  
    <Root>  
        <%= From i In arr Select <Child><%= i %></Child> %>  
    </Root>  
  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="ebc7b-134">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="ebc7b-134">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Child>3</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-node-names"></a><span data-ttu-id="ebc7b-135">Katıştırılmış ifadeler için düğüm adlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="ebc7b-135">Using Embedded Expressions for Node Names</span></span>  
 <span data-ttu-id="ebc7b-136">Katıştırılmış ifadeler, öznitelik adları, öznitelik değerleri, öğe adları ve öğe değerleri hesaplamak için de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ebc7b-136">You can also use embedded expressions to calculate attribute names, attribute values, element names, and element values:</span></span>  
  
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
  
 <span data-ttu-id="ebc7b-137">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="ebc7b-137">This example produces the following output:</span></span>  
  
```xml  
<Root att="aValue">  
  <ele>eValue</ele>  
</Root>  
```  
  
### <a name="cloning-vs-attaching"></a><span data-ttu-id="ebc7b-138">Kopyalama vs. Ekleme</span><span class="sxs-lookup"><span data-stu-id="ebc7b-138">Cloning vs. Attaching</span></span>  
 <span data-ttu-id="ebc7b-139">Varolan düğümleri üst öğe zaten varsa yeni bir XML ağacına (öğeleri dahil) varolan düğümleri ve öznitelikler eklemek için katıştırılmış bir ifade kullanırsanız, daha önce belirtildiği gibi düğümleri kopyalandığı ve yeni kopyalanmış düğümleri yeni XML ağacına bağlı.</span><span class="sxs-lookup"><span data-stu-id="ebc7b-139">As mentioned earlier, if you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree, if the existing nodes are already parented, the nodes are cloned and the newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="ebc7b-140">Varolan düğümleri üst öğe değil, yalnızca yeni bir XML ağacı eklenir.</span><span class="sxs-lookup"><span data-stu-id="ebc7b-140">If the existing nodes are not parented, they are simply attached to the new XML tree.</span></span>  
  
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
  
 <span data-ttu-id="ebc7b-141">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="ebc7b-141">This example produces the following output:</span></span>  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="ebc7b-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ebc7b-142">See Also</span></span>  
 [<span data-ttu-id="ebc7b-143">Oluşturma XML ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ebc7b-143">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
