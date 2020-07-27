---
title: Bellek içi XML ağacı değişikliği ile Işlevsel oluşturma (LINQ to XML) (C#)
description: Bu örnekler, bir XML belgesinin şeklini yerinde değiştirerek ve C# içinde LINQ to XML işlevsel oluşturma kullanarak değiştirir.
ms.date: 07/20/2015
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 7a2e3d2ddcd452cf6a58e9d5cc886f3e8b8dd325
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165789"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-c"></a><span data-ttu-id="58f87-103">Bellek içi XML ağacı değişikliği ile Işlevsel oluşturma (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="58f87-103">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (C#)</span></span>
<span data-ttu-id="58f87-104">Bir XML ağacını yerinde değiştirmek, bir XML belgesinin şeklini değiştirmenin geleneksel bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="58f87-104">Modifying an XML tree in place is a traditional approach to changing the shape of an XML document.</span></span> <span data-ttu-id="58f87-105">Tipik bir uygulama, bir belgeyi DOM veya gibi bir veri deposuna yükler [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ; düğüm eklemek, düğümleri silmek ya da düğümlerin içeriğini değiştirmek için bir programlama arabirimi kullanır ve ardından XML 'i bir dosyaya kaydeder veya bir ağ üzerinden iletir.</span><span class="sxs-lookup"><span data-stu-id="58f87-105">A typical application loads a document into a data store such as DOM or [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; uses a programming interface to insert nodes, delete nodes, or change the content of nodes; and then saves the XML to a file or transmits it over a network.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="58f87-106">birçok senaryoda faydalı olan başka bir yaklaşımı sağlar: *işlevsel oluşturma*.</span><span class="sxs-lookup"><span data-stu-id="58f87-106">enables another approach that is useful in many scenarios: *functional construction*.</span></span> <span data-ttu-id="58f87-107">İşlevsel oluşturma, verileri bir veri deposunun ayrıntılı olarak değiştirilmesi yerine dönüşümde bir sorun olarak değiştirir.</span><span class="sxs-lookup"><span data-stu-id="58f87-107">Functional construction treats modifying data as a problem of transformation, rather than as detailed manipulation of a data store.</span></span> <span data-ttu-id="58f87-108">Verilerin bir temsilini alıp bir formdan diğerine verimli bir şekilde dönüştürebiliyorsanız, sonuç bir veri deposu alıp başka bir şekil almak için bir şekilde işleneceğinden aynı olur.</span><span class="sxs-lookup"><span data-stu-id="58f87-108">If you can take a representation of data and transform it efficiently from one form to another, the result is the same as if you took one data store and manipulated it in some way to take another shape.</span></span> <span data-ttu-id="58f87-109">İşlevsel oluşturma yaklaşımına bir anahtar, sorguların sonuçlarını <xref:System.Xml.Linq.XDocument> ve oluşturuculara geçirmektir <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="58f87-109">A key to the functional construction approach is to pass the results of queries to <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> constructors.</span></span>  
  
 <span data-ttu-id="58f87-110">Çoğu durumda, dönüştürme kodunu veri mağazasının yönetilmesi için gereken sürede yazabilir ve bu kodun daha sağlam ve bakımını daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="58f87-110">In many cases you can write the transformational code in a fraction of the time that it would take to manipulate the data store, and that code is more robust and easier to maintain.</span></span> <span data-ttu-id="58f87-111">Bu durumlarda, dönüştürme yaklaşımının daha fazla işlem gücü sürmesine rağmen, verileri değiştirmek için daha etkili bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="58f87-111">In these cases, even though the transformational approach can take more processing power, it is a more effective way to modify data.</span></span> <span data-ttu-id="58f87-112">Bir geliştirici işlevsel yaklaşımı kullanıyorsa, sonuçta elde edilen kodun çoğu anlaşılması daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="58f87-112">If a developer is familiar with the functional approach, the resulting code in many cases is easier to understand.</span></span> <span data-ttu-id="58f87-113">Ağacın her bölümünü değiştiren kodu bulmak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="58f87-113">It is easy to find the code that modifies each part of the tree.</span></span>  
  
 <span data-ttu-id="58f87-114">Bir XML ağacını yerinde değiştirdiğiniz yaklaşımda birçok DOM programcısı daha tanıdık gelecektir. işlevsel yaklaşım kullanılarak yazılan kod, bu yaklaşımı henüz anlayamamış bir geliştiriciye tanıdık görünebilir.</span><span class="sxs-lookup"><span data-stu-id="58f87-114">The approach where you modify an XML tree in-place is more familiar to many DOM programmers, whereas code written using the functional approach might look unfamiliar to a developer who doesn't yet understand that approach.</span></span> <span data-ttu-id="58f87-115">Büyük bir XML ağacında yalnızca küçük bir değişiklik yapmanız gerekiyorsa, bir ağacı birçok durumda değiştirdiğiniz yaklaşım daha az CPU süresi alır.</span><span class="sxs-lookup"><span data-stu-id="58f87-115">If you have to only make a small modification to a large XML tree, the approach where you modify a tree in place in many cases will take less CPU time.</span></span>  
  
 <span data-ttu-id="58f87-116">Bu konu, her iki yaklaşımdan de uygulanan bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="58f87-116">This topic provides an example that is implemented with both approaches.</span></span>  
  
## <a name="transforming-attributes-into-elements"></a><span data-ttu-id="58f87-117">Öznitelikleri öğelere dönüştürme</span><span class="sxs-lookup"><span data-stu-id="58f87-117">Transforming Attributes into Elements</span></span>  
 <span data-ttu-id="58f87-118">Bu örnekte, özniteliklerin öğe haline gelmesi için aşağıdaki basit XML belgesini değiştirmek istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="58f87-118">For this example, suppose you want to modify the following simple XML document so that the attributes become elements.</span></span> <span data-ttu-id="58f87-119">Bu konu öncelikle geleneksel yerinde değişiklik yaklaşımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="58f87-119">This topic first presents the traditional in-place modification approach.</span></span> <span data-ttu-id="58f87-120">Ardından işlevsel oluşturma yaklaşımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="58f87-120">It then shows the functional construction approach.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a><span data-ttu-id="58f87-121">XML ağacını değiştirme</span><span class="sxs-lookup"><span data-stu-id="58f87-121">Modifying the XML Tree</span></span>  
 <span data-ttu-id="58f87-122">Özniteliklerden öğe oluşturmak için bazı yordamsal kodlar yazabilir ve ardından aşağıdaki gibi öznitelikleri silebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="58f87-122">You can write some procedural code to create elements from the attributes, and then delete the attributes, as follows:</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
foreach (XAttribute att in root.Attributes()) {  
    root.Add(new XElement(att.Name, (string)att));  
}  
root.Attributes().Remove();  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="58f87-123">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="58f87-123">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a><span data-ttu-id="58f87-124">İşlevsel oluşturma yaklaşımı</span><span class="sxs-lookup"><span data-stu-id="58f87-124">Functional Construction Approach</span></span>  
 <span data-ttu-id="58f87-125">Bunun aksine, işlevsel bir yaklaşım, yeni bir ağaç oluşturmak, kaynak ağaçtan öğe ve öznitelik seçmek ve seçmek ve bunları yeni ağaca eklendikçe uygun şekilde dönüştürmek için koddan oluşur.</span><span class="sxs-lookup"><span data-stu-id="58f87-125">By contrast, a functional approach consists of code to form a new tree, picking and choosing elements and attributes from the source tree, and transforming them as appropriate as they are added to the new tree.</span></span> <span data-ttu-id="58f87-126">İşlevsel yaklaşım aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="58f87-126">The functional approach looks like the following:</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
XElement newTree = new XElement("Root",  
    root.Element("Child1"),  
    from att in root.Attributes()  
    select new XElement(att.Name, (string)att)  
);  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="58f87-127">Bu örnek, ilk örnekle aynı XML 'e çıktı verir.</span><span class="sxs-lookup"><span data-stu-id="58f87-127">This example outputs the same XML as the first example.</span></span> <span data-ttu-id="58f87-128">Bununla birlikte, yeni XML 'nin ortaya çıkan yapısını işlevsel yaklaşımda görbildiğinize dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="58f87-128">However, notice that you can actually see the resulting structure of the new XML in the functional approach.</span></span> <span data-ttu-id="58f87-129">`Root`Öğesinin oluşturulmasını, `Child1` kaynak ağacından öğeyi çeken kodu ve kaynak ağaç içindeki öznitelikleri yeni ağaç içindeki öğelere dönüştüren kodu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58f87-129">You can see the creation of the `Root` element, the code that pulls the `Child1` element from the source tree, and the code that transforms the attributes from the source tree to elements in the new tree.</span></span>  
  
 <span data-ttu-id="58f87-130">Bu örnekte işlevsel örnek, ilk örnekte daha kısa değildir ve gerçekten daha basit değildir.</span><span class="sxs-lookup"><span data-stu-id="58f87-130">The functional example in this case is not any shorter than the first example, and it is not really any simpler.</span></span> <span data-ttu-id="58f87-131">Ancak, bir XML ağacına yaptığınız birçok değişiklik varsa, işlevsel olmayan yaklaşım oldukça karmaşık ve biraz daha kolay hale gelir.</span><span class="sxs-lookup"><span data-stu-id="58f87-131">However, if you have many changes to make to an XML tree, the non functional approach will become quite complex and somewhat obtuse.</span></span> <span data-ttu-id="58f87-132">Buna karşılık, işlevsel yaklaşımı kullanırken, istenen içeriği çekmek için istenen XML 'yi, uygun şekilde ekleme sorgularını ve ifadeleri yazmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="58f87-132">In contrast, when using the functional approach, you still just form the desired XML, embedding queries and expressions as appropriate, to pull in the desired content.</span></span> <span data-ttu-id="58f87-133">İşlevsel yaklaşım, bakımı daha kolay olan kodu verir.</span><span class="sxs-lookup"><span data-stu-id="58f87-133">The functional approach yields code that is easier to maintain.</span></span>  
  
 <span data-ttu-id="58f87-134">Bu durumda, işlevsel yaklaşımın büyük olasılıkla ağaç işleme yaklaşımının çok iyi gerçekleştirmediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="58f87-134">Notice that in this case the functional approach probably would not perform quite as well as the tree manipulation approach.</span></span> <span data-ttu-id="58f87-135">Ana sorun, işlevsel yaklaşımın daha kısa süreli nesneler oluşturmasıdır.</span><span class="sxs-lookup"><span data-stu-id="58f87-135">The main issue is that the functional approach creates more short lived objects.</span></span> <span data-ttu-id="58f87-136">Ancak, işlevsel yaklaşımın kullanılması daha fazla programcı verimliliğine izin veriyorsa zorunluluğunu getirir geçerli bir değer.</span><span class="sxs-lookup"><span data-stu-id="58f87-136">However, the tradeoff is an effective one if using the functional approach allows for greater programmer productivity.</span></span>  
  
 <span data-ttu-id="58f87-137">Bu çok basit bir örnektir, ancak iki yaklaşım arasındaki FI 'teki farkı göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="58f87-137">This is a very simple example, but it serves to show the difference in philosophy between the two approaches.</span></span> <span data-ttu-id="58f87-138">İşlevsel yaklaşım, büyük XML belgelerini dönüştürmek için daha fazla verimlilik artışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="58f87-138">The functional approach yields greater productivity gains for transforming larger XML documents.</span></span>  
  