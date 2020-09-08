---
title: Visual Basic XML sabit değerleri LINQ to XML
description: XML sabit değerlerini ve katıştırılmış ifadeleri kullanarak Visual Basic bir XML ağacı oluşturabilirsiniz. Katıştırılmış ifadeler bir ifadeyi değerlendirmenizi ve ifadenin sonuçlarını XML ağacına eklemeyi sağlar.
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: e3b1213672a6a7ddd71fcc38b4502108a6f49881
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553206"
---
# <a name="xml-literals-in-visual-basic-linq-to-xml"></a><span data-ttu-id="c54a4-104">Visual Basic XML değişmez değerleri (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="c54a4-104">XML Literals in Visual Basic (LINQ to XML)</span></span>

<span data-ttu-id="c54a4-105">Bu makalede, XML sabit değerleri ve katıştırılmış ifadeler kullanılarak Visual Basic XML ağaçları oluşturma hakkında bilgi sağlanır.</span><span class="sxs-lookup"><span data-stu-id="c54a4-105">This article provides information about creating XML trees in Visual Basic using XML literals and embedded expressions.</span></span>

## <a name="example-use-xml-literals-to-create-an-xml-tree"></a><span data-ttu-id="c54a4-106">Örnek: XML ağacı oluşturmak için XML değişmez değerlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="c54a4-106">Example: Use XML literals to create an XML tree</span></span>

<span data-ttu-id="c54a4-107">Aşağıdaki örnek, <xref:System.Xml.Linq.XElement> Bu örnekte `contacts` XML değişmez değerleri ile nasıl oluşturulacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="c54a4-107">The following example shows how to create an <xref:System.Xml.Linq.XElement>, in this case `contacts`, with XML literals:</span></span>

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

## <a name="example-use-xml-literals-to-create-an-xelement-with-simple-content"></a><span data-ttu-id="c54a4-108">Örnek: basit içerikli bir XElement oluşturmak için XML değişmez değerlerini kullanın</span><span class="sxs-lookup"><span data-stu-id="c54a4-108">Example: Use XML literals to create an XElement with simple content</span></span>

<span data-ttu-id="c54a4-109"><xref:System.Xml.Linq.XElement>Basit içerik içeren bir oluşturmak için aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="c54a4-109">You can create an <xref:System.Xml.Linq.XElement> that contains simple content, as follows:</span></span>

```vb
Dim n as XElement = <Customer>Adventure Works</Customer>
Console.WriteLine(n)
```

<span data-ttu-id="c54a4-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="c54a4-110">This example produces the following output:</span></span>

```xml
<Customer>Adventure Works</Customer>
```

## <a name="example-use-an-xml-literal-to-create-an-empty-element"></a><span data-ttu-id="c54a4-111">Örnek: boş bir öğe oluşturmak için bir XML sabit değeri kullanın</span><span class="sxs-lookup"><span data-stu-id="c54a4-111">Example: Use an XML literal to create an empty element</span></span>

<span data-ttu-id="c54a4-112">Şu şekilde boş bir oluşturabilirsiniz <xref:System.Xml.Linq.XElement> :</span><span class="sxs-lookup"><span data-stu-id="c54a4-112">You can create an empty <xref:System.Xml.Linq.XElement>, as follows:</span></span>

```vb
Dim n As XElement = <Customer/>
Console.WriteLine(n)
```

<span data-ttu-id="c54a4-113">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="c54a4-113">This example produces the following output:</span></span>

```xml
<Customer />
```

## <a name="use-embedded-expressions-to-create-content"></a><span data-ttu-id="c54a4-114">İçerik oluşturmak için katıştırılmış ifadeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="c54a4-114">Use embedded expressions to create content</span></span>

<span data-ttu-id="c54a4-115">XML sabit değerlerinin önemli bir özelliği, katıştırılmış ifadelere izin verleridir.</span><span class="sxs-lookup"><span data-stu-id="c54a4-115">An important feature of XML literals is that they allow embedded expressions.</span></span> <span data-ttu-id="c54a4-116">Katıştırılmış ifadeler bir ifadeyi değerlendirmenizi ve ifadenin sonuçlarını XML ağacına eklemeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c54a4-116">Embedded expressions enable you to evaluate an expression and insert the results of the expression into the XML tree.</span></span> <span data-ttu-id="c54a4-117">İfade bir türü olarak değerlendirilirse <xref:System.Xml.Linq.XElement> , ağaca bir öğe eklenir.</span><span class="sxs-lookup"><span data-stu-id="c54a4-117">If the expression evaluates to a type of <xref:System.Xml.Linq.XElement>, an element is inserted into the tree.</span></span> <span data-ttu-id="c54a4-118">İfade bir türü olarak değerlendirilirse <xref:System.Xml.Linq.XAttribute> , ağaca bir öznitelik eklenir.</span><span class="sxs-lookup"><span data-stu-id="c54a4-118">If the expression evaluates to a type of <xref:System.Xml.Linq.XAttribute>, an attribute is inserted into the tree.</span></span> <span data-ttu-id="c54a4-119">Öğeleri ve öznitelikleri yalnızca geçerli oldukları yerde ağaca ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c54a4-119">You can insert elements and attributes into the tree only where they're valid.</span></span>

<span data-ttu-id="c54a4-120">yalnızca tek bir ifadenin katıştırılmış ifadeye gidebileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c54a4-120">it's important to note that only a single expression can go into an embedded expression.</span></span> <span data-ttu-id="c54a4-121">Birden çok deyimi katıştıramazsınız.</span><span class="sxs-lookup"><span data-stu-id="c54a4-121">You can't embed multiple statements.</span></span> <span data-ttu-id="c54a4-122">Bir ifade tek bir çizgiyi aşarsa, satır devamlılık karakterini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c54a4-122">If an expression extends beyond a single line, you must use the line continuation character.</span></span>

<span data-ttu-id="c54a4-123">Varolan düğümleri (öğeler dahil) ve özniteliklerini yeni bir XML ağacına eklemek için katıştırılmış bir ifade kullanırsanız ve mevcut düğümlerin zaten üst öğesi varsa, düğümler klonlanır.</span><span class="sxs-lookup"><span data-stu-id="c54a4-123">If you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree and if the existing nodes are already parented, the nodes are cloned.</span></span> <span data-ttu-id="c54a4-124">Yeni kopyalanan düğümler yeni XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="c54a4-124">The newly cloned nodes are attached to the new XML tree.</span></span> <span data-ttu-id="c54a4-125">Mevcut düğümlerin üst öğesi yoksa, düğümler yalnızca yeni XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="c54a4-125">If the existing nodes aren't parented, the nodes are simply attached to the new XML tree.</span></span> <span data-ttu-id="c54a4-126">Bu makaledeki Son örnekte bu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c54a4-126">The last example in this article demonstrates this.</span></span>

## <a name="example-use-an-embedded-expression-to-insert-an-element"></a><span data-ttu-id="c54a4-127">Örnek: bir öğe eklemek için gömülü bir ifade kullanın</span><span class="sxs-lookup"><span data-stu-id="c54a4-127">Example: Use an embedded expression to insert an element</span></span>

<span data-ttu-id="c54a4-128">Aşağıdaki örnek, ağaca bir öğe eklemek için gömülü bir ifade kullanır:</span><span class="sxs-lookup"><span data-stu-id="c54a4-128">The following example uses an embedded expression to insert an element into the tree:</span></span>

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

<span data-ttu-id="c54a4-129">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="c54a4-129">This example produces the following output:</span></span>

```xml
<Root>
  <Child>Contents</Child>
</Root>
```

## <a name="example-use-an-embedded-expression-for-content"></a><span data-ttu-id="c54a4-130">Örnek: içerik için gömülü bir ifade kullanın</span><span class="sxs-lookup"><span data-stu-id="c54a4-130">Example: Use an embedded expression for content</span></span>

<span data-ttu-id="c54a4-131">Bir öğenin içeriğini sağlamak için gömülü bir ifade kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c54a4-131">You can use an embedded expression to supply the content of an element:</span></span>

```vb
Dim str As String
str = "Some content"
Dim root As XElement = <Root><%= str %></Root>
Console.WriteLine(root)
```

<span data-ttu-id="c54a4-132">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="c54a4-132">This example produces the following output:</span></span>

```xml
<Root>Some content</Root>
```

## <a name="example-use-a-linq-query-in-an-embedded-expression"></a><span data-ttu-id="c54a4-133">Örnek: katıştırılmış ifadede LINQ sorgusu kullanma</span><span class="sxs-lookup"><span data-stu-id="c54a4-133">Example: Use a LINQ query in an embedded expression</span></span>

<span data-ttu-id="c54a4-134">Bir LINQ sorgusunun sonuçlarını bir öğenin içeriğini sağlamak için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c54a4-134">You can use the results of a LINQ query to provide the content of an element:</span></span>

```vb
Dim arr As Integer() = {1, 2, 3}

Dim n As XElement = _
    <Root>
        <%= From i In arr Select <Child><%= i %></Child> %>
    </Root>

Console.WriteLine(n)
```

<span data-ttu-id="c54a4-135">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="c54a4-135">This example produces the following output:</span></span>

```xml
<Root>
  <Child>1</Child>
  <Child>2</Child>
  <Child>3</Child>
</Root>
```

## <a name="example-use-an-embedded-expression-to-provide-node-names"></a><span data-ttu-id="c54a4-136">Örnek: düğüm adları sağlamak için gömülü bir ifade kullanın</span><span class="sxs-lookup"><span data-stu-id="c54a4-136">Example: Use an embedded expression to provide node names</span></span>

<span data-ttu-id="c54a4-137">Ayrıca, öznitelik adlarını, öznitelik değerlerini, öğe adlarını ve öğe değerlerini hesaplamak için gömülü bir ifade kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c54a4-137">You can also use an embedded expression to calculate attribute names, attribute values, element names, and element values:</span></span>

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

<span data-ttu-id="c54a4-138">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="c54a4-138">This example produces the following output:</span></span>

```xml
<Root att="aValue">
  <ele>eValue</ele>
</Root>
```

## <a name="example-use-an-embedded-expression-to-clone-and-attach-nodes"></a><span data-ttu-id="c54a4-139">Örnek: düğümleri kopyalamak ve eklemek için gömülü bir ifade kullanın</span><span class="sxs-lookup"><span data-stu-id="c54a4-139">Example: Use an embedded expression to clone and attach nodes</span></span>

<span data-ttu-id="c54a4-140">Daha önce belirtildiği gibi, var olan düğümleri (öğeler dahil) ve özniteliklerini yeni bir XML ağacına eklemek için katıştırılmış bir ifade kullanırsanız ve eklenen düğümlerin düğümleri zaten üst öğe ise, düğümler kopyalanır ve kopyalar yeni XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="c54a4-140">As mentioned earlier, if you use an embedded expression to add existing nodes (including elements) and attributes to a new XML tree, and if the nodes being added nodes are already parented, the nodes are cloned and the clones are attached to the new XML tree.</span></span> <span data-ttu-id="c54a4-141">Mevcut düğümler üst öğe değilse, yeni XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="c54a4-141">If the existing nodes aren't parented, they're simply attached to the new XML tree.</span></span>

<span data-ttu-id="c54a4-142">Aşağıdaki kod, bir ağaca bir üst öğeye sahip bir öğe eklediğinizde ve bir ağaca üst öğesi olmayan bir öğe eklediğinizde davranışını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c54a4-142">The following code demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>

```vb
' Create a tree with a child element.
Dim xmlTree1 As XElement = _
    <Root>
        <Child1>1</Child1>
    </Root>

' Create an element that's not parented.
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

<span data-ttu-id="c54a4-143">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="c54a4-143">This example produces the following output:</span></span>

```output
Child1 was cloned
Child2 was attached
```

## <a name="see-also"></a><span data-ttu-id="c54a4-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c54a4-144">See also</span></span>

- [<span data-ttu-id="c54a4-145">İşlevsel oluşturma</span><span class="sxs-lookup"><span data-stu-id="c54a4-145">Functional construction</span></span>](functional-construction.md)
