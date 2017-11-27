---
title: "Bellek içi XML ağaç değişikliği vs. İşlev yapımı (LINQ-XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d91c4ebf-6549-43cc-9961-26d4a82f722b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3652933a5d25b298167f54525800eceee16264e8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-visual-basic"></a><span data-ttu-id="07191-102">Bellek içi XML ağaç değişikliği vs. İşlev yapımı (LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07191-102">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="07191-103">Bir XML ağacı yerinde değiştirme, bir XML belgesi şeklini değiştirmek için geleneksel bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="07191-103">Modifying an XML tree in place is a traditional approach to changing the shape of an XML document.</span></span> <span data-ttu-id="07191-104">Tipik bir uygulama bir belge DOM gibi bir veri deposu yükler veya [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; düğümlerini eklemek, düğümlerini silebilir veya düğümler; içeriğini değiştirmek için bir programlama arabirimi kullanır ve ardından XML bir dosyaya kaydeder veya bir ağ üzerinden iletir.</span><span class="sxs-lookup"><span data-stu-id="07191-104">A typical application loads a document into a data store such as DOM or [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; uses a programming interface to insert nodes, delete nodes, or change the content of nodes; and then saves the XML to a file or transmits it over a network.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="07191-105">pek çok durumda yararlıdır başka bir yaklaşım sağlar*: işlev yapım*.</span><span class="sxs-lookup"><span data-stu-id="07191-105"> enables another approach that is useful in many scenarios*: functional construction*.</span></span> <span data-ttu-id="07191-106">İşlev oluşturma değiştirme veri dönüşümünün bir sorun olarak yerine ayrıntılı işleme bir veri deposu olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="07191-106">Functional construction treats modifying data as a problem of transformation, rather than as detailed manipulation of a data store.</span></span> <span data-ttu-id="07191-107">Veri gösterimi alabilir ve verimli bir şekilde bir formdan başka dönüştürmek, bir veri deposu sürdü ve başka bir şekil yapılacak herhangi bir şekilde yönetilebilir gibi sonuç aynıdır.</span><span class="sxs-lookup"><span data-stu-id="07191-107">If you can take a representation of data and transform it efficiently from one form to another, the result is the same as if you took one data store and manipulated it in some way to take another shape.</span></span> <span data-ttu-id="07191-108">İşlev oluşturma yaklaşımın bir anahtar için sorguların sonuçlarını geçirmektir <xref:System.Xml.Linq.XDocument> ve <xref:System.Xml.Linq.XElement> oluşturucular.</span><span class="sxs-lookup"><span data-stu-id="07191-108">A key to the functional construction approach is to pass the results of queries to <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> constructors.</span></span>  
  
 <span data-ttu-id="07191-109">Çoğu durumda, veri deposu işlemek için harcanacak zaman kesir transformational kod yazabilirsiniz ve bu kodu daha sağlam ve sürdürmek daha kolay.</span><span class="sxs-lookup"><span data-stu-id="07191-109">In many cases you can write the transformational code in a fraction of the time that it would take to manipulate the data store, and that code is more robust and easier to maintain.</span></span> <span data-ttu-id="07191-110">Transformational yaklaşım daha fazla işlemci gücü, sürebilir olsa bile bu durumlarda, bu verileri değiştirmek için bir daha etkili yoldur.</span><span class="sxs-lookup"><span data-stu-id="07191-110">In these cases, even though the transformational approach can take more processing power, it is a more effective way to modify data.</span></span> <span data-ttu-id="07191-111">Bir geliştirici işlevsel yaklaşımda tanıdık ise, sonuçta elde edilen çoğu durumda anlamak daha kolay kodudur.</span><span class="sxs-lookup"><span data-stu-id="07191-111">If a developer is familiar with the functional approach, the resulting code in many cases is easier to understand.</span></span> <span data-ttu-id="07191-112">Her bölümü ağacının değiştirir kod Bul kolaydır.</span><span class="sxs-lookup"><span data-stu-id="07191-112">It is easy to find the code that modifies each part of the tree.</span></span>  
  
 <span data-ttu-id="07191-113">İşlev yaklaşımı kullanılarak yazılan kod henüz bu yaklaşımı anlamıyor bir geliştirici için tanınmayan görünebilir ancak burada bir XML ağaç yerinde değiştirme birçok DOM programcıları için daha tanıdık bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="07191-113">The approach where you modify an XML tree in-place is more familiar to many DOM programmers, whereas code written using the functional approach might look unfamiliar to a developer who doesn't yet understand that approach.</span></span> <span data-ttu-id="07191-114">Yalnızca büyük bir XML ağacı küçük bir değişiklik yapmak varsa, burada, çoğu durumda yerinde bir ağaç değişiklik yaklaşımı daha az CPU uzun sürer.</span><span class="sxs-lookup"><span data-stu-id="07191-114">If you have to only make a small modification to a large XML tree, the approach where you modify a tree in place in many cases will take less CPU time.</span></span>  
  
 <span data-ttu-id="07191-115">Bu konu, her iki yaklaşımın ile uygulanan bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="07191-115">This topic provides an example that is implemented with both approaches.</span></span>  
  
## <a name="transforming-attributes-into-elements"></a><span data-ttu-id="07191-116">Öznitelikleri elemanlara dönüştürme</span><span class="sxs-lookup"><span data-stu-id="07191-116">Transforming Attributes into Elements</span></span>  
 <span data-ttu-id="07191-117">Bu örnekte, böylece öğeler öznitelikleri hale aşağıdaki basit bir XML belge değiştirmek istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="07191-117">For this example, suppose you want to modify the following simple XML document so that the attributes become elements.</span></span> <span data-ttu-id="07191-118">Bu konuda, ilk geleneksel yerinde değişikliği yaklaşım sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="07191-118">This topic first presents the traditional in-place modification approach.</span></span> <span data-ttu-id="07191-119">Ardından, işlevsel yapım yaklaşım gösterir.</span><span class="sxs-lookup"><span data-stu-id="07191-119">It then shows the functional construction approach.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a><span data-ttu-id="07191-120">XML ağaç değiştirme</span><span class="sxs-lookup"><span data-stu-id="07191-120">Modifying the XML Tree</span></span>  
 <span data-ttu-id="07191-121">Öznitelikleri öğeleri oluşturmak için yordam bazı kodlar yazmak ve öznitelikler gibi silin:</span><span class="sxs-lookup"><span data-stu-id="07191-121">You can write some procedural code to create elements from the attributes, and then delete the attributes, as follows:</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
For Each att As XAttribute In root.Attributes()  
    root.Add(New XElement(att.Name, att.Value))  
Next  
root.Attributes().Remove()  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="07191-122">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="07191-122">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a><span data-ttu-id="07191-123">İşlev oluşturma yaklaşımı</span><span class="sxs-lookup"><span data-stu-id="07191-123">Functional Construction Approach</span></span>  
 <span data-ttu-id="07191-124">Bunun aksine, işlevsel bir yaklaşım çekme ve öğeleri ve özniteliklerinin kaynak ağacından seçme ve bunları yeni ağacına eklendikçe uygun şekilde dönüştürme yeni bir ağaç oluşturacak şekilde kodu oluşur.</span><span class="sxs-lookup"><span data-stu-id="07191-124">By contrast, a functional approach consists of code to form a new tree, picking and choosing elements and attributes from the source tree, and transforming them as appropriate as they are added to the new tree.</span></span> <span data-ttu-id="07191-125">İşlev yaklaşım aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="07191-125">The functional approach looks like the following:</span></span>  
  
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
  
 <span data-ttu-id="07191-126">Bu örnekte, ilk örnekle aynı XML çıkarır.</span><span class="sxs-lookup"><span data-stu-id="07191-126">This example outputs the same XML as the first example.</span></span> <span data-ttu-id="07191-127">Ancak, yeni XML işlevsel yaklaşımda elde edilen yapısı gerçekten görebilirsiniz dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="07191-127">However, notice that you can actually see the resulting structure of the new XML in the functional approach.</span></span> <span data-ttu-id="07191-128">Oluşturulmasını görebilirsiniz `Root` öğesi, çeker kodu `Child1` öğesinden kaynak ağaç ve yeni ağacındaki öğeler kaynak ağacından öznitelikleri dönüştüren kodu.</span><span class="sxs-lookup"><span data-stu-id="07191-128">You can see the creation of the `Root` element, the code that pulls the `Child1` element from the source tree, and the code that transforms the attributes from the source tree to elements in the new tree.</span></span>  
  
 <span data-ttu-id="07191-129">İşlevsel örneği bu durumda her ilk örnek kısa değil ve gerçekten herhangi daha basit değil.</span><span class="sxs-lookup"><span data-stu-id="07191-129">The functional example in this case is not any shorter than the first example, and it is not really any simpler.</span></span> <span data-ttu-id="07191-130">Bununla birlikte, bir XML ağacına yapmanız gereken çok sayıda değişikliği varsa, olmayan işlev yaklaşım oldukça karmaşık ve biraz geniş açılı olur.</span><span class="sxs-lookup"><span data-stu-id="07191-130">However, if you have many changes to make to an XML tree, the non functional approach will become quite complex and somewhat obtuse.</span></span> <span data-ttu-id="07191-131">Buna karşılık, işlevsel bir yaklaşım kullanırken, yalnızca form sorgular ve ifadeler, istenen içeriği çıkarmak uygun olarak katıştırma istenen XML hala.</span><span class="sxs-lookup"><span data-stu-id="07191-131">In contrast, when using the functional approach, you still just form the desired XML, embedding queries and expressions as appropriate, to pull in the desired content.</span></span> <span data-ttu-id="07191-132">İşlev yaklaşım oluşturmanın kodunu üretir.</span><span class="sxs-lookup"><span data-stu-id="07191-132">The functional approach yields code that is easier to maintain.</span></span>  
  
 <span data-ttu-id="07191-133">Bu durumda işlev yaklaşım büyük olasılıkla oldukça ağaç işleme yaklaşım yanı sıra gerçekleştireceği değil dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="07191-133">Notice that in this case the functional approach probably would not perform quite as well as the tree manipulation approach.</span></span> <span data-ttu-id="07191-134">Ana sorunu işlevsel yaklaşımı daha kısa süreli nesneleri oluşturmasıdır.</span><span class="sxs-lookup"><span data-stu-id="07191-134">The main issue is that the functional approach creates more short lived objects.</span></span> <span data-ttu-id="07191-135">Ancak, kolaylığını işlevsel yaklaşımı kullanmak için büyük Programcı üretkenlik veriyorsa etkili bir bölümdür.</span><span class="sxs-lookup"><span data-stu-id="07191-135">However, the tradeoff is an effective one if using the functional approach allows for greater programmer productivity.</span></span>  
  
 <span data-ttu-id="07191-136">Bu çok basit bir örnektir ancak felsefesi iki yaklaşım arasındaki farkı göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="07191-136">This is a very simple example, but it serves to show the difference in philosophy between the two approaches.</span></span> <span data-ttu-id="07191-137">İşlevsel bir yaklaşım, daha büyük XML belgelerini dönüştüren büyük üretkenlik kazançlar verir.</span><span class="sxs-lookup"><span data-stu-id="07191-137">The functional approach yields greater productivity gains for transforming larger XML documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07191-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07191-138">See Also</span></span>  
 [<span data-ttu-id="07191-139">XML ağaçları (LINQ-XML) değiştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07191-139">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
