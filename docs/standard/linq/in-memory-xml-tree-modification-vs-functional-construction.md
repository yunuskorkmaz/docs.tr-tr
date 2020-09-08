---
title: Bellek içi XML ağacı değişikliği ile işlevsel oluşturma-LINQ to XML
description: XML ağaçlarını değiştirmenin iki farklı yaklaşımının örneklerine bakın.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 71f76d12024bb07cf90df2299df14646ae271b47
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552973"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml"></a><span data-ttu-id="8e206-103">Bellek içi XML ağacı değişikliği ile işlevsel oluşturma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="8e206-103">In-memory XML tree modification vs. functional construction (LINQ to XML)</span></span>

<span data-ttu-id="8e206-104">Bir XML ağacını yerinde değiştirmek, bir XML belgesinin şeklini değiştirmenin geleneksel bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="8e206-104">Modifying an XML tree in place is a traditional approach to changing the shape of an XML document.</span></span> <span data-ttu-id="8e206-105">Tipik bir uygulama, bir belgeyi DOM veya LINQ to XML gibi bir veri deposuna yükler; düğüm eklemek veya silmek ya da içeriklerini değiştirmek için bir programlama arabirimi kullanır; ardından, XML dosyasını bir dosyaya kaydeder veya ağ üzerinden iletir.</span><span class="sxs-lookup"><span data-stu-id="8e206-105">A typical application loads a document into a data store such as DOM or LINQ to XML; uses a programming interface to insert or delete nodes, or change their content; and then saves the XML to a file or transmits it over a network.</span></span>

<span data-ttu-id="8e206-106">LINQ to XML, çok sayıda senaryoda faydalı olan başka bir yaklaşım sağlar: *işlevsel oluşturma*.</span><span class="sxs-lookup"><span data-stu-id="8e206-106">LINQ to XML enables another approach that is useful in many scenarios: *functional construction*.</span></span> <span data-ttu-id="8e206-107">İşlevsel oluşturma, verileri bir veri deposunun ayrıntılı olarak değiştirilmesi yerine dönüşümde bir sorun olarak değiştirir.</span><span class="sxs-lookup"><span data-stu-id="8e206-107">Functional construction treats modifying data as a problem of transformation, rather than as detailed manipulation of a data store.</span></span> <span data-ttu-id="8e206-108">Verilerin bir temsilini alıp bir formdan diğerine verimli bir şekilde dönüştürebiliyorsanız, sonuç bir veri deposu alıp başka bir şekil almak için bir şekilde işleneceğinden aynı olur.</span><span class="sxs-lookup"><span data-stu-id="8e206-108">If you can take a representation of data and transform it efficiently from one form to another, the result is the same as if you took one data store and manipulated it in some way to take another shape.</span></span> <span data-ttu-id="8e206-109">İşlevsel oluşturma yaklaşımına bir anahtar, sorguların sonuçlarını <xref:System.Xml.Linq.XDocument> ve oluşturuculara geçirmektir <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="8e206-109">A key to the functional construction approach is to pass the results of queries to <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> constructors.</span></span>

<span data-ttu-id="8e206-110">Çoğu durumda, dönüştürme kodunu veri deposunun yönetilmesi için gereken sürenin bir bölümünde yazabilir ve sonuçta elde edilen kod daha sağlam ve daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="8e206-110">In many cases you can write the transformational code in a fraction of the time that it would take to manipulate the data store, and the resulting code is more robust and easier to maintain.</span></span> <span data-ttu-id="8e206-111">Bu durumlarda, dönüştürme yaklaşımının daha fazla işlem gücü sürebilse de, verileri değiştirmek için daha etkili bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="8e206-111">In these cases, even though the transformational approach can take more processing power, it's a more effective way to modify data.</span></span> <span data-ttu-id="8e206-112">Bir geliştirici işlevsel yaklaşımı öğrenir, çok sayıda durumda elde edilen kodun anlaşılması daha kolaydır ve ağacın her bölümünü değiştiren kodu kolayca bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e206-112">If a developer is familiar with the functional approach, the resulting code in many cases is easier to understand, and it's easy to find the code that modifies each part of the tree.</span></span>

<span data-ttu-id="8e206-113">Yerinde bir XML ağacını değiştirdiğiniz yaklaşım birçok DOM programcısı için daha tanıdık gelecektir, ancak işlevsel yaklaşım kullanılarak yazılan kod, bu yaklaşımı henüz anlayamamış bir geliştiriciye tanıdık gelebilir.</span><span class="sxs-lookup"><span data-stu-id="8e206-113">The approach where you modify an XML tree in place is more familiar to many DOM programmers, whereas code written using the functional approach might look unfamiliar to a developer who doesn't yet understand that approach.</span></span> <span data-ttu-id="8e206-114">Büyük bir XML ağacında yalnızca küçük bir değişiklik yapmanız gerekiyorsa, bir ağacı birçok durumda değiştirdiğiniz yaklaşım daha az CPU süresi alır.</span><span class="sxs-lookup"><span data-stu-id="8e206-114">If you have to only make a small modification to a large XML tree, the approach where you modify a tree in place in many cases will take less CPU time.</span></span>

<span data-ttu-id="8e206-115">Bu makalede her iki yaklaşımdan örnekler sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8e206-115">This article provides examples of both approaches.</span></span> <span data-ttu-id="8e206-116">Aşağıdaki basit XML belgesini, özniteliklerin öğe olacak şekilde değiştirmek istediğinizi varsayalım:</span><span class="sxs-lookup"><span data-stu-id="8e206-116">Suppose you want to modify the following simple XML document so that the attributes become elements:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Root Data1="123" Data2="456">
  <Child1>Content</Child1>
</Root>
```

<span data-ttu-id="8e206-117">Aşağıdaki örneklerden ilki geleneksel yerinde değiştirme yaklaşımını kullanır ve ikincisi işlevsel oluşturma yaklaşımını kullanır.</span><span class="sxs-lookup"><span data-stu-id="8e206-117">The first of the following examples uses the traditional in-place modification approach, and the second uses the functional construction approach.</span></span>

## <a name="example-transform-attributes-into-elements-with-the-traditional-in-place-approach"></a><span data-ttu-id="8e206-118">Örnek: geleneksel yerinde yaklaşımla öznitelikleri öğelere Dönüştür</span><span class="sxs-lookup"><span data-stu-id="8e206-118">Example: Transform attributes into elements with the traditional in-place approach</span></span>

<span data-ttu-id="8e206-119">Özniteliklerden öğe oluşturmak için bazı yordamsal kodlar yazabilir ve ardından aşağıdaki gibi öznitelikleri silebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8e206-119">You can write some procedural code to create elements from the attributes, and then delete the attributes, as follows:</span></span>

```csharp
XElement root = XElement.Load("Data.xml");
foreach (XAttribute att in root.Attributes()) {
    root.Add(new XElement(att.Name, (string)att));
}
root.Attributes().Remove();
Console.WriteLine(root);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
For Each att As XAttribute In root.Attributes()
    root.Add(New XElement(att.Name, att.Value))
Next
root.Attributes().Remove()
Console.WriteLine(root)
```

<span data-ttu-id="8e206-120">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="8e206-120">This example produces the following output:</span></span>

```xml
<Root>
  <Child1>Content</Child1>
  <Data1>123</Data1>
  <Data2>456</Data2>
</Root>
```

## <a name="example-transform-attributes-into-elements-with-the-functional-construction-approach"></a><span data-ttu-id="8e206-121">Örnek: işlev oluşturma yaklaşımıyla öznitelikleri öğelere Dönüştür</span><span class="sxs-lookup"><span data-stu-id="8e206-121">Example: Transform attributes into elements with the functional construction approach</span></span>

<span data-ttu-id="8e206-122">Bunun aksine, işlevsel bir yaklaşım yeni bir ağaç oluşturacak, kaynak ağaçtan öğe ve öznitelik seçme, seçme ve bunları yeni ağaca eklendikçe uygun şekilde dönüştürme kodundan oluşur.</span><span class="sxs-lookup"><span data-stu-id="8e206-122">By contrast, a functional approach consists of code to form a new tree, picking and choosing elements and attributes from the source tree, and transforming them as appropriate as they're added to the new tree.</span></span>

```csharp
XElement root = XElement.Load("Data.xml");
XElement newTree = new XElement("Root",
    root.Element("Child1"),
    from att in root.Attributes()
    select new XElement(att.Name, (string)att)
);
Console.WriteLine(newTree);
```

```vb
Dim root As XElement = XElement.Load("Data.xml")
Dim newTree As XElement = _
    <Root>
        <%= root.<Child1> %>
        <%= From att In root.Attributes() _
            Select New XElement(att.Name, att.Value) %>
    </Root>
Console.WriteLine(newTree)
```

<span data-ttu-id="8e206-123">Bu örnek, ilk örnekle aynı XML 'e çıktı verir.</span><span class="sxs-lookup"><span data-stu-id="8e206-123">This example outputs the same XML as the first example.</span></span> <span data-ttu-id="8e206-124">Bununla birlikte, yeni XML 'nin ortaya çıkan yapısını işlevsel yaklaşımda görbildiğinize dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="8e206-124">However, notice that you can actually see the resulting structure of the new XML in the functional approach.</span></span> <span data-ttu-id="8e206-125">`Root`Öğesinin oluşturulmasını, `Child1` kaynak ağacından öğeyi çeken kodu ve kaynak ağaç içindeki öznitelikleri yeni ağaç içindeki öğelere dönüştüren kodu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8e206-125">You can see the creation of the `Root` element, the code that pulls the `Child1` element from the source tree, and the code that transforms the attributes from the source tree to elements in the new tree.</span></span>

<span data-ttu-id="8e206-126">Bu durumda işlevsel örnek, ilk örneğe göre daha kısa veya daha basit değildir.</span><span class="sxs-lookup"><span data-stu-id="8e206-126">The functional example in this case is neither shorter nor simpler than the first example.</span></span> <span data-ttu-id="8e206-127">Ancak, bir XML ağacına yaptığınız birçok değişiklik varsa, yordamsal yaklaşım oldukça karmaşık ve biraz daha kolay hale gelir.</span><span class="sxs-lookup"><span data-stu-id="8e206-127">However, if you have many changes to make to an XML tree, the procedural approach will become quite complex and somewhat obtuse.</span></span> <span data-ttu-id="8e206-128">Buna karşılık, işlevsel yaklaşımı kullanırken, istenen içeriği çekmek için istenen XML 'yi, uygun şekilde ekleme sorgularını ve ifadeleri yazmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="8e206-128">In contrast, when using the functional approach, you still just form the desired XML, embedding queries and expressions as appropriate, to pull in the desired content.</span></span> <span data-ttu-id="8e206-129">İşlevsel yaklaşım, bakımı daha kolay olan kodu verir.</span><span class="sxs-lookup"><span data-stu-id="8e206-129">The functional approach yields code that is easier to maintain.</span></span>

<span data-ttu-id="8e206-130">Bu durumda, işlevsel yaklaşımın büyük olasılıkla ağaç işleme yaklaşımının çok iyi gerçekleştirmediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="8e206-130">Notice that in this case the functional approach probably would not perform quite as well as the tree manipulation approach.</span></span> <span data-ttu-id="8e206-131">Ana sorun, işlevsel yaklaşımın daha kısa süreli nesneler oluşturmasıdır.</span><span class="sxs-lookup"><span data-stu-id="8e206-131">The main issue is that the functional approach creates more short-lived objects.</span></span> <span data-ttu-id="8e206-132">Ancak, işlevsel yaklaşımın kullanılması daha fazla programcı verimliliğine izin veriyorsa zorunluluğunu getirir geçerli bir değer.</span><span class="sxs-lookup"><span data-stu-id="8e206-132">However, the tradeoff is an effective one if using the functional approach allows for greater programmer productivity.</span></span>

<span data-ttu-id="8e206-133">Bu çok basit bir örnektir, ancak iki yaklaşım arasındaki FI 'teki farkı göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8e206-133">This is a very simple example, but it serves to show the difference in philosophy between the two approaches.</span></span> <span data-ttu-id="8e206-134">İşlevsel yaklaşım, büyük XML belgelerini dönüştürmek için daha fazla verimlilik artışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8e206-134">The functional approach yields greater productivity gains for transforming larger XML documents.</span></span>
