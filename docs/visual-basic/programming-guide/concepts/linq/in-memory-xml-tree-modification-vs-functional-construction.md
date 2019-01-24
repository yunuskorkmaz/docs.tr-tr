---
title: Bellek içi XML ağacı değişikliği ve İşlevsel oluşturma (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d91c4ebf-6549-43cc-9961-26d4a82f722b
ms.openlocfilehash: 0f33775656e92f4ca9d6158ea2a065bb533a944b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538602"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-visual-basic"></a><span data-ttu-id="2adfc-102">Bellek içi XML ağacı değişikliği ve İşlevsel oluşturma (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2adfc-102">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="2adfc-103">Bir XML ağacı yerde değiştirme, bir XML belgesi şeklini değiştirmek için geleneksel bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="2adfc-103">Modifying an XML tree in place is a traditional approach to changing the shape of an XML document.</span></span> <span data-ttu-id="2adfc-104">Tipik bir uygulama bir belge DOM gibi bir veri deposuna yükler ya da [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; düğümleri eklediğinizde, düğümleri silin veya düğümler; içeriğini değiştirmek için bir programlama arabirimi kullanır ve ardından XML bir dosyaya kaydeder veya bir ağ üzerinden iletir.</span><span class="sxs-lookup"><span data-stu-id="2adfc-104">A typical application loads a document into a data store such as DOM or [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; uses a programming interface to insert nodes, delete nodes, or change the content of nodes; and then saves the XML to a file or transmits it over a network.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="2adfc-105">pek çok senaryoda kullanışlıdır başka bir yaklaşım sağlayan *: işlev yapım*.</span><span class="sxs-lookup"><span data-stu-id="2adfc-105">enables another approach that is useful in many scenarios *: functional construction*.</span></span> <span data-ttu-id="2adfc-106">İşlevsel oluşturma, değiştirme veri dönüşümünün bir sorun, yerine ayrıntılı işleme bir veri deposu olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="2adfc-106">Functional construction treats modifying data as a problem of transformation, rather than as detailed manipulation of a data store.</span></span> <span data-ttu-id="2adfc-107">Bir veri temsilini alın ve verimli bir şekilde bir formdan başka bir dönüştürme, bir veri deposu sürdü ve başka bir şekil gerçekleştirilecek şekilde yönetilebilir gibi sonuç aynıdır.</span><span class="sxs-lookup"><span data-stu-id="2adfc-107">If you can take a representation of data and transform it efficiently from one form to another, the result is the same as if you took one data store and manipulated it in some way to take another shape.</span></span> <span data-ttu-id="2adfc-108">İşlevsel oluşturma yaklaşımını anahtarı için sorguların sonuçlarını geçirmektir <xref:System.Xml.Linq.XDocument> ve <xref:System.Xml.Linq.XElement> oluşturucular.</span><span class="sxs-lookup"><span data-stu-id="2adfc-108">A key to the functional construction approach is to pass the results of queries to <xref:System.Xml.Linq.XDocument> and <xref:System.Xml.Linq.XElement> constructors.</span></span>  
  
 <span data-ttu-id="2adfc-109">Çoğu durumda veri deposu işlemek için harcadığım süreyi kesir dönüşümsel kodu yazabilirsiniz ve bu kodu daha sağlam ve bakımı kolay.</span><span class="sxs-lookup"><span data-stu-id="2adfc-109">In many cases you can write the transformational code in a fraction of the time that it would take to manipulate the data store, and that code is more robust and easier to maintain.</span></span> <span data-ttu-id="2adfc-110">Daha fazla işlemci gücü, dönüşümsel yaklaşım sürebilir olsa bile bu gibi durumlarda, bu verileri değiştirmek için bir daha etkili yoludur.</span><span class="sxs-lookup"><span data-stu-id="2adfc-110">In these cases, even though the transformational approach can take more processing power, it is a more effective way to modify data.</span></span> <span data-ttu-id="2adfc-111">Bir geliştirici işlevsel yaklaşım ile ilgili bilgi sahibi ise, çoğu durumda Sonuç kodu anlamak daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="2adfc-111">If a developer is familiar with the functional approach, the resulting code in many cases is easier to understand.</span></span> <span data-ttu-id="2adfc-112">Her ağacın parçası değiştiren bir kodun bulmak daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="2adfc-112">It is easy to find the code that modifies each part of the tree.</span></span>  
  
 <span data-ttu-id="2adfc-113">İşlevsel yaklaşım kullanılarak yazılmış kod henüz bu yaklaşımı anlamıyor bir geliştirici için tanıdık gelmiyor ancak burada bir XML ağacı yerinde değişiklik birçok DOM programcıları için daha tanıdık bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="2adfc-113">The approach where you modify an XML tree in-place is more familiar to many DOM programmers, whereas code written using the functional approach might look unfamiliar to a developer who doesn't yet understand that approach.</span></span> <span data-ttu-id="2adfc-114">Yalnızca büyük bir XML ağacı için küçük bir değişiklik yapmak varsa, burada, çoğu durumda bir yerde bir ağaç değişiklik yaklaşım daha az CPU zaman alabilir.</span><span class="sxs-lookup"><span data-stu-id="2adfc-114">If you have to only make a small modification to a large XML tree, the approach where you modify a tree in place in many cases will take less CPU time.</span></span>  
  
 <span data-ttu-id="2adfc-115">Bu konu, her iki yaklaşım ile uygulanan bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="2adfc-115">This topic provides an example that is implemented with both approaches.</span></span>  
  
## <a name="transforming-attributes-into-elements"></a><span data-ttu-id="2adfc-116">Öğelerine dönüştürme öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="2adfc-116">Transforming Attributes into Elements</span></span>  
 <span data-ttu-id="2adfc-117">Bu örnekte, böylece öznitelikleri öğelerine haline gelir. aşağıdaki basit XML belgesi değiştirmek istediğiniz varsayalım.</span><span class="sxs-lookup"><span data-stu-id="2adfc-117">For this example, suppose you want to modify the following simple XML document so that the attributes become elements.</span></span> <span data-ttu-id="2adfc-118">Bu konuda, ilk yerinde değişikliği geleneksel yaklaşım sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2adfc-118">This topic first presents the traditional in-place modification approach.</span></span> <span data-ttu-id="2adfc-119">Ardından, bir işlev oluşturma yaklaşımı da gösterir.</span><span class="sxs-lookup"><span data-stu-id="2adfc-119">It then shows the functional construction approach.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a><span data-ttu-id="2adfc-120">XML ağacı değiştirme</span><span class="sxs-lookup"><span data-stu-id="2adfc-120">Modifying the XML Tree</span></span>  
 <span data-ttu-id="2adfc-121">Öznitelikleri öğeleri oluşturmak için yordam kod yazma ve öznitelikleri gibi silin:</span><span class="sxs-lookup"><span data-stu-id="2adfc-121">You can write some procedural code to create elements from the attributes, and then delete the attributes, as follows:</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
For Each att As XAttribute In root.Attributes()  
    root.Add(New XElement(att.Name, att.Value))  
Next  
root.Attributes().Remove()  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="2adfc-122">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="2adfc-122">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a><span data-ttu-id="2adfc-123">İşlevsel oluşturma yaklaşımı</span><span class="sxs-lookup"><span data-stu-id="2adfc-123">Functional Construction Approach</span></span>  
 <span data-ttu-id="2adfc-124">Bunun aksine, işlevsel bir yaklaşım çekme ve öğeler ve öznitelikler kaynak ağacından seçme ve bunları yeni ağacına eklendikçe uygun şekilde dönüştürme yeni bir ağaç oluşturmak için kod oluşur.</span><span class="sxs-lookup"><span data-stu-id="2adfc-124">By contrast, a functional approach consists of code to form a new tree, picking and choosing elements and attributes from the source tree, and transforming them as appropriate as they are added to the new tree.</span></span> <span data-ttu-id="2adfc-125">İşlevsel yaklaşım aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="2adfc-125">The functional approach looks like the following:</span></span>  
  
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
  
 <span data-ttu-id="2adfc-126">Bu örnekte, ilk örnekle aynı XML çıkarır.</span><span class="sxs-lookup"><span data-stu-id="2adfc-126">This example outputs the same XML as the first example.</span></span> <span data-ttu-id="2adfc-127">Ancak, elde edilen işlevsel yaklaşım yeni XML yapısını gerçekten görebilirsiniz dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="2adfc-127">However, notice that you can actually see the resulting structure of the new XML in the functional approach.</span></span> <span data-ttu-id="2adfc-128">Oluşturulmasını gördüğünüz `Root` öğesinde, kodu çeker `Child1` kaynak ağacının ve kaynak ağacının öznitelikleri öğelere yeni ağacında dönüştüren kod öğesi.</span><span class="sxs-lookup"><span data-stu-id="2adfc-128">You can see the creation of the `Root` element, the code that pulls the `Child1` element from the source tree, and the code that transforms the attributes from the source tree to elements in the new tree.</span></span>  
  
 <span data-ttu-id="2adfc-129">İşlevsel örneği bu durumda ilk örnek kısa herhangi değil ve gerçekten daha kolay değildir.</span><span class="sxs-lookup"><span data-stu-id="2adfc-129">The functional example in this case is not any shorter than the first example, and it is not really any simpler.</span></span> <span data-ttu-id="2adfc-130">Ancak, bir XML ağacına yapmak için birçok değişiklik varsa, işlev olmayan bir yaklaşım oldukça karmaşık ve biraz geniş açılı olur.</span><span class="sxs-lookup"><span data-stu-id="2adfc-130">However, if you have many changes to make to an XML tree, the non functional approach will become quite complex and somewhat obtuse.</span></span> <span data-ttu-id="2adfc-131">Buna karşılık, işlevsel yaklaşım kullanırken, yalnızca form istenen XML, sorguları ve ifadeler, istenen içeriği çekmek uygun olarak eklemeye devam.</span><span class="sxs-lookup"><span data-stu-id="2adfc-131">In contrast, when using the functional approach, you still just form the desired XML, embedding queries and expressions as appropriate, to pull in the desired content.</span></span> <span data-ttu-id="2adfc-132">İşlevsel yaklaşım oluşturmanın kod üretir.</span><span class="sxs-lookup"><span data-stu-id="2adfc-132">The functional approach yields code that is easier to maintain.</span></span>  
  
 <span data-ttu-id="2adfc-133">Bu durumda işlevsel yaklaşım büyük olasılıkla oldukça ağaç işleme yaklaşım yanı sıra gerçekleştirecek değil dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="2adfc-133">Notice that in this case the functional approach probably would not perform quite as well as the tree manipulation approach.</span></span> <span data-ttu-id="2adfc-134">Ana sorunu işlevsel yaklaşım daha kısa süreli nesneleri oluşturmasıdır.</span><span class="sxs-lookup"><span data-stu-id="2adfc-134">The main issue is that the functional approach creates more short lived objects.</span></span> <span data-ttu-id="2adfc-135">Ancak işlevsel yaklaşım kullanarak büyük Programcı verimliliği için izin veriyorsa etkili bir düşüş olur.</span><span class="sxs-lookup"><span data-stu-id="2adfc-135">However, the tradeoff is an effective one if using the functional approach allows for greater programmer productivity.</span></span>  
  
 <span data-ttu-id="2adfc-136">Bu çok basit bir örneği, ancak felsefesi iki yaklaşım arasındaki farkı göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2adfc-136">This is a very simple example, but it serves to show the difference in philosophy between the two approaches.</span></span> <span data-ttu-id="2adfc-137">İşlevsel yaklaşım daha büyük XML belgelerini dönüştürmek için büyük üretkenlik artışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2adfc-137">The functional approach yields greater productivity gains for transforming larger XML documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2adfc-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2adfc-138">See also</span></span>
- [<span data-ttu-id="2adfc-139">(LINQ to XML) XML ağaçlarını değiştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2adfc-139">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
