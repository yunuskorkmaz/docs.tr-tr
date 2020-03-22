---
title: Visual Basic2'de XML Literals'e Giriş2
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: 9f5c54574e51c537d9ea58d307afda10736d0d88
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266956"
---
# <a name="introduction-to-xml-literals-in-visual-basic"></a><span data-ttu-id="89d7a-102">Visual Basic'te XML Literals'e Giriş</span><span class="sxs-lookup"><span data-stu-id="89d7a-102">Introduction to XML Literals in Visual Basic</span></span>
<span data-ttu-id="89d7a-103">Bu bölümde Visual Basic'te XML ağaçları oluşturma hakkında bilgi verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="89d7a-103">This section provides information about creating XML trees in Visual Basic.</span></span>  
  
 <span data-ttu-id="89d7a-104">BIR XML ağacının içeriği olarak LINQ sorgularının sonuçlarını kullanma hakkında bilgi [için](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="89d7a-104">For information about using the results of LINQ queries as the content for an XML tree, see [Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="89d7a-105">Visual Basic'teki XML literalleri hakkında daha fazla bilgi için [Visual Basic'te LINQ'dan XML'e Genel Bakış bölümüne](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="89d7a-105">For more information on XML literals in Visual Basic, see [Overview of LINQ to XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md).</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="89d7a-106">XML Ağaçları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="89d7a-106">Creating XML Trees</span></span>  
 <span data-ttu-id="89d7a-107">Aşağıdaki örnek, bu durumda <xref:System.Xml.Linq.XElement> `contacts`nasıl oluşturulacak gösterir:</span><span class="sxs-lookup"><span data-stu-id="89d7a-107">The following example shows how to create an <xref:System.Xml.Linq.XElement>, in this case `contacts`:</span></span>  
  
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
  
### <a name="creating-an-xelement-with-simple-content"></a><span data-ttu-id="89d7a-108">Basit İçerikli XElement Oluşturma</span><span class="sxs-lookup"><span data-stu-id="89d7a-108">Creating an XElement with Simple Content</span></span>  
 <span data-ttu-id="89d7a-109">Aşağıdaki gibi <xref:System.Xml.Linq.XElement> basit içerik içeren bir oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="89d7a-109">You can create an <xref:System.Xml.Linq.XElement> that contains simple content, as follows:</span></span>  
  
```vb  
Dim n as XElement = <Customer>Adventure Works</Customer>  
Console.WriteLine(n)
```  
  
 <span data-ttu-id="89d7a-110">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="89d7a-110">This example produces the following output:</span></span>  
  
```xml  
<Customer>Adventure Works</Customer>  
```  
  
### <a name="creating-an-empty-element"></a><span data-ttu-id="89d7a-111">Boş Öğe Oluşturma</span><span class="sxs-lookup"><span data-stu-id="89d7a-111">Creating an Empty Element</span></span>  
 <span data-ttu-id="89d7a-112">Aşağıdaki gibi boş <xref:System.Xml.Linq.XElement>bir oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="89d7a-112">You can create an empty <xref:System.Xml.Linq.XElement>, as follows:</span></span>  
  
```vb  
Dim n As XElement = <Customer/>  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="89d7a-113">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="89d7a-113">This example produces the following output:</span></span>  
  
```xml  
<Customer />  
```  
  
### <a name="using-embedded-expressions"></a><span data-ttu-id="89d7a-114">Gömülü İfadeleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="89d7a-114">Using Embedded Expressions</span></span>  
 <span data-ttu-id="89d7a-115">XML literals önemli bir özelliği gömülü ifadeler izin olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="89d7a-115">An important feature of XML literals is that they allow embedded expressions.</span></span> <span data-ttu-id="89d7a-116">Katıştılmış ifadeler, bir ifadeyi değerlendirmenize ve ifadenin sonuçlarını XML ağacına eklemenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="89d7a-116">Embedded expressions enable you to evaluate an expression and insert the results of the expression into the XML tree.</span></span> <span data-ttu-id="89d7a-117">İfade bir <xref:System.Xml.Linq.XElement>tür, öğe ağaca eklenir değerlendirirse.</span><span class="sxs-lookup"><span data-stu-id="89d7a-117">If the expression evaluates to a type of <xref:System.Xml.Linq.XElement>, an element is inserted into the tree.</span></span> <span data-ttu-id="89d7a-118">İfade bir <xref:System.Xml.Linq.XAttribute>tür, bir öznitelik ağaca eklenir değerlendirirse.</span><span class="sxs-lookup"><span data-stu-id="89d7a-118">If the expression evaluates to a type of <xref:System.Xml.Linq.XAttribute>, an attribute is inserted into the tree.</span></span> <span data-ttu-id="89d7a-119">Öğeleri ve öznitelikleri yalnızca geçerli oldukları ağaca ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89d7a-119">You can insert elements and attributes into the tree only where they are valid.</span></span>  
  
 <span data-ttu-id="89d7a-120">Yalnızca tek bir ifadenin katıştırılmış bir ifadeye girebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="89d7a-120">It is important to note that only a single expression can go into an embedded expression.</span></span> <span data-ttu-id="89d7a-121">Birden çok deyim katıştıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="89d7a-121">You cannot embed multiple statements.</span></span> <span data-ttu-id="89d7a-122">Bir ifade tek bir satırın ötesine uzanıyorsa, satır devam karakterini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="89d7a-122">If an expression extends beyond a single line, you must use the line continuation character.</span></span>  
  
 <span data-ttu-id="89d7a-123">Yeni bir XML ağacına varolan düğümleri (öğeler dahil) ve öznitelikleri eklemek için katıştırılmış bir ifade kullanırsanız ve varolan düğümler zaten ebeveynlik varsa, düğümler klonlanır.</span><span class="sxs-lookup"><span data-stu-id="89d7a-123">If you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree and if the existing nodes are already parented, the nodes are cloned.</span></span> <span data-ttu-id="89d7a-124">Yeni klonlanan düğümler yeni XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="89d7a-124">The newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="89d7a-125">Varolan düğümler ebeveynli değilse, düğümler yalnızca yeni XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="89d7a-125">If the existing nodes are not parented, the nodes are simply attached to the new XML tree.</span></span> <span data-ttu-id="89d7a-126">Bu konudaki son örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="89d7a-126">The last example in this topic demonstrates this.</span></span>  
  
 <span data-ttu-id="89d7a-127">Aşağıdaki örnek, ağaca bir öğe eklemek için katışlı bir ifade kullanır:</span><span class="sxs-lookup"><span data-stu-id="89d7a-127">The following example uses an embedded expression to insert an element into the tree:</span></span>  
  
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
  
 <span data-ttu-id="89d7a-128">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="89d7a-128">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>Contents</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-content"></a><span data-ttu-id="89d7a-129">İçerik için Gömülü İfadeleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="89d7a-129">Using Embedded Expressions for Content</span></span>  
 <span data-ttu-id="89d7a-130">Bir öğenin içeriğini sağlamak için katıştırılmış bir ifade kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="89d7a-130">You can use an embedded expression to supply the content of an element:</span></span>  
  
```vb  
Dim str As String  
str = "Some content"  
Dim root As XElement = <Root><%= str %></Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="89d7a-131">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="89d7a-131">This example produces the following output:</span></span>  
  
```xml  
<Root>Some content</Root>  
```  
  
### <a name="using-a-linq-query-in-an-embedded-expression"></a><span data-ttu-id="89d7a-132">Gömülü İfadede LINQ Sorgusu Kullanma</span><span class="sxs-lookup"><span data-stu-id="89d7a-132">Using a LINQ Query in an Embedded Expression</span></span>  
 <span data-ttu-id="89d7a-133">Bir öğenin içeriği için LINQ sorgusunun sonuçlarını kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="89d7a-133">You can use the results of a LINQ query for the content of an element:</span></span>  
  
```vb  
Dim arr As Integer() = {1, 2, 3}  
  
Dim n As XElement = _  
    <Root>  
        <%= From i In arr Select <Child><%= i %></Child> %>  
    </Root>  
  
Console.WriteLine(n)  
```  
  
 <span data-ttu-id="89d7a-134">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="89d7a-134">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Child>3</Child>  
</Root>  
```  
  
### <a name="using-embedded-expressions-for-node-names"></a><span data-ttu-id="89d7a-135">Düğüm Adları için Gömülü İfadeleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="89d7a-135">Using Embedded Expressions for Node Names</span></span>  
 <span data-ttu-id="89d7a-136">Öznitelik adlarını, öznitelik değerlerini, öğe adlarını ve öğe değerlerini hesaplamak için közlediğiniz ifadeleri de kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="89d7a-136">You can also use embedded expressions to calculate attribute names, attribute values, element names, and element values:</span></span>  
  
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
  
 <span data-ttu-id="89d7a-137">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="89d7a-137">This example produces the following output:</span></span>  
  
```xml  
<Root att="aValue">  
  <ele>eValue</ele>  
</Root>  
```  
  
### <a name="cloning-vs-attaching"></a><span data-ttu-id="89d7a-138">Klonlama ve Takma</span><span class="sxs-lookup"><span data-stu-id="89d7a-138">Cloning vs. Attaching</span></span>  
 <span data-ttu-id="89d7a-139">Daha önce de belirtildiği gibi, varolan düğümleri (öğeler dahil) ve yeni bir XML ağacına öznitelikleri eklemek için katıştırılmış bir ifade kullanırsanız, varolan düğümler zaten ebeveynlik varsa, düğümler klonlanır ve yeni klonlanan düğümler yeni XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="89d7a-139">As mentioned earlier, if you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree, if the existing nodes are already parented, the nodes are cloned and the newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="89d7a-140">Varolan düğümler ebeveynli değilse, yalnızca yeni XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="89d7a-140">If the existing nodes are not parented, they are simply attached to the new XML tree.</span></span>  
  
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
  
 <span data-ttu-id="89d7a-141">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="89d7a-141">This example produces the following output:</span></span>  
  
```console  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="89d7a-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89d7a-142">See also</span></span>

- [<span data-ttu-id="89d7a-143">XML Ağaçları Oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89d7a-143">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
