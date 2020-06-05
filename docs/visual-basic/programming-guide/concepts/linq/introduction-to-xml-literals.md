---
title: Visual Basic2 'de XML değişmez değerlerine giriş
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: 8b92d22727c50274d57a5e407a0ca42807de3a94
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397590"
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a><span data-ttu-id="3cb72-102">Visual Basic XML değişmez değerlerine giriş</span><span class="sxs-lookup"><span data-stu-id="3cb72-102">Introduction to XML Literals in Visual Basic</span></span>
<span data-ttu-id="3cb72-103">Bu bölüm, Visual Basic XML ağaçları oluşturma hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3cb72-103">This section provides information about creating XML trees in Visual Basic.</span></span>  
  
 <span data-ttu-id="3cb72-104">XML ağacının içeriği olarak LINQ sorgularının sonuçlarını kullanma hakkında daha fazla bilgi için bkz. [Işlevsel oluşturma (LINQ to XML) (Visual Basic)](functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3cb72-104">For information about using the results of LINQ queries as the content for an XML tree, see [Functional Construction (LINQ to XML) (Visual Basic)](functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="3cb72-105">Visual Basic XML değişmez değerleri hakkında daha fazla bilgi için bkz. [Visual Basic LINQ to XML genel bakış](../../language-features/xml/overview-of-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3cb72-105">For more information on XML literals in Visual Basic, see [Overview of LINQ to XML in Visual Basic](../../language-features/xml/overview-of-linq-to-xml.md).</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="3cb72-106">XML Ağaçları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3cb72-106">Creating XML Trees</span></span>  
 <span data-ttu-id="3cb72-107">Aşağıdaki örnek, bu durumda nasıl oluşturulacağını gösterir <xref:System.Xml.Linq.XElement> `contacts` :</span><span class="sxs-lookup"><span data-stu-id="3cb72-107">The following example shows how to create an <xref:System.Xml.Linq.XElement>, in this case `contacts`:</span></span>  
  
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
  
### <a name="creating-an-xelement-with-simple-content"></a><span data-ttu-id="3cb72-108">Basit Içerikle XElement oluşturma</span><span class="sxs-lookup"><span data-stu-id="3cb72-108">Creating an XElement with Simple Content</span></span>  
 <span data-ttu-id="3cb72-109"><xref:System.Xml.Linq.XElement>Basit içerik içeren bir oluşturmak için aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="3cb72-109">You can create an <xref:System.Xml.Linq.XElement> that contains simple content, as follows:</span></span>  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)
```  
  
 <span data-ttu-id="3cb72-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="3cb72-110">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a><span data-ttu-id="3cb72-111">Boş bir öğe oluşturma</span><span class="sxs-lookup"><span data-stu-id="3cb72-111">Creating an Empty Element</span></span>  
 <span data-ttu-id="3cb72-112">Şu şekilde boş bir oluşturabilirsiniz <xref:System.Xml.Linq.XElement> :</span><span class="sxs-lookup"><span data-stu-id="3cb72-112">You can create an empty <xref:System.Xml.Linq.XElement>, as follows:</span></span>  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="3cb72-113">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="3cb72-113">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a><span data-ttu-id="3cb72-114">Katıştırılmış Ifadeler kullanma</span><span class="sxs-lookup"><span data-stu-id="3cb72-114">Using Embedded Expressions</span></span>  
 <span data-ttu-id="3cb72-115">XML sabit değerlerinin önemli bir özelliği, katıştırılmış ifadelere izin verleridir.</span><span class="sxs-lookup"><span data-stu-id="3cb72-115">An important feature of XML literals is that they allow embedded expressions.</span></span> <span data-ttu-id="3cb72-116">Katıştırılmış ifadeler bir ifadeyi değerlendirmenizi ve ifadenin sonuçlarını XML ağacına eklemeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3cb72-116">Embedded expressions enable you to evaluate an expression and insert the results of the expression into the XML tree.</span></span> <span data-ttu-id="3cb72-117">İfade bir türü olarak değerlendirilirse <xref:System.Xml.Linq.XElement> , ağaca bir öğe eklenir.</span><span class="sxs-lookup"><span data-stu-id="3cb72-117">If the expression evaluates to a type of <xref:System.Xml.Linq.XElement>, an element is inserted into the tree.</span></span> <span data-ttu-id="3cb72-118">İfade bir türü olarak değerlendirilirse <xref:System.Xml.Linq.XAttribute> , ağaca bir öznitelik eklenir.</span><span class="sxs-lookup"><span data-stu-id="3cb72-118">If the expression evaluates to a type of <xref:System.Xml.Linq.XAttribute>, an attribute is inserted into the tree.</span></span> <span data-ttu-id="3cb72-119">Öğeleri ve öznitelikleri yalnızca geçerli oldukları yerde ağaca ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cb72-119">You can insert elements and attributes into the tree only where they are valid.</span></span>  
  
 <span data-ttu-id="3cb72-120">Yalnızca tek bir ifadenin katıştırılmış ifadeye gidebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3cb72-120">It is important to note that only a single expression can go into an embedded expression.</span></span> <span data-ttu-id="3cb72-121">Birden çok deyimi katıştıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="3cb72-121">You cannot embed multiple statements.</span></span> <span data-ttu-id="3cb72-122">Bir ifade tek bir çizgiyi aşarsa, satır devamlılık karakterini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3cb72-122">If an expression extends beyond a single line, you must use the line continuation character.</span></span>  
  
 <span data-ttu-id="3cb72-123">Varolan düğümleri (öğeler dahil) ve özniteliklerini yeni bir XML ağacına eklemek için katıştırılmış bir ifade kullanırsanız ve mevcut düğümlerin zaten üst öğesi varsa, düğümler klonlanır.</span><span class="sxs-lookup"><span data-stu-id="3cb72-123">If you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree and if the existing nodes are already parented, the nodes are cloned.</span></span> <span data-ttu-id="3cb72-124">Yeni kopyalanan düğümler yeni XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="3cb72-124">The newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="3cb72-125">Mevcut düğümler üst öğe değilse, düğümler yalnızca yeni XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="3cb72-125">If the existing nodes are not parented, the nodes are simply attached to the new XML tree.</span></span> <span data-ttu-id="3cb72-126">Bu konudaki son örnekte bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3cb72-126">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="3cb72-127">Aşağıdaki örnek, ağaca bir öğe eklemek için gömülü bir ifade kullanır:</span><span class="sxs-lookup"><span data-stu-id="3cb72-127">The following example uses an embedded expression to insert an element into the tree:</span></span>  
  
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
  
 <span data-ttu-id="3cb72-128">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="3cb72-128">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>Contents</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-content"></a><span data-ttu-id="3cb72-129">Içerik için katıştırılmış Ifadeler kullanma</span><span class="sxs-lookup"><span data-stu-id="3cb72-129">Using Embedded Expressions for Content</span></span>  
 <span data-ttu-id="3cb72-130">Bir öğenin içeriğini sağlamak için gömülü bir ifade kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3cb72-130">You can use an embedded expression to supply the content of an element:</span></span>  
  
```vb  
Dim str As String  
str = "Some content"  
Dim root As XElement = <Root><%= str %></Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="3cb72-131">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="3cb72-131">This example produces the following output:</span></span>  
  
```xml  
<Root>Some content</Root>  
```  
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a><span data-ttu-id="3cb72-132">Katıştırılmış Ifadede LINQ sorgusu kullanma</span><span class="sxs-lookup"><span data-stu-id="3cb72-132">Using a LINQ Query in an Embedded Expression</span></span>  
 <span data-ttu-id="3cb72-133">Bir öğenin içeriği için LINQ sorgusunun sonuçlarını kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3cb72-133">You can use the results of a LINQ query for the content of an element:</span></span>  
  
```vb  
Dim arr As Integer() = {1, 2, 3}  
  
Dim n As XElement = _  
    <Root>  
        <%= From i In arr Select <Child><%= i %></Child> %>  
    </Root>  
  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="3cb72-134">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="3cb72-134">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Child>3</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-node-names"></a><span data-ttu-id="3cb72-135">Düğüm adları için katıştırılmış Ifadeler kullanma</span><span class="sxs-lookup"><span data-stu-id="3cb72-135">Using Embedded Expressions for Node Names</span></span>  
 <span data-ttu-id="3cb72-136">Öznitelik adlarını, öznitelik değerlerini, öğe adlarını ve öğe değerlerini hesaplamak için katıştırılmış ifadeler de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3cb72-136">You can also use embedded expressions to calculate attribute names, attribute values, element names, and element values:</span></span>  
  
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
  
 <span data-ttu-id="3cb72-137">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="3cb72-137">This example produces the following output:</span></span>  
  
```xml  
<Root att="aValue">  
  <ele>eValue</ele>  
</Root>  
```  
  
### <a name="cloning-vs-attaching"></a><span data-ttu-id="3cb72-138">Kopyalama ve Ekleme Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="3cb72-138">Cloning vs. Attaching</span></span>  
 <span data-ttu-id="3cb72-139">Daha önce belirtildiği gibi, var olan düğümleri (öğeler dahil) ve özniteliklerini yeni bir XML ağacına eklemek için katıştırılmış bir ifade kullanırsanız, varolan düğümlerin zaten üst öğesi varsa, düğümler kopyalanır ve yeni kopyalanan düğümler yeni XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="3cb72-139">As mentioned earlier, if you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree, if the existing nodes are already parented, the nodes are cloned and the newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="3cb72-140">Mevcut düğümler üst öğe değilse, bunlar yalnızca yeni XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="3cb72-140">If the existing nodes are not parented, they are simply attached to the new XML tree.</span></span>  
  
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
  
 <span data-ttu-id="3cb72-141">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="3cb72-141">This example produces the following output:</span></span>  
  
```console  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="3cb72-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3cb72-142">See also</span></span>

- [<span data-ttu-id="3cb72-143">XML ağaçları oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3cb72-143">Creating XML Trees (Visual Basic)</span></span>](creating-xml-trees.md)
